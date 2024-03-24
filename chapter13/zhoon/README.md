# 13장. 컴포넌트 응집도

## Introduction

- 어떤 클래스를 어느 컴포넌트에 포함시켜야 하는지는 중요한 결정이므로 제대로 된 소프트웨어 엔지니어링 원칙의 도움을 받아야 한다.
- 안타깝게도 수 년 동안 우리는 거의 순전히 상황에 따라 임시방편적으로 결정을 내려옴
- 이 장에서는 컴포넌트 응집도와 관련한 세 가지 원칙을 논의
  - REP
    - 재사용/릴리스 등가 원칙
    - Reuse/Release Equivalence Principle
  - CCP
    - 공통 폐쇄 원칙
    - Common Closure Principle
  - CRP
    - 공통 재사용 원칙
    - Common Reuse Principle

## REP: 재사용/릴리스 등가 원칙

> 재사용 단위는 릴리스 단위와 같다.

- 우리는 이제 소프트웨어 재사용의 시대에 살고 있다.
  - 지난 십 년은 메이븐, 라이닝언, RVM 같은 모듈 관리 도구가 우후죽순으로 등장한 시기
  - 이 기간에 재사용 가능한 컴포넌트나 컴포넌트 라이브러리가 엄청나게 많이 만들어졌기 때문
- 매우 당연해 보인다.
  - 소프트웨어 컴포넌트가 릴리스 절차를 통해 추적 관리되지 않거나, 릴리스 번호가 부여되지 않는다면 해당 컴포넌트를 재사용하고 싶어도 할 수도 없고, 하지도 않을 것
- 릴리스 번호가 없다면
  - 재사용 컴포넌트들이 서로 호환되는지 보증할 방법이 전혀 없음
  - 새로운 버전이 언제 출시되는지 알 수 없음
  - 무엇이 변했는지 알 수 없음
- 새로운 릴리스가 나온다면
  - 개발자는 새 릴리스의 변경 사항을 살펴보고 기존 버전을 계속 쓸지 여부를 결정
  - 따라서 릴리스 절차에는 적절한 공지와 함께 릴리스 문서 작성도 포함되어야 함
  - 그래야 개발자가 충분한 정보를 바탕으로 새 릴리스를 통합할 지, 한다면 언제 할 지를 결정할 수 있음

### 소프트웨어 설계와 아키텍처 관점

- 단일 컴포넌트는 응집성 높은 클래스와 모듈들로 구성되어야 함
- 컴포넌트를 구성하는 모든 모듈은 서로 공유하는 중요한 테마나 목적이 있어야 함
- 하나의 컴포넌트로 묶인 클래스와 모듈은 반드시 함께 릴리스 할 수 있어야 함
  - 하나의 컴포넌트로 묶인 클래스와 모듈은 버전 번호가 같아야 하고,
  - 동일한 릴리스로 추적 관리되고,
  - 동일한 릴리스 문서에 포함되어야 한다
  - 이러한 사실은 컴포넌트 제작자 입장이나 사용자 입장에서도 이치에 맞는 얘기
- 이 원칙 자체는 중요하고, 원칙을 어기면 ‘이치에 맞지’ 않게 된다
- 만약 우리가 만든 컴포넌트가 REP 를 위배하면 컴포넌트 사용자가 알게 되고, 당신의 아키텍트로서의 능력을 높게 평하지 않을 것
- 이 원칙의 약점은 다음에 다룰 두 원칙이 지닌 강점을 통해 충분히 보완할 수 있음
- 실제로 CCP 와 CRP 는 REP 를 엄격하게, 하지만 제약을 가하는 측면에서 정의함

## CCP: 공통 폐쇄 원칙

> 동일한 이유로 동일한 시점에 변경되는 클래스를 같은 컴포넌트로 묶어라.
> 서로 다른 시점에 다른 이유로 변경되는 클래스는 다른 컴포넌트로 분리해라.

- 이 원칙은 단일 책임 원칙 (SRP) 를 컴포넌트 관점에서 다시 쓴 것
  - 변경의 이유가 여러 개 있어서는 안된다고 말함
- 대다수의 애플리케이션에서 유지보수성 (maintainability) 은 재사용성보다 훨씬 중요함
  - 애플리케이션에서 코드가 반드시 변경되어야 한다면, 이러한 변경이 여러 컴포넌트 도처에 분산되어 발생하기보다는, 차라리 변경 모두가 단일 컴포넌트에서 발생하는 편이 낫다.
  - 만약 변경을 단일 컴포넌트로 제한할 수 있다면, 해당 컴포넌트만 재배포하면 됨
    - 변경된 컴포넌트에 의존하지 않는 다른 컴포넌트는 다시 검증하거나 배포할 필요가 없다.
- 물리적 또는 개념적으로 강하게 결합되어 항상 함께 변경되는 클래스들은 하나의 컴포넌트에 속해야 한다.
  - 이를 통해 소프트웨어를 릴리스, 재검증, 배포하는 일과 관련된 작업량을 최소화할 수 있음
- 이 원칙은 개방 폐쇄 원칙 (OCP) 과도 밀접하게 관련이 있음
  - CCP 와 OCP 의 C (폐쇄) 는 뜻이 같다.
