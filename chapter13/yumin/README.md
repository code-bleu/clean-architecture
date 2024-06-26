# 13장. 컴포넌트 응집도

### 컴포넌트 응집도와 관련된 세 가지 원칙

1. REP : 재사용 / 릴리스 등가 원칙
2. CCP : 공통 폐쇄 원칙
3. CRP : 공통 재사용 원칙

## REP : 재사용 / 릴리스 등가 원칙

---

재사용 단위는 릴리즈 단위와 같다.

재사용 / 릴리즈 등가 원칙은 너무 당연해 보인다. 소프트웨어 컴포넌트가 릴리즈 절차를 통해 추적 관리되지 않거나 릴리즈 번호가 부여되지 않는다면 해당 컴포넌트를 재사용하고 싶어도 할 수도 없고, 하지도 않을 것이다.

만약 컴포넌트가 REP를 위배한다면 컴포넌트 사용자가 알게 되고, 당신의 아키텍트로서의 능력을 높게 평하지 않을 것이다.

이 원칙의 약점은 다음에 다를 두 원칙이 지닌 강점을 통해 충분히 보완할 수 있다.

CCP와 CRP는 REP를 엄격하게, 하지만 제약을 가하는 측면에서 정의한다.

### CCP: 공통 폐쇄 원칙

---

동일한 이유로 동일한 시점에 변경되는 클래스를 같은 컴포넌트로 묶어라.

서로 다른 시점에 다른 이유로 변경되는 클래스는 다른 컴포넌트로 분리하라.

이 원칙은 단일 책임 원칙을 컴포넌트 관점에서 다시 쓴 것이다.

변경될 가능성이 있는 클래스는 모두 한곳으로 묶을것을 권한다.

CCP에서는 동일한 유형의 변경에 대해 닫혀 있는 클래스들을 하나의 컴포넌트로 묶음으로써 OCP에서 얻은 교훈을 확대 적용한다.

SRP의 컴포넌트 수준 : CCP

### CRP : 공통 재사용 원칙

---

컴포넌트 사용자들을 필요하지 않는것에 의존하게 강요하지 말라.

개별 클래스가 단독으로 재사용되는 경우는 거의 없다.

대체로 재사용 가능한 클래스는 재사용 모듈의 일부로써 해당 모듈의 다른 클래스와 상호작용 하는 경우가 많다.

ISP와의 관계

- CRP는 인터페이스 분리 원칙의 포괄적인 버전이다. CRP는 사용하지 않는 클래스를 가진 컴포넌트에 의존하지 말라고 한다.

- 필요하지 않은 것에 의존하지 말라.

### 컴포넌트 응집도에 대한 균형 다이어그램

---

REP - CCP : 포함 원칙, 두 원칙은 컴포넌트를 더욱 크게 만든다.

CRP : 배제 원칙

### 결론

과거에는 결합도에 대한 우리의 인식 수준이 REP, CCP, CRP가 의미하는 것 보다는 훨씬 단순했다.

응집도를 모듈은 단 하나의 기능만 수행해야 한다는 속성 정도로 단순하게 이해한 적도 있었다.

하지만 컴포넌트 응집도에 관한 세 가지 원칙은 응집도가 가질 수 있는 훨씬 복잡한 다양성을 설명해 준다.