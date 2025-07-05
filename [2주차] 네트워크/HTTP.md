# ✍️ 작성자
<!-- 이름을 작성하세요 -->
한지성

---

# ❓ 질문
<!-- 면접 질문을 작성하세요 -->
- HTTP의 특징에 대해 설명해주세요.
- HTTP와 HTTPS의 차이점에 대해 설명해주세요.
- HTTP Method에는 어떤 것들이 있는지 설명해주세요.
- 멱등성에 대해 설명하고, HTTP 메소드에서는 어떤 메소드가 멱등성 메소드인지 설명해주세요.

---

# 💬 답변 요약
<!-- 질문에 대한 간단한 답변을 적어주세요 -->

**HTTP 특징**: 무상태, 비연결성, 단순성, 확장성을 가진 텍스트 기반 프로토콜

**HTTP vs HTTPS**: HTTP는 평문 통신, HTTPS는 SSL/TLS를 통한 암호화 통신으로 보안성 강화

**HTTP Method**: GET, POST, PUT(전체 수정), PATCH(부분 수정), DELETE, HEAD, OPTIONS 등

**멱등성**: 동일한 요청을 여러 번 호출해도 같은 결과를 반환하는 성질, GET, PUT, DELETE가 멱등성 메소드

---

# 🧠 핵심 키워드
<!-- 답변을 위해 필요한 핵심 키워드를 적어주세요 -->
- HTTP 특징 (무상태, 비연결성, 단순성, 확장성)
- HTTP, HTTPS
- HTTP Method
- 멱등성
- SSL/TLS

---

# 🔥 상세 설명
<!-- 답변을 위해 필요한 CS 개념, 원리, 예시 등을 자세히 정리하세요 -->

###  HTTP의 특징
- **무상태성**: 서버가 클라이언트 상태를 보존하지 않음
- **비연결성**: 요청-응답 후 연결 종료
- **단순성**: 텍스트 기반 프로토콜로 읽기 쉬움
- **확장성**: 헤더를 통해 기능 확장 가능

###  HTTP vs HTTPS
| 구분 | HTTP | HTTPS |
|------|------|--------|
| 포트 | 80 | 443 |
| 보안 | 평문 통신 | SSL/TLS 암호화 |
| 속도 | 빠름 | 약간 느림 |
| 보안성 | 취약 | 안전 |

- HTTPS SSL 인증서는 무료로 발급 가능하지만 유료로 발급하는 것이 더 안전
  - NGINX의 NPM(Nginx Proxy Manager)와 같은 무료 SSL 인증서 발급 도구를 사용하면 무료로 SSL 인증서를 발급받을 수 있음

### HTTP Method
- **GET**: 리소스 조회 (읽기 전용 -> 멱등)
- **POST**: 리소스 생성 (호출할 때마다 새로운 리소스 생성 -> 비멱등)
- **PUT**: 리소스 전체 수정 (전체 리소스를 수정 -> 멱등)
- **PATCH**: 리소스 부분 수정 (부분 리소스를 수정 -> 비멱등)
- **DELETE**: 리소스 삭제 (삭제 후 동일한 요청 시 이미 삭제되어 상태 변경 없음 -> 멱등)
- **HEAD**: 헤더만 조회 (멱등)
- **OPTIONS**: 지원 메소드 확인 (멱등)

### 멱등성 (Idempotency)
- 동일한 요청을 여러 번 호출해도 결과가 같은 성질
- **멱등성 메소드**: GET, PUT, DELETE, HEAD, OPTIONS
- **비멱등성 메소드**: POST, PATCH
- **안전한 메소드**: GET, HEAD, OPTIONS (서버 상태 변경 안함)

---

# 🔗 참고 자료
<!-- 질문과 답변을 준비할 때 참고한 자료, 링크 등을 남겨주세요 -->

- [HTTP 개요](https://developer.mozilla.org/ko/docs/Web/HTTP/Guides/Overview)
- [MDN - 멱등성](https://developer.mozilla.org/ko/docs/Glossary/Idempotent)
- James F. Kurose, Keith W. Ross, Computer Networking: A Top-Down Approach
- 오키타 토시야, 한 권으로 끝내는 네트워크 기초