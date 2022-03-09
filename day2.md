<style>body {font-family: D2Coding;}</style>

# 의미 있는 이름

## 들어가면서

> ### 이장의 목적
>
> 이름을 잘 지어야 하는 이유  
> 이름을 잘 짓는 규칙

---

### 의도를 분명히 밝혀라

`의도가 분명하게 이름을 지어라`

의도가 분명한 이름은 따로 수행기능, 사용방법 등의 주석이 필요가 없다.

![코드예1]()  
`theList -> gameBoard`  
![코드예2]()  
`무의미한 이름 -> 유의미한 이름`  
![코드예3]()  
`상수 -> 함수`  
`클래스도 이름부여`  
<br>

---

### 그릇된 정보를 피하라

`코드에 그릇된 단서를 남기지 말라`

코드에 동음이의어, 이음동의어 등 일관성과 가독성을 해치지 말 것.

  1. 서로 흡사한 이름의 사요에 주의 - 가독성
  2. 유사한 개념은 유사한 표기법을 사용 - 일관성  
<br>

---

### 의미 있게 구분하라
<!-- TODO 불용어 주석달기-->
***불용어***를 추가하거나 숫자를 덧붙이는 방식은 좋지 않다.
이름이 달라진다면, 의미도 달라져야 한다.  

특히 연속적인 숫자를 덧붙이는 방식은 아무의미가 없다.

![코드예1]()  
`a1, a2 -> source, destination`

NameString vs `Name`  
ProductData vs ProductInfo vs `Product`  
CumstomerObject vs `Customer`  
moneyAmount vs `money`
theMessage vs `message`

getActiveAccount();  
getActiveAccounts();  
getActiveAccountInfo();

---

### 발음하기 쉬운 이름을 사용하라

generate date, year, month, day, hour, minute, second를 줄여 `genymdhms`라 표기한다면, 줄임말이라는 정보에 대한 '교육'이 필요하고, 발음한적 없는 단어기 때문에 공통된 발음(약속)을 갖지 못하게되어 '소통'이 원활하지 못하게된다.  
<br>

![코드예1]()  
![코드예2]()  

---

### 검색하기 쉬운 이름을 사용하라

문자 단위의 이름이나 숫자는 코드에서 구별해내기 어려운 문제가 있고, 검색할 때에도 문제를 야기한다.

`MAX_CLASSES_PER_STUDENT`는 검색하기 쉽지만, 숫자 '7'은 검색하면 이곳저곳에서 발견이 될 것이다.  

이러한 관점에서는 긴이름이 짧은 것보다 좋다.  
그렇다고, 무작정 긴 이름도 좋지 바람직하지 않으니, 이 기준을 `'범위 크기에 비례해야 한다'`로 정한다.[N5]

![코드예1]()  
![코드예2]()  

`사용된 숫자들을 적절하게 상수로 바꿈으로써, 코드가 길어지지만 훨씬 보기 편해진다`

---

### 인코딩을 피하라

앞선 '발음하기 쉬운 이름을 사용하라'와 겹치는 부분이 있다. 인코딩이란 결국 개념 혹은 단어를 코드화 한것인데, 코드체계를 모르면 읽을 수가 없다.  
또, 타입의 변경에 따른 상황에서도 코드 체계에 맞는 수정이 이루어져야해서 `유지보수 효율이 떨어지고`, `오표기로 인한` 코드의 잘못된 이해가 발생할 수도 있다.  

`따라서, 언어가 가진 객체(Object)를 활용하여 Type에 대한 표기를 생각하고, 코드화(인코딩)로인한 정보에대한 함축과 접두어 사용이 지양되어야한다.`  

#### *인코딩이 필요한 경우*

> 도형을 생성하는 interface class - ABSTRACT FACTORY의 구현  
> 구현은 구체 클래스(concrete class)에서 한다고 할 때, 두 크래스의 이름은?  
> IShapeFactory, ShapeFactory  
> ShapeFactory  
> ShapeFactoryImp  
> CShapeFactory

---

### 기억력을 자랑하지 마자

읽는 사람이 변수 이름을 변환하여 인지해야 한다면, 그 변수 이름은 구린 이름이다.  
일반적이고 보편적인 이름의 사용이 아니기 때문에 그렇게 느끼기 때문이다.  

`명료함이 최고다`  

1. 클래스 이름 - 명사, 명사구 -> O, 동사 -> X  
`Customer,WikiPage,Account`  
vs  
Manager,Processor,Data  
2. 메서드 명 - 동사, 동사구 -> O  
`postPayment,deletePage`  
접근자,변경자,조건자는 자바표준을 따른 `get,set,is`  

3. Override - 정적 팩토리 메서드  

```java
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
```

vs

```java
Complex fulcrumPoint = new Complex(23.0);
```

생성자 사용을 제한 하려면 `private!`

---

### 기발한 이름은 피하라

`센스고 나발이고 명료하게 하라`

---

### 한 개념에 한 단어를 사용하라

자바표준의 변경자,접근자,조건자(`set,get,is`)처럼 한 개념에 한단어로 일관성있어야하고, 다른 기능은 명확하게 다른 이름을 부여해야 한다.  

IDE에서도 메서드 목록을 보여줄 때, 주석은 보여주지 않고, 메서드 명과 인수명만 표시됨을 기억하라.  

`일관성있는 어휘!`  

[자바표준](http://www.oracle.com/technetwork/java/javase/documentation/spec-136004.html)

---

### 말장난 하지 마라

한 단어나 문장에 두가지 의미를 두거나 사람을 헛갈리게 하지마라

---

### 해법 영역에서 가져온 이름을 사용하라

코드를 읽는 사람도 프로그래머임을 인지하여 배경지식을 활용하고, 한편으로는 주의하라

---

### 문제 영역에서 가져온 이름을 사용하라

적절한 프로그래머 용어(해벙 영억)가 없다면, 문제 용어를 채택하라

`위 두가지를 실천하기 위해선는 해법 영역과 문제 영역을 구분할 능력이 필요하다`

---

### 의미 있는 맥락을 추가하라

state만 있을 때와 state,fisrtName,lastName,street,city,zipcode가 같이 있을 때의 이해도는 다르다.  
무엇을 나타내고, 무엇을 의도한 것인지 주석을 적기보다 맥락을 부여하라  
fisrtName, lastName, street, city, state, zipcode  
=> addrFisrtName, addrLastName...  `addr 접두어 부여`  
=> Address 클래스 생성  

![코드예1]()  
![코드예2]()  

---

### 불필요한 맥락을 제거하라

메서드의 모든 접두를 통일 시킨다면 IDE가 메서드 목록을 보여줄 때, 모든 메서드가 표출될 것이다.  
GSDaccountAdrress => `Address`

세부적인 accountAddress와 customerAddress는 클래스 인스터트로는 좋은 이름이다.

---

## 마치며

좋은 이름을 선택하려면 설명 능력이 뛰어나야하고, -> 개념을 명확하게 인지하여 쉽게 설명이 가능해야하고,  
문화적인배경이 같아야한다. -> 같은 배경지식을 공유해야한다.  

> ## `까먹은 코드를 다시 보았을 때, 최대한 빨리 효율적으로 이해할 수 있어야 좋은 코드다`
