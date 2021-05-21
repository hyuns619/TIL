# HTTP 기본 내용 정리

## HTTP

- Hyper Text Transfer Protocol
- 하이퍼 텍스트(HTML) 문서를 교환하기 위해 만들어진 통신 규약(protocol)
- 즉, 웹에서 네트워크로 서버 간의 통신을 할 때 어떠한 형식으로 서로 통신을 하자고 규정해 놓은 통신 규칙
- HTTP는 TCP/IP 기반

# HTTP 핵심 요소

## HTTP 통신 방식

- HTTP는 기본적으로 요청(request)에 응답(response)하는 구조로 구성되어 있다.

  - 클라이언트가 HTTP request를 서버에 보내면 서버에서는 HTTP response를 보내는 구조
  - 클라이언트와 서버의 모든 통신은 요청과 응답으로 이루어진다.

- HTTP는 Stateless이다.
  - Stateless, 말 그대로 상태(state)를 저장하지 않는다.
  - 즉, 요청이 오면 그에 대한 응답을 할 뿐, 여러 `요청/응답`끼리 연결되어 있지 않다. 각각의 `요청/응답`은 독립적인 `요청/응답`이다.
  - 예를 들어, 클라이언트가 요청을 보내고 응답을 받은 후, 다시 요청을 보낼 때 전에 보낸 `요청/응답`에 대해 알지 못한다는 뜻이다.
  - So, 여러 `요청/응답`의 진행 과정이나 데이터가 필요할 때는 쿠키나 세션 등을 사용하게 된다.

## HTTP Request 구조

- HTTP request 구조는 크게 3부분으로 구성되어 있다.

  - `status line`
  - `headers`
  - `body`

### Status Line

- HTTP request의 첫 라인이다.
- HTT request의 status line 또한 3부분으로 구성되어 있다.

  - **HTTP Method**

    - 해당 request가 의도한 action을 정의하는 부분
    - HTTP Methods에는 `GET`, `POST`, `DELETE`, `OPTIONS` 등등이 있다.
    - 주로 `GET`과 `POST`가 쓰인다.

  - **Request target**
    - 해당 request가 전송되는 목표 URI
    - 예를 들어서 `/login`
  - **HTTP Version**
    - HTTP version이다. `1.0`, `1.1`, `2.0` 등이 있다.

```http
GET /search HTTP/1.1
```

### Headers

- 해당 request에 대한 추가 정보(addtional information)를 담고 있는 부분이다.

  - 예를 들어, request 메세지 body의 총 길이(Content-Length) 등

- `Key:Value` 값으로 구성되어 있다. (콜론`:` 사용)
  - `Key:Value`
  - 예) `HOST: gogle.com`
  - Headers도 크게 3부분으로 나누어지지만 현 단계에서는 3부분으로 구성되어 있다는 것만 숙지해 두고 있자. (general headers, request headers, entity headers)
- 자주 사용되는 header 정보에는 다음이 있다.

  - Host

    - 요청이 전송되는 target의 host url : 예를 들어, gogle.com

  - User-Agent
    - 요청을 보내는 클라이언트에 대한 정보 : 예를 들어, 웹 브라우저에 대한 정보
    - Accept
      - 해당 요청이 받을 수 있는 응답(response) 타입
  - Connection
    - 해당 요청이 끝난 후에 클라이언트와 서버가 계속해서 네트워크 커넥션을 유지할 것인지 아니면 끊을 것인지에 대해 지시하는 부분
  - Content-Type
    - 해당 요청이 보내는 메세지 body의 타입. 예를 들어, JSON을 보내면 `application/json`
  - Content-Length
    - 메세지 body의 길이

```http
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Type: application/json
Content-Length: 257
Host: google.com
User-Agent: HTTPie/0.9.3
```

### Body

- 해당 request의 실제 메시지/내용
- Body가 없는 request도 많다.
  - 예를 들어서, GET request는 대부분 body가 없는 경우가 많다.

```http
POST /payment-sync HTTP/1.1

Accept: application/json
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 83
Content-Type: application/json
Host: intropython.com
User-Agent: HTTPie/0.9.3

{
    "imp_uid": "imp_1234567890",
    "merchant_uid": "order_id_8237352",
    "status": "paid"
}
```

## HTTP Response 구조

- Response도 request와 마찬가지로 크게 3부분으로 구성되어 있다.
  - Status line
  - Headers
  - Body

### Status Line

- Response의 상태를 간략하게 나타내주는 부분
- 3부분으로 구성되어 있다.
  - HTTP version : HTTP 버전
  - Status code : 응답 상태를 나타내는 코드
    - 예를 들어, 200
  - Status text : 응답 상태를 간략하게 설명해주는 부분
    - 예를 들어, "Not Found"

