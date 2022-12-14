## HTTP 프로토콜이 무엇인가요?
##### HTTP 프로토콜이란?
- HTTP는 Hypertext Transfer Protocol의 약자
- 인터넷상에서 데이터를 주고 받기 위한 서버/클라이언트 모델을 따르는 프로토콜
  > 프로토콜이란?
  > - 컴퓨터 내부 혹은 사이에서 데이터의 교환 방식을 정의하는 규칙 체계
- 애플리케이션 레벨의 프로토콜로써 **TCP/IP위에서 작동한다**
- HTTP로 보낼 수 있는 데이터는 **HTML문서, 이미지, 동영상, 오디오 등 여러 종류**가 있으며,
  **어떤 종류의 데이터**라도 전송할 수 있게 설계되었다
- Hypertext 기반으로 데이터를 전송하므로, **링크를 기반으로 데이터에 접속하겠다**는 의미가 된다

##### 작동방식
- 클라이언트에서 요청(request)을 보내면, 서버에서 요청을 처리한 뒤 응답(response)한다
  - 클라이언트
    - 서버에 요청을 보내는 클라이언트 소프트웨어가 설치된 컴퓨터를 의미
      IE, Chrome, Safari, Edge 등이 있다
    - **URI를 이용**하여 서버에 접속하고, 데이터를 요청할 수 있다
  - 서버
    - 클라이언트의 요청을 받아 응답을 하는 소프트웨어가 설치된 컴퓨터를 의미
      Apache, nginx 등이 있다
    - 표준포트로 80번 포트를 서비스한다

##### 무연결성(Connectionless)과 무상태성(Stateless)
- 무연결성(Connectionless)
  - 서버와 클라이언트 간의 통신 절차는 **연결 수립 => 요청 => 응답 => 연결 제거** 순으로 이루어진다
  - 응답이 완료되면 클라이언트와 서버의 연결은 끊어지게 된다
- 무상태성(Stateless)
  - 서버는 클라이언트가 이전에 요청을 보냈던 클라이언트인지 구분하지 못한다
  - 즉, **HTTP 요청은 독립적**이기 때문에 서버는 클라이언트의 상태를 기억하지 못한다
- 장점
  - 불특정 다수를 대상으로 하는 서비스에 적합하다
    서버와 클라이언트의 연결이 지속되지 않으므로, :star:서버-클라이언트 간 최대 연결 수보다 더 많은 요청 및 응답을 처리할 수 있기 때문!:star:
  - 접속유지를 최소한으로 할 수 있기 때문에 더 많은 요청을 처리할 수 있다
- 단점
  - 이전 상태 정보를 알 수 없기에 웹 서비스에 문제가 생기게 된다
  - 로그인 정보를 유지할 수 없으므로 쿠키(cookie)를 이용해서 문제를 해결한다
- 쿠키(Cookie)
  - 클라이언트와 서버의 상태 정보를 담고 있는 정보 조각
  - 로그인 문제를 쿠키로 해결하는 경우
    1. 로그인 성공 시 서버는 로그인 정보를 DB에 저장하며 쿠키를 클라이언트에 보낸다
    2. 다음 요청 시 클라이언트는 `header`에 쿠키 정보를 담아 요청한다
    3. 쿠키를 이용해 두 요청이 동일한 클라이언트에서 온 것인지 판단한다

##### URI(Uniform Resource Identifiers)
- 클라이언트 소프트웨어가 자원의 위치를 찾는데 사용
- HTTP와는 독립된 체계이다
  URI : 자원의 위치를 알려주는 프로토콜, HTTP : 전송 프로토콜
- EX) https://www.jinyong.com/example.php 이라 하자
  https : https 프로토콜을 사용하여 자원에 접근한다
  www.jinyong.com : 자원의 인터넷상에서의 위치
  example.php : 요청할 자원의 이름
- 즉, **프로토콜**, **위치**, **자원명**으로 자원이 어디에 있던지 접근할 수 있게 해준다

##### 메서드(Method)
- 요청의 종류를 서버에게 알려주기 위해서 사용한다
- 자원의 위치에 더하여 자원에 부여할 작업까지 명시할 수 있기 때문에 오픈 API에 많이 사용된다
  - GET : 정보를 요청할 때 사용(SELECT)
  - POST : 정보를 넣을 때 사용(INSERT)
  - PUT : 정보를 업데이트할 때 사용(UPDATE)
  - DELETE : 정보를 삭제할 때 사용(DELETE)
  - HEAD : (HTTP)헤더 정보만 요청, 해당 자원이 존재 여부 혹은 문제 여부를 확인할 때 사용
  - OPTIONS : 웹서버가 지원하는 메서드의 종류를 요청
  - TRACE : 클라이언트의 요청을 그대로 반환
- GET, POST 두 종류만으로 모든 종류의 요청을 표현할 수 있다