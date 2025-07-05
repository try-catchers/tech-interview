# ✍️ 작성자
이현지

---

# ❓ 질문
Cookie, Session, JWT의 차이점에 대해 설명해주세요.

---

# 💬 답변 요약
쿠키는 클라이언트에 데이터를 저장하는 방식이며, 세션은 서버에 상태 정보를 보관하고 식별자를 쿠키에 저장합니다. JWT는 서명된 토큰을 클라이언트에 저장해 서버에 별도의 상태를 유지하지 않고 인증을 수행합니다.

---

# 🧠 핵심 키워드
- Cookie
- Session
- JWT(Json Web Token)
- Stateless
- 상태 저장(Stateful)
- 인증(Authentication)
- 토큰 기반 인증

---

# 🔥 상세 설명

## 🟢 Cookie
- **정의**
    - 클라이언트에 저장되는 작은 데이터 조각으로, 서버가 응답 시 생성해 브라우저에 저장합니다.
- **특징**
    - 다음 요청 시 자동으로 서버에 함께 전송
    - 인증, 사용자 식별, 간단한 상태 관리에 사용
- **보안**
    - 탈취 시 세션 하이재킹 가능
    - HttpOnly, Secure 옵션 권장

---

### 🟡 Session
- **정의**
    - 서버에 사용자 상태 정보를 저장하고, 클라이언트에 세션 ID만 쿠키로 전달하는 방식입니다.
- **특징**
    - 서버 메모리나 저장소에 상태 유지
    - 세션 ID로 사용자 식별
- **보안**
    - 세션 관리와 만료 설정 필요
    - 서버에 상태를 저장하므로 수평 확장에 제약

---

### 🟣 JWT(Json Web Token)
- **정의**
    - 사용자 정보를 서명된 토큰에 담아 클라이언트에 저장하는 방식입니다.
- **특징**
    - 무상태 인증(Stateless)
    - 토큰 자체에 식별자, 만료일자 포함
    - 서버가 별도 저장소에 상태를 보관할 필요 없음
- **보안**
    - 서명 검증으로 위조 방지
    - 토큰 탈취 시 재사용 방지 어려움
    - 적절한 만료 시간 설정 필수

---

## 🟢 비교 요약
| 구분 | 쿠키 | 세션 | JWT |
|---|---|---|---|
| 저장 위치 | 클라이언트 | 서버 | 클라이언트 |
| 상태 관리 | 클라이언트가 관리 | 서버가 상태 유지 | 무상태(Stateless) |
| 확장성 | 높음 | 서버 부하 증가 | 매우 높음 |
| 보안 | 탈취 위험 | 비교적 안전 | 위조 방지 가능 |

---

# 🔗 참고 자료
- [Do it! 네트워크 기초](https://product.kyobobook.co.kr/detail/S000213766983)
- [MDN Web Docs - HTTP Cookies](https://developer.mozilla.org/ko/docs/Web/HTTP/Cookies)
- [OWASP Session Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html)
- [JWT.io Introduction](https://jwt.io/introduction/)
- [RFC 7519 - JSON Web Token (JWT)](https://datatracker.ietf.org/doc/html/rfc7519)
