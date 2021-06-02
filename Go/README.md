# Go

- [Go](#go)
  - [설치하기](#설치하기)
    - [Mac](#mac)
  - [VSCode extension 설치](#vscode-extension-설치)
  - [go mod init](#go-mod-init)
  - [전체 테스트 코드 실행](#전체-테스트-코드-실행)
  - [Module](#module)
    - [추가하기](#추가하기)
    - [모듈이 추가되는 위치](#모듈이-추가되는-위치)
    - [사용하지 않는 모듈 삭제하기](#사용하지-않는-모듈-삭제하기)

---

## 설치하기

### Mac

```bash
brew install go
```

- [https://formulae.brew.sh/formula/go](https://formulae.brew.sh/formula/go)

## VSCode extension 설치

- [Go](https://marketplace.visualstudio.com/items?itemName=golang.go) 하나만 설치

## go mod init

```bash
go mod init github.com/bossm0n5t3r/learning-go
```

- 꼭 깃허브 주소가 아니어도 된다.
  - 일반적인 패키지 주소도 가능하다.
  - [**그런데 왜 깃허브 주소를 많이 쓰지...?**](#모듈-추가-추가되는-위치-삭제하기)
- 테스트 코드를 작성하려면 기본적으로 `Module` 설정을 해두어야 한다.
  - 없으면 왜인지 안됨...

## 전체 테스트 코드 실행

```bash
go test ./...
```

- [https://stackoverflow.com/questions/16353016/how-to-go-test-all-tests-in-my-project](https://stackoverflow.com/questions/16353016/how-to-go-test-all-tests-in-my-project)

## Module

### 추가하기

- 아래처럼 다른 모듈을 가져와서 사용할 수도 있다.
  ```bash
    go get github.com/gin-gonic/gin
  ```
- 이 경우, `go.mod`파일이 수정된다.

  ```bash
  # 기존 go.mod 파일
  module github.com/bossm0n5t3r/learning-go

  go 1.16

  # go get 후 go.mod 파일
  module github.com/bossm0n5t3r/learning-go

  go 1.16

  require github.com/gin-gonic/gin v1.7.2 // indirect

  ```

### 모듈이 추가되는 위치

- 모듈은 어디에 추가되는가
  - `~/go` 안에 아래 위치에 모듈이 추가된다.
    ```bash
    zhoon 🚀   ~
     cd go/pkg/mod/github.com
    zhoon 🚀   ~/go/pkg/mod/github.com
     ll
    total 0
    drwxr-xr-x  3 matt  staff    96B  5 28 18:15 !burnt!sushi
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 cosiner
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 cpuguy83
    drwxr-xr-x  3 matt  staff    96B  6  1 01:01 cweill
    drwxr-xr-x  5 matt  staff   160B  6  1 18:40 fatih
    drwxr-xr-x  3 matt  staff    96B  6  2 14:48 gin-contrib
    drwxr-xr-x  3 matt  staff    96B  6  2 14:48 gin-gonic
    drwxr-xr-x  4 matt  staff   128B  6  1 18:40 go-delve
    drwxr-xr-x  5 matt  staff   160B  6  2 14:48 go-playground
    drwxr-xr-x  3 matt  staff    96B  6  2 14:48 golang
    drwxr-xr-x  4 matt  staff   128B  6  1 18:40 google
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 hashicorp
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 haya14busa
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 inconshreveable
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 josharian
    drwxr-xr-x  3 matt  staff    96B  6  2 14:48 json-iterator
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 karrick
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 konsorten
    drwxr-xr-x  3 matt  staff    96B  6  2 14:48 leodido
    drwxr-xr-x  5 matt  staff   160B  6  2 14:48 mattn
    drwxr-xr-x  4 matt  staff   128B  6  2 14:48 modern-go
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 peterh
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 pkg
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 ramya-rao-a
    drwxr-xr-x  4 matt  staff   128B  6  1 18:40 russross
    drwxr-xr-x  3 matt  staff    96B  5 28 18:15 sergi
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 sirupsen
    drwxr-xr-x  3 matt  staff    96B  6  1 18:40 skratchdot
    drwxr-xr-x  4 matt  staff   128B  6  1 18:40 spf13
    drwxr-xr-x  4 matt  staff   128B  6  2 14:48 ugorji
    drwxr-xr-x  5 matt  staff   160B  6  1 18:40 uudashr
    ```

### 사용하지 않는 모듈 삭제하기

- 사용하지 않는 모듈을 삭제하려면?
  ```bash
    go mod tidy
  ```
  - 이 경우 `go.mod` 의 `require`도 삭제된다.