```http
HTTP/1.1 404 Not Found
```

### Headers

- Response의 headers와 동일하다.
- 다만, response에서만 사용되는 header 값이 있다.
  - 예를 들어, User-Agent 대신에 Server 헤더가 사용된다.

### Body

- Response의 body와 일반적으로 동일하다.
- Request와 마찬가지로 모든 response에 body가 있지는 않다. 데이터를 전송할 필요가 없을 경우에 body가 비어있게 된다.

```http
HTTP/1.1 404 Not Found

Connection: close
Content-Length: 1573
Content-Type: text/html; charset=UTF-8
Date: Mon, 20 Aug 2018 07:59:05 GMT

<!DOCTYPE html>
<html lang=en>
  <meta charset=utf-8>
  <meta name=viewport content="initial-scale=1, minimum-scale=1, width=device-width">
  <title>Error 404 (Not Found)!!1</title>
  <style>
  </style>
```

## 자주 쓰이는 HTTP Methods

**GET**

- 데이터를 서버에서 받아올 때(GET) 주로 사용하는 Methods
- 데이터 `생성/수정/삭제` 없이 받아오기만 할 때 사용한다.
- 가장 간단하고 많이 사용되는 HTTP Method
- 언급한 것처럼 주로 데이터를 받아올 때 사용되기 때문에 request에 body를 안 보내는 경우가 많다.

**POST**

- 데이터를 `생성/수정/삭제` 할 때 주로 사용되는 Method.
- 데이터를 생성 및 수정할 때 많이 사용하기 때문에 대부분의 경우 request body가 포함돼서 보내진다.

## 알고 있으면 좋은 HTTP Methods

**OPTIONS**

- 주로 요청 URI에서 사용할 수 있는 Method를 받아올 때 사용된다.
- 예를 들어, /update uri에서 어떤 method를 요청 가능한지(GET?POST?)를 알고 싶으면 먼저 OPTIONS를 사용해서 확인하게 된다.

```http
http -v OPTIONS http://example.org

OPTIONS / HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 0
Host: example.org
User-Agent: HTTPie/0.9.3



HTTP/1.1 200 OK
Allow: OPTIONS, GET, HEAD, POST
Cache-Control: max-age=604800
Content-Length: 0
Date: Mon, 20 Aug 2018 08:37:45 GMT
Expires: Mon, 27 Aug 2018 08:37:45 GMT
Server: EOS (vny006/0450)
```

**PUT**

- POST와 비슷하다. 데이터를 생성할 때 사용되는 Method.
- POST와 겹치기 때문에 PUT을 사용하는 곳도 있고 POST로 통일해서 사용하는 곳도 있는데, 최근에는 POST를 많이 사용하는 추세이다.

**DELETE**

- 특정 데이터를 서버에서 삭제 요청을 보낼 때 쓰이는 Method
- PUT과 마찬가지로 POST에 밀려서 잘 사용하지 않는 추세이다.

## 자주 쓰이는 HTTP Status Code

200 OK

- 문제없이 실행 되었을때 보내는 코드

301 Moved Permanently

- 해당 URI가 다른 주소로 바뀌었을때 보내는 코드

```http
HTTP/1.1 301 Moved Permanently
Location: http://www.example.org/index.asp
```

400 Bad Request

- 해당 요청이 잘못되었을 때 보내는 코드
- 주로 요청에 포함된 input 값에 잘못된 값이 보내졌을 때 사용되는 코드
- 예를 들어, 전화번호를 보내야 되는데 text가 보내졌을 때 등.

401 Unauthorized

- 유저가 해당 요청을 진행하려면 먼저 회원가입과 로그인이 필요하다는 것을 나타내려고 할 때 사용되는 코드

403 Forbidden

- 유저가 해당 요청에 대한 권한이 없다는 뜻
- 예를 들어, 오직 과금을 한 유저만 볼 수 있는 데이터를 요청 했을 때

404 Not Found

- 요청된 uri가 존재 하지 않는다는 뜻

```http
http -v google.com/no-such-uri

GET /no-such-uri HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
Host: google.com
User-Agent: HTTPie/0.9.3

HTTP/1.1 404 Not Found
Content-Length: 1572
Content-Type: text/html; charset=UTF-8
Date: Mon, 20 Aug 2018 08:46:48 GMT
Referrer-Policy: no-referrer
```

500 Internal Sever Error

- 서버에서 에러가 났을 때 사용되는 코드
