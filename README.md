# Git 자주 사용하는 명령어 정리
자주 사용하는 기본적인 명령어들을 정리했습니다.

-- 최근 수정이 : 2017-07-25

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

# LICENSE
이 저장소는 WTFPL 라이센스에 의해 보호를 받습니다.

# 상대
수정하고있습니다.
그렇다고합니다.
github에서 
