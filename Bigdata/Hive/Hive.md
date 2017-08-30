### 빅쿼리(BigQuery)

#### 데이터 타입
테이블에 저장될 수 있는 데이터 구조는 다음과 같다.
* STRING : UTF-8 encoding, 최대 2MB
* INTEGER : 64bit
* FLOAT : Double precision
* BOOLEAN
* RECORD : Collection of one or more field
* TIMESTAMP

특이한 것이 `RECORD` 라는 데이터 타입인데, 레코드는 JSON과 같이 여러개의 데이터를 가지는 데이터형을 말한다.

예시)
![record_type](http://cfile23.uf.tistory.com/image/244A644E576503AD058508)

이렇게 생성된 테이블의 구조는 다음과 같이 된다.

![record_table](http://cfile5.uf.tistory.com/image/2322F04E576503AF2556C0)

RECORD 형 데이터 타입 안에는 앞서 정의된 STRING, INTEGER 등의 데이터 타입으로 컬럼 정의가 가능하며, RECORD형 데이터 타입이 또 그 안에 들어갈 수 있다.
(JSON 형태과 매우 유사함)

---
### Hive Architecture

Hive는 Hadoop 클러스터에 저장된 데이터를 MR을 직접 구현하여 데이터를 분석하기엔 개발 스킬과 경험이 필요하며,
이를 이해하고 구현하는 시간과 노력을 줄이고자 보다 편리하게 데이터 분석이 가능하게 한다.

![Hive Architecture](http://hochul.net/blog/wp-content/uploads/2015/07/hive_architecture.png)

주요 구성요소를 보면
* JDBC/ODBC : SQL을 MR로 변환해주는 Query Compiler 및 실행 Engine
* UDF/UDAF : 직접 필요한 함수를 만들어 사용할 수 있음
* Metastore
  - HDFS 상의 데이터를 DB Table 형식으로 관리하기 위한 meta 정보, table, partitions, column 정보를 저장.
  - 임베디드 되어 있는 Apache Derby를 사용하거나 Local 또는 Remote의 RDBMS를 Metastore로 사용할 수 있다.
