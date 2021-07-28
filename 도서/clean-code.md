# Clean Code
Notes on the book Clean Code - A Handbook of Agile Software Craftsmanship by Robert C. Martin

# Index
1. [Clean Code](#clean-code)
2. [Meaningful Names](#meaningful-names)
3. [Functions](#functions)
4. [Comments](#comments)
5. [Formatting](#formatting)
6. [Objects and Data Structures](#objects-and-data-structures)
7. [Error Handling](#error-handling)
8. [Boundaries](#boundaries)
9. [Unit Tests](#unit-tests)
10. [Classes](#classes)
11. [Systems](#systems)
12. [Emergence](#emergence)
13. [Concurrency](#concurrency)
14. [Successive Reﬁnement](#successive-refinement)
15. [JUnit Internals](#junit-internals)
16. [Refactoring SerialDate](#refactoring-serialdate)
17. [Smells and Heuristics](#smells-and-heuristics)


# <a name="clean-code">1. Clean Code</a>

### 코드가 존재하리라 ( There Will Be Code )

Nonsense : 앞으로 코드가 사라질 가망은 전혀 없다! 왜? 코드는 요구사항을 상세히 표현하는 수단이니까! 어느 수준에 이르면 코드의 도움없이 요구사항을 상세하게 표현하기란 불가능하다. 추상화도 불가능하다. 정확히 명시하는 수밖에 없다. 기계가 실행할 정도로 상세하게 요구사항을 명시하는 작업, 바로 이것이 프로그래밍이다. 이렇게 명시한 결과가 바로 코드다.
앞으로 우리 프로그래밍 언어에서 추상화 수준은 점차 높아지리라 예상한다.

궁극적으로 코드는 요구사항을 표현하는 언어라는 사실을 명심한다.

### 나쁜 코드 ( Bad Code )

잘못된 코드는 회사를 망칠 수 있습니다.
나쁜 코드에는 변명의 여지가 없고 이유도 없습니다. 상사가 시간을 주지 않고 더 많은 백로그의 이야기를 끝내기 위해 더 빨리 끝내고 싶어합니다...
하지만 나중은 결코 오지 않습니다.

### 나쁜 코드로 치르는 대가 ( The Total Cost of Owning a Mess )

생산성이 0을 향해 나아갈 것이다.

### 원대한 재설계의 꿈 ( The Grand Redesign in the Sky )

다른 팀과 함께 시스템을 재설계하기로 결정하면 다음과 같다.
- 한 레이스의 두 팀
- 동일한 기능을 제공하려면 수년간의 개발이 필요하다.
- 초창기 사람들이 회사를 떠나고 새로운 개발자가 다시 시스템을 재설계를 하고 싶어한다.

왜? 다년간 개발해온 시스템이 다시... 또 너무 엉망이라서..

### 태도 ( Attitude )

코드가 왜 그렇게 되었을까? 요구 사항?, 어리석은 관리자?, 일정 ?? **아니요**.
그것은 모두 비전문성에 관한 것 .
대부분의 관리자는 좋은 코드를 원합니다. 그렇지 않다면 우리는 그들이 나쁜 코드의 위험을 이해하도록 도와야 합니다.


### 원초적 난제 ( The Primal Conundrum )

빨리 가는 유일한 방법은 코드를 최대한 깔끔하게 만드는 것입니다.

### 깨끗한 코드라는 예술 ? ( The Art of Clean Code? )

깨끗한 코드를 작성하려면 훈련이 필요합니다. 우리는 "코드 센스"를 얻기 위해 열심히 노력해야 합니다.