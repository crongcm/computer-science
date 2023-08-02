# Network

## OSI 7 Layer
    
- application layer - 어플리케이션 목적에 맞는 통신 방법을 제공 (HTTP, DNS, STMP, FTP)
- presentation layer - 어플리케이션 간의 통신에서 메세지 포맷 관리 (인코딩 - 디코딩, 암호화 - 복호화, 압축 - 압출풀기)
- session layer - RPC(remote procedure call)
- transport layer - 어플리케이션 간의 통신담당<br/>목적지 어플리케이션으로 데이터 전송 (TCP, UDP)
- network layer - 호스트 간의 통신 담당(IP)<br/>목적지 호스트로 데이터 전송, 네트워크 간의 최적의 경로 결정
- data link layer - 직접 연결된 노드 간의 통신 담당<br/>MAC 주소 기반 통신 (ARP)
- physical layer - bits 단위로 데이터 전송

## Socket
    
<img src="image/socket%201.png" width="700">

<img src="image/socket%202.png" width="700">

<img src="image/socket%203.png" width="700">

<img src="image/socket%204.png" width="700">

### TCP socket 동작 방식

1. 클라이언트 쪽에서 먼저 서버쪽으로 요청을 보내야한다.
2. 서버는 connection 맺는 요청을 기다리는 listening socket
3. 클라이언트에서 connection을 맺자는 요청을 하면 3-way-handshake를 통해 커넥션을 맺는 과정을 진행한다
4. 커넥션이 성립되고나면 서버쪽에서 새로운 소켓을 만들고 해당 소켓으로 클라이언트와 데이터를 주고 받는다
5. 다른 클라이언트에서 connection을 맺자는 요청을 하면 3-way-handshake를 통해 커넥션을 맺는 과정을 진행한다
6. 또 새로운 별도의 소켓을 만들고 해당 소켓으로 클라이언트와 데이터를 주고 받는다
7. 세 개의 TCP 소켓이 모두 같은 IP address, port number를 가진다

<img src="image/socket%205.png" width="700">

- connection 연결 요청 : listening socket으로 연결 요청
- connection이 성립된 이후 : <src IP, src port, dest IP, dest port>로 socket 식별

❓클라이언트 쪽에서도 같은 IP와 port를 가지는 서로 다른 TCP 소켓이 생길 수 있을까 ? YES !

결론 <src IP, src port, dest IP, dest port>로 socket 식별

<img src="image/socket%206.png" width="700">

### Port number

- 16bit로 이루어진 숫자 (0 ~ 65535)
- 0 ~ 1023 : well-known ports, system port
    - e.g.) HTTP(80), HTTPS(443), DNS(53)
- 1024 ~ 49151 : registered ports (IANA에 등록된 번호)
    - e.g.) MySQL DB(3306), Apache tomcat server(8080)
- 49152 ~ 65535 : dynamic ports (등록 안된 번호, 임시로 혹은 자동 할당될 때 사용)

<img src="image/socket%207.png" width="700">

## Reference
[쉬운코드](https://www.youtube.com/@ez.)
[널널한 개발자 TV](https://www.youtube.com/@nullnull_not_eq_null)
