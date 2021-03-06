>Robert C. Martin의 [Clean Code]를 공부하며 기록한 내용 입니다.

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

## 기발한 이름은 피하라 ( Don’t Be Cute )

속어를 사용하지 마십시오!: kill() 대신 whack() 이라 부르거나 Abort() 대신 eatMyShort()라고 부르는 것.

**의도를 분명하고 솔직하게 표현하라.**

## 한 개념에 한 단어를 사용하라 ( Pick One Word per Concept )

- 추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다.
- fetch, retrieve, get, etc 중에서 **get()** 을 선택하는 경우 항상(일관되게) 사용하십시오.

## 말장난을 하지 마라 ( Don’t Pun )

한 단어를 두 가지 목적으로 사용하지 마십시오. 다른 개념에 같은 단어를 사용한다면 그것은 말장난에 불과합니다.

**Make your code as easy as possible to understand.**

## 해법 영역에서 가져온 이름을 사용하라 ( Use Solution Domain Names )

패턴 이름 사용: Factory, Visitor, Decorator 등. 코드를 읽는 사람은 프로그래머일 것이므로 일반적으로 이해되는 용어가 있으면 사용해도 좋습니다.
예시로 Visitor 패턴에 친숙한 프로그래머는 AccountVisitor 라는 이름을 금방 이해합니다. JobQueue 라고 쓴다고 해서 모르는 프로그래머가 있을까요? 기술 개념에는 기술 이름이 가장 적합한 선택입니다.

## 문제 영역에서 가져온 이름을 사용하라 ( Use Problem Domain Names )

적절한 '프로그래머 용어'가 없다면 문제 영역에서 이름을 가져옵니다. 그러면 코드를 보수하는 프로그래머가 분야 전문가에게 의미를 물어 파악할 수 있습니다.

우수한 프로그래머라와 설계자라면 해법 영역과 문제 영역을 구분할 줄 알아야 합니다. 문제 영역 개념과 관련이 깊은 코드라면 문제 영역에서 이름을 가져와야 합니다.

## 의미 있는 맥락을 추가하라 ( Add Meaningful Context )

스스로 의미가 분명한 이름이 있지만 대다수 이름은 그렇지 못하다. 그래서 클래스, 함수, 이름 공간에 넣어 맥락을 부여한다. 모든 방법이 실패하면 마지막 수단으로 접두어를 붙인다.
예를들어, firstName, lastName, street, postalCode 등의 변수들을 보면 주소라는 사실을 알아챕니다. 하지만 맥락의 문제가 있는 경우 addrFirstName, addrLastName 등의 접두사를 추가할 수 있습니다.
그러나 차라리 Address Class 를 만드는 것이 더 나은 맥락을 가지게 됩니다.

메서드에 맥락이 불분명한 변수가 많을 때 맥락을 개선하면 함수를 쪼개기가 쉬워지므로 알고리즘도 좀 더 명확해집니다.

## 불필요한 맥락을 없애라 ( Don’t Add Gratuitous Context )

특정 맥락에 속한다고 모든 클래스/메서드에 접두사를 사용하지 마십시오.
예를들어, 고급 휘발유 충전소 ( Gas Station Deluxe ) 어플리케이션을 짠다고 가정하면 GSDAccountAddress... 좋은 이름이 아닙니다.

**일반적으로 짧은 이름이 일반적으로 긴 이름보다 낫습니다**. 단, 의미가 분명한 경우에 한해서 입니다.

## 마치면서 ( Final Words )

이러한 규칙을 따라서 리팩터링 하십시오. 다른 사람이 짠 코드를 손본다면 리팩터링 도구를 사용해 문제 해결 목적으로 이름을 개선하십시오.

단기적인 효과는 물론 장기적인 이익도 보장합니다.

# <a name="functions">3. Functions</a>

- 어떤 프로그램이든 가장 기본적인 단위가 함수입니다.
- 함수는 투명하고 명확해야 합니다.

## 작게 만들어라! ( Small! )

- 함수를 만드는 첫째 규칙은 '작게!'다. 함수를 만드는 둘째 규칙은 '더 작게!'다. ( 모든 함수가 2, 3, 4줄 정도이고 각 함수가 너무도 명백하면 나도 감탄하지 않을까?)
- if / else 문, while 문 등에 들어가는 블록은 한 줄이면 좋습니다. 그러면 바깥을 감싸는 함수가 작아질 뿐 아니라, 블록 안에서 호출하는 함수 이름을 적절히 짓는다면, 코드를 이해하기도 쉬워집니다. 이 말은 중첩 구조가 생길만큼 함수가 커져서는 안 된다는 뜻입니다.  
- 함수에서 들여쓰기 수준은 1단이나 2단을 넘어서면 좋지 않습니다.

## 한 가지만 해라! ( Do One Thing ! )

```
함수는 한 가지를 해야 한다. 그 한 가지를 잘 해야 한다. 그 한 가지만을 해야 한다.
```

- 지정된 함수 이름 아래에서 추상화 수준이 하나인 단계만 수행한다면 그 함수는 한 가지 작업만 하는 것이 됩니다. 우리가 함수를 만드는 이유는 큰 개념을 (다시말해, 함수 이름을) 다음 추상화 수준에서 여러 단계로 나눠 수행하기 위해서가 아니었습니까?
- 함수가 '한 가지' 만 하는지 판단하는 방법이 하나 더 있습니다. 단순히 다른 표현이 아니라 의미 있는 이름으로 다른 함수를 추출할 수 있다면 그 함수는 여러 작업을 하는 셈입니다.

