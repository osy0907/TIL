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

### 깨끗한 코드란 ? ( What Is Clean Code? )
- 깨진 창문 컨셉: 아무도 신경 쓰지 않는 것 같은 인상을 풍긴다 - 나쁜 코드는 나쁜 코드를 유혹한다.
- 테스트 없는 코드는 깨끗하지 않습니다.
- 깨끗한 코드는 항상 주의깊게 신경쓰는 누군가가 작성한 것처럼 보입니다.
- **No duplication, one thing, expressiveness, tiny abstractions**.
- 예상한 대로 작동합니다. 명확하고 간단하며 설득력이 있습니다.

## Schools of Thought

## We Are Authors

- *@author* 필드는 우리가 누구인지 알려줍니다. 우리는 저자다.
- 새 코드를 작성하려면 이전 코드를 읽어야 합니다. 이전 코드가 읽기 쉬우면 새로운 코드도 작성하기 쉬워집니다.
- 코드 읽기와 쓰기의 비율은 10:1입니다.

## The Boy Scout Rule

**Leave the campground cleaner than you found it**.

## 1장을 끝으로..

SRP, OCP, DIP 등 다양한 설계 원칙을 공부해야 한다. 설레인다.

# <a name="meaningful-names">2. Meaningful Names</a>

## Introduction

Names are everywhere in software: variables, functions, args, classes, packages, files...

## 의도를 분명히 밝혀라 ( Use Intention-Revealing Names )

이름은 모든 중요한 질문에 답해야 한다.
- 그것이 존재하는 이유가 무엇인지?
- 그것이 무엇을 하는지?
- 어떻게 사용되는지?


다음과 같이 사용하지 마십시오.
```java
int d; // elapsed time in days
```
그 대신 측정 대상과 단위를 지정하는 이름을 사용하십시오.
```java
int elapsedTimeInDays;
```
의도를 나타내는 이름을 선택하면 코드를 훨씬 더 쉽게 이해하고 변경할 수 있습니다. 이것은 다른 사람과 미래의 자신에게 도움이 됩니다. 이 코드의 목적은 무엇입니까?

From this:
```java
public List<int[]> getThem() {
	List<int[]> list1 = new ArrayList<int[]>();
	for (int[] x : theList)
		if (x[0] == 4)
			list1.add(x);
	return list1;
}
```
We can improve it only with revealing naming:
```java
public List<int[]> getFlaggedCells() {
	List<int[]> flaggedCells = new ArrayList<int[]>();
	for (int[] cell : gameBoard)
		if (cell[STATUS_VALUE] == FLAGGED)
			flaggedCells.add(cell);
	return flaggedCells;
}
```
And it is still better with a Cell class:
```java
public List<Cell> getFlaggedCells() {
	List<Cell> flaggedCells = new ArrayList<Cell>();
	for (Cell cell : gameBoard)
		if (cell.isFlagged())
			flaggedCells.add(cell);
	return flaggedCells;
}
```

## 그릇된 정보를 피하라 ( Avoid Disinformation )

- 여러 계정을 그룹으로 묶을 때, 실제 List가 아니라면, accountList라 명명하지 않는다.
프로그래머에게 List라는 단어는 특수한 의미다. 그러므로 accountGroup, bunchOfAccounts, 아니면 단순히 Accounts라 명명한다.
- *XYZFooBarClassForBlabla* 및 *XYZFooBarClassForBlablable*과 매우 유사한 이름 사용에 주의하십시오.
- 소문자 *l*(1처럼 보임)과 대문자 *O*(0처럼 보임)를 사용하는 것도 도움이 되지 않습니다.

## 의미 있게 구분하라 ( Make Meaningful Distinctions )

숫자 시리즈 이름을 사용하지 마십시오: a1, a2, ... aN

컴파일러를 통과할지라도 연속된 숫자를 덧붙이거나 불용어(noise word)를 추가하는 방식은 적절하지 못하다. 이름이 달라야 한다면 의미도 달라져야 한다.

```java
public static void copyChars(char a1[], char a2[]) {
	for (int i = 0; i < a1.length; i++) {
		a2[i] = a1[i];
	}
}
```

