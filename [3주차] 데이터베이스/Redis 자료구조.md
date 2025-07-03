# ✍️ 작성자
김지수

---  

# ❓ 질문
Redis 자료구조와 활용 예시에 대해 설명해주세요.

---  

# 💬 답변 요약
| 자료구조          | 설명                           | 활용 예시                    |
|:--------------|:-----------------------------|:-------------------------|
| String        | 기본 키-값 저장, 숫자 증가 가능          | 인증 정보 저장, 좋아요 기능, 캐싱     |
| List          | 순서 있는 문자열 목록, 양쪽 끝 추가/삭제 가능  | 최근 방문 기록, 큐/스택           |
| Set           | 중복 없는 문자열 집합                 | 방문자 집계, 좋아요 중복 방지        |
| Sorted Set    | 점수로 정렬된 집합                   | 게임 순위, 실시간 시세 관리         |
| Hash          | 키 안에 필드-값 쌍 저장               | JSON 객체 캐싱, 빈번한 데이터 수정   |
| Bitmap        | 비트 단위 저장 및 연산                | 대량 사용자 접속 카운팅            |
| HyperLogLogs  | 중복 제거한 유니크 값 개수 추정           | 방문 IP 수, 대규모 유니크 데이터 집계  |
| Stream        | 저장되는 메시지 로그, 소비자 그룹 지원       | 메시징 브로커, 이벤트 기반 시스템, 채팅  |
| Pub/Sub       | 실시간 메시지 발행/구독 시스템            | 채팅, 실시간 알림 서비스           |

---  

# 🧠 핵심 키워드
String, List, Set, Sorted Set, Hash, Bitmap, HyperLogLogs, Stream, Pub/Sub, 캐싱, 메시징, 실시간 처리, 데이터 구조

---  

# 🔥 상세 설명

## 📌 Redis 개요 및 특징
- 고성능 인메모리 키-값 저장소: 메모리 기반으로 빠른 읽기/쓰기 지원
- 주요 활용: 캐싱, 인증 관리, DB 동시성 제어 등 다양한 목적 사용
- 단순화된 데이터 구조: 키-값 형태로 SQL 쿼리 사용 불필요
- 싱글 스레드 구조: 동시성 이슈 발생 가능성 낮음

## 🚀 String
- 가장 기본적인 데이터 타입으로, `SET` 명령어로 키-값 저장
- 카운팅 기능: `INCR`(1 증가), `INCRBY`(지정 값 증가) 사용
- 다양한 활용: `EX`(만료 시간 설정), `NX`(키 부재 시 값 설정) 옵션 적용
- 주요 명령어
    - `SET key value` (값 설정)
    - `GET key` (값 조회)
    - `INCR key` (값 1 증가)
    - `INCRBY key increment` (값 지정 만큼 증가)
    - `SET key value NX` (키 없을 때 설정)
    - `SET key value EX seconds` (만료 시간 설정)
    - `TTL key` (남은 만료 시간 조회)

## 📋 List
- 순서 있는 데이터 저장, Deque(Double-Ended Queue)와 유사 구조
- 큐/스택 활용에 적합하며 자체 Blocking 기능으로 불필요한 폴링 방지
- 주요 명령어
    - `LPUSH key value` (왼쪽에 값 추가)
    - `RPUSH key value` (오른쪽에 값 추가)
    - `LPOP key` (왼쪽에서 값 추출)
    - `RPOP key` (오른쪽에서 값 추출)
    - `LPUSHX key value` (키 있을 때 왼쪽에 추가)
    - `RPUSHX key value` (키 있을 때 오른쪽에 추가)

## 🔢 Set
- 중복 없는 문자열 집합, 데이터 순서 없음
- 주요 명령어
    - `SADD key member` (멤버 추가)
    - `SMEMBERS key` (모든 멤버 조회)
    - `SCARD key` (멤버 개수 조회)
    - `SREM key member` (특정 멤버 삭제)

## 📊 Sorted Set (ZSET)
- 점수(`score`) 기반 정렬된 중복 없는 값 집합
- 정렬 기준: `score` (동일 시 사전 순)
- 주요 명령어
    - `ZADD key score member` (멤버 및 점수 추가)
    - `ZRANGE key start stop [WITHSCORES]` (순위 범위 조회)
    - `ZREVRANGE key start stop` (점수 내림차순 조회)
    - `ZRANK key member` (멤버 순위 조회)

## 🗂 Hash
- 키 내 필드-값 쌍 저장, JSON 객체 데이터 캐싱에 유용
- 필드 단위로 효율적 수정/삭제 가능
- 주요 명령어
    - `HSET key field value` (필드 값 설정)
    - `HGET key field` (특정 필드 조회)
    - `HGETALL key` (전체 필드 및 값 조회)
    - `HINCRBY key field increment` (필드 값 지정 만큼 증가)

## 🧩 Bitmap
- String 변형, 비트 단위 연산 가능
- 저장 공간 절약 효과 큼
- 주요 명령어
    - `SETBIT key offset value` (비트 설정)
    - `BITCOUNT key` (1로 설정된 비트 수 카운팅)

## 🔢 HyperLogLogs
- 대량 데이터 유니크 카운팅에 특화, 중복 없는 값 개수 계산
- 고정 크기 12KB 사용, 데이터 크기 무관
- 주요 명령어
    - `PFADD key element [element ...]` (데이터 추가)
    - `PFCOUNT key [key ...]` (유니크 값 개수 조회)
    - `PFMERGE destkey sourcekey [sourcekey ...]` (여러 키 병합)

## 📼 Stream
- 로그 저장에 최적화된 append-only 데이터 구조
- 메시지 저장 후 나중에 읽을 수 있음 
- 주요 명령어
    - `XADD key * field value [field value ...]` (데이터 추가, ID 자동 생성)
    - `XREAD [BLOCK milliseconds] STREAMS key id` (메시지 읽기)

## 📢 Pub/Sub
- 메시지 발행/구독 시스템, 발행된 메시지가 구독자 모두에 즉시 전달
- 메시지를 저장하지 않고 발송 즉시 소멸 <-> Stream
- 주요 명령어
    - `SUBSCRIBE channel [channel ...]` (채널 구독)
    - `PUBLISH channel message` (메시지 발행)

> ⚠️ 엄밀히 말하면 Pub/Sub은 자료구조가 아니라 메시징(발행/구독) 기능

---  

# 🔗 참고 자료
- [인프런 - 개발자라면 알아야 할 redis 기본](https://www.inflearn.com/course/%EA%B0%9C%EB%B0%9C%EC%9E%90%EB%9D%BC%EB%A9%B4-%EC%95%8C%EC%95%84%EC%95%BC%ED%95%A0-redis-%EA%B8%B0%EB%B3%B8%EA%B8%B0%EB%B3%B8/dashboard)
- [유튜브 - Redis 야무지게 사용하기](https://www.youtube.com/watch?v=92NizoBL4uA)