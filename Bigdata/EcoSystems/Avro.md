### Avro 포맷

[Avro](http://www-01.ibm.com/software/data/infosphere/hadoop/avro/) 는 데이터 저장 포맷이다.
데이터 직렬화를 네트워크를 통해 전송하거나 몇몇 영구 저장 매체에 저장 될 수있는 바이너리 또는 txt 형태로 (메모리 버퍼, 데이터 구조 또는 개체의 상태와 같은) 컴퓨터 환경에 데이터를 변환하는 tool이다.
Avro는 schema-based system이다.
JSON을 이용해서 구조를 정의하며
전송 또는 저장 데이터의 포맷을 정의한다.
기본적으로 binary 구조의 데이터와 JSON 구조의 데이터 통신 Schema 를 지원한다

Avro는 Thrift와 비슷한 기능을 대부분 지원하며, 구글의 프로토콜 버퍼와 같은 RPC(Remote Procedure Call)[^1] 메커니즘과 데이터 직렬화를 제공한다.

Avro는 Thrift보다 확실한 장점이 있는데, 특히 application에서 RPC를 사용하기 위해 필요한 정적 코드 생성을 하지 않아도 된다.

[^1] : RPC : 동적으로 서비스와 포트를 연결할 떄 사용하는 방법.
@import "../../Network/RPC.md"


### Parquet 포맷

Parquet파일은 하둡에서 컬럼 기반 스토리지를 제공하는 오픈소스 파일 포맷이다.
[parquet 설명](http://myownopinions.tistory.com/2)


### Arrow 포맷

[Apache Arrow 설명 및 Parquet 부가설명](http://www.hanbit.co.kr/media/channel/view.html?cms_code=CMS9615655185)
