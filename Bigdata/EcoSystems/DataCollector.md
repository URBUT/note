#### 데이터의 수집방법
모델 구축을 위해서는 대량의 데이터가 반드시 필요하여 이를 위해 대표적인 수집을 위한 오픈소스 툴로 `Flume`, `Sqoop`, `Kafka` 등이 있다.
File, RDB의 데이터를 수집하기 위해서는 Sqoop, Gobblin 등이 있으며
그 외의 Event 기반 데이터는 Flume 을 사용하여 수집할 수 있으며
메시지 유실, 분산처리 scale out 을 위해서 Kafka를 사용할 수 있다.

### Flume

Source-Channel-Sink의 구조로 이루어져 있다. 이미 다양한 유형의 데이터에 대해서 Source, Sink 등이 구현되어 있어 손쉽게
데이터를 가져다 사용할 수 있으며 필요한 부분은 사용자 구미에 맞게 코딩할 수 있다.

---
### Kafka

Kafka는 pub/sub 구조의 message queue로 볼 수 있는데, 저장소로 Disk 공간을 쓰는 것이 특징이다.
따라서 메시지 유실이 되지 안흔 것을 최우선으로 하는 시스템에서 사용한다.
