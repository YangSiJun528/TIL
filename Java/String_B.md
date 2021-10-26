# **String**

- String은 불변(immutable)의 속성을 갖는다. → 멀티쓰레드 환경에서 안전하다(thread-safe)
- 변하지 않는 문자열을 자주 사용하는 경우 좋은 성능을 보여준다.
- 문자열을 수정하는 시점에 새로운 String Instance가 생성된다 → 문자열 추가,수정,삭제 등의 연산이 빈번하게 발생 하는 알고리즘에 String Class를 사용하면 힙 메모리(Heap)에 많은 가비지(Garbage)가 생성되어 성능에 부정적인 영향을 준다.

# **StringBuffer**

- 가변(mutable)성을 가진다.
- 문자열의 변경이 잦은 경우 좋은 성능을 보인다.
- StringBuffer 는 동기화를 지원하여 멀티쓰레드 환경에서 안전하다.(thread-safe)

# **StringBuffer**

- 가변(mutable)성을 가진다.
- 문자열의 변경이 잦은 경우 좋은 성능을 보인다.
- StringBuilder는 동기화를 지원하지 않는다 → 단일쓰레드에서 성능이 StringBuffer에 비해 좋다.
