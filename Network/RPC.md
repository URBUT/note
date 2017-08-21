### RPC 동작원리(mechanism)

RPC(Remote Procedure Call)은 동적으로 서비스와 포트를 연결할 때 사용하는 방법이다.

기본적으로 포트와 서비스가 정적으로 구성될 때는 /etc/services 파일을 참조하지만 동적으로 포트를 할당받아 사용할 때는 RPC를 담당하는 데몬인 rpcbind를 사용한다.

1. 동적으로 포트를 할당받기 위한 원격서비스는 rpcbind를 접속한다.

2. 접속 후 서비스를 위해 포트번호를 할당받도록 요구한다.

3. rpcbind는 현재 시스템에서 사용되지 않고 있는 포트번호를 RPC를 이용하여 요청한 시스템에 전달하고, 그 포트번호를 자신이 동작하는 시스템의 해당 서비스에 할당한다.

4. 할당받은 포트를 사용하여 다시 패킷을 수신할 시스템에 서비스를 요청한다.

5. 서비스 요청을 받은 시스템은 포트번호에 해당하는 서비스를 처리할 프로그램에 패킷을 전달한다.


참고#1

RPC를 이용하여 포트번호를 할당할때 현재 사용하지 않는 포트번호가 아닌 번호를 이미 정해진 포트번호를
사용하는 경우도 있다. rpcbind 데몬이 실행을 시작할때 /etc/rpc 파일을 읽어서 명시된 바에 따라 서비스와 포트 번호를 할당한다.


참고#2

서비스를 요청한 시스템과 서비스를 제공하는 시스템과의 포트번호 변환방법은 동일 해야 한다.
즉, 서비스를 요청한 시스템이 /etc/services파일을 사용하면 서비스를 제공한 시스템도 /etc/services를
사용하여야 한다. RPC도 마찬가지이다.