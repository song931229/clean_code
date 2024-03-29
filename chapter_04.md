<style>body {font-family: D2Coding;}</style>

# 함수

> 시스템을 나누는 기준의 변화  
> 초창기 -> 루틴:하위루틴  
> 포트란<sup>[1](#1)</sup> & PL/1<sup>[2](#2)</sup> -> 프로그램:하위프로그램:함수  
> 오늘날 -> `함수`

- 어떤 프로그램이든 가장 기본적인 단위는 `함수`이다  
- 3장에서는 `함수를 잘만드는 법을` 소개한다  

![코드예3-1]()  
길고, 중복, 이상한 문자열, 이상한 자료형의 향연  
줄바꿈도 이상하고, 이상한 플래그도 있다.

![코드예3-2]()  
-> 메서드 추출, 이름 변경, 구조 변경
: 훨씬 더 읽기 좋고 이해가 쉬움  

## 작게 만들어라

`함수는 첫째도 작게, 둘째도 작게`  
80년대에는 한 함수가한화면을 넘어서는 안되었다 ( 80자*24줄 )  

얼마나 짧게?  

`3-2`는 아래의 `3-3`만큼 줄어야한다.  
![코드예3-3]()  

## 블록과 들여쓰기

`if문/else문/while문 등에 들어가는 블록은 한 줄이어야 한다`  
왜냐하면, 대체로 함수를 호출하는 부분이기 때문이다.  
바꿔말하면, 함수의 들여쓰기 수준을 1~2단으로 유지하란 말이다.  
이를 통해 함수는 더욱 더 읽고 이해하기 쉬워진다.  

## 한가지만 해라

`함수는 한가지를 해야하고, 그 한가지를 잘해야하며, 그 한가지만을 해야한다` - TODO원어가 궁금함.

`3-1`에선

1. 버퍼 생성
2. 페이지 가져오기
3. 상속 페이지 검색
4. 경로 랜더링
5. 문자열 붙이기
6. HTML생성

등을 하는 반면, `3-3`은 한 가지만 처리한다  

그렇다면, '한가지'의 기준은 무엇인가?

우선 `3-3`의 코드가 한가지가 맞는가?  

1. isTestPage - 테스트 페이지 여부 체크
2. includeSetupAndTeardownPages - 1에서 true면 설정페이지와 해제페이지를 넣는다.
3. pageData.getHTML - 페이지를 HTML로 랜더링

이렇게 나열하면, `3-3`은 세가지인가? 한가지인가?  
위에서 언급하는 세가지는 지정된 함수 이름 아래에서 추상화 수준이 하나.  
함수는 간단한 TO<sup>[3](#3)</sup>문단으로 기술할 수 있다.

> TO: RenderPageWithSetupsAndTearDowns, 페이지가 테스트 페이지인지 확인한 후 테스트 페이지라면 설정 페이지와 해제 페이지를 넣는다. 테스트 페이지든 아니든 페이지를 HTML로 렌더링한다.

우리가 함수를 만드는 이유는 큰개념(시스템)을 단계적인 추상화를 통하여 단계적 수행을 하기 위해서이다.

따라서, 한가지만 하는 함수란 `추상화 수준이 하나인 단계만 수행하는 함수`라고 할 수 있다.

추상화 수준이 하나라면, 의미 있는 이름으로 다른 함수를 추출할 수 없을 것이고, 추출할 수 있다면 그 함수는 여러 작업을 하는 샘이다.`[G34]` & `p90_4-7/generatePrime/declarations,initalizations,sieve`

TODO `3-1`, `3-2`도 TO문을 작성해보기

---

## 함수 당 추상화 수준은 하나로

`함수 내 모든 문장의 추상화 수준이 같아야 한다`

`3-1`에서의 추상화 수준 정리

```java
pateDate.getHtml(); // 추상화수준 높음
String pagePathName = PathParser.render(pagepath); // 추상화 수준 중간
StringBuffer.append("\n"); // 추상화수준 낮음
```

함수의 추상화 수준을 섞으면 코드를 읽는 독자에게 혼돌을 준다. 근본 개념인지, 세부사항인지 구분하기 어렵기 때문이다.  
또, 근본 개념과 세부사항을 섞어놓으면 깨어진 창문처럼 사람들이 추가하는 코드도 추상화 수준이 뒤섞이여 추가된다.

---

## 위에서 아래로

코드는 하나의 이야기처럼 읽혀야 한다. 한 함수 다음에는 추상화 수준이 한 단계 낮은 함수가 나온다.  
프로그램을 위에서 아래로 읽으면 함수 추상화 수준이 한번에 한단계씩 감소해야 자연스럽게 읽힌다.  
마치 TO문단을 읽어내려 가듯이 코드를 구현하는 것이다. 이처럼 코드를 구현한다면, 추상화 수준이 일관되게 유지할 수 있다.

TODO TO문단 내용 추가

위 규칙을 따라 `3-1`을 완전히 재구성한 `3-7`을 참고하라

추상화 수준이 하나인 함수를 구현하기란 쉽지만 매우 중요한 규칙이다.  
핵심은 짧으면서도 `'한 가지'`만 하는 함수이다.

## Switch 문

switch문은 작게만들기 어렵지만 피할 수 없다. 하지만, 다형성(polymorphism)을 활용하여 저차원 클래스에 숨기고, 반복하지 않는 방법은 있다. `3-4` -> `3-5`  
![코드예3-4]()  
>문제점

1. 함수가 길다
2. 여러가지를 처리한다
3. SRP위반 - TODO SRP 개념정리
4. OCP위반 - TODO OCP 개념정리
5. switch문을 활용한 위와같은 구조는 무한히 생길 수 있음.

다음과 같이 해결이 가능하다 - switch문을 추상 팩토리(ABSTRACT FACTORY)에 숨긴다.[G23]  

![코드예3-5]()  
되도록 지향하고, 불가피한 상황에만 switch문을 노출하도록 하자.

## 서술적인 이름을 사용하라

`3-7`에서 함수 이름을 'testableHtml' -> 'SetupTeardownIncluder.render'로 변경  
함수가하는 일을 좀 더 잘 표현하므로 훨씬 좋은 이름

private 함수명도 isTestable, includesetupAndTeardownPage 등과 같이 서술적인 이름  
좋은이름은 아무리강조해도 중요하다.  
`코드를 읽으면서 짐작했떤 기능을 각 함수가 수행하면 깨끗한 코드라 불리울만 하다.`  
좋은이름은 설계에 대한 개념도 뚜렷해지고 이는 곧 코드개선으로 이어진다.  

또, 이름을 지을 때는 일관성을 중시해야한다.  
모듈내에서 같은 문구, 명사, 동사를 사용 - includeSetupAndTeardownPages, includeSetupPages, includeSuiteSetupPage, includeSetupPage 등  
문체가 비슷하면 이야기를 순차적으로 풀어가기도 쉬워진다.  

---

## 함수 인수

> 함수 이상적인 인수 개수  
> 0개(무항) > 1개(단항) > 2개 >>>>>>> 3개부터는 쓰레기 >>>>>> 4개부터는 핵폐기물

`3-7`  
private StringBuffer newPageContent를 인스턴스 변수로 선언하는 대신  
함수 인수로 넘기는 방법도 있었지만, 그렇다면 StringBuffer를 만날 때마다 의미를 해야하함  
코드를 읽는사람에게는 includeSetupPageInto( new PageContent ) 보단 includeSetupPage()가 이해하기 더쉽다.

테스트관점에서는 인수가 많을수록 갖가지 인수 조합에대한 테스트를 작성해야한다. 테스트마저 조악해지고 -> 효율 떡락  
`최선은 0개, 차선은 1개`

### 많이 쓰는 단항 형식

> 함수에 인수를 1개 넘기는 경우  
>
> 1. 인수에 질문을 던지는 경우 - ex) boolean fileExists("MyFile");  
> 2. 인수를 뭔가로 변환해 결과를 반환하는 경우 - ex) inputStream fileOpen("MyFile"); -> String을 InputStream으로 반환

