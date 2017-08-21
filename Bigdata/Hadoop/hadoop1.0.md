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

참고 사이트 : https://kmongcom.wordpress.com/tag/hadoop/
