<style>
body {
  font-family: D2Coding;
}
</style>

# chapter_00

## 복간에 부쳐

- 자매품 Clean Coder를 읽고 전문가 정신, 장인 정신에 대한 의문점 해결
- 오래된 책이기 때문에 유효하지 않은 충고가 있음
- 요즘엔 fluent interface<a id="rfn-1" href="#fn-1"><sup>[1]</sup></a>가 등장 : TODO
- 책을 읽고 자괴감이 들었음.

---
<!-- 주석모음 -->
<a id="fn-1" href="#rfn-1">[1]</a>fluent interface : [참조](https://ko.wikipedia.org/wiki/%ED%94%8C%EB%A3%A8%EC%96%B8%ED%8A%B8_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4){:target="_blank"}

## 옮긴이의 말

축약하면 체크아웃코드가 체크인코드보다 깨끗해야 할것이라 말한다.

책의 전반부에서는 클린코드에 대한 패턴을 수립하여 개념을 정리하고,

후반부에는 bad to clean을 비교하고, 사고흐름까지 확인하여 이해하고 응용

( 코드의 처음부터 끝까지 리팩터링을 제시)

-> 저자의 경험을 체험하고, 공감하며 최종적으로 clean code를 이해하는 것.

개념서처럼 반복적으로 읽고, 계속 참고하며, '올바른 코드'에 대한 가치관을 설립하길 바람

1) 메타포 : TODO

---

## 추천사

덴마크 속담 - 추후 첨부

: 사소한 곳에서 발휘하는 정직은 사소하지 않다

소프트웨어의 80% 이상은 '유지보수' 공수이다.

따라서, 제품을 찍어내는 것에 집중하는 것은 제품의 유지보수에 집중하는 것보다 비효율 적이다.

### 5S

> __정리__ - 올바른 명명법 [무엇이 어디에 있는가?]  
> ___정돈___ - 올바른 위치, 적절한 위치 [그것이 그곳에 있는가?]  
> ___청소___ - 주석을 감싼코드 (과겨이력, 반영할내용) [그곳에 그것만 >있는가?]  
> ___청결___ - 모두 혹은 집단과 동의한 약속(규칙,원칙) [무엇을 어디에 둘건가?]  
> ___생활화___ - 위 4S의 연속, 반복 [약속을 지키는가?]

[TMP 품질관리론](https://m.cafe.daum.net/yasungmi/LljJ/572)

- 제품에는 생명주기가 있고, 제품의 생산자는 이 점을 고려하여 어떠한 부분이 과잉되거나 결여되지 않도록 주의하여야한다.

'읽기 좋은 코드' & '작동하는 코드'  => IMPORTANT

크리스토퍼 알렉산더(패턴과 패턴언어의 아버지)

- "모든 설계는 국부적인 수리 행위이다. "

- "전체구조를 훌륭하게 만드는 것이 장인으로서 건축가가 유일하게 해야할 일이다. "

-> 주택의 형태는 거주자에게 맡김

대다수의 예술도 비슷하다.

"시란 영원히 미완성이라, 끝없는 재작없이 필요하며 포기할 때에만 끝난다" - 폴 발레리

위와같이 세세함에 몰두하는 태도는 탁월함을 추구하는 모든 노력에서 공통으로 발견

벨 연구소 소프트웨어 제조 연구소의 조사

일관적인 들여쓰기(indent) 스타일이 버그 수를 줄여주는 가장 중요한 용인 중 하나라고 추측.

[style-guide](https://cfss.uchicago.edu/notes/style-guide/)

Bugs and styling code | Computing for the Social Sciences
library(tidyverse) set.seed(1234) Admiral Grace Hopper discovered the first bug in a computer Run the code below in your console to download this exercise as a set of R scripts. usethis::use_course("uc-cfss/debugging-and-defensive-programming") A software bug is “an error, flaw, failure or fault in ...

cfss.uchicago.edu

TODO - 실재 스터디 찾아보기(위에것은 임시)

소위 전문가들은 고상한 설계 방법론과 도구에 통달해야한다고 말하며, 생각한다.

때문에, 들여쓰기(indent)에 가치를 더하는 것에 모욕을 느낀다.

이와 같은 태도의 차이가 탁월함과 능숙함을 구분짓는다.

품질은 하늘에서 뚝 떨어지는 것이 아니라, 사심없이 기울이는 무수한 관심에서 얻어진다.

"처음 왔을 때보다 캠프장을 더 깨끗이 치우고 떠나라"

0장.들어가면서

코드의 품질을 측정하는 척도 WTF/m - 분당 WTF(What The Fxxk)

장인 정신의 2단계

1.이론 - 원칙,패턴,기법,경험

2.실천 - 열심히 실행(연습)하여 몸과 마음으로 체득

자전거에대한 이론이 빠삭해도 자전거를 처음타는 사람이라면 100% 넘어진다.

(동의할 수 없는 여지가 있는 비유이긴함)

요지는 구현이라는 과정은 필연적으로 이론과 경험 혹은 실재기능이 필요하다는 것이다.

바로 나에게 스스로 대입하여, 클린코드에대한 이론만 알려주어서는 진실로 깨달을 수 없음으로,

코드를 많이 읽고, 많이 고치고, 많이 쓰고 반복하자.

책의 구성

1 원칙,패턴,실기

2 사례연구, 에제연습, 코드와 해설, 코드 변경의 목적, 이해, 납득

3 사례연구의 해설 (냄새와 휴리스틱), 생각묘사, 공감

휴리스틱(heuristic) : TODO

1장.개끗한 코드

- 좋은 코드와 나쁜 코드를 구분하는 능력

- 좋은 코드를 작성하는 능력

- 나쁜 코드를 좋은 코드로 바꾸는 능력
