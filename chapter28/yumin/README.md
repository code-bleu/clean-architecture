# 28. 테스트 경계

테스트는 시스템의 일부이며, 아키텍처에도 관여한다.

시스템의 나머지 요소가 아키텍처에 관여하는 것과 동등하게 말이다.

### 시스템 컴포넌트인 테스트

---

아키텍처 관점에서는 모든 테스트가 동일하다.

테스트는 아키텍처적으로 모두 동등하다. (TDD로 생성하든, 대규모의 테스트이든..)

테스트는 태생적으로 의존성 규칙을 따른다.

아키텍처에서 가장 바깥쪽 원으로 생각할 수 있다.

- 테스트는 독립적으로 배포 가능하다. 사실 대다수의 경우 테스트는 테스트 시스템에만 배포하며, 상용 시스템에 배포하지 않는다.
    - 따라서 심지어 배포 독립성이 달리 필요하지 않은 시스템에서도 테스트는 독립적으로 배포 될 것이다.
- 테스트는 시스템 컴포넌트 중에서 가장 고립되어 있다.
    - 테스트가 시스템 운영에 꼭 필요치는 앖다.

### 테스트를 고려한 설계

---

시스템에 강하게 결합된 테스트라면 시스템이 변경될 때 함께 변경되어야만 한다.

깨지기 쉬운 테스트는 시스템을 뻣뻣하게 만든다는 부작용을 낳을 때가 많다.

### 테스트 API

---

테스트가 모둔 업무 규칙을 검증하는 데 사용할 수 있도록 특화된 API를 만들면 된다.

API는 사용자 인터페이스가 사용하는 인터랙터와 인터페이스 어댑터들의 상위 집합이 될 것이다.

구조적 결합

구조적 결합은 테스트 결합 중에서 가장 강하며, 가장 은밀하게 퍼져 나가는 유형이다.

이러한 테스트 스위트는 애플리케이션 구조에 강하게 결합되어 있다.

상용 클래스나 메서드 중 하나라도 변경되면 딸려 있는 다수의 테스트가 변경되어야만 한다.

결과적으로 테스트는 깨지기 쉬워지고, 이로 인해 상용 코드를 뻣뻣하게 만든다.

테스트 API의 역할은 애플리케이션의 구조를 테스트로부터 숨기는 데 있다.

보안

테스트 API가 지닌 강력한 힘을 운영 시스템에 배포하면 위험이 처할 수 있다.

위험을 피하고 싶다면 테스트 API 자체와 테스트 API 중 위험한 부분의 구현부는 독립적으로 배포할 수 있는 컴포넌트로 분리해야 한다.

### 결론

---

테스트는 시스템 외부에 있지 않다.

- 오히려 시스템의 일부다.
- 테스트는 잘 설계되어야만 한다.
- 테스트를 시스템의 일부로 설계하지 않으면 테스트는 깨지기 쉽고 유지보수하기 어려워지는 경향이 있다.
- 이러한 테스트는 유지보수하기가 너무 힘들기 때문에 결국 방바닥의 휴지처럼 버려지는 최후를 맞이한다.