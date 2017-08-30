## Lambda Architecture for Bigdata

@import "../Language/Java/Java8.md"

![conceptMap](http://lambda-architecture.net/img/la-overview_small.png)

batch layer : 배치 작업을 통해 데이터 생산
servcing layer : 데이터 조회(view)
speed layer : 실시간 데이터 처리 등 데이터의 저장보다 데이터의 연산처리가 먼저 처리 된 후 조회 가능.

(1) 원천데이터 : Transaction data 혹은 Event Log 데이터가 될 수 있다.
(2) master dataset : HDFS에 저장되어있는 데이터들
(3) batch view : HDFS에 적재된 데이터를 MR 처리등을 통하여 결과값 추출
(4) real-time view : new data로부터 받은 데이터를 저장 없이 데이터 처리(HDFS에 적재는 실시간이 아니므로) & 데이터 저장을 위하여 HDFS 적재는 HBase/Redis/Cassandra 를 이용하여 병렬로 처리가 될 수 있다. 

Bigdata ecosystem을 이용하여 구축한다고 하였을 때 아키텍쳐는 아래의 도식으로 표현할 수 있다.

![bigdata Architecture](https://dzone.com/storage/temp/3361733-implemntation.png)


