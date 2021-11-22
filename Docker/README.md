# Docker

- [Docker](#docker)
  - [컨테이너에서 localhost 연결하는 방법](#컨테이너에서-localhost-연결하는-방법)
    - [References](#references)

## 컨테이너에서 localhost 연결하는 방법

- 도커 컨테이너를 실행한 후, 로컬에서 실행한 localhost 에 붙어야 하는 경우가 있을 것이다.
- 그럴땐 당황하지말고, `127.0.0.1` 대신에 `host.docker.internal` 를 사용하면 된다.
- 물론 연결할 포트도 뚫어 놓아야 한다.
- 그 밖의 설정은 아래 글을 참고하자.

### References

- [https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach](https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach)
- [https://docs.docker.com/desktop/mac/networking/](https://docs.docker.com/desktop/mac/networking/)
- [https://docs.docker.com/desktop/windows/networking/](https://docs.docker.com/desktop/windows/networking/)
