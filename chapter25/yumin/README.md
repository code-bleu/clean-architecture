# 25. 계층과 경계

### 클린 아키텍처?

---

분명하게도 움퍼스 사냥 계임 예제의 맥락이라면 클린 아키텍처 접근법을 적용해서 유스케이스, 경계, 엔티티, 그리고 관련된 데이터 구조를 모두 만드는 일도 쉬운 일이다.

UI에서 언어가 유일한 변경의 축은 아니다. 이 밖에도 텍스트를 주고받는 메커니즘을 다양하게 만들고 싶을 수도 있다.

예를 들어 일반적인 셸 창을 사용하고 싶을 때도 있고, 텍스트 메시지나 채팅 애플리케이션을 사용하기를 원할수도 있다.

### 흐름 횡단하기

---

흐름은 여러가지일 수 있다.

컴포넌트가 만약 하나 추가될 경우 데이터 흐름이 두 개에서 세 개의 흐름으로 분리가 될 수 있으며, 상위의 흐름을 통할수도 있고, 시스템이 복잡해질수록 컴포넌트 구조는 더 많은 흐름으로 분리될 것이다.

### 흐름 분리하기

---

이쯤 되면 모든 흐름이 결국 상단의 단일 컴포넌트에서 서로 만난다고 생각할 수도 있다.

인생이 이처럼 단순하면 얼마나 좋을까! 물론 현실은 훨씬 복잡하다.

게임 규칙 중 일부는 지도와 관련된 메커니즘을 처리한다. 이 규칙들은 동굴이 서로 어떻게 연결될지, 각 동굴에 어떤 물체가 위치할지 등을 알고 있다. 또한 플레이어가 동굴에서 동굴로 이동하는 방법이나, 플레이어가 반드시 처리해야 하는 사건을 결정하는 방법도 알고 있다.

이보다 더 높은 수준에는 또 다른 정책 집합이 존재한다.

### 결론

---

이 모든 것이 의미하는 바는 무엇일까?

콘 셸에서 단 200줄이면 구현할 수 있는 터무니없이 간단한 프로그램을 가져와서, 이처럼 정신없는 아키텍처 경계를 모두 추론해 내는 이유는 무엇일까?

아키텍처 경계가 어디에나 존재한다는 사실을 보여주기 위함이다.

아키텍트로서 우리는 아키텍처 경계가 언제 필요한지를 신중하게 파악해내야 한다.

또한 우리는 이러한 경계를 제대로 구현하려면 비용이 많이 든다는 사실도 인지하고 있어야 한다.

이와 동시에 경계가 무시되었다면 나중에 다시 추가하는 비용이 크다는 사실도 알아야 한다.

포괄적인 테스트 스위트가 존재하고 리팩터링으로 단련되었더라도 마찬가지다.

아키텍트인 우리는 어떻게 해야 할까?

정답은 만족스럽지 못하다.

한편으로는 매우 똑똑한 일부 사람들이 우리에게 수년 동안 말해왔듯이, 추상화가 필요하리라고 미리 예측해서는 안 된다. 이것이 바로 You Aren`t Going to Need it가 말하는 철학이다.

이 문구에는 지혜가 담겨져 있는데, 오버 엔지니어링이 언더 엔지니어링보다 나쁠 때가 훨씬 많기 때문이다.

다른 한편으로는 어떤 아키텍처 경계도 존재하지 않는 상황에서 경계가 정말로 필요하다는 사실을 발견한 경우, 그때서야 경계를 추가하려면 비용이 많이 들고 큰 위험을 감수해야 한다.

당신은 비용을 산정하고, 어디에 아키텍처 경계를 둬야 할지, 그리고 완벽하게 구현할 경계는 무엇인지와 부분적으로 구현할 경계와 무시할 경계는 무엇인지를 결정해야만 한다.

프로젝트 초반에는 구현할 경계가 무엇인지와 무시할 경계가 무엇인지를 쉽게 결정할 수 없다. 대신 지켜봐야 한다. 시스템이 발전함에 따라 주의를 기울여야 한다. 경계가 필요할 수도 있는 부분에 주목하고, 경계가 존재하지 않아 생기는 마찰의 어렴풋한 첫 조짐을 신중하게 관찰해야 한다.

첫 조짐이 보이는 시점이 되면, 해당 경계를 구현하는 비용과 무시할 때 감수할 비용을 가늠해 본다. 그리고 결정된 사항을 자주 검토한다.

우리의 목표는 경계의 구현 비용이 그걸 무시해서 생기는 비용보다 적어지는 바로 그 변곡점에서 경계를 구현하는 것이다.

목표를 달성하려면 빈틈없이 지켜봐야 한다.