**source**와 **destination**을 인수 이름으로 사용하면 훨씬 더 좋습니다.
노이즈 단어 피하기(Info, Data, a, an, the, variable, table, String):
- ProductInfo와 ProductData는 거의 동일합니다.
- nameString이 name보다 나은가요? 아니요.
  방법에 대해서도 마찬가지입니다.
  프로그래머는 어느함수를 호출해야 할까? getActiveAccount() getActiveAccounts() getActiveAccountInfo()

## 발음하기 쉬운 이름을 사용하라 ( Use Pronounceable Names )

발음하기 어려운 이름은 토론하기도 어렵다. 바보처럼 들리기 십상이다.

```java
// generation date, year, months, day, hour, minute, and second
class DtaRcrd102 {
	private Date genymdhms;
	/* ... */
}
// better:
class Customer {
	private Date generationTimestamp;
	/* ... */
}
```

## 검색하기 쉬운 이름을 사용하라 ( Use Searchable Names )

단일 문자 이름과 숫자 상수는 텍스트 본문에서 찾기가 쉽지 않습니다.

```java
for (int j=0; j<34; j++) {
	s += (t[j]*4)/5;
}
```

검색 가능한 이름이 있을 때 더 좋습니다.

```java
int realDaysPerIdealDay = 4;
const int WORK_DAYS_PER_WEEK = 5;
int sum = 0;
for (int j=0; j < NUMBER_OF_TASKS; j++) {
	int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
	int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
	sum += realTaskWeeks;
}
```

## 인코딩을 피하라 ( Avoid Encodings )

## 헝가리식 표기법 ( Hungarian Notation ), 맴버 변수 접두어 ( Member Preﬁxes )

객체는 강한 타입이며, IDE는 코드를 컴파일하지 않고도 타입 오류를 감지할 정도로 발전했다. 따라서 이제는 헝가리식 표기법이나 기타 인코딩 방식이 오히려 방해가 될 뿐이다. 
옛날에 작성한 구닥다리 코드라는 징표가 되어버렸다...우리는 비지니스 로직에만 집중하기도 바쁘고 그 이외의 것들은 관심 밖으로 밀리기 마련이다.

## 인터페이스 클래스와 구현클래스 ( Interfaces and Implementations )

인터페이스를 꾸미지 않은 상태로 두십시오.
*ShapeFactory* 및 *ShapeFactoryImp*는 *IShapeFactory* 및 *ShapeFactory*보다 우수합니다.

인터페이스 이름은 접두어를 붙이지 않는 편이 좋다고 생각합니다. 접두어 I는 잘해봤자 주의를 흐트리고 나쁘게는 과도한 정보를 제공합니다. 나로서는 내가 다루는 클래스가 인터페이스라는 사실을 남에게 알리고 싶지 않습니다. 클래스 사용자는 그냥 shapeFactory라고만 생각하면 좋겠습니다.

## 자신의 기억력을 자랑하지 마라 ( Avoid Mental Mapping )

`this`가 `that`을 의미한다는 것을 *기억할 수* 있다고 해서 코드를 그런 식으로 작성해야 한다는 의미는 아닙니다.

똑똑한 프로그래머와 전문가 프로그래머 사이에서 나타나는 차이점은 전문가 프로그래머는 **명료함이 최고**라는 사실을 이해합니다. 전문가 프로그래머는 자신의 능력을 좋은 방향으로 사용해 남들이 이해하는 코드를 작성합니다.

## Class Names

클래스 이름은 동사가 아닌 **명사**여야 합니다. Manager, Processor, Data, or Info와 같은 단어를 피하십시오.
좋은 이름은 Customer, WikiPage, Account, AddressParser일 수 있습니다.

## Method Names

메소드에는 postPayment, deletePage, save...와 같은 동사 또는 동사 구 이름이 있어야 합니다.
접근자 (Accessor), 변경자 (Mutator), 조건자 (Predicate)는 javabean 표준에 따라 값 앞에 get, set, is를 붙입니다.

```java
String name = employee.getName();
customer.setName("oh");
if (payCheck.isPosted())...
```

생성자가 오버로드되면 인수를 설명하는 이름으로 정적 팩토리 메서드를 사용합니다.

```java
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
```

아래보다 위가 낫습니다.

```java
Complex fulcrumPoint = new Complex(23.0);
```