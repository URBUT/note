## 환경구성
1. IDE
: `Intellij`사용 (개인용) , `Eclipse`(회사)

2. Editor
: `Atom` (github 연동), `Haroopad`(markdown editor)
Atom에서도 마크다운 문법 작성 가능하고 preview 또한 가능하지만, 도움말 기능등이 있는 하루패드를 더 애용한다.
하루 패드는 설치 이외에 별도의 작업이 필요 없음.

3. 저장소
: `github` , 단 혹시모를 일을 위해 home의 git local dir을 `dropbox` 로 설정해놓음

***
## Atom 설치 후 작업 내역

#### Markdown-preview 설치
기본적으로 markdown 문법처리에는 문제가 없으나 실시간으로 작성되는 preview를 사용하기 위해서
`markdown-preview-enhanced`  plugi-in을 설치.
이 외에 글꼴 수정(on Windows, Linux)
자세한 내용은 [여기](http://futurecreator.github.io/2016/06/14/atom-as-markdown-editor/)를 참고.

#### Github 연동
###### 1. Git 설치
**Linux**

A.
- [repository에서 설치] : 향후 버전업그레이드를 고려하면 더 나을 듯 하다.
```
$ sudo add-apt-repository ppa:git-core/ppa
$ sudo apt-get update && sudo apt-get dist-upgrade
$ sudo apt-get install git
$ sudo apt-get install git-core
$ sudo apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev build-essential
```
- [소스 코드 컴파일을 통한 설치]
[http://git-scm.com/download](http://git-scm.com/download) 에서 소스 다운로드
```
$ tar -xzf git-x.x.x.x.tar.gz
$ cd git-x.x.x.x
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install
```

B.
```
<name setting>
$ git config --global user.name="URBUT"

<email setting>
$ git config --global user.email="hojun188@gmail.com"

<Check setting result>
$ git config --global --list
```


**Windows**
###### 2. Atom `git-plus` plug in설치