우리가 함수를 만드는 이유는 큰 개념을 (다시말해, 함수 이름을) 다음 추상화 수준에서 여러 단계로 나눠 수행하기 위해서가 아니었습니까?

## 함수 내 섹션 ( Sections within Functions )

섹션으로 나뉘는 함수는 아마도 한 가지 이상의 일을 할 것입니다.
한 가지 작업만 하는 함수는 자연스럽게 섹션으로 나누기 어렵습니다.

## 함수 당 추상화 수준은 하나로! ( One Level of Abstraction per Function! )

함수가 확실히 '한 가지' 작업만 하려면 함수 내 모든 문장의 추상화 수준이 동일해야 합니다. (추상화 수준을 혼합하지 마십시오.)

- 예시로 ```getHtml()```은 추상화 수준히 아주 높습니다. 반면, ```String pagePathName = PathParser.render(pagepath);```는 추상화 수준이 중간입니다. 그리고 ```.append("/n")```와 같은 코드는 추상화 수준이 아주 낮습니다.

한 함수 내에 추상화 수준을 섞으면 코드를 읽는 사람이 헷갈립니다. 특정 표현이 근본 개념인지 아니면 세부사항인지 구분하기 어려운 탓입니다. 하지만 문제는 이 정도로 그치지 않습니다. 근본 개념과 세부사항을 뒤섞기 시작하면, 깨어진 창문처럼 사람들이 함수에 세부사항을 점점 더 추가하게 됩니다.

## 위에서 아래로 코드 읽기: 내려가기 규칙 ( Reading Code from Top to Bottom: The Stepdown Rule )

코드는 위에서 아래로 이야기처럼 읽혀야 좋습니다. 한 함수 다음에는 추상화 수준이 한 단계 낮은 함수가 옵니다. 즉, 위에서 아래로 프로개름을 읽으면 함수 추상화 수준이 한 번에 한 단계씩 낮아집니다. 이것을 내려가기 규칙이라 부릅니다.
하지만 추상화 수준이 하나인 함수를 구현하기란 쉽지 않습니다. 핵심은 짧으면서도 '한 가지'만 하는 함수입니다.
위에서 아래로 문단을 읽어내려 가듯이 코드를 구현하면 추상화 수준을 일관되게 유지하기가 쉬워집니다.


## Switch 문 ( Switch Statements )

Switch 문은 항상 N개의 작업을 수행합니다.
불행하게도 완전히 피할 방법은 없습니다. 하지만 각 switch 문을 저차원 클래스에 숨기고 절대로 반복하지 않는 방법이 있습니다. 다형성(polymorphism)을 이용합니다.

```java
public Money calculatePay(Employee e) throws InvalidEmployeeType {
    switch (e.type) {
        case COMMISSIONED:
            return caclculateCommissionedPay(e);
        case HOURLY:
            return calculateHourlyPay(e);
        case SALARIED:
            return calculateSalariedPay(e);
        default:
            throw new InvalidEmployeeType(e.type);
    }
}
```

위 함수에는 몇 가지 문제가 있습니다.
1. 함수가 길다.
2. '한 가지' 작업만 수행하지 않는다.
3. SRP를 위반한다. 코드를 변경할 이유가 여럿이기 때문이다.
4. OCP를 위반한다. 새 직원 유형을 추가할 때마다 코드를 변경하기 때문이다.

```java
public abstract class Employee {
    public static boolean isPayday();

    public static Money calculatePay();

    public static void deliverPay(Money pay);
}

```

```java
public interface EmployeeFactory {
    public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}

public class EmployeeFactoryImpl implements EmployeeFactory {
    public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
        switch (r.type) {
            case COMMISSIONED:
                return new CommissionedEmployee(r);
            case HOURLY:
                return new HourlyEmployee(r);
            case SALARIED:
                return new SalariedEmployee(r);
            default:
                throw new InvalidEmployeeType(r.type);
        }
    }
}
```

- switch 문을 Abstract Factory에 꽁꽁 숨겨서 아무에게도 보여주지 않습니다.
- Factory는 Switch 문을 사용해 적절한 Employee 파생 클래스의 인스턴스를 생성합니다.
- calculatePay(), isPayday(), deliverPay() 등과 같은 함수는 Employee 인터페이스를 거쳐 호출 됩니다.
- 그러면 다형성으로 인해 실제 파생 클래스의 함수가 실행됩니다.

이렇게 쓰이는 swich 문을 단 한 번만 참아줍니다. 대신 조건으로 다형적 객체를 생성하는 코드 안에서 입니다.
이렇게 상속 관계로 숨긴 후에는 절대로 다른 코드에 노출하지 않습니다.

## 서술적인 이름을 사용하라! ( Use Descriptive Names )

좋은 이름이 주는 가치는 아무리 강조해도 지나치지 않습니다. 워드가 말했던 원칙을 기억합니까? "코드를 읽으면서 짐작했던 기능을 각 루틴이 그대로 수행한다면 깨끗한 코드라 불러도 되겠다".
한 가지만 하는 작은 함수에 좋은 이름을 붙인다면 이런 원칙을 달성함에 있어 이미 절반은 성공했습니다. 함수가 작고 단순할수록 서술적인 이름을 고르기도 쉬워집니다.

