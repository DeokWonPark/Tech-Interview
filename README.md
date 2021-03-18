

# Tech Interview

</br></br>





<img src="https://uxwing.com/wp-content/themes/uxwing/download/07-design-and-development/administrator-developer.png" width="300px" />



</br>

### Introduce

제가 웹 프론트엔드 개발자로 취업을 준비하며 배운 유용한 지식과, 기업의 기술면접을 준비하며 다른 블로그나 깃허브 저장소를 참고하고 저만의 생각을 포함하여 정리한 개념,  실제로 면접때 받은 질문들을 모아 도움이 되도록 정리한 저장소입니다.



</br></br></br>



### Contents

- [자료구조](#자료구조)
- [HTTP](#HTTP)
- [동기/비동기](#동기/비동기)
- [쓰레드/프로세스](#쓰레드/프로세스)
- [Restful API](#Restful-API)
- [메시지 큐](#메시지-큐)
- [동시성 이슈](#동시성-이슈)
- [Garbage Collection](#Garbage-Collection)
- [테스트 코드](#테스트-코드)
- [리팩토링](#리팩토링)



</br></br></br>



#### 자료구조





----

</br></br></br>

#### HTTP

HTTP란 `Hyper Text Transfer Protocol` 의 약자로 웹 상에서 웹 브라우저와 같은 클라이언트와 웹 서버간 통신을 위해 정해진 통신 규약이다.

네트워크 최상위 계층  Application Layer에서 사용되는 프로토콜이며 비연결형 프로토콜이다.

</br></br>

- 요청방식

  - GET 방식

    요청 데이터가 `HTTP Request Message Header`에 포함되어 전송된다.

    url에 request data가 포함되어 전송되는 방식이기 때문에 전송할 데이터의 크기가 제한적이며, 보안에 취약하다.

    **서버에서 데이터를 읽어오는 용도로 사용된다.**

  - POST 방식

    요청 데이터가 `HTTP Request Message Body`에 포함되어 전송된다.

    전송가능한 데이터의 크기가 GET방식보다 크다.

    **서버에 데이터를 수정하거나, 추가하는 용도로 사용된다.**

</br></br>

- 응답코드 정리
  - 1xx : 서버에서 사용자의 요청을 정상적으로 받았지만, 아직 제대로된 응답을 할 수 없는 상태
  - 2xx: success 성공적인 응답
  - 3xx: 서버에서 사용자의 요청을 제대로 받았고, 처리를 완료하기위해 페이지의 리다이렉션이 필요한 상태
  - 4xx: 서버로 전달된 올바르지 않은 요청
  - 5xx: 사용자의 올바른 요청에 웹서버가 제대로된 응답을 할 수 없는 상태

</br></br>

- TCP와 UDP 비교 정리
  - UDP (User Datagram Protocol)
    - 비연결형 프로토콜
    - 오류제어를 하지 않기 때문에 오류가 발생되어 누락된 세그먼트나, 손상된 세그먼트에 대한 재전송을 하지 않는다.
    - TCP에 비해 연결작업이 필요 없으므로 빠르다.
  - TCP (Transmission Control Protocol)
    - 연결형 프로토콜
    - 3-way handshake를 통한 두 종단점 간의 연결 설정을 통한 송신지 부터 수신지 노드까지 순차적이고, 신뢰성있는 데이터 전송



</br></br>

- HTTPS

  - HTTP의 보안상 문제
    - 평문 통신으로 이루어지기 때문에 도청 발생 가능
    - 서로의 통신 상대를 확인 할 수 없어 위장 및 변조 가능

  

  따라서 HTTP에 SSL을 조합하여 통신내용을 암호화 => HTTPS

  - HTTP
    - HTTP -> TCP (직접통신)
  - HTTPS
    - HTTP -> SSL -> TCP (보안계층을 추가)

</br></br>

- 모든 웹 페이지에서 HTTPS를 사용하지 않는 이유

  평문 통신에 비해서 암호화 통신은 CPU나 메모리등 리소스가 많이 필요하게 된다. 따라서 많은 리소스 소모는 웹 서버 한대당 처리 할 수 있는 request 수를 감소시키므로 보안이 필요한 곳에서 사용하는 것이 좋다.