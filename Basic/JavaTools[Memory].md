자바 어플리케이션을 개발하다 보면, OutOfMemoryError (또는 OutOfMemoryException, 이하 OOM)을 종종 만나게 된다.
이 때 도대체 어디서 문제가 생기는 것인지 발견하기 어렵다.

그래서 다음의 `JavaTool`에 대해서 알아보자.
```
javac - Java Source Code -> ByteCode로 compile
java   - ByteCode 실행
```
위 명령어들은 java를 처음에 배울 때 IDE 없이 cmd창 혹은 terminal 창에서 HelloWorld와 함께 입력해봤을만한 명령어다.

1. jps
>>
jps 는 unix 명령어인 ps와 같이 실행 중인 java process를 보여주는 tool이다.
일반적으로 ps 명령어와 grep 명령어의 조합으로 실행 중인 java process를 찾을 수도 있지만 jps를 사용하면 좀더 편하다.
>>


2. jstat

3. jmap

4. jhat

```
$JAVA_HOME/bin/jstack [PID]                  // JVM Stack Trace [ Hotspot JDK ]  (daed lock 분석)

$ kill -3 [PID]                              // JVM Stack Trace & Heap Dump [IBM JDK]  (daed lock 분석)

$ jmap -dump:format=b,file=heap.hprof [pid]  // runtime heap dump [ Hotspot JDK ]

$ jstat -gc -h20 [PID] 3000                  // JVM Heap 사용량 및 GC(garbage collection) 통계

$ ps -mo pid,lwp,stime,time,pcpu -C java | more  // java 프로세스의 쓰레드별 CPU 사용량 확인
```