이름과 일관성을 유지하고 항상 같은 동사, 명사 등을 사용하십시오.
*includeSetupAndTeardownPages, includeSetupPages, includeSetupPage...*

## 함수 인수 ( Function Arguments )

함수에서 이상적인 인수 0개(무항)입니다.
다음은 1개(단항)고, 다음은 2개(이항)입니다. 3개(삼항)는 가능한 피하는 편이 좋습니다. 4개 이상(다항)은 특별한 이유가 필요합니다. 특별한 이유가 있어도 사용하면 안됩니다.

테스트 관점에서 보면 인수는 더 어렵습니다. 갖가지 인수 조합으로 함수를 검증하는 테스트 케이스를 작성한다고 상상해보십시오.

## 많이 쓰는 단항 형식 ( Common Monadic Forms )

- 하나는 인수에 질문을 던지는 경우.

```java
boolean fileExists("MyFile")
```

- 인수를 뭔가로 변환해 결과를 반환하는 경우.

```java
InputStream fileOpen("MyFile"); // string 형의 파일 이름을 InputStream 으로 변환합니다.
```

  
## 플래그 인수 ( Flag Arguments )

플래그 인수(true|false)는 보기 흉합니다. 해당 함수는 참이면 한 가지 작업을 수행하고 거짓이면 다른 작업을 수행합니다.
함수를 둘로 나눕니다.
*render(boolean isSuite) => renderForSuite() , renderForSingleTest()*

## 이항 함수 ( Dyadic Functions )

인수가 2개인 함수는 인수가 1개인 함수보다 이해하기 어렵습니다.

`writeField(name)` better than `writeField(outputStream, name)`

어떻게 단항함수로 바꿀까요? writeField 메서드를 outputStream 클래스 구성원으로 만들어 outputStream, writeField(name)으로 호출합니다. 아니면 outputStream 을 현재 클래스 구성원 변수로 만들어 인수로 넘기지 않습니다.
아니면 FieldWriter라는 새 클래스를 만들어 구성자에 outputStream 을 받고 write 메서드를 구현합니다.

## 삼항 함수 ( Triads )

인수가 3개인 함수는 인수가 2개인 함수보다 훨씬 더 이해하기 어렵습니다.
순서, 주춤, 무시로 야기되는 문제가 두 배 이상 늘어납니다.
*assertEquals(msg, expected, actual)* ... now the msg seems to be the expected value.

## 인수 객체 ( Argument Objects )

인수가 2-3개 필요하다면 일부를 독자적인 클래스 변수로 선언할 가능성을 짚어 봅니다.
```java
makeCircle(double x, double y, double radius) =>  makeCircle(Point center, double radius);
```
이러한 예시가 작은 추상화를 이해하는데 도움이 되지 않을까?

## 인수 목록 ( Argument Lists )

때로는 인수 개수가 가변적인 함수도 필요합니다.
`String.format` 메서드가 좋은 예시입니다.

```java
// 밑의 예시처럼 가변 인수를 전부를 동등하게 취급하면 List 형 인수 하나로 취급할 수 있다.
String.format("%s worked %.2f", name, hours);

// 실제로 String.format 선언부
public String format(String foramt, Object... args) // 이항 함수
```

## 동사와 키워드 ( Verbs and Keywords )

함수의 의도나 인수의 순서와 의도를 제대로 표현하려면 좋은 함수이름이 필수 입니다. 단항 함수는 함수와 인수가 동사/명사 쌍을 이뤄야 합니다.
```java
write(name) => writeField(name)
```

함수 이름에 키워드를 추가하는 형식으로 명확하게 할 수 있습니다. 그러면 인수 순서를 기억할 필요도 없어집니다.
```java
assertEquals => assertExpectedEqualsActual
```

## 부수 효과를 일으키지 마라! ( Have No Side Effects )

부수 효과는 거짓말입니다. 함수에서 한 가지를 하겠다고 약속하고선 나몰래 다른 것도 하기 때문입니다.

```java
public class UserValidator {
	private Cryptographer cryptographer;
	public boolean checkPassword(String userName, String password) { 
		User user = UserGateway.findByName(userName);
		if (user != User.NULL) {
			String codedPhrase = user.getPhraseEncodedByPassword(); 
			String phrase = cryptographer.decrypt(codedPhrase, password); 
			if ("Valid Password".equals(phrase)) {
				Session.initialize();
				return true; 
			}
		}
		return false; 
	}
}
```
```Session.initialize();```는 함수명과 맞지 않는 부수 효과입니다.
위의 함수명은 checkPasswordAndInitializeSession() 이 더 낫습니다. 하지만 여전히 함수가 '한 가지' 만 한다는 규칙을 위반하기는 합니다. 

## 출력 인수 ( Output Arguments )

OOP로 피해야 합니다. 
함수에서 상태를 변경해야 한다면 함수가 속한 객체 상태를 변경하는 방식을 택합니다.

## 명령과 조회를 분리하라 ( Command Query Separation )

함수는 뭔가를 수행하거나 뭔가에 답하거나 둘 중 하나만 해야 합니다. 둘 다 하면 안됩니다. 객체 상태를 변경하거나 아니면 객체 정보를 반환하거나 둘중 하나 입니다.
둘 다 하면 혼란을 초래합니다.

## 오류 코드보다 예외를 사용하라 ( Prefer Exceptions to Returning Error Codes )

