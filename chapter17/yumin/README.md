# 17. 경계 : 선 긋기

소프트웨어 아키텍처는 선을 긋는 기술이며, 나는 이러한 선을 경계라고 부른다.

경계는 소프트웨어 요소를 서로 분리하고, 경계 한편에 있는 요소가 반대편에 있는 요소를 알지 못하도록 만든다.

아키텍트의 목표는 필요한 시스템을 만들고 유지하는 데 드는 인적 자원을 최소화하는 것이라는 사실을 상기하자.

결합은 너무 일찍 내려진 결정에 따른 결합이다.

좋은 시스템 아키텍처란 이러한 결정이 부수적이며, 결정을 연기할 수 있는 아키텍처다. 좋은 시스템 아키텍처는 이런 결정에 의존하지 않는다.

### 어떻게 선을 그을까? 그리고 언제 그을까?

---

관련이 있는 것과 없는 것 사이에 선을 긋는다.

데이터베이스는 GUI와는 관련이 없으므로, 이 둘 사이에도 반드시 선이 있어야 한다.

데이터베이스는 업무 규칙과 관련이 없으므로 이 둘 사이에도 선이 있어야 한다.

데이터베이스는 업무 규칙이 간접적으로 사용할 수 있는 도구다.

선은 Database / Interface바로 아래에 그어진다.

DatabaseAccess에서 출발하는 두 화살표에 주목해야 한다.

이들 두 화살표는 DatabaseAccess클래스로부터 바깥쪽으로 향한다.

이 도표에서 DatabaseAccess가 존재한다는 사실을 알고 있는 클래스는 없다.

데이터베이스에 대한 결정은 연기할 수 있으며, 데이터베이스를 결정하기에 앞서 업무 규칙을 먼저 작성하고 테스트하는 데 집중할 수 있음을 의미한다.

### 입력과 출력은?

---

모델은 인터페이스를 전혀 필요로 하지 않는다.

관련성이 낮은 컴포넌트가 관련성이 높은 컴포넌트에 의존한다는 사실을 다시 한번 볼 수 있다.

### 플러그인 아키텍처

---

데이터베이스와 GUI에 대해 내린 두 가지 결정을 하나로 합쳐서 보면 컴포넌트 추가와 관련한 일종의 패턴이 만들어진다.

사실 소프트웨어 개발 기술의 역사는 플러그인을 손쉽게 생성하여, 확장 가능하며 유지보수가 쉬운 시스템 아키텍처를 확립할 수 있게 만드는 방법에 대한 이야기다.

### 플러그인에 대한 논의

---

경계는 변경의 축이 있는 지점에 그어진다.

경계의 한쪽에 위치한 컴포넌트는 경계 반대편의 컴포넌트와는 다른 속도로, 그리고 다른 이유로 변경된다.

GUI는 업무 규칙과는 다른 시점에 다른 속도로 변경되므로, 둘 사이에는 반드시 경계가 필요하다. 

단일 책임 원칙은 어디에 경계를 그어야 할지를 알려준다.

### 결론

---

소프트웨어 아키텍처에서 경계선을 그리려면 먼저 시스템을 컴포넌트 단위로 분할해야 한다.

일부 컴포넌트는 핵심 업무 규칙에 해당한다.

이는 의존성 역전 원칙과 안정된 추상화 원칙을 응용한 것임을 눈치챌 수 있어야 한다.

의존성 화살표는 저수준 세부사항에서 고수준의 추상화를 향하도록 배치된다.