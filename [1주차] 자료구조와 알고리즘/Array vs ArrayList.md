# ✍️ 작성자
김지수

---

# ❓ 질문
Array와 ArrayList를 비교해주세요.

---

# 💬 답변 요약
- Array는 동일 타입의 값을 `고정된 개수`만큼 저장하는 객체입니다.
- ArrayList는 `동적으로 크기 조절`이 가능한 배열 기반 리스트입니다.
- Array는 크기가 고정되지만, ArrayList는 내부 배열 용량이 부족하면 자동으로 확장됩니다.

---

# 🧠 핵심 키워드
- 용량
- 고정 크기 vs 동적 크기

---

# 🔥 상세 설명

## 1️⃣ Array`[1]`
- 같은 타입의 값을 고정된 개수만큼 저장하는 객체입니다.
- 0부터 시작하는 인덱스로 요소에 접근합니다.
- 기본형 배열과 객체형 배열이 있습니다.
    - 기본형: int[], char[] 등
    - 객체형: String[], Object[] 등

## 2️⃣ ArrayList`[2]`

### 📌 개요
- List 인터페이스를 크기 조절이 가능한 배열로 구현한 클래스입니다.
- null 포함 모든 요소를 추가할 수 있습니다.
- 동기화는 지원하지 않습니다.

### 💪 성능
- ArrayList는 LinkedList보다 상수 계수가 작아 일반적으로 더 빠릅니다.

| 연산 종류                          | 시간 복잡도                      |
|-----------------------------------|---------------------------------|
| size, isEmpty, get, set           | O(1)                            |
| getFirst, getLast, removeLast     | O(1)                            |
| iterator, listIterator, reversed  | O(1)                            |
| add, addLast                      | *평균* O(1), n개 추가 시 O(n)  |
| 기타 연산   | O(n)                            |

### 🎁 내부 용량 관리
- 용량은 내부 배열의 크기로, 요소 수보다 크거나 같아야 합니다.
- 기본 초기 용량(DEFAULT_CAPACITY)은 10입니다.
- 요소 추가 시 용량이 부족하면 아래처럼 자동으로 배열을 확장합니다.

```java
  private Object[] grow(int minCapacity) {
      int oldCapacity = elementData.length; // 기존 배열 크기
      if (oldCapacity > 0 || elementData != DEFAULTCAPACITY_EMPTY_ELEMENTDATA) {
          int newCapacity = ArraysSupport.newLength(oldCapacity,
                  minCapacity - oldCapacity, // 최소 증가량
                  oldCapacity >> 1);         // 선호 증가량 (1/2배)
          return elementData = Arrays.copyOf(elementData, newCapacity); // 배열 확장
      } else {
          return elementData = new Object[Math.max(DEFAULT_CAPACITY, minCapacity)];
      }
  }
  
  private Object[] grow() {
    return grow(size + 1);
  }
```

### 🚨 동기화 관련 주의 사항
- 기본적으로 동기화되어 있지 않아 스레드 안전하지 않습니다.
- 여러 스레드가 동시에 접근하고, 그 중 하나라도 구조적 수정을 하면 외부에서 동기화해야 합니다.
- 생성 시 아래처럼 Collections.synchronizedList()로 래핑하면 안전합니다.

```java
  List<Integer> list = Collections.synchronizedList(new ArrayList<>());
```

---

# 🔗 참고 자료
- [1] https://www.baeldung.com/java-arrays-guide#definition
- [2] java.util.ArrayList Javadoc
- 이준형, 이것이 취업을 위한 백엔드 개발이다 with 자바, 한빛미디어(2024), 101p