위 뒤가지 경우는 무리없이 이해하기 좋은 예시이다.  
당연히 함수 이름을 지을 때는 두 경우를 부명히 구분한다. 또한 언제나 일괄적인 방식으로 두형식을 사용(명령과 조회릘 구분하라 챕터에서 계속)  

다소 드문 단항 형식 - 이벤트 함수 : 입력 인수만 있고, 출력 인수는 없다. - ex) passwordAttemptFailedNtimes(int attempts)  
이벤트 함수는 이벤트라는 사실이 코드에 명확히 드러나도록 이름과 문맥을 주의해서 선택하여야한다

p.s. StringBuffer transform(StringBuffer in)이 StringBuffer transform(StringBuffer out)보다 좋다.

## 플래그 인수

플래그 인수는 추하다. `함수로 Bool 값을 넘겨? -> 나가죽어라`
`3-7`에서는 render(true)보다는  
> renderForSuite()  
> renderForSimpleTest()  

로 나누어야 한다.

## 이항 함수

이항 함수는 단항 함수보다 이해하기 어렵다. 아래의 예를 보자.  
`writeField(name)`은 write(outputStream, name)보다 이해하기 쉽다.  
둘 다 명백한 의미이지만 전자가 더 쉽게 읽히고 더 빨리 이해된다.  
결국에 후자의 방식은 outputStream을 무시하게 되고, 이는 곧 오류가 숨어드는 부분으로 발전한다. 때문에 되도록 함수 인수를 적게 사용하는 것이 바람직하다.

assertEquals(expected, actual)에도 문제가 있다.  
expected에 actual값을 넣는 등의 실수이다.  
다음 과같이 수정하면 순서를 기억할 필요가 없다.  
`assertExpectedEqualsActual(expected,actual)`

---

## 삼항 함수

삼항 함수는 이항 함수보다 이해하기 어렵다. 그러니, 삼항 함수는 심사숙고 후에 결정하도록 하자.

assertEquals(message, expected, actual) -> 첫 인수가 message임을 예상하기 어렵다.  

## 인수 객체

인수가 2~3개 혹은 그이상이 필요하다면, 독자적인 클래스 변수로 선언하여 사용하는 방법을 시도해보자.  

> Circle makeCircle(double x, double y, double radius);  
> Circle makeCircle(Point center, double radius);

객체를 만듦으로써 인수간의 연관성을 좀 더 명확하게 알려줄 수 있다.

## 인수 목록

인수의 개수가 가변적인 함수가 필요할 때가 있다.  
그러나, 이는 본질적으로는 사실상 단항함수 혹은 이항함수의 반복일 뿐이다.  

String.format은 아래와같이 구성된다.

```java
String.format("%s worked %.2f hours.", name, hours);

public String format(String format, Object.... args)
```

가변 인수를 취하는 모든 함수에 같은 원리가 적용된다.

## 동사와 키워드