- 변경이 필요한 요구사항이 발생했을 때, 그 변경이 영향을 주는 컴포넌트들이 최소한으로 한정될 가능성이 확실히 높아짐

### SRP 와의 유사성

- CCP 는 컴포넌트 수준의 SRP
- 두 원칙 모두 다음와 같은 교휸으로 요약할 수 있음

> 동일한 시점에 동일한 이유로 변경되는 것들을 한데 묶어라.
> 서로 다른 시점에 다른 이유로 변경되는 것들은 서로 분리하라.

## CRP: 공통 재사용 원칙

> 컴포넌트 사용자들은 필요하지 않는 것에 의존하게 강요하지 말라.

- 재사용되는 경향이 있는 클래스와 모듈들은 같은 컴포넌트에 포함해야 한다고 말함
- 컴포넌트 내부에서는 클래스들 사이에 수많은 의존성이 있으리라고 예상할 수 있음
  - 예를 들어 컨테이너 클래스와 해당 클래스의 이터레이터 클래스
  - 서로 강하게 결합되어 있기 때문에 함께 재사용됨
  - 따라서 이들 클래스는 반드시 동일한 컴포넌트에 위치해야 함
- CRP 는 각 컴포넌트에 어떤 클래스들을 포함시켜야 하는지를 설명
- CRP 는 동일한 컴포넌트로 묶어서는 안되는 클래스가 무엇인지도 말해줌
  - 어떤 컴포넌트가 다른 컴포넌트를 사용하면, 두 컴포넌트 사이에는 의존성이 생김
  - 의존성으로 인해 사용되는 컴포넌트가 변경될 때마다 사용하는 컴포넌트도 변경해야 할 가능성이 높음
  - 또는 사용하는 컴포넌트를 변경하지 않더라도, 재컴파일, 재검증, 재배포를 해야 하는 가능성은 여전히 남아 있음
  - 심지어 사용되는 컴포넌트에서 발생한 변경이 사용하는 컴포넌트와는 전혀 관련이 없는 경우라도!
- 따라서 의존하는 컴포넌트가 있다면 해당 컴포넌트의 모든 클래스에 대해 의존함을 확실히 인지해야 함
  - **즉, 한 컴포넌트에 속한 클래스들은 더 작게 그룹지을 수 없다.**
- CRP 는 어떤 클래스를 한데 묶어도 되는지보다는, 어떤 클래스를 한데 묶어서는 안 되는지에 대해서 훨씬 더 많은 것을 이야기함
- CRP 는 강하게 결합되지 않은 클래스들을 동일한 컴포넌트에 위치시켜서는 안 된다고 말함

### ISP 와의 관계

- CRP 는 인터페이스 분리 원칙 (ISP) 의 포괄적인 버전
- 두 조언 모두 다음의 한 문장으로 요약 가능

> 필요하지 않은 것에 의존하지 말라.

## 컴포넌트 응집도에 대한 균형 다이어그램

- 응집도에 관한 세 원칙이 서로 상충됨을 알 수 있다.
- REP 와 CCP 는 포함 원칙 (inclusive)
  - 컴포넌트를 더욱 크게 만듦
- CRP 는 배제 원칙 (exclusive)
  - 컴포넌트를 더욱 작게 만듦
- **뛰어난 아키텍트라면 이 원칙들이 균형을 이루는 방법을 찾아야 한다.**

![0.png](/clean-architecture/img/chapter13/zhoon/0.png)

- 뛰어난 아키텍트라면 이 규형 삼각형에서 개발팀이 현재 관심을 기울이는 부분을 충족시키는 위치를 찾아야 함
  - 또한 시간이 흐르면서 개발팀이 주의를 기울이는 부분 역시 변한다는 사실도 이해하고 있어야 함
- 프로젝트 초기에는 CCP 가 REP 보다 훨씬 중요함
  - 개발 가능성 (developability) 이 재사용성보다 더욱 중요하기 때문
- 일반적으로 프로젝트는 삼각형의 오른쪽에서 시작하는 편
  - 이때는 오직 재사용성만 희생하면 된다.
- 프로젝트가 성숙하고, 그 프로젝트로부터 파생된 또 다른 프로젝트가 시작되면, 프로젝트는 삼각형에서 점차 왼쪽으로 이동
  - **즉, 프로젝트의 컴포넌트 구조는 시간과 성숙도에 따라 변한다.**
- 다시 말해 프로젝트가 실제로 수행하는 일 자체보다는 프로젝트가 발전되고 사용되는 방법과 더 관련이 깊다.

## 결론

- 컴포넌트 응집도에 관한 세 가지 원칙은 응집도가 가질 수 있는 훨씬 복잡한 다양성을 설명
- 어느 클래스를 묶어서 컴포넌트로 만들지를 결정할 때, 재사용성과 개발 가능성이라는 상충하는 힘을 반드시 고려해야 함
- 이들 사이에서 애플리케이션의 요구에 맞게 균형을 잡는 일은 중요, 그리고 이 균형점은 항상 유동적임
- 시간이 흐름에 따라 프로젝트의 초점이 개발가능성에서 재사용성으로 바뀌고, 그에 따라 컴포넌트를 구성하는 방식도 조금씩 흐트러지고 또 진화함