# 프로토콜과 HTTP

- 컴퓨터는 정해진 동작만 수행하므로 데이터 전송 방식을 명시해줘야 한다
    - 혼란 방지를 위해 규칙이 필요
- HTTP Method, URL은 편지 봉투 겉면에 적는 받는 주소와 같은 개념
    - 편지 봉투 속에 담을 내용에 대한 규칙 필요

## 프로토콜

- 네트워크 안에서 요청과 응답을 보내는 규칙
- 웹에서는 HTTP라는 프로토콜을 사용

- HTTP를 통해 요청을 보낼 땐 HTTP Method, URL이 필요하다
    - HTTP Method : 데이터를 다루는 방법
    - URL : 다룰 데이터의 위치

## HTTP Method

- GET : 데이터를 가져온다 (조회)
- POST : 데이터를 게시한다 (생성)
- PUT : 데이터를 교체한다 (수정)
- PATCH : 데이터를 수정한다 (수정)
- DELETE : 데이터를 삭제한다 (삭제)

### POST

- 데이터를 중복적으로 생성

### PUT

- 데이터가 없으면 생성, 있으면 교체 (중복 X)

## URL 구조

- 프로토콜(scheme) - 서버 주소(domain) - 서버 내 데이터 위치 (path)
    - http://www.example.com/user/1/nickname
- 1번이라는 표현 대신 일반화된 표현으로 사용할 수 있다

### Path Parameter

- URL의 일반화된 표현 방법
    - http://www.example.com/user/{user_id}/nickname

### Query String

- 서버 주소(domain) - 데이터 위치(path) - Query String
    - .com/post/search?page=1&keyword=hello

## HTTP로 주고받는 데이터의 구조

- HTTP 데이터 → HTTP 헤더, HTTP 바디

### HTTP 헤더

- 통신에 대한 정보 (언제, 누가 보내는지, HTTP Method 종류, 요청 경로 등)

### HTTP 바디

- 주고 받으려는 데이터 (보통 json형식)

## 상태 코드

- 요청에 대한 처리 결과를 상태코드와 함께 응답한다
- 상태코드는 응답 데이터의 HTTP 헤더에 들어간다

### 대표적인 상태코드

- 200 : 처리 성공 (ok)
- 201 : 데이터 생성 성공 (created)
    - 2xx 는 성공 관련
- 400 : 클라이언트 요청 오류 (bad request)
- 404 : 요청 데이터 없음 (not found)
    - 4xx 는 클라이언트 이슈
- 500 : 서버 에러 (internal server error)
    - 5xx 는 서버 이슈

# 프론트엔드와 백엔드

- 응답받은 화면에는 매일 바뀌는 컨텐츠들이 포함된다
- html 코드를 매일 수정해야 하는가?
    - 자주 변하지 않는 화면UI와, 자주 변하는 컨텐츠를 분리한다
- 프론트(클라이언트)는 화면에 채울 컨텐츠 데이터를 백엔드에게 요청
- 백엔드(서버)는 DB에서 가져온 컨텐츠 데이터를 프론트에게 응답
- 프론트와 백엔드 모두 웹에서 동작하는 컴퓨터 프로그램
    - HTTP를 사용하여 서로 데이터를 주고 받는다
- HTTP는 웹에서 데이터를 주고 받는 단순한 규칙
    - 구체적인 통신 방법은 규칙 안에서 직접 정의한다

# API

- Application Programming Interface
- 어플리케이션에서 원하는 기능을 수행하기 위해 어플리케이션과 소통하는 방법(창구)을 정의한 것

## 백엔드 API

- 프론트가 백엔드에 요청을 보낼 때
    - 어떤 HTTP method, URL을 사용해야 하는지 정의한 것
    - 각 요청에 대해 어떤 응답을 보내는지 정의한 것

## REST API

- REST 아키텍처를 따르도록 설계한 API
    - URL : 조작할 데이터
    - HTTP method : 데이터에 대한 행위
- https://velog.io/@somday/RESTful-APl-%EC%9D%B4%EB%9E%80



# API 명세서

- 친구찾기
    - GET /{friend_id}
- 팔로우,언팔로우
    - POST /follow/{friend_id}
    - POST /unfollow/{friend_id}
- 친구 리스트 조회
    - GET /friendlist/{todo_id}
- 특정 친구의 할 일 조회
    - GET /todo/{friend_id}