### 클라이언트 서버 구조
* 컴퓨터 네트워크에서 가장 기본적인 아키텍처 중 하나이다.
* 클라이언트는 서비스를 요청하고, 서버는 요청된 서비스를 제공한다.

### 상태유지, 무상태
* 상태유지(Stateful)
  * 클라이언트와 서버 간의 통신에서 서버가 클라이언트의 상태 정보를 계속해서 유지하는 것을 의미한다.
* 무상태(Stateless)
  * 클라이언트와 서버 간의 통신에서 서버가 클라이언트의 상태 =정보를 유지하지 않는 것을 의미한다.
* 무상태 방식은 서버의 부담을 중리고, 확장성이 좋지만, 클라이언트의 상태 정보를 다루는 일이 필요한 경우에는 상태유지 방식이 사용됩니다. 상태유지 방식은 상태 정보를 유지하는 비용이 들지만, 상태 정보를 활용하여 개인화된 서비스를 제공할 수 있으며, 보안 등의 이유로 사용자의 상태 정보를 유지해야 하는 경우에도 적합하다.

### 비 연결성
* 클라이언트와 서버 간의 통신에서 연결을 맺고 유지하지 않고, 각각의 요청과 응답을 독립적으로 처리하는 것을 의미한다.
* 클라이언트는 서버에 요청을 보내고, 서버는 해당 요청을 처리하고 응답을 보내면 클라이언트와의 연결을 끊는다.

### HTTP MESSAGE
* 요청메시지와 응답 메시지로 나뉘어 진다.
  * 요청 메시지
    * 요청 라인 : 요청 라인은 요청 메서드, 요청 URI, HTTP 버전 정보로 구성된다. 예를들어 GET /index.html HTTP/1.1과 같이 구성됨
    * 헤더 : 헤더는 요청 메시지에 대한 부가적인 정보를 제공한다. 예를들어 요청 메시지의 인증 정보, 요청한 콘텐츠의 타입, 캐시 정책 등이 포함된다.
    * 본문 : 요청 본문은 요청 메시지에 대한 추가적인 데이터를 포함한다. 예를 들어 HTTP POST 요청에서는 폼 데이터나 파일 업로드와 같은 데이터가 요청 본문에 담겨서 전송된다.
  * 응답 메시지
    * 상태 라인 : 상태 라인은 HTTP 버전 정보, 상태 코드, 상태 메시지로 구성된다. 예를 들어 HTTP/1.1 200 OK와 같이 구성된다.
    * 헤더 : 헤더는 응답 메시지에 대한 부가적인 정보를 제공합니다. 예를 들어 응답 콘텐츠의 타입, 캐시 제어 정책, 서버 정보 등이 포함됩니다.
