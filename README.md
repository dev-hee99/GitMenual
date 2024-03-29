Github


## **기본용어 정리**

```

0. 용어1

- 추적(스테이지; stage): 작업공간에서 변경이 발생한 파일을 다음 커밋에 포함되도록 예약하는 것을 추적이라고 합니다. 어떤 파일을 추적하면 그 파일을 스테이지되었다고 합니다. 추적되는 파일은 스테이지 영역(stage area)에 들어가 있게 됩니다.

- 추적해제(언스테이지; unstage): 추적하고 있는 파일을 스테이지 영역에서 제외하는 것을 언스테이지라고 합니다.

- 커밋해시(commit hash): git log 명령어로 조회할 수 있는 커밋 해시는 각 커밋을 구분하는 Extended SHA-1 형식의 식별자입니다.


0. 용어2

- 브랜치(branch): 커밋에서 분기하면 브랜치가 됩니다. 말 그대로 한 갈래; 가지를 의미합니다.

- master: 기본 설정된 브랜치에 붙는 이름입니다.

- origin: 기본 설정된 원격 주소에 붙는 별명입니다.

- 태그(Tag): 알아보기 쉽게 하기 위해서 커밋(commit)에 달아 주는 별명입니다.

- HEAD: 현시점에서 작업중인 브랜치를 가리키는 포인터입니다. 작업공간이 현재 위치해 있는 브랜치를 가리킵니다.


1. 로컬 명령어

- git status : 마지막 커밋 이후 작업공간에서 변경이 일어난 모든 파일들을 나열하는 명령어입니다. 현재 추적되고 있는 파일을 초록색으로 표시하고 그렇지 않은 파일은 빨간색으로 나타냅니다.

- git add : 해당 파일을 추적(stage)시키는 명령어입니다. 추적되고 있는 파일만 커밋에 포함됩니다. 주로 git add . 의 형태로 사용합니다. git add . 명령어는 변경이 일어난 모든 파일을 추적하게 합니다.

- git rm : 해당 파일을 추적해제(unstage)시키는 명령어입니다. git add 명령어의 반대입니다.

- git commit : 커밋을 추가하는 명령어입니다. 커밋 명령어를 사용해서 커밋을 추가하는 것을 가리켜 '커밋한다'라고 부릅니다. 주로 git commit -m "(코멘트; 커밋에 덧붙일 말)" 형식으로 사용합니다. (참고: 명령어 입력중 덧붙일 말 사이에 줄바꿈을 추가하고 싶을 수 있습니다. 터미널에서는 Shift + Enter 를 입력하면 개행합니다.)

- git log : 커밋 이력을 열람할 수 있도록 하는 명령어입니다.

- git checkout : 커밋을 불러오는 명령어입니다. git checkout (커밋 해시) 형식으로 사용합니다. 커밋 해시는 전부 적을 필요는 없고 다른 커밋 해시와 중복되지 않아 고유하다면 앞의 몇 자리만 기입해도 인식됩니다. (팁: 가장 최근의 커밋을 기준으로 하여 작업공간에서 발생한 변경사항을 모두 버리고 원래 상태로 돌아가는 명령어는 git checkout -- . 입니다.)

- git diff : 커밋과 커밋 사이의 변경사항을 확인할 수 있게 하는 명령어입니다.


2. 원격 명령어

- git remote : 원격과 로컬 저장소를 연결시키는 명령어입니다.

- git clone : 로컬에서의 git init에 해당하는 명령어입니다. 원격에서 저장소를 최초로 가져올 때는 git pull 대신 git clone을 쓰는 것입니다.

- git fetch : 원격에서 업데이트된 저장소를 받아와서 로컬 저장소를 갱신하는 명령어입니다.

- git pull : git fetch 한 다음 작업공간까지도 갱신하는 명령어입니다.

- git push : 원격에 내 로컬 저장소를 올리는 명령어입니다. 원격과 로컬 저장소 변경 사이에 충돌이 있는 경우에 덮어씌운다, 합친다, 브랜치 등 선택할 수 있는 몇 가지 옵션은 있지만 그런 일은 거의 일어나지 않습니다.

3. 파일

- .git : 깃 저장소(레포지토리; repository) 폴더입니다.

- .gitignore : 작업공간 안에서 깃이 무시하게 하고 싶은 파일을 정의하는 파일입니다. 이 때 .gitignore 파일 자신도 커밋되어 있어야 효력이 적용됩니다. .gitignore 파일 안에 추적을 원하지 않는 파일들의 이름 패턴을 적어 넣고 커밋하면 그 파일들은 git status 목록에서 빨간색으로 나타지도 않고 git add . 명령어에서 제외됩니다.

```

## 로컬저장소와 원격 저장소 연결 방법

``` 
git init
(이 명령은 .git이라는 하위 디렉토리를 만든다. .git 디렉토리에는 저장소에 필요한 뼈대 파일(Skeleton)이 들어 있다)

git remote add origin https://github.com/계정명/레포지토리주소.git
(origin은 별칭)

git remote -v - 원격저장소 등록후 확인

삭제법
git remote remove origin

```
### push하는 방법 

```
#작업 영영 상의 변경 사항들을 staging area에 추가
git add . ( .은 폴더아래 모든 폴더,파일)

#add된 내용 확인
git status

# add 취소 
git reset HEAD . (파일명 . 전체 )

# add에서 추가한 변경 내용을 기록
git commit -m "메세지" (메세지에는 커밋시 남길 메세지)

# 원격 저장소에 푸쉬
git push origin 브랜치명

```

### branch 생성
```
git branch - 현재 선택된 브랜치를 알 수 있음 

git branch 생성할 브랜치명

git checkout 브랜치명 - 브랜치 변경 기본 master에서 새로 생성한 브랜치로 변경하기위해 주로 사용 
```

### pull하는 방법
```
git pull origin 브랜치명 - 원격저장소에 있는 데이터를 로컬로 가져와 병합시킴
```

### git 설정 확인
```
# 설정 확인
git config --list 

# 설정 등록
git config --global user.name "김OO'
git config --global user.email "test@google.com"

# 설정 삭제
git config --unset --global user.name
git config --unset --global user.email

```


#### reference
>https://github.com/progit/progit/blob/master/ko/02-git-basics/01-chapter2.markdown
>https://backlog.com/git-tutorial/kr/stepup/stepup3_1.html
