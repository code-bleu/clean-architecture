# 34장. 빠져 있는 장

## Introduction

- 설계나 코드 조직화와 관련된 몇 가지 접근법을 살펴보자

## 계층 기반 패키지

- 가장 단순한 첫 번째 설계 방식은 전통적인 수평 계층형 아키텍처
- 기술적인 관점에서 해당 코드가 하는 일에 기반해 그 코드를 분할함
- 흔히 우리는 이 방식을 ‘계층 기반 패키지’라고 부름
- 이 아키텍처는 엄청난 복잡함을 겪지 않고도 무언가를 작동시켜 주는 아주 빠른 방법
- 소프트웨어가 커지고 복잡해지기 시작하면, 머지 않아 큰 그릇 세 개만으로는 모든 코드를 담기엔 부족하다는 사실을 깨닫고, 더 잘게 모듈화해야 할지를 고민하게 될 것
- 계층형 아키텍처는 업무 도메인에 대해 아무것도 말해주지 않는다는 문제도 있음

## 기능 기반 패키지

- 서로 연관된 기능, 도메인 개념, 또는 Aggregate Root 에 기반하여 수직의 얇은 조각으로 코드를 나누는 방식
- 저자가 본 전형적인 구현에서는 모든 타입이 하나의 자바 패키지에 속하며, 패키지 이름은 그 안에 담긴 개념을 반영해 지음
- 저자는 소프트웨어 개발팀이 수평적 계층화(계층 기반 패키지)의 문제를 깨닫고, 수직적 계층화(기능 기반 패키지)로 전환하는 걸 자주 목격함
  - 저자가 보기에 두 접근법은 모두 차선책

## 포트와 어댑터

- “포트와 어댑터 ports and adapters” 혹은 “육각형 아키텍처 hexagonal architecture”, “경계, 컨트롤러, 엔티티 BCE” 등의 방식으로 접근하는 이유는 업무/도메인에 초점을 둔 코드가 프레임워크가 데이터베이스 같은 기술적인 세부 구현과 독립적이며 분리된 아키텍처를 만들기 위해서임
- 그런 코드 베이스는 내부(도메인)와 외부(인프라)로 구성됨을 흔히 볼 수 있음
- 내부 영역
  - 도메인 개념을 모두 포함
- 외부 영역
  - 외부 세계와의 상호작용을 포함함
- 주요 규칙
  - 외부가 내부에 의존하며, 절대 그 반대로는 안된다는 점
- 도메인 주도 설계에서는 내부에 존재하는 모든 것의 이름은 반드시 유비쿼터스 도메인 언어 관점에서 기술하라고 조언함

## 컴포넌트 기반 패키지

- 코드를 조직화하는 방법에 대해 또 다른 선택지
- 지금까지 우리가 본 모든 것들을 혼합한 것
- 큰 단위의 단일 컴포넌트와 관련된 모든 책임을 하나의 자바 패키지로 묶는 데 주안점을 둠
- 이 접근법은 서비스 중심적인 시각으로 소프트웨어 시스템을 바라보며, 마이크로서비스 아키텍처가 가진 시각과도 동일함
- 사용자 인터페이스를 큰 단위의 컴포넌트로부터 분리해서 유지함
- 본질적으로 이 접근법에서는 ‘업무 로직’과 영속성 관련 코드를 하나로 묶는데, 이 묶음을 저자는 ‘컴포넌트’라고 부름
- 컴포넌트에 대한 엉클 밥의 정의
  - 컴포넌트는 배포 단위다. 컴포넌트는 시스템의 구성 요소로, 배포할 수 있는 가장 작은 단위다. 자바의 경우 jar 파일이 컴포넌트다.
- 컴포넌트에 대한 저자의 정의
  - 컴포넌트는 멋지고 깔끔한 인터페이스로 감싸진 연관된 기능들의 묶음으로, 애플리케이션과 같은 실행 환경 내부에 존재한다.
- 이 방법론에서 소프트웨어 시스템은 하나 이상의 컨테이너로 구성되며, 각 컨테이너는 하나 이상의 컴포넌트를 포함함
  - 또한 각 컴포넌트는 하나 이상의 클래스 (또는 코드) 로 구현됨
  - 이때 각 컴포넌트가 개별 jar 파일로 분리될지 여부는 직교적인 관심사 orthogonal concern
- 컴퍼넌트 기반 패키지 접근법의 주된 이점
  - 도메인과 관련된 무언가를 코딩할 때 오직 한 곳, 컴포넌트만 둘러보면 된다는 점
  - 이 컴포넌트 내부에서 관심사의 분리는 여전히 유효하며, 따라서 업무 로직은 데이터 영속성과 분리되어 있음
  - 하지만 이는 컴포넌트 구현과 관련된 세부사항으로, 사용자는 알 필요가 없음
  - 이는 마이크로서비스나 서비스 지향 아키텍처를 적용했을 때 얻는 이점과도 유사함

## 구현 세부사항엔 항상 문제가 있다

## 조직화 vs. 캡슐화

- 계층 기반 패키지, 기능 기반 패키지, 포트와 어댑터, 컴포넌트 기반 패키지 각각의 접근법에서 다이어그램이 인상적으로 변함

## 다른 결합 분리 모드

- 프로그래밍 언어가 제공하는 방법 외에도 소스 코드 의존성을 분리하는 방법이 존재할 수 있음
- 다른 선택지로는 소스 코드 수준에서 의존성을 분리하는 방법도 있음
  - 정확하게는 서로 다른 소스 코드 트리로 분리하는 방법
- 소스 코드 트리로 분리하는 방법은 빌드 도구를 사용해서 모듈이나 프로젝트가 서로 분리되도록 구성해야 함
  - 이는 너무 이상적인 해결책
- 포트와 어댑터 접근법을 적용할 때는 이보다 더 간단한 방법을 사용하기도 함
  - 단순히 소스 코드 트리를 두 개만 만드는 것
  - 도메인 코드 (내부)
  - 인프라 코드 (외부)
- 이 방법은 잠재적으로 절충해야 할 부분이 있음을 알고 있어야만 함
- 저자는 이를 “포트와 어댑터에 대한 페리페리크 안티 패턴” 이라 부름

## 결론: 빠져 있는 조언

- 이 장은 최적의 설계를 꾀했더라도, 구현 전략에 얽힌 복잡함을 고려하지 않았으면 설계가 순식간에 망가질 수 있다는 사실을 강조하는 데 그 목적이 있음
- 설계를 어떻게 해야만 원하는 코드 구조로 매핑할 수 있을지, 그 코드를 어떻게 조직화할지, 런타임과 컴파일타임에 어떤 결합 분리 모드를 적용할지를 고민하라
- 가능하다면 선택사항을 열어두되, 실용주의적으로 행하라
- 그리고 팀의 규모, 기술 수준, 해결책의 복잡성을 일정과 예산이라는 제약과 동시에 고려하라
- 또한 선택된 아키텍처 스타일을 강제하는 데 컴파일러의 도움을 받을 수 있을지를 고민하며, 데이터 모델과 같은 다른 영역에 결합되지 않도록 주의하라
- 구현 세부사항에는 항상 문제가 있는 법이다