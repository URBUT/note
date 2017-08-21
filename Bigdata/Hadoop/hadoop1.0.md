##YARN
하둡2.0의 리소스 관리 플랫폼인 YARN은 하둡 클러스터의 각 어플리케이션에 필요한 리소스를 할당하고 모니터링하는 업무에 집중함으로써 다양한 어플리케이션이 하둡 클러스터의 리소스를 공유할 수 있도록 하는 핵심 요소이다.
![yarn](http://cfile10.uf.tistory.com/image/22704C4853DF17AE1B74C5)

하둡1에서는 하나의 클러스터에서 다양한 하둡 에코시스템이 적재적소에 시스템 자원을 할당받고, 할당된 자원이 모니터링되고 해제되어야 하는데, 하둡1에는 기능 부재.

또한 하둡의 `SPOF(Single Point Of Failure, 단일고장점)`인 네임노드의 이중화 문제는 단골 소재가 됐고, 데이터노드 블록들이 하나의 `네임스페이스`만 사용하는 데 따른 단점과 성능 개선 요청이 있었다.

###하둡2 주요 개선 기능
- YARN
- Namenode High-Availability
- HDFS Federation
- HDFS SNAPSHOT
- NFSv3 FS support
- 성능 개선

####YARN
######JobTracker를 Resource Manager와 Application Master로 분리
하둡 1.0 MapReduce 프레임워크의 JobTracker는 두가지 기능을 수행하고 있다.
하나는 **클러스터 전체의 리소스 관리**이고 다른 하나는 **여러 잡(Job)을 수행하면서 그것들이 성공적으로 끝날때까지 관리**해주는 것이다.

이를 YARN에서는 `Resource Manager`와 `Application Master` 두개로 분리하였다.
YARN 클러스터마다 Applcation Master라는 것이 존재하고 클러스터 내의 각 서버마다  Node Manager가 존재한다.
이런 분산환경 위에서 실행되는 잡(Job)마다 하나의 서버가 Application Master로 실행되어 해당 잡(Job)에 필요한 자원을 Resource Manager로부터 받아내고 해당 잡(Job)내의 태스크(Task)들을 관리하는 역할을 하게 된다.

######효율적인 자원 관리
하둡 1.0에서는 MapReduce가 돌 때, Mapper와 Reducer가 따로 설정되다 보니, Mapper가 모두 동작하지만 Reducer는 놀고 있는 케이스가 발생한다.
즉, 클러스터 전체의 사용률이 굉장히 낮았다.
하둡 2.0에서는 Mapper와 Reducer 둘다 컨테이너 안에서 동작하며 컨테이너 자체도 따로 슬롯이 있는 것이 아니라 전체 클러스터의 리소스 상황과 요청된 잡(Job)의 리소스 요구에 따라 Container가 몇 개나 실행될 지 등이 결정된다.

## 하둡 1.0
### 하둡 1.0 구성요소
![hadoop-1.0](https://kmongcom.files.wordpress.com/2014/03/hadoop_diagram.png?w=584&h=340)
HDFS/MapReduce.

#####Namenode
하둡은 Master/Slave 구조를 가진다.
Namenode는 HDFS에서 마스터 역할을 하며, 슬레이브 역할을 하는 Datanode에게 I/O 작업을 할당한다.
Namenode는 메타데이터를 관리하기 위해 `EditLog` 와 `FsImage` 파일을 사용한다.
**하둡 1.0에서는 Namenode는 이중화 구성을 할 수 없어서 하둡 클러스터를 운영할 때 SPOF(단일고장점)가 된다.**

네임노드는 시스템의 메타데이터와 블록에 대한 위치정보를 메모리에 유지한다. 네임노드는 드라이브 문제로 인한 데이터 손실을 막기 위해 RAID 드라이브를 사용해야 한다.

네임노드는 HDFS에 저장된 파일의 블록에 대한 매핑정보를 메모리에 유지하므로 블록이 많아질 수록 성능이 느려질 수 있다.
따라서 블록사이즈를 크게 하면 매핑정보가 그만큼 줄어들게 된다. 반면에 블록 사이즈가 커지면 맵리듀스에서 병렬적으로 처리할 수 있는 태스크의 개수가 작아지므로, 입력 파일의 사이즈가 작은 경우 Job 프로그램의 실행속도가 느려질 수도 있다.

![Namenode_SecondaryNamenode](https://kmongcom.files.wordpress.com/2014/03/secodary-name-node.png?w=467&h=506)

