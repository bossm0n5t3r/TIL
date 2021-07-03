# Linux

- [Linux](#linux)
  - [Shell](#shell)
    - [`sudo !!`](#sudo-)
    - [text를 자르고 붙이기](#text를-자르고-붙이기)
    - [터미널 재시작할 때](#터미널-재시작할-때)
    - [Referencs](#referencs)

## Shell

현재 예제 코드는 `macOS` 의 `zsh` 에서 실행한 결과입니다.

### `sudo !!`

임의의 명령어를 실행했을 때, `sudo` 권한이 필요해서 다시 `sudo`를 통해서 해당 명령어를 실행하려고 할 때,

`sudo !!`을 치게 되면 `sudo` + 바로 이전에 실행했던 명령어로 할 수 있다.

```sh
# 당연히 읽기 전용이기 때문에 수정할 수 가 없다.
# 수정하려면 다시 sudo vim /etc/hosts 를 치거나, sudo !!을 하면 된다.
$ vim /etc/hosts
$ sudo !!
$ sudo vim /etc/hosts
Password:
```

### text를 자르고 붙이기

`control + k` : 현재 커서 위치 ~ 끝까지 자른다.

`control + u` : 처음 ~ 현재 커서 위치까지 자른다.

`control + w` : 현재 커서에서 바로 앞의 단어(앞 스페이스)까지 자른다.

`control + y` : 다시 자른 부분을 다시 붙인다.

### 터미널 재시작할 때

터미널을 끄고 재시작할 필요가 있을 때, 그냥 `reset` 하면 된다.

### Referencs

- [My 5 Favorite Linux Shell Tricks for SPEEEEEED (and efficiency)
  ](https://www.youtube.com/watch?v=V8EUdia_kOE)
