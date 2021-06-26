# Software Design Pattern

- [Software Design Pattern](#software-design-pattern)
  - [MVC (Model-View-Controller)](#mvc-model-view-controller)
    - [Model](#model)
    - [View](#view)
    - [Controller](#controller)
    - [References](#references)

## MVC (Model-View-Controller)

![MVC-Process.svg](../assets/images/SoftwareDesignPattern/MVC-Process.svg)

### Model

> The central component of the pattern. It is the application's dynamic data structure, independent of the user interface. It directly manages the data, logic and rules of the application.

- 패턴의 중앙 구성 요소.
- 사용자 인터페이스와 관계없이 애플리케이션의 동적 데이터 구조이다.
- 애플리케이션의 데이터, 논리 및 규칙을 직접 관리한다.

### View

> Any representation of information such as a chart, diagram or table. Multiple views of the same information are possible, such as a bar chart for management and a tabular view for accountants.

- 차트, 다이어그램, 표와 같은 모든 정보의 표현.
- 관리에 대한 막대 차트 및 회계사에 대한 표 보기와 같이 동일한 정보를 여러 개 볼 수 있다.

### Controller

> Accepts input and converts it to commands for the model or view.

- 입력을 수용하고, 입력을 모델이나 뷰에 대한 명령어로 변환한다.

어플리케이션을 을 이러한 구성 요소로 나누는 것 외에도, model-view-controller 패턴은 이들 구성요소 사이의 상호관계를 아래와 같이 정의한다.

- `모델`은 **애플리케이션의 데이터를 관리하는 역할**을 한다. `컨트롤러`에서 **사용자 입력을 수신**한다.
- `뷰`는 `모델`을 **특정 형식으로 표시하도록 렌더링**한다.
- `컨트롤러`는 **사용자 입력에 응답**하고 **데이터 모델 객체에 대해 상호 작용을 수행**한다. `컨트롤러`는 **입력을 수신하고 선택적으로 유효성을 검사**한 다음 `모델`에 **입력을 전달**한다.

다른 소프트웨어 패턴과 마찬가지로 MVC는 문제에 대해 "솔루션의 핵심"을 표현하면서 각 시스템에 맞게 문제를 조정할 수 있도록 한다. 특정 MVC 설계는 기존의 설명과 크게 다를 수 있다.

### References

- [https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)