명령 함수에서 오류 코드를 반환하는 방식은 명령/조회 분리 규칙을 미묘하게 위반합니다. 

```java
if (deletePage(page) == E_OK) {
	if (registry.deleteReference(page.name) == E_OK) {
		if (configKeys.deleteKey(page.name.makeKey()) == E_OK) {
			logger.log("page deleted");
		} else {
			logger.log("configKey not deleted");
		}
	} else {
		logger.log("deleteReference from registry failed"); 
	} 
} else {
	logger.log("delete failed"); return E_ERROR;
}
```
위 코드는 동사/형용사 혼란을 일으키지 않는 대신 여러 단계로 중첩되는 코드를 야기합니다. 오류 코드를 반환하면 호출자는 오류 코드를 곧바로 처리해야 한다는 문제에 부딪힙니다.

```java
try {
    deletePage(page);
    registry.deleteReference(page.name);
    configKeys.deleteKey(page.name.makeKey());
} catch (Exception e) {
    logError(e);
}

```
반면 오류 코드 대신 예외를 사용하면 오류 처리 코드가 원래 코드에서 분리되므로 코드가 깔끔해집니다.

## Try/Catch 블록 뽑아내기 ( Extract Try/Catch Blocks )

Try/Catch 블록은 원래 추합니다. 코드 구조에 혼란을 일으키며, 정상 동작과 오류 처리 동작을 뒤섞습니다. 그러므로 Try/Catch 블록을 별도 함수로 뽑아내는 편이 좋습니다. 

```java
public void delete(Page page) {
    try {
        deletePageAndAllReferences(page);
    } catch (Exception e) {
        logError(e);
    }
}

private void deletePageAndAllReferences(Page page) throws Exception {
        deletePage(page);
        registry.deleteReference(page.name);
        configKyes.deleteKey(page.name.makeKey());
}

private void logError(Exception e) {
        logger.log(e.getMessage());
}
```

정상 동작과 오류 처리 동작을 분리하면 코드를 이해하고 수정하기 쉬워집니다.

## 오류 처리도 한 가지 작업이다. ( Error Handling Is One Thing )

함수는 '한 가지' 작업만 해야 합니다. 오류 처리도 '한 가지' 작업에 속합니다. 그러므로 오류를 처리하는 함수는 오류만 처리해야 마땅합니다.

## Error.java 의존성 자석 ( The Error.java Dependency Magnet )

오류 코드를 반환한다는 이야기는, 클래스든 열거형 변수든, 어디선가 오류 코드를 정의한다는 뜻입니다.

```java
public enum Error { 
	OK,
	INVALID,
	NO_SUCH,
	LOCKED,
	OUT_OF_RESOURCES, 	
	WAITING_FOR_EVENT;
}
```

위와 같은 클래스는 의존성 자석입니다. Error enum 이 변한다면 Error enum 을 사용하는 클래스 전부를 다시 컴파일하고 다시 배치해야합니다. 그래서 Error 클래스 변경이 어려워집니다.

오류 코드 대신 예외를 사용하면 새 예외는 Exception 클래스에서 파생됩니다. 따라서 재컴파일/재배치 없이도 새 예외 클래스를 추가할 수 있습니다.


## 반복하지 마라 ( Don’t Repeat Yourself )

중복은 소프트웨어의 모든 악의 근원일 수 있습니다.

- 코드 길이가 늘어납니다.
- 알고리즘이 변하면 중복된 코드 모두 수정해야 합니다.
- 오류가 발생할 확률도 몇 배로 높습니다.

## 구조적 프로그래밍 ( Structured Programming )

모든 함수와 함수 내 모든 블록에 입구와 출구가 하나만 존재해야 합니다.
함수가 아주 클 때 구조적 프로그래밍의 목표와 규율이 효과적 입니다.

## 함수를 어떻게 짜죠? ( How Do You Write Functions Like This? )

소프트웨어를 짜는 행위는 여느 글짓기와 비슷합니다. 논문이나 기사를 작성할 때는 먼저 생각을 기록한 후 읽기 좋게 다듬습니다. 초안은 대게 서투르고 어수선하므로 원하는 대로 읽힐 때까지 말을 다듬고 문장을 고치고 문단을 정리합니다.

- 서투른 코드에도 단위 테스트 케이스를 만듭니다.
- 그런 다음 코드를 다듬고, 함수를 만들고, 이름을 바꾸고, 중복을 제거하고, 메서드를 줄이고 순서를 바꾸고 때로는 쪼개기도 합니다.
- 이와중에도 코드는 항상 단위 테스트를 통과합니다.

## 결론 ( Conclusion )

모든 시스템은 특정 응용 분야 시스템을 기술할 목적으로 프로그래머가 설계한 도메인 특화 언어 (Domain Specific Language) 로 만들어집니다.
함수는 그 언어에서 동사며, 클래스는 명사입니다.

대가(master) 프로그래머는 시스템을(구현할) 프로그램이 아니라 (풀어갈) 이야기로 여깁니다. 프로그래밍 언어라는 수단을 사용해 좀 더 풍부하고 좀 더 표현력이 강한 언어를 만들어 이야기를 풀어갑니다.
시스템에서 발생하는 모든 동작을 설명하는 함수 계층이 바로 그언어에 속합니다.

