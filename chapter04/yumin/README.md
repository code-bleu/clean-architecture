# 4장. 구조적 프로그래밍

### 증명

증명이라는 수학적인 원리를 적용하여 데이크스트라는 문제를 해결하고자 했다.

다익스트라는 goto문장이 모듈을 더 작은 단위로 재귀적으로 분해하는 과정에 방해가 되는 경우가 있다는 사실을 발견했다.

뵘과 야코피니가 다익스트라보다 2년 앞서 발견 한 사실

- 모든 프로그램을 순차, 분기, 반복이라는 세 가지 구조만으로 표현할 수 있다는 사실을 증명함.

분기

분기의 경우 다익스트라는 열거법을 재적용하는 방식으로 처리함.

분기를 통한 각 경로를 열거한다.

반복

반복이 올바름을 증명하기 위해 다익스트라는 귀납법을 사용했다.

현재의 우리 모두는 구조적 프로그래머이며, 여기에는 선택의 여지가 없다. 제어흐름을 제약 없이 직접 전환할 수 있는 선택권 자체를 언어에서 제공하지 않기 때문이다.

### 테스트

다익스트라는 테스트는 버그가 있음을 보여줄 뿐, 버그가 없음을 보여줄수는 없다고 말한적이 있다.

소프트웨어는 과학과 같다. 최선을 다하더라도 올바르지 않음을 증명하는 데 실패함으로써 올바름을 보여주기 때문이다.