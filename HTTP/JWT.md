출처 : https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC#jwt_json_web_token_%EC%9D%B4%EB%9E%80

### JWT (json web token) 이란
* JWT(JSON WEB TOKEN)란 인증에 필요한 정보들을 암호화시킨 JSON 토큰이다.
* JWT기반 인증은 JWT토큰을 HTTP헤더에 실어 서버가 클라이언트를 식별하는 방식이다.
* JWT는 JSON 데이터를 Base64 URLL-safe Encode를 통해 인코딩ㅎ여 직렬화한 것이며, 토큰 내부에는 위변조 방식을 위해 전자서명도 포함돼 있다.
* JWT를 서버로 전송하면 서버는 서명을 검증하는 과정을 거치게 되며 검정이 완료되면 요청한 응답을 돌려준다.
###### Base64 URL-safe Encode 는 일반적은 Base64 Encode 에서 URL 에서 오류없이 사용하도록 '+', '/' 를 각각 '-','_'로 표현한 것이다.

### JWT 구조
* JWT는 . 을 구분자로 나누어지는 세 가지 문자열의 조합이다.
* . 을 기준으로 좌측부터 Header.Payload.Signature 을 의미한다.
* Header에는 JWT에서 사용할 타입과 해시 알고리즘을 포함한고 Payload는 서버에서 첨부한 사용자 권한 정보와 데이터가 담겨있다.
* Signature에는 Header,Payload를 Base64 URL-safe Encode 를 한 이후 Header에 명시된 해시함수를 적용하고, 개인키로 서명한 전자서명이 담겨있다.
