# ✍️ 작성자
<!-- 이름을 작성하세요 -->
이현지

---

# ❓ 질문
<!-- 면접 질문을 작성하세요 -->
AVL 트리는 무엇인가요?

---

# 💬 답변 요약
<!-- 질문에 대한 간단한 답변을 적어주세요 -->
AVL 트리: 각 노드에서 왼쪽 서브 트리의 높이와 오른쪽 서브트리의 높이차가 1 이하인 이진 탐색 트리이다. 

---

# 🧠 핵심 키워드
<!-- 답변을 위해 필요한 핵심 키워드를 적어주세요 -->
- 균형 이진 탐색 트리 (Balanced Binary Search Tree)
AVL 트리는 균형 잡힌 이진 탐색 트리의 일종으로, 모든 노드의 왼쪽 서브트리와 오른쪽 서브트리의 높이 차이가 1 이하로 유지되도록 합니다.
- 균형 팩터 (Balance Factor)
각 노드의 균형 팩터는 왼쪽 서브트리의 높이 - 오른쪽 서브트리의 높이로 정의됩니다. 이 값은 -1, 0, 1로 제한되어야 하며, 이를 통해 트리의 균형을 유지합니다.
- 회전 (Rotation)
트리가 불균형해지면, 트리의 균형을 맞추기 위해 회전을 수행합니다. 회전은 크게 4가지 유형으로 나눌 수 있습니다:
좌측 회전 (Left Rotation)
우측 회전 (Right Rotation)
좌우 회전 (Left-Right Rotation)
우좌 회전 (Right-Left Rotation)
- 삽입 (Insertion)
AVL 트리에서 새로운 노드를 삽입할 때, 삽입 후 균형 팩터를 확인하고, 필요에 따라 회전을 통해 트리의 균형을 맞춥니다.
삭제 (Deletion)
노드를 삭제할 때에도 균형 팩터를 확인하고, 트리의 균형을 맞추기 위해 회전을 사용합니다.
- 높이 (Height)
AVL 트리에서는 각 노드의 높이가 중요한데, 이는 트리의 균형을 유지하는 데 사용됩니다. 노드의 높이는 해당 노드가 포함된 서브트리의 깊이를 의미합니다.
- 시간 복잡도 (Time Complexity)
삽입, 삭제, 탐색 연산은 모두 **O(log n)**의 시간 복잡도를 가집니다. 이는 트리가 균형을 유지하기 때문에 가능하며, 최악의 경우에도 트리의 깊이가 로그 수준으로 제한됩니다.

---

# 🔥 상세 설명
<!-- 답변을 위해 필요한 CS 개념, 원리, 예시 등을 자세히 정리하세요 -->
[AVL 트리 개념]
-AVL 트리는 트리가 비균형 상태로 되면 스스로 노드들을 재배치하여 균형 상태로 만든다->균형 트리가 항상 보장
-시간 복잡도: O(log n)
-균형인수(balance factor)= (왼쪽 서브 트리의 높이) - (오른쪽 서브트리의 높이)
-모든 노드의 균형인수가 ±1 이하이면 AVL 트리이다
 
[AVL 트리의 탐색 연산]
-이진탐색트리와 동일
-O(log2(n))
 
[AVL 트리의 삽입 연산]
- 삽입 시 균형인수가 ±2가 된 가장 가까운 조상노드의 서브트리들에 대하여 다시 균형을 잡아야 한다
- 새로운 노드부터 균형인수가 ±2가 된 가장 가까운 조상 노드까지를 회전시키는 것

---

# 🔗 참고 자료
<!-- 질문과 답변을 준비할 때 참고한 자료, 링크 등을 남겨주세요 -->
- 천인국 · 공용해 · 하상호 지음,『C언어로 쉽게 풀어쓴 자료구조』, 생능출판(2016)
