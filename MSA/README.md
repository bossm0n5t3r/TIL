# MSA

- [MSA](#msa)
  - [API Gateway](#api-gateway)
    - [개념](#개념)
    - [필요한 이유](#필요한-이유)
    - [주요 기능](#주요-기능)
    - [고려해야 할 사항](#고려해야-할-사항)
    - [Open Source](#open-source)
    - [References](#references)

## API Gateway

### 개념

- 서버 최선단에 위치하여 모든 API 호출을 받는 곳
- 받은 API를 인증한 후, 적절한 서비스들에 메세지가 전달될 수 있도록 한다.
- 모든 클라이언트 요청에 대한 엔드 포인트를 통합하는 서버
  - 마치 프록시 서버처럼 동작
- 인증 및 권한, 모니터링, 로깅등 추가적인 기능이 있다.

### 필요한 이유

- 각각의 서비스마다 인증/인가 등 공통된 로직을 구현해야하는 번거로움을 줄일 수 있다.
- 수많은 API 호출을 기록하고 관리할 수 있다.
- 클라이언트에서 여러 마이크로서비스에 대한 번거로운 호출을 해야할 필요가 없다.
- 내부의 비즈니스 로직이 드러나게 되어 보안이 취약해지는 것을 방지할 수 있다.

### 주요 기능

- 인증 및 인가 (Authentication and Authorization)
  - 인증 및 인가와 같은 소스코드에 대해서 각 MSA 마다 중복을 줄일 수 있다.
  - 인증서 관리나 인증, SSL, 프로토콜 변환
  - 각각의 서비스의 부담을 줄이고, 서비스의 관리 및 업그레이드를 보다 쉽게 할 수 있게 한다.
- 요청 절차의 단순화
  - 여러 MSA를 대상으로 하는 기능을 이용하려 할 때, API Gateway는 여러 클라이언트의 요청을 단일 클라이언트 요청으로 대체 가능
  - 클라이언트와 백엔드 간의 API 통신량을 줄여주어 대기시간을 줄이고, 효율성을 높일 수 있음
- 라우팅 및 로드밸런싱
  - 서비스 인스턴스들에 대한 부하분산 가능
- 서비스 오케스트레이션
  - 여러개의 MSA를 묶어서 새로운 서비스를 만드는 개념
  - 과도한 오케스트레이션 로직은 API Gateway의 부담을 늘려서 성능 저하를 일으킬 수 있으므로, 높은 이해가 선행되어야 한다.
- 서비스 디스커버리
  - 클라우드 환경에서 동적인 IP 주소와 포트번호를 찾는 것을 가리킨다.
  - API Gateway 에서는 서버사이드나, 클라이언트 사이드를 기준으로 하여 서비스 디스커버리를 구현할 수 있다.

### 고려해야 할 사항

- scale-out 적용이 유연하지 않을 경우, 병목지점이 되어 성능저하가 발생할 수 있다.
- 추가적인 계층이 만들어지는 것이기 때문에, 네트워크 latency 가 증가하게 된다.

### Open Source

1. Kong

- [https://github.com/kong](https://github.com/kong)

2. API Umbrella

- [https://github.com/NREL/api-umbrella](https://github.com/NREL/api-umbrella)

3. tyk.io

- [https://github.com/TykTechnologies/tyk](https://github.com/TykTechnologies/tyk)

4. Zuul

- [https://github.com/Netflix/zuul](https://github.com/Netflix/zuul)

### References

- [https://blog.naver.com/dktmrorl/222129517689](https://blog.naver.com/dktmrorl/222129517689s)
