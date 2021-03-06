# HTTP/1.1 vs HTTP/2.0

## HTTP/1.0

* 1연결당 1Req,1Res를 처리
* 브라우저에서 요청에 대한 성공과 실패를 바로 알 수 있게 됨.
* 이전에는 GET만 사용, POST 추가됨



## HTTP/1.1

* 가장 많이 사용되고 있는 프로토콜(Rest API가 사용)

* **파이프라이닝** 도입

  * 이전 요청 다 수행하기 전에 다음 요청 보냄.

* 1연결당 1Req,1Res를 처리

  * 그러나 HTTP/1.1에서는 일정 시간 내 연결 정보를 기억해 연결 **재사용**
  * 동시전송문제, 다수의 리소스 처리 시 성능 이슈
  
  #### 단점
  
  * **HOLB(Head Of Line Blocking)** - 특정 응답 지연
    * Pipelining을 통해 1연결 1req,res - > 1연결 N req,res 기법으로 해결하는 과정에서 발생
      * 문제점: 파이프라인의 앞선작업 하나의 res가 지연되면 다른 res도 지연됨
  * **RPP(Round Trip Time) 증가**
    * 재사용이 있더라도, 기본적으로 1 연결 1 req이기 때문에 connection마다 TCP 연결
      * 이 때 3-way handshake or 4-way handshake -> 오버헤드
  * **heavy header**
    * header의 많은 중복된 값이 전송됨. 이 중 cookie가 가장 문제라고 함



## HTTP/2.0

* HTTP 1.1과 동일한 API면서 성능 향상에 초점
* **Multiplexed Streams**
  * 1 con N message, Res는 순서에 상관 없이 stream으로 주고받음
* **Stream Prioritization**
  * 리소스간 우선순위 -> Client가 필요한 리소스 부터 Response
* **Server Push**
  * 클라이언트가 요청하지 않은 리소스(필요하게 될 리소스)를 마음대로 보내줌
  * HTTP/1.1에서는 요청한 html 문서를 해석하면서 필요한 리소스를 재요청하지만 HTTP/2에서는 이러한 것들을 push해주어 클라이언트의 요청 최소화
* **Header Compression**
  * HPACK 압축방식을 통해 Header 정보 압축



![img](https://user-images.githubusercontent.com/31475037/89241056-d77c9480-d638-11ea-8ef4-7d9d475ac560.png)



#### Reference)

#### https://chacha95.github.io/2020-06-15-gRPC1/

#### https://velog.io/@taesunny/HTTP2HTTP-2.0-%EC%A0%95%EB%A6%AC

#### https://developers.google.com/web/fundamentals/performance/http2?hl=ko

#### https://developer.mozilla.org/ko/docs/Web/HTTP/Overview#http_%EA%B8%B0%EB%B0%98_%EC%8B%9C%EC%8A%A4%ED%85%9C%EC%9D%98_%EA%B5%AC%EC%84%B1%EC%9A%94%EC%86%8C