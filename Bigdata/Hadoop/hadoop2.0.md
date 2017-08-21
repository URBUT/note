###Hadoop의 특징

Fault Tolerance


#### CAP Theorem
>분산시스템에서 일관성(Consistency), 가용성(Availability), 분할 용인(Partition Tolerance) 이라는 세 가지 조건을 모두 만족할 수 없다.

![CAP Theorem](http://eincs.com/images/2013/06/truth-of-cap-theorem-diagram.png)

[StackOverFlow질문: CAP theorem - Availability and Partition Tolerance](https://stackoverflow.com/questions/12346326/cap-theorem-availability-and-partition-tolerance)

```
Answer :  
Consistency means that data is the same across the cluster, so you can read or write to/from any node and get the same data.

Availability means the ability to access the cluster even if a node in the cluster goes down.

Partition Tolerance means that the cluster continues to function even if there is a "partition" (communications break) between two nodes (both nodes are up, but can't communicate).

In order to get both availability and partition tolerance, you have to give up consistency. Consider if you have two nodes, X and Y, in a master-master setup. Now, there is a break between network comms in X and Y, so they can't synch updates. At this point you can either:

A) Allow the nodes to get out of sync (giving up consistency), or

B) Consider the cluster to be "down" (giving up availability)


All the combinations available are:

CA - data is consistent between all nodes - as long as all nodes are online - and you can read/write from any node and be sure that the data is the same, but if you ever develop a partition between nodes, the data will be out of sync (and won't re-sync once the partition is resolved).

CP - data is consistent between all nodes, and maintains partition tolerance (preventing data desync) by becoming unavailable when a node goes down.

AP - nodes remain online even if they can't communicate with each other and will resync data once the partition is resolved, but you aren't guaranteed that all nodes will have the same data (either during or after the partition)
You should note that CA systems don't practically exist (even if some systems claim to be so).
```

```
내 해석 :
Consistency(일관성) : 클러스터 내에서 데이터가 모두 동일한 것, 즉 어느 노드에서든 읽거나 혹은 썼을 때 클러스터 내의 데이터는 동일하다.
Availability(가용성) : 클러스터 하나가 죽더라도 다른 클러스터에서 읽기와 쓰기가 가능하다.
Partition Tolerance(분할 용인) : 두 노드 사이가 분리가 되었더라도, 클러스터 기능은 유지가 된다.(시스템은 물리적인 네트워크 파티션을 넘어서도 잘 동작하여야 한다.)
```

CAP 이론에 따르면 위 3가지 중에 동시에 2가지만 보장할 수 있고 3개를 모두 보장하는 것이 불가능하다고 나와있다.
그래서 데이터를 관리할 때 이 3가지 중에 어느 2가지에 중점을 두냐는 것은 아주 중요한 부분이다.
이 부분을 이해하는데 [Nathan Hurst](http://blog.nahurst.com/)이 만든 아래의 [Visual Guide to NoSQL Sytems](http://blog.nahurst.com/visual-guide-to-nosql-systems)는 큰 도움이 된다.
![Nathan Hurst NoSQL Sys, CAP](https://blog.outsider.ne.kr/attach/1/550x412x1153500148.png.pagespeed.ic.qpvvoA4tBw.webp)

기존에 많이 사용하던 **RDBMS는 3가지 중 CA에 집중**하고 있다. 웹이 발전하면서 다양한 요구사항이 생겨나고 엄청난 양의 데이터를 처리해야 하게 되면서 RDBMS가 갖지 못한 P의 특성이 필요해졌고 그러면서 등장한 것이 NoSQL이다.