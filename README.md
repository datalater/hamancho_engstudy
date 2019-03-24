<!-- TOC START min:1 max:4 link:true asterisk:true update:true -->
* [Hamancho Study 가이드](#hamancho-study-가이드)
  * [Git 사용법](#git-사용법)
    * [00 Git config](#00-git-config)
    * [01 Git add](#01-git-add)
    * [02 Git commit](#02-git-commit)
      * [Rules](#rules)
    * [03 Git push](#03-git-push)
    * [04 New Pull Request](#04-new-pull-request)
      * [Rules](#rules-1)
    * [05 Git pull](#05-git-pull)
<!-- TOC END -->

---

# Hamancho Study 가이드

## Git 사용법

### 00 Git config

로컬 저장소가 참조할 upstream 저장소와 origin 저장소를 설정한다.

> 일반적으로 upstream 저장소는 원본 저장소를 뜻하며, 본 프로젝트에서 upstream 저장소는 <kbd>`github.com/datalater/hamancho_eng_study`</kbd>이다. origin 저장소는 원본 저장소를 fork, 즉 복제한 저장소이며 <kbd>`github.com/likelion-louie/hamancho_engstudy`</kbd>이다.

```bash
$ git remote add upstream git@github.com:datalater/hamancho_engstudy.git
$ git remote add origin <YOUR_FORKED_REMOTE_REPOSITORY>
```

> remote 명령어를 쓰는 이유는 upstream 저장소와 origin 저장소가 Github에서 관리하는 원격 저장소(remote repository)이기 때문이다.

다음 명령어를 실행하면 `git l`이라는 명령어를 사용할 수 있다. git에서 오류가 나면 현재 상황을 파악해야 하는데 `git l`을 사용하여 커밋 히스토리를 한눈에 조망할 수 있다.

```bash
$ git config --global alias.l log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%C(cyan)<%an>%Creset' --abbrev-commit
```

설정은 한 번만 해두면 영구적으로 적용된다.

### 01 Git add

<kbd>`script`</kbd> 폴더에서 <kbd>`20190125-any-recommendations-jmc.md`</kbd> 파일을 작성했다고 해보자. 이제 작성한 파일을 `git add` 해야 한다. git 명령어는 항상 프로젝트 루트 폴더에서 입력하는 것을 전제로 한다.

```bash
$ pwd
# make sure your pwd is hamanacho_engstudy
$ git add script/20190125-any-recommendations-jmc.md
```

`git add` 뒤에 경로를 어느 정도 구분 가능하게 적은 후, 예를 들어 `git add script/20190125`까지, <kbd>`tab`</kbd>을 눌러서 자동완성을 이용하자. 자동완성이 되지 않는다면 컴퓨터가 해당 파일을 찾을 수 없는 것이고 대개 오타가 발생한 것이다. 인간의 타이핑을 온전히 믿지 말고 컴퓨터가 자동완성할 수 있도록 <kbd>`tab`</kbd>을 적극적으로 활용하는 것이 현명하다.


### 02 Git commit

위에서 add 했던 파일을 commit 한다. commit은 git의 데이터베이스에 스냅샷을 저장하는 행위를 말한다. 쉽게 말해 현재 프로젝트 버전을 기록하는 것이다.

```bash
# -v means to view your diff
$ git commit -v
```

`git commit` 명령어를 입력하면 vim 모드에 진입한다. vim 초보자라면 vim모드에서 키보드를 함부로 입력하면 안된다. 안전하게 아래 명령어를 순서대로 타이핑하자.

1. <kbd>`shift + o`</kbd>
2. `<WRITE_YOUR_COMMIT_MESSAGE>`
3. <kbd>`Esc`</kbd>
4. <kbd>`:x` + `enter`</kbd>

#### Rules

커밋 메시지 작성법은 프로젝트마다 다르게 규정할 수 있지만, 일반적으로 합의된 기본 규칙이 있다. 농구장에 가면 농구 규칙을, 축구장에 가면 축구 규칙을 따라야 하듯, git을 사용한다면 git의 규칙을 따르자.

* 커밋 메시지의 첫글자는 반드시 대문자로 작성한다.
* (This commit will)이 생략되어 있는 것으로 간주하여 동사의 원형으로 적는다.
* 예를 들어 `Add 20190125-any-recommendations-jmc.md`라고 작성한다.

### 03 Git push

현재 작업하고 있는 컴퓨터인 로컬 저장소에 저장된 내용을 원격 저장소에 올린다.

```bash
$ git push -u origin master
```

지금은 <kbd>`origin`</kbd> 저장소에 올렸기 때문에 원본 저장소인 <kbd>`upstream`</kbd>에는 반영이 되지 않았다. 따라서 <kbd>`origin`</kbd>저장소의 내용을 <kbd>`upstream`</kbd>에 합쳐 달라고 요청하는 PR(pull request)를 보내야 한다.

### 04 New Pull Request

Github의 <kbd>`github.com/likelion-louie/hamanacho_engstudy`</kbd> 저장소로 이동하여 <kbd>`New pull request`</kbd>를 클릭하여 PR을 작성한다. PR을 작성할 때는 반드시 아래의 사항을 모두 지킨다.

#### Rules

커밋 메시지와 마찬가지로 PR 작성할 때도 기본 규칙이 있다. 아래 세 가지 중 어느 하나라도 소홀히 하면 따가운 눈총을 받을 수 있다.

  1. **제목 작성**: 커밋의 요약을 적는다.
  2. **내용 작성**: 커밋의 상세 내용 또는 주의사항을 적는다.
  3. **Reviewer 설정**: <kbd>`datalater`</kbd>를 선택한다.

제목에 적은 사항이 곧 내용이어서 내용에 무엇을 적어야 할지 애매할 때가 있다. 현업에서는 여러 가지 방법이 있지만, 본 프로젝트는 개발 프로젝트가 아니기 때문에 커밋이 한 개일 때 제목과 내용을 일치하게 적는 것을 허용한다.

### 05 Git pull

PR이 머지되었거나 새로운 커밋이 올라왔을 경우 로컬 저장소에 동기화를 해야 한다.

```bash
$ git pull --rebase upstream master
```

원격 저장소의 내용이 모두 동기화되었는지 확인하기 위해 다음 명령어를 입력한다.

```bash
$ git l
```
`git l` 명령어를 입력하면 `git commit`과 같이 vim 모드로 진입한다. vim 모드에서는 키보드 타이핑을 함부로 하면 안 된다. 커밋 명을 보며 나의 PR 커밋이 있는지, 새로 업데이트 된 내용이 무엇인지 확인을 끝마치면 <kbd>`:q` + `enter`</kbd>를 누른다.

---

**END**
