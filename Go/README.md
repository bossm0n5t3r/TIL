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
  - [프로젝트 레이아웃](#프로젝트-레이아웃)
  - [Go 디렉터리](#go-디렉터리)
    - [/cmd](#cmd)
  - [GOPATH, PATH 설정하기](#gopath-path-설정하기)
  - [프로토콜 컴파일러 플러그인 설치하기](#프로토콜-컴파일러-플러그인-설치하기)
    - [직접 설치하기](#직접-설치하기)
    - [도커로 설치해서 사용하기](#도커로-설치해서-사용하기)

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

## 프로젝트 레이아웃

- 정해진 프로젝트 레이아웃은 따로 없지만, Go 생태계에서 역사적이거나 급부상중인 프로젝트 레이아웃 패턴들의 공통된 부분에 대한 레이아웃은 있다.
- [https://github.com/golang-standards/project-layout](https://github.com/golang-standards/project-layout)

## Go 디렉터리

- Go 디렉터리는 아래와 같이 나눠져 있다.
  - `/cmd`
  - `/pkg`
  - `/internal`
  - `/assets`

### /cmd

- 프로젝트의 메인 애플리케이션들
- 각 애플리케이션의 디렉터리명은 만들고싶은 실행 파일 이름과 같아야 한다.
- 흔히 `/internal`와 `/pkg` 디렉터리 코드를 임포트, 호출만 하는 작은 `main` 함수는 흔히 볼 수 있다.
- 그러면 로직 코드들은 어디에?
  - `/pkg`
    - 공통 로직 코드를 넣는 곳
  - `/internal`
    - 코드가 재사용성이 없거나 다른사람들이 재사용하지 않기를 바란다면 코드를 넣는 곳

## GOPATH, PATH 설정하기

- `~/.zshrc` 에 다음을 추가해주면 된다.

```zsh
# GOPATH
export GOPATH=$HOME/go
export PATH="$PATH:$GOPATH/bin"
```

## 프로토콜 컴파일러 플러그인 설치하기

- 이 부분은 직접 설치하는 방법도 있는데, 도커를 통해서 깔끔하게 설치하는 방법을 알게 되어, 도커 방법으로 진행해 보려고 한다.

### 직접 설치하기

- 참고링크
  - [https://grpc.io/docs/languages/go/quickstart/#prerequisites](https://grpc.io/docs/languages/go/quickstart/#prerequisites)

```sh
$ go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.26
$ go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.1
```

- 물론 이 방법은 직접 해보지도 않아서 결과가 없다.

### 도커로 설치해서 사용하기

- 참고링크
  - [https://hub.docker.com/r/znly/protoc](https://hub.docker.com/r/znly/protoc)
  - [https://github.com/znly/docker-protobuf](https://github.com/znly/docker-protobuf)
- `znly` 라는 어플에서 만들어서 사용하는 도커라고 한다.
  - 실제로 도커허브에서 보면 `100K+` 정도니 많이들 사용하는 모양이다.
- 설치하기

```sh
$ docker pull znly/protoc
```

- 명령어 확인하기

```sh
 docker run --rm znly/protoc --help
Usage: /usr/bin/protoc [OPTION] PROTO_FILES
Parse PROTO_FILES and generate output based on the options given:
-IPATH, --proto_path=PATH   Specify the directory in which to search for
                            imports.  May be specified multiple times;
                            directories will be searched in order.  If not
                            given, the current working directory is used.
--version                   Show version info and exit.
-h, --help                  Show this text and exit.
--encode=MESSAGE_TYPE       Read a text-format message of the given type
                            from standard input and write it in binary
                            to standard output.  The message type must
                            be defined in PROTO_FILES or their imports.
--decode=MESSAGE_TYPE       Read a binary message of the given type from
                            standard input and write it in text format
                            to standard output.  The message type must
                            be defined in PROTO_FILES or their imports.
--decode_raw                Read an arbitrary protocol message from
                            standard input and write the raw tag/value
                            pairs in text format to standard output.  No
                            PROTO_FILES should be given when using this
                            flag.
--descriptor_set_in=FILES   Specifies a delimited list of FILES
                            each containing a FileDescriptorSet (a
                            protocol buffer defined in descriptor.proto).
                            The FileDescriptor for each of the PROTO_FILES
                            provided will be loaded from these
                            FileDescriptorSets. If a FileDescriptor
                            appears multiple times, the first occurrence
                            will be used.
-oFILE,                     Writes a FileDescriptorSet (a protocol buffer,
  --descriptor_set_out=FILE defined in descriptor.proto) containing all of
                            the input files to FILE.
--include_imports           When using --descriptor_set_out, also include
                            all dependencies of the input files in the
                            set, so that the set is self-contained.
--include_source_info       When using --descriptor_set_out, do not strip
                            SourceCodeInfo from the FileDescriptorProto.
                            This results in vastly larger descriptors that
                            include information about the original
                            location of each decl in the source file as
                            well as surrounding comments.
--dependency_out=FILE       Write a dependency output file in the format
                            expected by make. This writes the transitive
                            set of input file paths to FILE
--error_format=FORMAT       Set the format in which to print errors.
                            FORMAT may be 'gcc' (the default) or 'msvs'
                            (Microsoft Visual Studio format).
--print_free_field_numbers  Print the free field numbers of the messages
                            defined in the given proto files. Groups share
                            the same field number space with the parent
                            message. Extension ranges are counted as
                            occupied fields numbers.

--plugin=EXECUTABLE         Specifies a plugin executable to use.
                            Normally, protoc searches the PATH for
                            plugins, but you may specify additional
                            executables not in the path using this flag.
                            Additionally, EXECUTABLE may be of the form
                            NAME=PATH, in which case the given plugin name
                            is mapped to the given executable even if
                            the executable's own name differs.
--cpp_out=OUT_DIR           Generate C++ header and source.
--csharp_out=OUT_DIR        Generate C# source file.
--java_out=OUT_DIR          Generate Java source file.
--javanano_out=OUT_DIR      Generate Java Nano source file.
--js_out=OUT_DIR            Generate JavaScript source.
--objc_out=OUT_DIR          Generate Objective C header and source.
--php_out=OUT_DIR           Generate PHP source file.
--python_out=OUT_DIR        Generate Python source file.
--ruby_out=OUT_DIR          Generate Ruby source file.
```
