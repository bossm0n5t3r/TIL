# Go

- [Go](#go)
  - [설치하기](#설치하기)
    - [Mac](#mac)
  - [VSCode extension 설치](#vscode-extension-설치)
  - [Module](#module)
  - [전체 테스트 코드 실행](#전체-테스트-코드-실행)

---

## 설치하기

### Mac

```bash
brew install go
```

- [https://formulae.brew.sh/formula/go](https://formulae.brew.sh/formula/go)

## VSCode extension 설치

- [Go](https://marketplace.visualstudio.com/items?itemName=golang.go) 하나만 설치

## Module

```bash
go mod init github.com/bossm0n5t3r/learning-go
```

- 꼭 깃허브 주소가 아니어도 된다.
  - 일반적인 패키지 주소도 가능하다.
  - **그런데 왜 깃허브 주소를 많이 쓰지...?** (나중에 확인하고 추가할 것)
- 테스트 코드를 작성하려면 기본적으로 `Module` 설정을 해두어야 한다.
  - 없으면 왜인지 안됨...

## 전체 테스트 코드 실행

```bash
go test ./...
```

- [https://stackoverflow.com/questions/16353016/how-to-go-test-all-tests-in-my-project](https://stackoverflow.com/questions/16353016/how-to-go-test-all-tests-in-my-project)
