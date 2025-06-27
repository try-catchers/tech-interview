# ✍️ 작성자
김지수

---

# ❓ 질문
멀티 스레드 환경에서의 HashMap, Hashtable, ConcurrentHashMap을 비교해주세요.

---

# 💬 답변 요약
- HashMap, Hashtable, ConcurrentHashMap은 모두 Java의 Map 인터페이스를 구현하지만, 동기화 방식과 멀티 스레드 환경에서의 동작 방식이 다릅니다.
- HashMap은 동기화를 지원하지 않아 싱글 스레드 환경에 적합합니다.
- Hashtable은 모든 메서드가 synchronized 처리되어 멀티 스레드 환경에서 안전하지만 성능이 떨어집니다.
- ConcurrentHashMap은 버킷 단위로 락을 분산시켜 동시성과 성능을 모두 보장합니다. 멀티 스레드 환경에서 가장 적합한 Map 구현체입니다.

---

# 🧠 핵심 키워드
- HashMap: 비동기, null key/value 허용, 싱글 스레드
- Hashtable: 메서드에 synchronized, 레거시, 느림
- ConcurrentHashMap: 세분화된 락, 멀티 스레드 안전

---

# 🔥 상세 설명

## 📊 비교

| 항목         | `HashMap`                                | `Hashtable`                 | `ConcurrentHashMap`                     |
| ---------- | ---------------------------------------- | --------------------------- |-----------------------------------------|
| 동기화        | ❌ 비동기                                    | ✅ 모든 메서드에 `synchronized` 적용 | ✅ 세분화된 락 (Java 8+: 버킷 단위)               |
| 멀티 스레드 환경  | ❌ 스레드 안전하지 않음                            | ✅ 스레드 안전하지만 전체 락으로 병목 발생    | ✅ 스레드 안전 + 높은 동시성 확보                    |
| 성능         | ✅ 가장 빠름 (단일 스레드 기준)                      | ❌ 느림 (모든 메서드가 락으로 감싸짐)      | ✅ 읽기 병렬화 + 쓰기도 부분 락으로 병목 최소화            |
| null 허용 여부 | ✅ `null` key(1개) / `null` value(여러 개) 허용 | ❌ 모두 허용 안 됨                 | ❌ 모두 허용 안 됨                             |
| 사용 용도      | 단일 스레드 환경, 간단한 캐시 등                      | 과거 레거시 코드 유지용               | 멀티 스레드 환경에서 기본 추천 (동시 접근 시 안전 + 효율적)    |
| 락 범위       | ❌ 없음                                     | 전체 객체 단위 락                  | Java 8+: 버킷 단위 락                        |
| JDK 등장 시기  | ✅ JDK 1.2                                | ✅ JDK 1.0                   | ✅ JDK 1.5  |

## 💡 요약

- HashMap: 동기화를 지원하지 않기 때문에 싱글 스레드 환경에서 사용해야 합니다.
- Hashtable: 모든 메서드에 스레드간 동기화 락을 걸어 멀티 스레드 환경에서는 안전하지만, 성능이 떨어집니다.
- ConcurrentHashMap: 세분화된 락 구조로 성능과 안정성을 모두 확보하여, 멀티 스레드 환경에서 가장 이상적인 선택입니다.

## ✅ 사용 추천

- HashMap: 성능이 중요한 싱글 스레드 환경
- Hashtable: 레거시 코드 유지 보수 목적 외에는 사용 비추천 (JDK 1.8부터 deprecated)
- ConcurrentHashMap: 동시성과 성능이 모두 필요한 멀티 스레드 환경

---

# 🔗 참고 자료
- https://www.baeldung.com/java-hashtable-vs-concurrenthashmap
- https://tecoble.techcourse.co.kr/post/2021-11-26-hashmap-hashtable-concurrenthashmap/