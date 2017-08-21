## 톰캣 메모리 설정

###==JVM 구조==

![JVM Memory Model](http://cfile2.uf.tistory.com/image/276BA941552BBB1928C4DE)

Heap 영역 : Object들이 저장되는 공간.
예를 들어 아래와 같은 코드가 있을 때,
```java
Member member = new Member();
```
여기서 new 명령을 통해 생성된 Member Instance가 Heap 영역에 저장된다.
그리고 `member` 참조 변수는 생성된 Instance의 Heap 영역을 가리키며, Stack 영역에 저장된다.
즉, `Java.lang.OutOfMemoryError : Java Heap Space` 에러는 할당된 영역에 Object들이 꽉 찼다는 의미이다.

Permanent 영역은 Class들의 정보가 저장되는 곳이다.
Permanent 영역은 JVM 객체의 생명주기가 길다고 판단되는 객체들을 이 영역에 할당하며, Permanent 영역에 있는 객체들은 GC(Garbatge Collector)의 대상에서 제외된다.

```
-Xms<size>
: Java Heap의 최소 크기값
-Xmx<size>
: Java Heap의 최대 크기값
-XX:PermSize=<size>
: Permanent Generation의 최초 크기 지정
-XX:MaxPermSize=<size>
: Permanent Generation의 최대 크기 지정
```

###==메모리 옵션==
JVM 메모리 튜닝은 매우 중요하다. 결국 Full GC 시간을 줄이는 것이 관건인데, 큰 요구 사항만 없다면, 전체 Heap Size는 1G 정도가 적당하다. 그리고 PermSize는 위에 말했듯이, Class들의 정보가 로딩되는 공간인데, 배포하고자 하는 Application이 엄청 크지 않다면, 128m 정도면 적당하다. (보통은 256m를 넘지 않는다.)
그리고 Heap size는 JVM에서 자동으로 늘리거나 줄일 수가 있다. 그래서 `-Xms`와 `-Xmx`로 최소, 최대 Heap size를 정할 수 있는데, Server 시스템의 경우 항상 최대 메모리로 잡아 놓는 것이 좋다.
메모리가 늘어난다는 것은 부하가 늘어난다는 것이고, 부하가 늘어날 때 메모리를 늘리는 작업 자체가 새로운 부하가 될 수 있기 때문에, 같은 값을 사용하는 것이 좋다.
이렇게 JVM 메모리를 튜닝하면 다음과 같은 옵션이 된다.
>-Xmx1024m -Xms1024m -XX:MaxNewSize=384m -XX:MaxPermSize=128m

이렇게 하면 전체 메모리 사용량은 Heap 1024m (이 중에 new가 384m) 그리고 perm이 128m이 되고, JVM 자체가 사용하는 메모리가 보통 300~500m 내외가 되서 java process가 사용하는 메모리 량은 1024 + 128 + 300~500 = 1.5G 정도가 된다.

###==Out Of Memory(OOM)==
자바 어플리케이션에서 주로 문제가 되는 것 중 하나가 Out Of Memory 에러다. JVM이 메모리를 자동으로 관리해줌에도 불구하고, 이런 문제가 발생하는 원인은 사용이 끝난 객체를 release하지 않는 경우이다. 예를 들어 static 변수를 통해서 대규모 array나 hashmap을 reference하고 있으면, GC가 되지 않고 계속 메모리를 점유해서 결과적으로 Out Of Memory 에러를 만들어낸다.
Out Of Memory 에러를 추적하기 위해서는 그 순간의 Memory layout인 Heap Dump가 필요한데, 이 옵션을 적용해놓으면 Out Of Memory가 나올 때 순간적으로 Heap Dump를 떠서 파일로 저장해놓기 때문에, 장애 발생시 추적이 용이하다.
>-XX:-HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=./java_pid<pid>.hprof

###==GC Option==
Memory 옵션만큼이나 중요한 GC Option이다.
Parallel GC + Concurrent GC는 요즘 거의 공식처럼 사용된다.
이 때 Paraleel GC에 대한 Thread 수를 정해야 하는데, 이 Thread 수는 전체 CPU Core 수보다는 적어야 하고, 2~4개 정도가 적당하다.
>-XX:ParallelGCThreads=2 -XX:-UseConcMarkSweepGCp

###### GC Log 옵션
서버와 JVM이 건강한지 메모리상 문제는 없는지 GC 상황은 어떻게 되는지를 추적하기 위해서는 GC Log를 되도록 자세하게 추출할 필요가 있다.
*GC Log를 상세하게 걸어놓아도 성능저하는 거의 없다.
>-XX:-PrintGC -XX:-PrintGCDetails -XX:-PrintGCTimeStamps -XX:-TraceClassUnloading -XX:-TraceClassLoading

마지막에 적용된 TraceClassLoading은 Class가 Loading되는 순간 Log를 남긴다. 일반적으로 사용하지 않아도 되나, OutOfMemory 에러 발생시 Object가 아니라 Class에서 발생하는 경우는 Heap dump로는 분석이 불가능하기 때문에, Out Of Memory 에러 시 같이 사용함녀 좋다.