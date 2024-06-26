# 11장. DIP : 의존성 역전 원칙

의존성 역전 원칙에서 말하는 ‘유연성이 극대화된 시스템’ 이란 소스 코드 의존성이 추상에 의존하며 구체에는 의존하지 않는 시스템이다.

자바와 같은 정적 타입 언어에서 이 말은 use, import, include 구문은 오직 인터페이스나 추상 클래스 같은 추상적인 선언만을 참조해야 한다는 뜻이다. 구체적인 대상에는 절대로 의존해서는 안 된다.

DIP를 논할 때 운영체제나 플랫폼 같이 안정성이 보장된 환경에 대해서는 무시하는 편이다.

우리가 의존하지 않도록 피하고자 하는 것은 변동성이 큰 구체적인 요소다.

이 구체적인 요소는 우리가 열심히 개발하는 모듈들이 될 수 있다.

### 안정된 추상화

추상 인터페이스에 변경이 생기면 이를 구체화한 구현체들도 따라서 수정해야 한다.

반대로 구체적인 구현체에 변경이 생기더라도 그 구현체가 구현하는 인터페이스는 항상 좀 더 정확히 말하면 대다수의 경우 변경될 필요가 없다. 따라서 인터페이스는 구현체보다 변동성이 낮다.

뛰어난 소프트웨어 설계자와 아키텍트라면 인터페이스의 변동성을 낮추기 위해 애쓴다.

안정된 소프트웨어 아키텍처란 변동성이 큰 구현체에 의존하는 일은 지양하고, 안정된 추상 인터페이스를 선호하는 아키텍처라는 뜻이다.

- 변동성이 큰 구체 클래스를 참조하지 말라. 대신 추상 인터페이스를 참조하라.
- 변동성이 큰 구체 클래스로부터 파생하지 말라.
- 구체 함수를 오버라이드 하지 말라.

### 팩토리

추상 컴포넌트와 구체 컴포넌트

- 추상 컴포넌트는 애플리케이션의 모든 고수준 업무 규칙을 포함한다.
- 구체 컴포넌트는 업무 규칙을 다루기 위해 필요한 모든 세부사항을 포함한다.

소스 코드 의존성은 제어흐름과는 반대 방향으로 역전된다. 이러한 이유로 이 원칙을 의존성 역전이라고 부른다.

### 결론

앞으로 고수준의 아키텍처 원칙을 다루게 되면서 DIP는 몇 번이고 계속 등장할 것이다.

의존성은 앞의 곡선을 경계로(구체 / 추상 컴포넌트) 더 추상적인 엔티티가 있는 쪽으로만 향한다.

추후 이 규칙은 의존성 규칙(Dependency rule)이라 부를 것 이다.