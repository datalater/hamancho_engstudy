
# Hamancho Study 가이드

## Git 사용법

### Git config

로컬 저장소가 참조할 upstream 저장소와 origin 저장소를 설정한다.

```bash
$ git remote add upstream git@github.com:datalater/hamancho_engstudy.git
$ git remote add origin git@github.com:likelion-louie/hamancho_engstudy.git
```

> remote 명령어를 쓰는 이유는 upstream 저장소와 origin 저장소는 Github에서 관리하는 원격 저장소(remote repository)이기 때문이다.

git에서 오류가 났거나 현재 진행상황을 파악하고 싶을 때 한 눈에 알아보기 위해 다음 명령어를 실행한다.

```bash
$ git config --global alias.l log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%C(cyan)<%an>%Creset' --abbrev-commit
```

### Git add

`script` 폴더에서 `20190125-any-recommendations-jmc.md` 파일을 작성했다. 이제 작성한 파일을 `git add` 한다. git 명령어를 입력할 때는 프로젝트 루트 폴더에서 하도록 통일한다.

```bash
$ pwd
# make sure your pwd is hamanacho_engstudy
$ git add script/20190125-any-recommendations-jmc.md
```

`git add` 뒤에 경로를 어느 정도 구분 가능하게 적은 후 `<tab>`을 눌러서 자동완성을 이용하자. 자동완성이 되지 않는다면 컴퓨터가 해당 파일을 찾을 수 없는 것이고 대개 오타가 발생한 것이다. 그러니 인간의 타이핑을 온전히 믿지 말고 컴퓨터가 자동완성할 수 있도록 `<tab>`을 적극적으로 활용하는 것이 현명하다.


### Git commit

위에서 add 했던 파일을 commit 한다.

```bash
# -v means to view your diff
$ git commit -v
```

`git commit` 명령어를 입력하면 vim 모드에 진입한다. vim모드에서는 키보드를 함부로 입력하면 안된다. 아래 정해진 명령어만 타이핑하도록 한다.

1. `shift + o`: 한 줄 띄우고 Insert 모드 진입
2. `Add <추가한 파일명>`: 커밋메시지 작성
3. `<Esc>`: 이스케이프 버튼 누르기
4. `:x<enter>`: 콜론(:)을 누르고 x를 타이핑한후 엔터를 누른다.

예를 들어 커밋 메시지 작성할 때는 `Add 20190125-any-recommendations-jmc.md`라고 쓴다. 커밋 메시지의 첫글자는 반드시 대문자로 작성하며, 앞에 (This commit will)이 생략되어 있는 것으로 간주하여 동사의 원형으로 적는다.

### Git push

로컬 저장소(현재 작업 중인 컴퓨터)에 저장된 내용을 원격 저장소(Github repository)에 올린다.

```bash
$ git push -u origin master
```

### New Pull Request

Github의 hamanacho_engstudy 저장소로 이동하여 PR을 작성한다. PR을 작성할 때는 반드시 아래의 사항을 모두 지킨다.

  1. **제목 작성**: 커밋의 요약을 적는다.
  2. **내용 작성**: 커밋의 상세 내용 또는 주의사항을 적는다.
  3. **Reviewer 설정**: datalater를 선택한다.

대개 PR을 보낼 때는 여러 개의 커밋이 올라가기 때문에 제목과 내용이 구분된다. 하지만 본 프로젝트에서는 커밋이 한 개일 때 제목과 내용을 일치하게 적는 것을 허용한다.

### Git pull

PR이 머지되었거나 새로운 커밋이 올라왔을 경우 로컬 저장소에 동기화를 해야 한다.

```bash
$ git pull --rebase upstream master
```

원격 저장소의 내용이 모두 동기화되었는지 확인하기 위해 다음 명령어를 입력한다.

```bash
$ git l
```

커밋 명을 보며 모두 확인이 되었다면 `:q<enter>`를 누른다.

---

**END**