이 장에서 설명한 규칙을 따른다면 길이가 짧고, 이름이 좋고, 체계가 잡힌 함수가 나옵니다.
하지만 진짜 목표는 시스템이라는 이야기를 풀어가는 데 있다는 사실을 명심하기 바랍니다. 여러분이 작성한ㄴ 함수가 분명하고 정확한 언어로 깔끔하게 같이 맞아떨어져야 이야기를 풀어가기가 쉬워진다는 사실을 기억하기 바랍니다.

# <a name="comments">4. Comments</a>

프로그래밍 언어로 충분히 표현할 수 있다면 주석이 필요하지 않을 것 입니다.
주석이 필요하다는 것은 자신의 코드의 표현력이 없다는 사실을 푸념해야 마땅합니다.

코드는 변화하고 진화합니다. 일부가 여기서 저기로 옮겨지기도 합니다. 조각이 나뉘고 갈라지고 합쳐지면서 괴물로 변하기도 합니다.
불행하게도 주석이 언제나 코드를 따라가지 않습니다. 따라가지 못합니다. 주석이 코드에서 분리되어 점점 더 부정확한 고아로 변하는 사례가 너무도 흔합니다.

## 주석은 잘못된 코드를 보완하지 않습니다 ( Comments Do Not Make Up for Bad Code )

"Ooh, I would better comment that!" => No! You would be better clean it!

## 좋은 주석 ( Good Comments )

진정으로 좋은 댓글은 쓰지 않을 방법을 찾는 것 입니다.

### 법적인 주석 ( Legal Comments )

저작권 정보와 소유권 정보는 필요하고도 타당합니다. 소스 파일 첫머리 들어가는 주석이 반드시 계약 조건이나 법적인 정보일 필요는 없습니다. 모든 조항과 조건을 열거하는 대신에, 가능하다면, 표준 라이선스나 외부 문서를 참조해도 됩니다.

```java
// Copyright (C) 2003, 2004, 2005 by Object Montor, Inc. All right reserved.
// GNU General Public License
```

### 정보를 제공하는 주석 ( Informative Comments )

```java
// 테스트 중인 Responder 인스턴스를 반환
protected abstract Responder responderInstance();
```

물론 이 주석도 함수 이름에 정보를 담아 responderBeingTested로 바꾸면 없앨 수 있습니다. 

더 나은 예:

```java
// kk:mm:ss EEE, MMM dd, yyyy 형식이다.
Pattern timeMatcher = Pattern.compile("\\d*:\\d*\\d* \\w*, \\w*, \\d*, \\d*");
```

### 의도를 설명하는 주석 ( Explanation of Intent )

때로는 주석은 구현을 이해하게 도와주는 선을 넘어 결정에 깔린 의도까지 설명합니다.

```java
// 스레드를 대량 생성하는 방법으로 어떻게든 경쟁 조건을 만들려 시도한다.
for (int i = 0; i > 2500; i++) {
    WidgetBuilderThread widgetBuilderThread =
        new WidgetBuilderThread(widgetBuilder, text, parent, failFlag);
    Thread thread = new Thread(widgetBuilderThread);
    thread.start();
}
```

### 결과를 경고하는 주석 Warning of Consequences 

다른 프로그래머에게 경고할 목적으로 주석을 사용하는 경우에도 유용하게 쓰일 수 있습니다.

```java
 // 여유 시간이 충분하지 않다면 실행하지 마십시오.
 public void _testWithReallyBigFile() {
     ...
 }
```

```java
 public static SimpleDateFormat makeStanardHttpDateFormat() {
     // SimpleDateFormat은 스레드에 안전하지 못하기 때문에 각 인스턴스를 독립적으로 생성해야 한다.
     SimpleDateFormat df = new SimpleDateFormat(".......");
     return df;
 }
```

### TODO Comments

```java
// TODO-MdM 현재 필요하지 않다.
// 체크아웃 모델을 도입하면 함수가 필요 없다.
protected VersionInfo makeVersion() throws Exception {
    return null;
}
```

### 중요성을 강조하는 주석 ( Ampliﬁcation )

```java
String listItemContent = match.group(3).trim();
// 여기서 trim은 정말 중요하다. trim 함수는 문자열에서 시작 공백을 제거한다.
// 문자열에 시작 공백이 있으면 다른 문자열로 인식되기 때문이다.
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));String listItemContent = match.group(3).trim();
```

### 공개 API 에서 Javadocs ( Javadocs in Public APIs )

설명이 잘 된 공개 API 는 참으로 유용하고 만족스럽습니다. 표준 자바 라이브러리에서 사용한 Javadocs 가 좋은 예시 입니다.
하지만 이 장에서 제시하는 나머지 충고도 명심하기 바랍니다. 여느 주석과 마찬가지로 Javadocs 역시 독자를 오도하거나, 잘못 위치하거나, 그릇된 정보를 전달할 가능성이 존재합니다.

## 나쁜 주석 ( Bad Comments )

### 주절거리는 주석 ( Mumbling )

```java
public void loadProperties() {
    try {
        String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
        FileInputStream propertiesStream = new FileInputStream(propertiesPath);
        loadedProperties.load(propertiesStream);
    } catch (IOException e) {
        // 속성 파일이 없다면 기본값을 모두 메모리로 읽어 들였다는 의미다.
    }
}
```

catch 블록에 있는 주석은 저자에게야 의미가 있겠지만 다른 사람들에게는 전해지지 않습니다. 저 주석의 의미를 알아내려면 다른 코드를 뒤져보는 수밖에 없다. 이해가 안되어 다른 모듈까지 뒤져야 하는 주석은 제대로 된 주석이 아닙니다.

