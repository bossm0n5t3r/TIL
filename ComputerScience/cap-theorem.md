# CAP Theorem (Brewer's theorem)

![truth-of-cap-theorem-diagram.png](../assets/images/ComputerScience/truth-of-cap-theorem-diagram.png)[1]

- [CAP Theorem (Brewer's theorem)](#cap-theorem-brewers-theorem)
  - [CP 시스템](#cp-시스템)
  - [AP 시스템](#ap-시스템)
  - [CA 시스템](#ca-시스템)
  - [결론](#결론)
  - [References](#references)

> It is impossible for a distributed data store to simultaneously provide more than two out of the following three guarantees.

- 분산 데이터스토어가 다음 세 가지 guarantee 중 두 가지를 초과해서 동시에 제공하는 것은 불가능하다.
  - 3가지를 모두 만족할 수는 없다.
  - 최대 2개까지 만족할 수 있다.

> Consistency: Every read receives the most recent write or an error

- `Consistency` (일관성)
  - 모든 읽기에 최근 쓰기 또는 오류가 수신됩니다.

> Availability: Every request receives a (non-error) response, without the guarantee that it contains the most recent write

- `Availability` (가용성)
  - 모든 요청은 최근 쓰기가 포함되어 있다는 보장 없이 (오류 없음) 응답을 수신한다.

> Partition tolerance: The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes

- `Partition tolerance` (분할 내성)
  - 노드 간 네트워크에서 임의의 수의 메시지를 삭제(또는 지연)하더라도 시스템은 계속 작동한다.

## CP 시스템

- `Consistency` (일관성), `Partition tolerance` (분할 내성)
- 완벽한 일관성을 갖는 분산 시스템에서 데이터 변경은 모든 노드에 복제가 되어야 완료된다.
  - **가용성과 성능에 악영향**을 끼친다.
- 하나의 노드라도 문제가 있으면 트랜잭션 실패
- 노드가 늘어날수록 지연시간 증가

## AP 시스템

- `Availability` (가용성), `Partition tolerance` (분할 내성)
- 완벽한 가용성을 갖는 분산 시스템에서는 모든 노드가 어떤 상황에서도 응답해야한다.
- **네트워크 문제가 발생**해서 어떤 노드에 Replication이 제대로 이뤄지지 않아도 **가용성을 위해서 해당 노드에 접근한 사용자에게 데이터를 반환**한다면,
  - **일관성이 깨지고**, **사용자는 문제가 발생한 것도 인지 못할 것**이다.

## CA 시스템

- `Consistency` (일관성),`Availability` (가용성)
- 일관성과 가용성을 동시에 만족하려면, 네트워크 장애를 허용하지 않아야 한다.
- 하지만, 네트워크 장애가 절대 일어나지 않는 네트워크 구성은 없다.

## 결론

- 결국 CAP 이론은 `Partition tolerance`을 기본적으로 깔고 시작해야 한다.
- 무조건 P를 선택하고, C와 A 중 하나를 골라야 한다면, CP, AP 시스템을 골라야 하는데,
- 어느 한 쪽을 완벽히 만족하는 시스템을 구축하는 것이 아니라 **일관성과 가용성을 서비스 목적에 맞게 균형잡힌 시스템**은 없을까?

## References

- [https://en.wikipedia.org/wiki/CAP_theorem](https://en.wikipedia.org/wiki/CAP_theorem)
- [https://www.ibm.com/cloud/learn/cap-theorem](https://www.ibm.com/cloud/learn/cap-theorem)
- [https://ohjongsung.io/2019/05/01/cap-%EC%9D%B4%EB%A1%A0%EA%B3%BC-pacelc-%EC%9D%B4%EB%A1%A0](https://ohjongsung.io/2019/05/01/cap-%EC%9D%B4%EB%A1%A0%EA%B3%BC-pacelc-%EC%9D%B4%EB%A1%A0)

[1]: https://ohjongsung.io/2019/05/01/cap-%EC%9D%B4%EB%A1%A0%EA%B3%BC-pacelc-%EC%9D%B4%EB%A1%A0
