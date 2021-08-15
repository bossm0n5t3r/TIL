# Interval Trees

- 먼저 우리는 각 변과 평행한 선분들(segments)들로 이뤄진 케이스로 가정한다.
  - 다른 말로, 밑변을 x축, 왼쪽변을 y축으로 가정하면, 임의의 선분들은 모두 x축또는 y축과 평행하다.
  - 그 선분들을 `axis-parallel`, 또는 `orthogonal`이라고 한다.
- 우리는 `query window`가 `axis-parallel`한 정사각형으로 가정한다.

---

- Let `S` be a set of n axis-parallel line segments
- `windowing queries`를 풀기 위해서, 우리는 segments들이 query windows `W`와 충분히 겹치는 `S`를 포함하는 data structures가 필요하다.
  - `W := [x:x']x[y:y']`
- 여기에는 몇 가지 케이스들이 있다.
  1. 선분이 `W`안에 온전히 포함되는 경우
  2. `W`의 경계와 딱 한 번 겹치는 경우
  3. `W`의 경계와 두 번 겹치는 경우
  4. `W`의 경계에 온전히 또는 부분적으로 겹치는 경우
  - 대부분의 경우 선분은 `W`안에 적어도 하나의 endpoint를 가지고 있다.
- 우리는 S 안에 있는 모든 선분들의 2n개의 endpoints들의 집합에 대해서 range query를 수행함으로써 몇몇 선분들을 찾을 수 있다.
  - Chapter 5에서 우리는 이것에 대한 data structures를 봤었다.
    - the range tree
  - 2차원 range tree는 O(nlogn) 스토리지를 사용하고, range querysms O(log^2n + k) (where, k는 reported points의 개수) 시간응답도를 갖는다.
  - 우리는 fractional를 적용해서 query time을 O(logn + k)까지 줄일 수 있음을 보였다.
- 여기에 한 가지 작은 문제점이 있다.
- 만약 우리가 W에 대해서 선분들의 endpoints들의 집합에서 range query를 할 경우, W 안에 두 endpoints 모두 포함된 선분들에 대해서 두 번씩 report하게 된다.
- 해결책
  - 이것은 우리가 처음 report한 선분들에 대해서 마킹을 하고, 마킹되지 않은 선분들을 report함으로써 해결할 수 있다.
  - 우리는 W안에 endpoint가 놓인 선분을 찾을 때, 다른 endpoint가 W안에 놓였는지, 놓이지 않았는지 체크할 수 있다.
    - 만약 아니라면, 우리는 segment를 report하면 된다.
    - 만약 다른 endpoint가 W안에 놓였다면, 우리는 현재 endpoint가 왼쪽이거나 아래에 있는 endpoint일 때만 segment를 report 하면 된다.
      - 왜냐하면, 두 endpoint가 모두 W안에 놓여있기 때문에, 두 개 모두 report하면 중복이라, 왼쪽이거나, 아래쪽일 때만 report해서 중복을 피하기 위함
    - 이를 통해서 아래 `lemma`가 도출된다.

Lemma 10.1 >> `S`가 평면 위에 n개의 `axis-parallel`한 선분들의 집합이라고 하자. `axis-parallel`한 query window `W`안에 적어도 하나의 endpoint가 포함되어있는 선분들은 O(nlogn) 스토리지와 전처리시간을 사용하는 data structure에서 O(logn + k) 시간동안 report할 수 있다. (k는 reported 선분들의 개수)