### 같은 이야기를 중복하는 주석 ( Redundant Comments ) 

코드 내용을 그대로 중복하는 주석이 있습니다. 전혀 필요없습니다.

```java
// this.closed가 true일 때 반환되는 유틸리티 메서드다.
// 타임아웃에 도달하면 예외를 던진다.
public synchronized void waitForClose(final long timeoutMillis) throws Exception {
    if (!closed) {
        wait(timeoutMillis);
        if (!closed) {
            throw new Exception("MockResponseSender could not be closed");
        }
    }
}
```

### 오해할 여지가 있는 주석 ( Misleading Comments )

위 코드를 다시 봅니다. 중복이 많으면서도 오해할 여지가 살짝 있습니다.
this.closed 가 true 로 변하는 순간에 메서드는 반환되지 않습니다.
this.closed 가 true 여야 메서드는 반환됩니다.
아니면 무조건 타임아웃을 기다립니다 this.closed 가 그래도 true 가 아니면 예외를 던집니다. 주석에 담긴 ‘살짝 잘못된 정보’로 인해 어느 프로그래머가 경솔하게 함수를 호출해 자기 코드가 아주 느려진 이유를 못찾게 되는 것 입니다.

### 뜻을 그대로 위임하는 또는 의무적으로 다는 주석 ( Mandated Comments )

모든 함수에 Javadocs 를 달거나 모든 변수, 속성에 주석을 달아야 한다는 규칙은 어리석기 그지없습니다.
이런 주석은 코드를 복잡하게 만들며, 거짓말을 퍼뜨리고, 혼동과 무질서를 초래합니다.
아래와 같은 주석은 아무 가치도 없습니다.

```java
/**
 *
 * @param title CD 제목
 * @param author CD 저자
 * @param tracks CD 트랙 숫자
 * @param durationInMinutes CD 길이(단위: 분)
 */
public void addCD(String title, String author, int tracks, int durationInMinutes) {
    CD cd = new CD();
    cd.title = title;
    cd.author = author;
    cd.tracks = tracks;
    cd.duration = durationInMinutes;
    cdList.add(cd);
}
```

### 이력을 기록하는 주석 ( Journal Comments )

지금은 소스 코드 관리 시스템이 있으니 전혀 필요없습니다.
```java
* 변경 이력 (11-Oct-2001부터)
* ------------------------------------------------
* 11-Oct-2001 : 클래스를 다시 정리하고 새로운 패키징
* 05-Nov-2001: getDescription() 메소드 추가
* 이하 생략
```

### 있으나 마나한 주석 ( Noise Comments ) 

```java
/*
 * 기본 생성자
 */
protected AnnualDateRule() {

}
```

### 함수나 변수로 표현할 수 있다면 주석을 달지 마라 ( Don’t Use a Comment When You Can Use a Function or a Variable )

```java
// 전역 목록 <smodule>에 속하는 모듈이 우리가 속한 하위 시스템에 의존하는가?
if (module.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

주석을 제거하고 다시 표현하면 다음과 같습니다.

```java
ArrayList moduleDependencies = smodule.getDependSubSystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

### 위치를 표시하는 주석 ( Position Markers )

```java
// Actions ////////////////////////////////////////////////
```

극히 드물지만 위와 같은 배너 아래 특정 기능을 모아놓으면 유용한 경우도 있긴 있습니다.
하지만 일반적으로 위와 같은 주석은 가독성만 낮추므로 제거해야 마땅합니다.
특히 뒷부분에 슬래시(/)로 이어지는 잡음은 제거하는 편이 좋습니다.
너무 자주 사용하지 않는다면 배너는 눈에 띄며 주의를 환기 합니다. 그러므로 반드시 필요할 때만, 아주 드물에 사용하는 편이 좋습니다. 배너를 남용하면 독자가 흔한 잡음으로 여겨 무시합니다.

### 닫는 괄호에 다는 주석 ( Closing Brace Comments )

중첩이 심하고 장황한 함수라면 의미가 있을지도 모르지만 (우리가 선호하는) 작고 캡슐화된 함수에는 잡음일 뿐입니다.
그러므로 닫는 괄호에 주석을 달아야겠다는 생각이 든다면 대신에 함수를 줄이려 시도하십시오.

### 공로를 돌리거나 저자를 표시하는 주석 ( Attributions and Bylines )

소스 코드 관리 시스템은 누가 언제 무엇을 추가했는지 귀신처럼 기억하기 때문에 저자 이름으로 코드를 오염시킬 필요가 없습니다.
주석이 있으면 다른 사람들이 코드에 관해 누구한테 물어볼지 알기 때문에 아래와 같은 주석이 유용하다 여길지도 모르겠습니다.
하지만 현실적으로 이런 주석을 그냥 오랫동안 코드에 방치되어 점차 부정확하고 쓸모없는 정보로 변하기 쉽습니다.

```java
/* 릭이 추가함 */ 
```

### 주석으로 처리한 코드 ( Commented-Out Code )

```java
this.bytePos = writeBytes(pngIdBytes, 0);
//hdrPos = bytePos;
writeHeader();
writeResolution();
//dataPos = bytePos;
if (writeImageData()) {
    wirteEnd();
    this.pngBytes = resizeByteArray(this.pngBytes, this.maxPos);
} else {
    this.pngBytes = null;
}
return this.pngBytes;
```

