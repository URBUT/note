## Cassandra의 특징
- - -
Cassandra는 scalability와 high availability에 최적화된 대표적인 분산형 Data Storage이다.

##### 장점
`Consistent hashing`을 이용한 Ring 구조와 Gossip protocol을 구현하였으며, 때문에 각 노드 장비들의 추가, 제거 등이 자유롭고 데이터센터까지 고려할 수 있는 데이터 복제 정책을 사용하여 안정성 측면에서 많은 장점을 가지고 있습니다. Cassandra를 이용하면 Sharding을 고려해야 할 필요도 없고 Master-Slave 와 같은 정책이 없이도 장애에 대응할 수 있으며, 필요에 따라 장비들을 늘리고 줄이는 데 큰 비용이 들지 않습니다.

quorom distributed system.

##### 단점
Cassandra는 Join이나 Transaction을 지원하지 않고 Index 등의 검색을 위한 기능도 매우 단촐합니다.
게다가 Cassandra의 구조상 RDBMS와 같은 Paging을 구현하는 것이 힘들고 KeySpace(RDBMS의 DB 같은)나 Table 등을 과도하게 생성할 경우 Memory Overflow가 발생할 수 있음을 고려해야 합니다.

###### Cassandra Ring
![Cassandra ring](http://image.toast.com/aaaadh/real/2016/techblog/apache2.png)

Cassandra는 기본적으로 Ring구조를 띠고 있다. 그리고 Ring을 구성하는 각 노드에 Data를 분산하여 저장한다.
그렇다면 데이터를 분산하는 기준을 무엇일까? `Partition Key`라고 불리는 데이터의 hash값을 기준으로 Data를 분산하게 된다.
처음 각 노드가 Ring에 참여하게 되면, Cassandra의 conf/cassandra.yaml에 정의된 각 설정을 통하여 각 노드마다 고
이렇게 계산된 partition key의 hash값을 `token` 이라고 한다.

http://d2.naver.com/helloworld/1039
