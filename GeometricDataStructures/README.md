# Geometric Data Structures

- [Geometric Data Structures](#geometric-data-structures)
  - [개요](#개요)
  - [Tables](#tables)
  - [References](#references)

## 개요

- 네비게이션 시스템을 생각해보자.
  - 이 시스템은 전체 지도를 시스템에 가지고 있어야 한다.
  - 이용자의 현재 위치를 추적해야한다.
  - 이용자의 현재 위치와 적절한 부분을 화면에 보여줘야 한다.
  - 이것은 언제나 사용자의 현재 위치 주변의 정사각형 지역이 된다.
- 지도는 충분한 디테일을 가져야 한다.
  - 유럽 전체의 상세한 지도는 어마어마한 데이터가 포함되어있다.
  - 다행히, 그 지도의 작은 부분만 항상 표시된다.
  - 그럼에도 불구하고, 시스템은 반드시 주어진 정사각형 지역, 또는 `window`에 놓여질 지도의 파트를 찾아야 하고, 결정해서 표시해야한다.
  - 이것을 `windowing query`라고 부른다.

> Window
>
> 시스템에서 보여지는 정사각형의 지역

> Windowing query
>
> 시스템에서 `window`에 놓여질 파트를 찾고, 결정해서 나타내는 것

- `Windowing queries`는 지도에서 유용한 연산일뿐만 아니라, 컴퓨터 그래픽과 CAD/CAM에서 몇몇 애플리케이션에서 중요한 역할을 맡고 있다.
- `Windowing queries`는 `Chapter 5`에서 공부했던 `range queries`와 비슷하다.
- 차이점은 다루는 데이터의 타입이다.
  - `range queries`
    - 데이터
      - points (점)
    - search places
      - 높은 차원의 검색 공간(higher dimensional search places)을 다룬다.
  - `Windowing queries`
    - 데이터
      - line segments (선분)
      - polygons (다면체)
      - curves (곡선)
      - 등등
    - search places
      - 2- or 3-dimensional

## Tables

- [Segment Trees](./segment-trees.md)

## References

- de Berg, Mark; van Kreveld, Marc; Overmars, Mark; Schwarzkopf, Otfried (2000). "More Geometric Data Structures". Computational Geometry: algorithms and applications (2nd ed.). Springer-Verlag Berlin Heidelberg New York. doi:10.1007/978-3-540-77974-2. ISBN 3-540-65620-0.