1960년대 즈음에는 주석으로 처리한 코드가 유용했었지만 우리는 우수한 소스 코드 관리 시스템을 사용하기 때문에 우리를 대신에 코드를 기억해준다. 그냥 삭제하십시오. 잃어버릴 염려는 없습니다. 약속합니다.

### HTML 주석 ( HTML Comments )

소스 코드에서 HTML 주석은 혐오 그 자체입니다.
HTML 주석은 (주석을 읽기 쉬워야 하는) 편집기/IDE에서조차 읽기 어렵습니다.
(javadocs와 같은) 도구로 주석을 뽑아 웹 페이지에 올릴 작정이라면 주석에 HTML 태그를 삽입해야 하는 책임은 프로그래머가 아니라 도구가 져야 합니다. 

### 전역 정보 ( Nonlocal Information )

주석을 달아야 한다면 근처에 있는 코드만 기술하십시오. 시스템의 전반적인 정보를 기술하지 마라. 해당 시스템의 코드(아래의 예시라면 포트 기본값을 설정하는 코드)가 변해도 아래 주석이 변하리라는 보장은 전혀 없습니다. 그리고 심하게 중복된 주석도 확인합니다.

```java
/**
 * 적합성 테스트가 동작하는 포트: 기본값은 <b>8082</b>.
 *
 * @param fitnessePort
 */
public void setFitnessePort(int fitnessePort) {
    this.fitnewssePort = fitnessePort;
}
```

### 너무 많은 정보 ( Too Much Information )

주석에다 흥미로운 역사나 관련 없는 정보를 장황하게 늘어놓지 마십시오.
독자에게 불필요하며 불가사의한 정보일 뿐입니다.

### 모호한 관계 ( Inobvious Connection )

주석과 주석이 설명하는 코드는 둘 사이 관계가 명백해야 합니다.

```java
/*
 * 모든 픽셀을 담을 만큼 충분한 배열로 시작 (여기에 필터 바이트를 더한다.)
 * 그리고 헤더 정보를 위해 200바이트를 더한다.
 */
this.pngBytes = new byte[((this.width + 1) * this.height * 3) + 200]
```
여기서 필터 바이트란 무엇일까? +1과 관련이 있을까? 아니면 *3과 관련이 있을까? 아니면 둘 다? 한 픽셀이 한 바이트인가? 200을 추가하는 이유는?
주석을 다는 목적은 코드만으로 설명이 부족해서 입니다. 그런데 주석 자체가 다시 설명을 요구하고 있는 상태이기 때문에 안타깝기 그지없습니다.

### 함수 헤더 ( Function Headers )

짧은 함수는 긴 설명이 필요 없습니다. 짧고 한 가지만 수행하며 이름을 잘 붙인 함수가 주석으로 헤더를 추가한 함수보다 훨씬 좋습니다.

### 비공개 코드에서 Javadocs ( Javadocs in private code )

공개 API는 Javadocs가 유용하지만 공개하지 않을 코드라면 Javadocs는 쓸모가 없습니다.
시스템 내부에 속한 클래스와 함수에 Javadocs를 생성할 필요는 없습니다.
유용하지 않을 뿐만 아니라 Javadocs 주석이 요구하는 형식으로 인해 코드만 보기 싫고 산만해질 뿐입니다.

# <a name="comments">5. Formatting</a>

## 형식을 맞추는 목적 ( The Purpose of Formatting )

오늘 구현한 기능이 다음 버전에서 바뀔 확률은 아주 높습니다. 그런데 오늘 구현한 코드의 가독성은 앞으로 바뀔 코드의 품질에 지대한 영향을 미칩니다.
오랜 시간이 지나 원래 코드의 흔적을 더 이상 찾아보기 어려울 정도로 코드가 바뀌어도 맨 처음 잡아놓은 구현스타일과 가독성 수준은 유지보수 용이성과 확장성에 계속 영향을 미칩니다.
원래 코드는 사라질지라도 개발자의 스타일과 규율은 사라지지 않습니다.

## 적절한 행 길이를 유지하라 ( Vertical Formatting )

세로 길이부터 살펴보자. JUnit, FitNesse, Time and Money는 상대적으로 파일 크기가 작습니다. 500줄을 넘어가는 파일이 없으며 대다수가 200줄 미만입니다.
500줄을 넘지 않고 대부분 200줄 정도인 파일로도 커다란 시스템을 구축할 수 있다는 사실입니다. (FitNesse는 50,000줄에 육박하는 시스템입니다.)

반드시 지킬 엄격한 규칙은 아니지만 바람직한 규칙으로 삼으면 좋겠습니다. 일반적으로 큰 파일보다 작은 파일이 이해하기 쉽습니다.

### 신문 기사처럼 작성하라 ( The Newspaper Metaphor )

소스 파일도 신문 기사와 비슷하게 작성합니다.
이름은 간단하면서도 설명이 가능하게 짓습니다.
이름만 보고도 올바른 모듈을 살펴보고 있는지 아닌지를 판단 할 정도로 신경 써서 짓습니다.
소스 파일 첫 부분은 고차원 개념과 알고리즘을 설명합니다.
아래로 내려갈수록 의도를 세세하게 묘사합니다. 마지막에는 가장 저차원 함수와 세부 내역이 나옵니다.

