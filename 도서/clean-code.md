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