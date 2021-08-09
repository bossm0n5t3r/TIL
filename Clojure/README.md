# Clojure

- [Clojure](#clojure)
  - [개요](#개요)
  - [설치](#설치)
    - [확인하기](#확인하기)
  - [References](#references)

## 개요

- 그 사이를 못 참고 결국 새로운 언어를 설치했다.
  - 이것도 오래 안가겠지...
  - ~~사실 심심해서...~~
- 이게 전부다. 그럼 설치부터 고고!

## 설치

- Homebrew

```sh
 brew install clojure/tools/clojure
Updating Homebrew...
==> Auto-updated Homebrew!
Updated Homebrew from 6bb369916 to ea7540be8.
Updated 2 taps (homebrew/core and homebrew/cask).
==> New Formulae
bupstash                          docuum                            rsc_2fa
==> Updated Formulae
Updated 237 formulae.
==> New Casks
blackhole-64ch                    jiohome                           wifi-explorer-pro
==> Updated Casks
Updated 60 casks.

==> Tapping clojure/tools
Cloning into '/usr/local/Homebrew/Library/Taps/clojure/homebrew-tools'...
remote: Enumerating objects: 443, done.
remote: Counting objects: 100% (179/179), done.
remote: Compressing objects: 100% (134/134), done.
remote: Total 443 (delta 87), reused 136 (delta 45), pack-reused 264
Receiving objects: 100% (443/443), 50.32 KiB | 464.00 KiB/s, done.
Resolving deltas: 100% (204/204), done.
Tapped 60 formulae (72 files, 112.5KB).
==> Installing clojure from clojure/tools
==> Downloading https://ghcr.io/v2/homebrew/core/rlwrap/manifests/0.45.2
######################################################################## 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/rlwrap/blobs/sha256:4776bfe5bf3753463d331b150b37be72
==> Downloading from https://pkg-containers.githubusercontent.com/ghcr1/blobs/sha256:4776bfe5bf375346
######################################################################## 100.0%
==> Downloading https://download.clojure.org/install/clojure-tools-1.10.3.933.tar.gz
######################################################################## 100.0%
==> Installing dependencies for clojure/tools/clojure: rlwrap
==> Installing clojure/tools/clojure dependency: rlwrap
==> Pouring rlwrap--0.45.2.big_sur.bottle.tar.gz
🍺  /usr/local/Cellar/rlwrap/0.45.2: 45 files, 389KB
==> Installing clojure/tools/clojure
==> ./install.sh /usr/local/Cellar/clojure/1.10.3.933
🍺  /usr/local/Cellar/clojure/1.10.3.933: 11 files, 14.3MB, built in 5 seconds
```

### 확인하기

- `$ clj` 를 통해서 확인할 수 있다.

```sh
 clj
Downloading: org/clojure/clojure/1.10.3/clojure-1.10.3.pom from central
Downloading: org/clojure/spec.alpha/0.2.194/spec.alpha-0.2.194.pom from central
Downloading: org/clojure/core.specs.alpha/0.2.56/core.specs.alpha-0.2.56.pom from central
Downloading: org/clojure/pom.contrib/0.3.0/pom.contrib-0.3.0.pom from central
Downloading: org/clojure/clojure/1.10.3/clojure-1.10.3.jar from central
Downloading: org/clojure/core.specs.alpha/0.2.56/core.specs.alpha-0.2.56.jar from central
Downloading: org/clojure/spec.alpha/0.2.194/spec.alpha-0.2.194.jar from central
Clojure 1.10.3
user=>
```

- `Ctrl + D` 를 누르면 나올 수 있다.

```sh
 clojure
Clojure 1.10.3
user=>
```

- `$ clojure` 도 가능하다.

## References

- [https://clojure.org/guides/getting_started](https://clojure.org/guides/getting_started)