### 개념은 빈 행으로 분리하라 ( Vertical Openness Between Concepts )

생각 사이는 빈 행을 넣어 분리해야 마땅합니다.
빈 행은 새로운 개념을 시작한다는 시각적 단서입니다.

### 세로 밀집도 ( Vertical Density )

서로 밀접한 코드 행은 세로로 가까이 놓여야 합니다.

### 수직 거리 ( Vertical Distance )

서로 밀접한 개념은 세로로 가까이 둬야 합니다. 물론 두 개념이 서로 다른 파일에 속한다면 규칙이 통하지 않습니다.
하지만 타당한 근거가 없으면 서로 밀접한 개념은 한 파일에 속해야 마땅합니다.
이게 바로 protected 변수를 피해야 하는 이유 중 하나입니다.
같은 파일에 속할 정도로 밀접한 두 개념은 세로 거리로 연관성을 표현합니다.
여기서 연관성이란 한 개념을 이해하는 데 다른 개념이 중요한 정도입니다.

#### 변수 선언 ( Variable declaration )

변수는 사용하는 위치에서 최대한 가까이 선언한다. 우리가 만든 함수는 매우 짧다.

```java
// InputStream이 함수 맨 처음에 선언 되어있다.

private static void readPreferences() {
    InputStream is = null;
    try {
        is = new FileInputStream(getPreferencesFile());
        setPreferences(new Properties(getPreferences()));
        getPreferences().load(is);
    } catch (IOException e) {
        try {
            if (is != null)
                is.close();
        } catch (IOException e1) {
        }
    }
}
```

```java
// 루프 제어 변수는 Test each처럼 루프 문 내부에 선언

public int countTestCases() {
    int count = 0;
    for (Test each : tests)
        count += each.countTestCases();
    return count;
}
```

```java
// 드물지만, 긴 함수에서는 블록 상단 또는 루프 직전에 변수를 선언 할 수도 있다.
...
for (XmlTest test : m_suite.getTests()) {
    TestRunner tr = m_runnerFactory.newTestRunner(this, test);
    tr.addListener(m_textReporter);
    m_testRunners.add(tr);

    invoker = tr.getInvoker();

    for (ITestNGMethod m : tr.getBeforeSuiteMethods()) {
        beforeSuiteMethods.put(m.getMethod(), m);
    }

    for (ITestNGMethod m : tr.getAfterSuiteMethods()) {
        afterSuiteMethods.put(m.getMethod(), m);
    }
}
...
```

#### 인스턴스 변수 ( Instance variables )

- 변수를 선언하는 위치는 잘 알려진 위치여야 합니다.
  - 클래스 맨 처음에 선언(java), 클래스 마지막에 선언(c/c++, scisors rule)
- Method 중간에 숨겨두면 찾기 어려워집니다.

#### 종속 함수 ( Dependent functions )

- 한 함수가 다른 함수를 호출한다면 두 함수는 세로로 가까이 배치합니다.
- 가능하다면 호출하는 함수를 호출되는 함수보다 먼저 배치합니다.
  - 코드가 자연스럽게 읽힘(높은 추상화 -> 낮은 추상화)
  - 이 규칙이 일관적으로 적용되면 독자는 방금 호출된 함수가 곧 정의될 거라 예측할 수 있습니다.

```java
  public class WikiPageResponder implements SecureResponder { 
      
      protected WikiPage page;
      protected PageData pageData;
      protected String pageTitle;
      protected Request request; 
      protected PageCrawler crawler;

      public Response makeResponse(FitNesseContext context, Request request) throws Exception {
          String pageName = getPageNameOrDefault(request, "FrontPage");
          loadPage(pageName, context); 
          if (page == null)
              return notFoundResponse(context, request); 
          else
              return makePageResponse(context); 
      }

      private String getPageNameOrDefault(Request request, String defaultPageName) {
          String pageName = request.getResource(); 
          if (StringUtil.isBlank(pageName))
              pageName = defaultPageName;

          return pageName; 
      }

      protected void loadPage(String resource, FitNesseContext context)
          throws Exception {
          WikiPagePath path = PathParser.parse(resource);
          crawler = context.root.getPageCrawler();
          crawler.setDeadEndStrategy(new VirtualEnabledPageCrawler()); 
          page = crawler.getPage(context.root, path);
          if (page != null)
              pageData = page.getData();
      }

      private Response notFoundResponse(FitNesseContext context, Request request)
          throws Exception {
          return new NotFoundResponder().makeResponse(context, request);
      }

      private SimpleResponse makePageResponse(FitNesseContext context)
          throws Exception {
          pageTitle = PathParser.render(crawler.getFullPath(page)); 
          String html = makeHtml(context);

          SimpleResponse response = new SimpleResponse(); 
          response.setMaxAge(0); 
          response.setContent(html);
          return response;
      } 
  ...
```

#### 개념적 유사성 ( Conceptual Affinity )

코드간의 개념적인 친하돠고 높다면 가까이 배치합니다.
친화도가 높은 요인으로는 다음과 같은 예들이 있습니다.

- 한 함수가 다른 함수를 호출해 생기는 직접적인 종속성ㄱ
- 변수와 그 변수를 사용하는 함수
- 동작을 수행하는 일군의 함수

### 세로 순서 ( Vertical Ordering ) 

함수 호출 종속성은 아래 방향으로 유지합니다. 즉, 호출되는 함수를 호출하는 함수보다 나중에 배치합니다.