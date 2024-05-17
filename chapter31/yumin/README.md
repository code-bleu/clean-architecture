# 31. 웹은 세부사항이다

사실 웹이 바꾼 것은 아무것도 없었다.

### 끝없이 반복하는 추

---

이처럼 반복되는 진동이 웹으로부터 시작되었다고 보는 일은 옳지 않다.

웹이 있기 전에는 클라이언트-서버 아키텍처가 있었다. 

그 전에는 다수의 멍청한 단말기가 연결되는 중앙집중식 미니컴퓨터가 있었다. 

IT역사 전체로 시야를 넓히면 웹은 아무것도 바꾸지 않았다. 웹은 우리가 발버둥치면서 생기는 여느 수많은 진동 중 하나에 불과하다. 이 진동은 우리가 태어나기 전에도 있어 왔고, 우리가 은퇴한 뒤에도 지속될 것이다.

아키텍트로서 우리는 멀리 내다봐야 한다. 이 진동은 그저 핵심 업무 규칙의 중심에서 밀어내고 싶은 단기적인 문제일 뿐이다.

### 요약

---

요약하면 다음과 같다.

GUI는 세부사항이다. 웹은 GUI다. 따라서 웹은 세부사항이다.

그리고 아키텍터라면 이러한 세부사항을 핵심 업무 로직에서 분리된 경계 바깥에 두어야 한다.

이렇게 생각해 보자. 웹은 입출력 장치다. 1960년대에 우리는 애플리케이션을 장치 독립적으로 만들면 어떤 가치가 있는지 배웠다. 장치 독립적으로 만들어야 했던 동기 자체는 지금도 유효하다. 웹도 이 규칙에서 예외가 될 수 없다.

애플리케이션과 GUI의 상호작용은 빈번하며 또한 이러한 상호작용 방식도 사용 중인 GUI 종류에 따라 차이가 매우 크다. 브라우저와 웹 애플리케이션이 함께 추는 춤은 데스크톱 GUI와 데스크톱 애플리케이션이 함께 추는 춤과는 차이가 난다.

UI와 애플리케이션 사이에는 추상화가 가능한 또 다른 경계가 존재한다. 업무 로직은 다수의 유스케이스로 구성되며, 각 유스케이스는 사용자를 대신해서 일부 함수를 수행하는 것으로 볼 수 있다. 각 유스케이스는 입력 데이터, 수행할 처리 과정, 출력 데이터를 기반으로 기술할 수 있다.

완전한 입력 데이터와 그에 따른 출력 데이터는 데이터 구조로 만들어서 유스케이스를 실행하는 처리 과정의 입력 값과 출력 값으로 사용할 수 있다.

### 결론

---

이러한 종류의 추상화는 만들기 쉽지 않고, 제대로 만들려면 수차례의 반복 과정을 거쳐야 할 것이다. 하지만 가능하다. 그리고 세상은 마케팅 귀재로 가득하기 때문에 이러한 추상화가 꼭 필요할 때가 많다고 주장하기는 어렵지 않다.