

# Tech Interview

</br></br>



<p align="center"> <img src="https://uxwing.com/wp-content/themes/uxwing/download/07-design-and-development/administrator-developer.png" width="300px" /></p>

</br>

## Introduce

제가 웹 프론트엔드 개발자로 취업을 준비하며 배운 유용한 지식과, 기업의 기술면접을 준비하며 다른 블로그나 깃허브 저장소를 참고하고 저만의 생각을 포함하여 정리한 개념,  실제로 면접때 받은 질문들을 모아 도움이 되도록 정리한 저장소입니다.



</br></br></br>



## Contents

- [자료구조](#자료구조)
- [HTTP](#HTTP)
- [동기/비동기](#동기/비동기)
- [쓰레드/프로세스](#쓰레드/프로세스)
- [Restful API](#Restful-API)
- [메시지 큐](#메시지-큐)
- [동시성 이슈](#동시성-이슈)
- [GarbageCollection](#Garbage-Collection)
- [테스트 코드](#테스트-코드)
- [리팩토링](#리팩토링)



</br></br></br>



### 자료구조

**자료구조란 ?**

상황에 맞게 데이터를 적절히 저장 할 수 있는 구조이다.

상황에 맞게 데이터에 효율적으로 접근하고, 조작하기 위한 방법

- 선형구조
  - Array, List, Stack, Queue ...
- 비선형구조
  - Tree, Graph ...

</br>



#### Array

- 연속적인 데이터 처리에 적합하다.
- 정적인 자료구조로 크기확장이 어렵다,
- index를 통해서 배열의 원소에 접근하기 때문에 index를 안다면 O(1)시간에 원소 접근이 가능하다.
- 데이터 삭제시 빈공간이 생기게 되어 공간의 낭비가 발생한다.



</br>

#### Linked List

자료항목 노드에 포인터 부분을 이용해서 노드를 연결시킨 자료구조

- 크기가 동적으로 변하기 때문에 크기에 구애받지 않는다.
- 데이터 삭제시 공간낭비가 발생하지 않는다.
- 특정한 원소를 찾기 위해 O(n) 시간이 발생한다.



</br>

#### Stack

선형자료구조이며 한쪽 끝에서 원소의 삽입 삭제가 이루어지는 자료구조이다. (LIFO)

</br>



#### Queue

선형 자료구조이며 리스트의 한쪽 끝에서 삽입이 이루어지고, 반대편 끝에서 삭제가 이루어지는 자료구조로써 FIFO방식으로 자료를 처리한다.

rear, front 두 개의 포인터를 사용해서 시작과 끝을 가리킨다.

</br>



#### Priority Queue

큐는 선입선출로 먼저 들어간 데이터가 먼저 나오는 구조이지만 우선순위큐는 먼저 들어간 데이터와 관계없이 정해진 우선순위가 높은 원소가 가장 먼저 나오게 되는 자료구조이다.

</br>



#### Tree

트리는 노드와 간선을 사용해서 노드를 연결한 사이클이 존재하지 않는 그래프이다.

- 계층적 관계를 표현하는 자료구조
- 트리구조 최상위에 루트노드 존재
- 파일시스템, 계보, 조직도를 표현하기에 적합한 자료구조



**이진트리**

최대 2개의 자식노드를 가지는 트리



**이진탐색트리**

효율적인 데이터 탐색을 위한 데이터 구조 **순차탐색 O(n)  이진탐색 O(logn)**

- 트리의 모든 노드는 유일한 키 값을 가진다.
- 부모 노드의 키값이 왼쪽 자식 노드의 키 값보다 크다.
- 부모 노드의 키값이 오른쪽 자식 노드의 키 값보다 작다.
- 왼쪽과 오른쪽 서브트리도 이진탐색트리이다.
- 트리의 삽입, 삭제, 탐색의 시간복잡도 O(h) h: 트리의 높이

</br>



#### 그래프

연결되어있는 정점간의 관계를 표현하는 자료구조

연결되어있는 정점들의 집합으로, 트리도 일종의 그래프이다.

방향성에 따라 단방향 그래프, 양방향 그래프로 나눠진다.

</br>

**그래프의 표현**

- 인정행렬
  - 그래프의 정점간의 연결정보를 2차원 배열 형태로 표현
  - 두 정점간의 연결정보를  O(1) 시간에 확인 가능
  - V^2의 공간이 필요하므로 공간낭비가 발생한다. V : 정점



- 인접리스트
  - 정점에 연결된 정점을 리스트에 저장
  - 두 정점간의 연결정보를 확인하기 위해 O(n)만큼 탐색의 시간이 필요하다.
  - V+E 만큼의 공간이 필요하여 공간낭비가 발생하지 않는다.  E : 간선



</br>

**그래프의 탐색**

- DFS (깊이 우선 탐색)
  - 갈 수 있는 만큼 최대한 깊이 탐색을 진행하고, 더 이상 갈 수 있는 정점이 없을 경우 이전 정점으로 돌아와 다시 탐색을 진행하는 방식이다.
- BFS (너비 우선 탐색)
  - 정점의 인접한 모든 정점들을 큐에 넣어 인접한 정점들 부터 우선 방문해 나아가는 방식이다. 
  - 간선의 모든 가중치가 동일한 그래프에서 최단거리를 찾는 알고리즘으로 자주 활용된다.



<p align="center"> <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcFgEJ6%2FbtqKmoJkq5a%2Fpwm3O8T4rERuL4wSTrkgnK%2Fimg.gif" width="500px" /></p>



</br>



#### 최소신장트리

가중치를 가지는 간선 그래프에서 모든정점을 가장적은 비용의 간선으로 연결하는 신장트리

- Kruskal MST - 가중치가 작은 간선 순서대로 포함시킨다.
  - 간선의 가중치가 작은 순서대로 오름차순 정렬한다.
  - 가중치가 작은 간선부터 순서대로 정점-1개의 간선을 포함시킬 때 까지 사이클이 생성되지 않는다는 전제하에 간선을 포함시킨다.
- Prim MST
  - 시작정점부터 집합을 구성해 집합에서부터 가장 적은 가중치를 가진 간선을 선택해 집합을 확장시켜 나가는 방식 (정점-1 개의 간선 수 만큼)

</br>



#### 해싱

Key와 Value로 데이터를 저장하는 자료구조중 하나로 빠르게 데이터를 검색 할 수 있다. O(1)의 시간복잡도

<p align="center"> <img src="https://lh3.googleusercontent.com/proxy/YwsopYdeiFqC_fr0HKXTkDwZL0jAsTwTnV7cf7xoc68YL7cxkp121V_ry-FOk0j-o0VAHFMryFCX3kwVc0OsJfbphlBdyJ0JBDd6xYMjW9UxSShvnqHAQnqYVnlvEfU5juG_Zabu-AZkT63mGNPtgwI61r_rSIWUHvvmSpIVcgxpNzbQS-cDmzvQB3SPqs37-9LLtKew-e51-qbanRrTSgbDEnk5ee7L8XGC6hOiE7CVjYQRJQ7pLTABwCgBqdL7R0LHIGS4ewnrYU4x-hGaMp0Yqkn7HP0fz8gbGw" width="500px" /></p>



Key값에 Hash Function을 적용시켜 생성된 index값을 가지고 데이터에 접근한다.



**해시 충돌해결**

- 개방주소법 (Open Addressing)
- 분리연결법 (Separate Chaining)

[해시 충돌해결](https://mangkyu.tistory.com/102 )

</br>

----

</br></br>

### HTTP

HTTP란 `Hyper Text Transfer Protocol` 의 약자로 웹 상에서 웹 브라우저와 같은 클라이언트와 웹 서버간 통신을 위해 정해진 통신 규약이다.

네트워크 최상위 계층  Application Layer에서 사용되는 프로토콜이며 비연결형 프로토콜이다.

</br></br>

- **요청방식**

  - GET 방식

    요청 데이터가 `HTTP Request Message Header`에 포함되어 전송된다.

    url에 request data가 포함되어 전송되는 방식이기 때문에 전송할 데이터의 크기가 제한적이며, 보안에 취약하다.

    **서버에서 데이터를 읽어오는 용도로 사용된다.**

  - POST 방식

    요청 데이터가 `HTTP Request Message Body`에 포함되어 전송된다.

    전송가능한 데이터의 크기가 GET방식보다 크다.

    **서버에 데이터를 수정하거나, 추가하는 용도로 사용된다.**

</br></br>

- **응답코드 정리**
  - 1xx : 서버에서 사용자의 요청을 정상적으로 받았지만, 아직 제대로된 응답을 할 수 없는 상태
  - 2xx: success 성공적인 응답
  - 3xx: 서버에서 사용자의 요청을 제대로 받았고, 처리를 완료하기위해 페이지의 리다이렉션이 필요한 상태
  - 4xx: 서버로 전달된 올바르지 않은 요청
  - 5xx: 사용자의 올바른 요청에 웹서버가 제대로된 응답을 할 수 없는 상태

</br></br>

- **TCP와 UDP 비교 정리**
  - UDP (User Datagram Protocol)
    - 비연결형 프로토콜
    - 오류제어를 하지 않기 때문에 오류가 발생되어 누락된 세그먼트나, 손상된 세그먼트에 대한 재전송을 하지 않는다.
    - TCP에 비해 연결작업이 필요 없으므로 빠르다.
  - TCP (Transmission Control Protocol)
    - 연결형 프로토콜
    - 3-way handshake를 통한 두 종단점 간의 연결 설정을 통한 송신지 부터 수신지 노드까지 순차적이고, 신뢰성있는 데이터 전송



</br></br>

- **HTTPS**

  - HTTP의 보안상 문제
    - 평문 통신으로 이루어지기 때문에 도청 발생 가능
    - 서로의 통신 상대를 확인 할 수 없어 위장 및 변조 가능

  

  따라서 HTTP에 SSL을 조합하여 통신내용을 암호화 => HTTPS

  - HTTP
    - HTTP -> TCP (직접통신)
  - HTTPS
    - HTTP -> SSL -> TCP (보안계층을 추가)

</br></br>

- **모든 웹 페이지에서 HTTPS를 사용하지 않는 이유**

  평문 통신에 비해서 암호화 통신은 CPU나 메모리등 리소스가 많이 필요하게 된다. 따라서 많은 리소스 소모는 웹 서버 한대당 처리 할 수 있는 request 수를 감소시키므로 보안이 필요한 곳에서 사용하는 것이 좋다.

</br>

----

</br></br>

### 동기/비동기

동기방식과 비동기 방식은 카페를 예로 들어서 설명 할 수 있다. 카페에 손님들이 주문을 하기 위해 일렬로 줄 서있는 모습을 상상해 보자 

동기 방식의 카페는 손님 한명의 주문을 받음과 동시에 커피를 만들어서 내어주고 그 다음에 다음손님의 주문을 받는 방식으로 가게가 운영된다.

반면에 비동기 방식의 카페는 모든 손님의 주문을 차례대로 받고 진동벨을 나눠주어 커피가 완성되면 손님에게 알려주는 방식으로 가게가 운영된다.



- 동기 방식 : 요청을 보낸 후 응답을 받아야만 다음 동작이 이루어지는 방식 
  - 이는 시스템 전체적인 효율을 저하시킬 우려가 있다.
- 비동기 방식: 요청을 보낸 후 응답과 관계없이 즉시 다음로직을 수행하는 방식으로 이전에 요청한 응답이 도착하면 등록한 콜백함수를 실행시킨다.
  - 결과가 주어지는데 시간이 걸리더라도 다른 작업을 처리하기 때문에 효율적인 수행이 가능하다.

</br>

----

</br></br>

### 쓰레드/프로세스

- **프로세스 (Process)**
  - 실행중인 프로그램
  - 메모리상에 올라와 실행되고있는 프로그램의 인스턴스
  - 운영체제로부터 CPU,메모리 영역, 주소공간을 할당 받는다.
  - **독자적인 자원을 가지며, 다른 프로세스의 자원에 접근 할 수 없다.**
    - 다른 프로세스의 자원을 사용하려면 프로세스간의 통신이 필요하다.
  - **PCB (프로세스 제어 블럭)**
    - 프로세스에 대한 중요한 정보를 저장하고 있는 운영체제의 자료구조이다.
    - 프로세스 전환 (Context Switch)이 발생할 때 프로세스 작업의 진행 상황 등을 저장한다.

</br>



- **쓰레드(Thread)**
  - 프로세스 내에서 실행되는 하나의 독립적인 실행흐름이다.
  - 쓰레드는 각자의 독립적인 스택공간만을 가지며 힙 영역과 같은 나머지 프로세스의 자원을 여러 쓰레드가 공유한다. 
  - 여러 쓰레드가 프로세스 내의 자원을 공유하기 때문에 병행성 제어가 필요하다.
  - 새로운 쓰레드를 생성해서 사용하는 것이 프로세스를 생성하는 것 보다 빠르다.



</br></br>

- **멀티 프로세스**

  하나의 응용프로그램을 여러 개의 프로세스로 구성해서 각 프로세스가 하나의 작업을 처리하도록 하는 것

  - 장점 
    -  하나의 프로세스가 문제가 생겨 죽어버리더라도 다른 프로세스에 영향을 미치지 않는다.
  - 단점 
    - Context Switch 시간이 멀티 스레드 보다 느리다.

</br>

- **멀티 프로세스**

  하나의 응용프로그램을 여러개의 쓰레드로 구성하고 각 쓰레드가 하나의 작업을 처리하도록 하는 것

  - 장점 : 
    - 자원을 공유하기때문에 통신의 부담이 줄어든다.
    - Context Switch의 부담이 줄어든다.
  - 단점 
    - 여러 쓰레드가 자원을 공유하므로 동기화 문제가 발생한다.
    - 한 쓰레드의 문제가 생기면 전체에 문제가 발생하게 된다.

</br>

----

</br></br>

### Restful API

REST의 기본 원칙을 성실히 지켜 디자인 한 API

**REST란 ?**

- URI를 통해서 웹 상의 자원을 명시하고, HTTP Method(GET, POST, PUT, PATCH, DELETE)를 통해 자원에 CRUD연산을 적용하는 것을 의미한다.

</br>

**[ REST 구성요소 ]**

- **Resource (자원)** : 서버는 고유한 URI를 가진다.
- **Method (행위)** : 서버에게 요청을 보내기 위한 방식 (GET, POST, PUT, PATCH, DELETE)
- **Representation (표현)** : 클라이언트가 서버와 주고받는 데이터 형태 (json,xml 등)

</br>

----

</br></br>

### 메시지 큐

비동기 메시지 처리방식이다.

메시지 기반 미들웨어로 메시지를 이용하여 여러 어플리케이션, 시스템, 서비스들을 연결해주는 솔루션이다.

**기본원리**

- Producer가 메시지를 Queue에 넣어두면 Consumer가 비동기적으로 메시지를 가져가 처리하는 방식이다.

<p align="center"> <img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile25.uf.tistory.com%2Fimage%2F226FFA4E587107DE285DF4" width="500px" /></p>



Client와 동기적으로 많은 데이터를 통신하게되면 병목현상으로 서비스의 성능이 저하 될 수 있다.

</br>

----

</br></br>

### 동시성 이슈

멀티 쓰레드 프로그램에서 다수의 쓰레드가 임계영역에 동시에 접근하게 되어 프로그램의 실행결과가 원하는 실행결과와 달라지는 이슈  

**이를 해결하기위해 임계영역에는 오직 한 쓰레드만이 접근하여 작업 할 수 있도록 보장해 주어야 한다 (상호배제)**

</br>

- 임계영역에 대한 상호배제 기법
  - **락** 
  - **컨디션 변수**
  - **세마포어**

</br>

- **교착상태**
  - 락을 기다리며 무한정 대기에 빠진 상태
  - 두 쓰레드가 하나의 락을 소유한 채로 서로의 락이 해제되기를 기다리는 상태

</br>

----

</br></br>

### GarbageCollection

**가비지란 ?**

시스템이 더 이상 사용하지 않는 유효하지 않은 할당된 메모리이다.



**Garbage Collection** 

이러한 유효하지 않은 할당된 메모리를 찾아 자동으로 회수하여 반환시키는 것

</br>

**Garbage Collector 원리**

1. Mark - 스택의 모든 변수, 객체를 확인하여 사용중인 메모리인지 확인한다.
2. Stop the World -  Garbage Collection실행을 위해 모든 어플리케이션의 실행을 중단시키고 Garbage Collector만 실행시킨다.
3. Sweep - 1번에서 Mark되지 않은 메모리를 반환한다.



**Garbage Collection의 한계** 

- 실행시간에 동작하여 성능이 하락될 수 있다.
- 더이상 접근 불가능한 객체만 회수하기 때문에 다른 문제로 메모리 누수가 발생 할 수 있다.

</br>

----

</br></br>

### 테스트 코드

테스트 코드는 작성한 기능이 예외적인 에러없이 잘 작동하는지 검증하는 코드이다.

단, 100% 정확성을 가진 테스팅은 존재하지 않는다.

테스트 코드는 예외적인 에러 없이 잘 작동하는 깔끔한 코드를 얻기위해 작성된다.

테스트 코드를 작성하면 제품의 안정성을 높일 수 있으며, 기능 추가 및 수정으로 인해 생기는 Side-Effect를 줄일 수 있다.

**깔끔한 코드란 ?**

- 가독성이 좋은 코드
- 중복이 최소화된 코드



**테스트 코드를 작성 해야 하는 이유**

- 새로운 기능을 추가하거나 기존의 코드를 수정했을 때 이전의 기능이 제대로 동작하지 않을 수 있다.
- 테스트 해야 할 기능의 경우의 수가 많다면 수동적으로 테스트 하는 것에 한계가 있다.
- 코드를 리팩토링하는 과정에서 테스트 코드없이 코드가 망가지지 않았는지 확인하기가 쉽지 않다.

</br>

**TDD (Test-Driven Development)**

- 테스트가 개발을 주도해나가는 형태의 개발 방법론
- 테스트 코드를 먼저 작성하고 기능을 구현한다.



**TDD 3가지 절차**

1. 실패 - 실패하는 테스트 케이스를 먼저 만들어라.
2. 성공 - 실패하는 테스트 케이스를 통과시키기 위한 코드를 작성하라
3. 리팩토링 - 구현한 코드에 중복을 제거하고 개선할 부분을 개선해라



**TDD의 장점**

- 작은 기능단위로 개발이 이루어지기 때문에 자연스럽게 모듈화가 이루어진다.
- 테스트 코드를 먼저 작성하고 기능을 개발하기 때문에 리팩토링과 유지보수가 쉽다.

</br>

**Refactor Code**

`좋은 코드`를 작성하기는 쉽지 않다.

1. 가독성이 좋게 Coding Convention을 맞춰야한다.
2. 네이밍 규칙을 적용하여 변수명, 클래스명, 함수명을 일관되게 정해야한다.
3. 확장성을 고려한 코드를 작성해야 한다.
4. 비즈니스 로직에 대한 고려
5. 예외처리

**이러한 모든 것을 고려하며 코딩하면 코드의 양이 방대해 질 수 있어 리팩토링 과정이 필요하게 된다.**

**=> 이때 테스트 코드가 중심을 잡아 줄 수 있다.**

</br>

----

</br></br>

### 리팩토링

리팩토링은 이미 공사가 끝나 완성된 집을 더 튼튼하고 멋진 집으로 만들기 위해 내부를 리모델링 하는 작업과 유사하다.



**리펙토링이란 ?**

결과의 변경없이 코드의 구조를 개선하여 가독성을 높이고, 유지보수가 용이한 코드로 변경하는 작업이다.

- 일관성있는 네이밍 규칙
- 중복이 최소화된 코드
- 의존성이 제거된 코드
- 하나의 클래스, 하나의 메소드는 하나의 기능만을 수행하는 코드

</br>

----

</br></br>

### Reference

- [Technical Interview Guidelines for Beginners](https://github.com/JaeYeopHan/Interview_Question_for_Beginner)
- [망나니개발자](https://mangkyu.tistory.com/102)
- [코딩팩토리](https://coding-factory.tistory.com/610)

