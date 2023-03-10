### IP(Internet Protocol)
#### 인터넷 프로토콜 역할
* 지정한 IP주소에 데이터를 전달한다.
* 패킷(Packet)이라는 통신 단위로 데이터를 전달한다.
  * IP 패킷 정보에는 출발지IP, 목적지IP, 그리고 전송 데이터 등등이 존재한다.
* 인터넷 안에있는 노드들을 통해 전달한다.
#### IP 프로토콜의 한계
* 비연결성
  * 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷을 전송한다.
* 비신뢰성
  * 중간에 패킷이 사라질 수 있다.
  * 패킷이 순서대로 전달이 안될 수 있다.
* 프로그램 구분
  * 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상일 수 있다.

### TCP/UDP
#### TCP 특징
* 연결지향 - TCP 3 handshake (가상 연결)
  * 1. 클라이언트가 서버에게 접속 요청을 한다.
  * 2. 서버가 확인하면 클라이언트에게 접속요청과,요청수락을 한번에 한다.
  * 3. 그리고 다시 클라이언트가 요청 수락을 한다.
  * 4. 데이터를 전송한다.
  * %. 3번 과정에서 데이터를 같이 전송할 수 있다.
* 데이터 전달 보증
* 순서 보장
  * 패킷 1,2,3 순서대로 서버에게 보냈지만 만약 서버가 1,3,2 순서대로 받았다면 클라이언트에게 패킷2번부터 다시 보내라고 한다.
* 신뢰할 수 있는 프로토콜
* 현재는 대부분 TCP를 사용한다.
#### UDP 특징
* 하얀 도와지랑 같다 (기능의 거의 없음)
* 연결지향 - TCP 3 way handshake 가 없다.
* 데이터 전달 보증이 되지 않는다.
* 순서 보장 안된다.
* 데이터 전달 및 순서 보장이 되지 않지만, 속도가 빠른다.
  * IP와 거의 같다, +PORT, +체크섬 기능정도만 추가되었다.
  * 애플리케이션에서 추가 작업을 해야한다.

### PORT
* 만약 한 클라이언트에서 여러개의 애플리케이션이 열려 있다면 서버는 어떤 애플리케이션에 패킷을 보내야할지 모를것이다. 이때 포트를사용한다.
* IP는 무슨 아파트이고 PORT 는 몇동 몇호 인지라고 생각하면 이해하기 쉽다
* 패킷에 출발지 IP,PORT 도착지 IP,PORT 를 적는다.
<br>

* 0 ~ 65535 할당 가능
* 0 ~ 102 : 잘 알려진 포트, 사용하지 않는게 좋다.
 * FTP - 20,21
 * TELNET - 23
 * HTTP - 80
 * HTTPS - 443

### DNS ( Domain Name System )
* 아이피는 1.23.123.4.125.1 처럼 기억하기 어렵다. 그리고 IP가 변경된다면 클라이언트는 엉뚱한 곳에 패킷을 보낼 수 있다. 따라서 DNS를 쓴다.
* 우리가 흔히 사용하는 naver.com과 같은 사이트도 원래 아이피로 연결을 해야하지만 외우기 힘드니까 DNS라는것을 쓴다.
* 도메인 명에 아이피를 적어놓고 만약 도메인에 접속하면 클라이언트에게 아이피 주소를 받고 다시 그 아이피를 통해 서버에 통신한다.
* 아이피가 변경되어도 도메인에대한 아이피만 변경하면 되기때문에 편리하다.



#### 지금까지
지금까지 HTTP 를 배우기 위한 기본적인 지식을 알아봤다. 들어는 봤지만 무슨 역할을 하는지 몰랐는데 공부를 하고 틀이 잡힌것 같다.
