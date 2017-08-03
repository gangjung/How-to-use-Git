# Git 자주 사용하는 명령어 정리
자주 사용하는 기본적인 명령어들을 정리했습니다.

-- 최근 수정이 : 2017-07-26

## 저장소 생성(초기화) 하기
```bash
git init    # 저장소 생성
```

## 커밋하기
```bash
git add README.md    # 커밋할 파일 추가
git status    # 현재 stage 상태를 확인
git commit -m "init:README.md"    # 인라인 커밋 메시지 작성
git log --deccorate=full --online --graph    # 커밋 로그 확인
```

## 브랜치 생성하기
```bash
git checkout -b readme    # readme 라는 이름의 브랜치를 생성한 후, 생성된 브랜치로 체크아웃
```

## 머지하기
```bash
git merge readme --no-ff # readme 브랜치의 내용을 자겨와서 머지함, fast-forword기능 끔
```

## Fast Forward란?
```bash
Merge할 브랜치가 가리키고 있던 커밋이 현 브랜치가 가리키는 것 보다 '앞으로 진행한'커밋이기 때문에 master 브랜치 포인터는 최신 커밋으로 이동한다. 이런 Merge 방식을 'Fast forward'라고 부른다. 다시 말해서 A 브랜치에서 다른 B 브랜치를 Merge할 때 B가 A 이후의 커밋을 가리키고 있으면 그저 A가 B의 커밋을 가리키게 할 뿐이다.
```

## branch 제거하기
```bash
문제를 급히 해결하고 master 브랜치에 적용하고 나면 다시 일하던 브랜치로 돌아가야 한다. 하지만, 그전에 필요없는 브랜치를 삭제한다. git branch 명령에 -d 옵션을 주고 브랜치를 삭제한다.

$ git branch -d [필요없는 브랜치 이름]
Deleted branch [필요없는 브랜치 이름] (was 3a0874c).
```

## 3-way merge
```bash
A - 공통 - B 를 비교하여 A와 B 중 공통 부분과 다른 부분이 한 곳에만 있을 시, 그 부분이 수정되었다고 판단해 그 다른 부분을 가져온다. 하지만 만약, A,공통,B 전부 다른 내용이면 A와 B에서 둘 다 수정이 되었다고 판단해 Conflict를 건다. 그리고 전부 확인하면 부분별로 판단한 정보들을 모아 새로운 정보를 만든다.

-2-way merge-
***
2-way merge는 그냥 새로운 정보가 아니라 서로 다른 정보를 가진 부분이 있으면 무조건 Conflict를 건다.
***

[ A ][ 공통 ][ B ][ 2-way ][ 3-way ]
[ 1 ][   1  ][ 0 ][   ?   ][   0   ]
[ 2 ][   2  ][ 2 ][   2   ][   2   ]
[ 5 ][   3  ][ 6 ][   ?   ][   ?   ]
[ 0 ][   4  ][ 4 ][   ?   ][   0   ]

서로 다른 2개의 branch를 merge할 때, 둘 중의 하나가 남은 하나의 조상 branch가 아니라면, 두 branch commit의 공통 조상commit을 찾아 3-way merge를 진행하고 그 결과로 새로운 commit을 만들어 merge를 실행한 branch의 포인터가 그 커밋을 가르키도록 한다.

이러한 것을 <Merge Commit>이라고 한다.

Merge Commit을 이용하면 commit history를 깔끔하게 관리할 수 있다.
```

## Rebase -> Merge를 이용하자(모든 Branch가 다른 작업을 할 때)
```bash
상황에 따라 다르겠지만, 
Merge를 실행할 때, rebase를 실행하지 않고 단순히 merge만드로 branch를 병합하게되면 History가 복잡해지고, log도 보기 힘들어진다.

하지만, rebase 후, merge를 하게되면, 여러 깊이가 아닌 하나의 깊이로 깔끔하게 정리된 History와 log를 볼 수 있다.

History를 깔끔하게 정리하는 것은 협업에서 정말 중요하다!
```

## 충돌이 일어났을 시
```bash
충돌이 일어나는 상황은 Merge할 시, 각각의 브렌치가 공동으로 가지고 있는 정보가 서로 수정되어 내용이 다르게 됬을 때 발생한다.
충돌이 발행해서 Merge가 중단되면, git status로 충돌이 일어난 파일을 확인하여, 해당 내용을 수정한 뒤, git add로 Staging area에 저장한다음 다시 commit하면 Merge가 수행된다.
```

## Clone vs Remote
```bash
Clone은 클라이언트 상에 아무것도 없을 때, 서버의 프로젝트를 내려받는 명령어로서, 저장소의 내용을 다운로드 받고 자동으로 init처리된다.

Remote는 원격 저장소를 관리할 수 있는 명령어로서, 원격저장소를 등록하여 접속할 수 있도록 해준다.
```

## Fork를 통한 협업
```bash
Fork를 하여 원본repository에서 개인repository로 복사한다.
git clone 원본repository주소
를 통해 remote repository를 복사 등록하고 (대부분 이름을 upstream이라고 한다.)
git remote add 개인repository주소
를 통해 개인repository를 등록한다.

1. 원본 clone하기
2. 개인 저장소 remote하기
```

## Branch를 만들기!
```bash
branch를 만들기 전에는 upstream을 이용하여 항상 최신 상태로 유지하는게 좋다.

git checkout master
git pull upstream

pull은 내부적으로 fetch를 실행하여 최신 버전을 가져온 다음, 현재 위치한 branch에 merge하는 과정을 수행한다.

branch를 만들 때에는, 일반적인 branch 이름을 사용한다.(다음 항목 참조)

git checkout -b 이름 upstream/master # git checkout -b branchB branchA, branchA에서 branchB라는 새로운 branch를 만들면서 checkout한다.
```

## upstream/master?
```bash
clone을 하고나서 git branch -a 를 실행시켜보면 다음과 같이 나온다.

* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master

여기서 master는 로컬 저장소의 branch이고 remotes/origin/master는 origin 원격의 master branch 이름이다. 
이런 것을 사용하는 상황은

git diff origin/master..master
git diff remotes/origin/master..master

등에서 사용을 한다.

이 두가지 명령은 같은 것을 나타내며, 'remote master와 로컬 master의 다른점이 무엇인지 보여달라'는 것이다.

remotes/origin/HEAD 는 origin의 default branch이며, origin/master 대신에 origin이라고 부를 수 있게 한다.
```

## Branch name
```bash
일반적으로 "이슈ID" of "이슈ID" + "이유(내용)" 을 사용하여 생성한다.
```

## 참고 사이트
```bash
http://www.popit.kr/%EC%98%A4%ED%94%88%EC%86%8C%EC%8A%A4-git-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-pull-request-%EB%B3%B4%EB%82%B4%EA%B8%B0/
```

##
```bash
```