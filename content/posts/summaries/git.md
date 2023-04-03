---
title: "Git"
showDate: false
categories:
  - \summaries
tags:
  - git
---

## 1) 기본 설정

| Command                                                    | Details          |
| ---------------------------------------------------------- | ---------------- |
| git init                                                   | 깃 추적 시작     |
| git config \-\-global \-\-list                             | 기본 설정 보기   |
| git config \-\-global core.autocrlf true                   | 개행문자 설정    |
| git config \-\-global user.name YuchanJeong                | 사용자 이름 설정 |
| git config \-\-global user.email yuchanjeong0923@gmail.com | 사용자 메일 설정 |
| git config \-\-global core.editor vim                      | 기본 에디터 설정 |
| git config \-\-global init.defaultBranch main              | 기본 브랜치 설정 |
| git config \-\-global commit.template ~/.gitmessage.txt    | 커밋 템플릿 설정 |

<details>
<summary>.vimrc</summary>
<div markdown="1">

```text
set nocompatible     " 오리지날 VI와 호환하지 않음
set autoindent       " 자동 들여쓰기
set cindent          " C 프로그래밍용 자동 들여쓰기
set smartindent      " 스마트한 들여쓰기
set wrap
set nowrapscan       " 검색할 때 문서의 끝에서 처음으로 안돌아감
set nobackup         " 백업 파일을 안만듬
set noswapfile
"set visualbell      " 키를 잘못눌렀을 때 화면 프레시
set ruler            " 화면 우측 하단에 현재 커서의 위치(줄,칸) 표시
set shiftwidth=4     " 자동 들여쓰기 4칸
set number           " 행번호 표시, set nu 도 가능
set fencs=ucs-bom,utf-8,euc-kr.latin1 " 한글 파일은 euc-kr로, 유니코드는 유니코드로
set fileencoding=utf-8 " 파일저장인코딩
set tenc=utf-8       " 터미널 인코딩
"set expandtab       " 탭대신 스페이스
set hlsearch         " 검색어 강조, set hls 도 가능
set ignorecase       " 검색시 대소문자 무시, set ic 도 가능
set tabstop=4        " 탭을 4칸으로
set lbr
set incsearch        " 키워드 입력시 점진적 검색
set cursorline       " 편집 위치에 커서 라인 설정
set laststatus=2     " 상태바 표시를 항상한다
syntax on "  구문강조 사용
filetype indent on   " 파일 종류에 따른 구문강조
set background=dark  " 하이라이팅 lihgt / dark
set backspace=eol,start,indent "  줄의 끝, 시작, 들여쓰기에서 백스페이스시 이전줄로
set history=1000     " vi 편집기록 기억갯수 .viminfo에 기록
highlight Comment term=bold cterm=bold ctermfg=4 " 코멘트 하이라이트
set mouse=a          " vim에서 마우스 사용
set t_Co=256         " 색 조정
```

</div>
</details>

## 2) 원격 저장소

| Command                               | Details                        |
| ------------------------------------- | ------------------------------ |
| git remote -v                         | 원격 저장소 연결 확인          |
| git remote add [name] [url]           | 원격 저장소 연결               |
| git remote remove [name]              | 원격 저장소 연결 해제          |
| git push [name] [branch] (-f)         | 원격 저장소에 Push (강제)      |
| git pull [name] [branch] (\-\-rebase) | 원격 저장소 Pull (이어 붙히기) |
| git clone [url] ([directory])         | 원격 저장소 복사 (폴더명)      |

## 3) 파일 상태

| Command                    | Details                                         |
| -------------------------- | ----------------------------------------------- |
| git status                 | 파일 상태 확인                                  |
| git diff                   | 파일 상태 비교<br/>\*_작업역역과 스테이지 차이_ |
| git diff \-\-cached        | 파일 상태 비교<br/>\*_스테이지와 저장소 차이_   |
| git diff [commit] [commit] | 커밋 간 상태 비교                               |
| git diff [branch] [branch] | 브랜치 간 상태 비교                             |

## 4) 스테이징 (추가)

| Command             | Details                                                              |
| ------------------- | -------------------------------------------------------------------- |
| git add -p          | 변경 내용을 확인 후 청크 별로 추가<br/>\*_y(추가), n(제외), q(종료)_ |
| git add [directory] | 해당 폴더 및 하위 폴더의 변경 내용을 추가                            |
| git add .           | 현재 폴더 및 하위 폴더의 변경 내용을 추가                            |

## 5) 커밋 (확정)

| Command                | Details                                                                          |
| ---------------------- | -------------------------------------------------------------------------------- |
| git commit             | 커밋 생성                                                                        |
| git commit -m "[msg]"  | 커밋 메시지와 함께 커밋 생성                                                     |
| git commit -am "[msg]" | 스테이징 후 커밋 메시지와 함께 커밋 생성 <br/>\*_한 번 이상 커밋 한 파일만 가능_ |
| git commit \-\-amend   | 마지막 커밋 메시지 수정                                                          |

## 6) 커밋 기록

| Command                    | Details                      |
| -------------------------- | ---------------------------- |
| git log                    | 커밋 기록 보기               |
| git log -p                 | 커밋 기록과 패치내용 보기    |
| git log \-\-stat           | 커밋 기록과 패치통계 보기    |
| git log \-\-graph          | 커밋 기록과 그래프 보기      |
| git log [branch]..[branch] | 후자에만 있는 커밋 기록 보기 |

## 7) 되돌리기

| Command                                 | Details                                                                                                                                                                                                                                                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| git reset \-\-hard [commit] \| HEAD[~n] | 해당 커밋으로 되돌린 후<br/>이후의 커밋, 스테이징, 작업 초기화                                                                                                                                                                                                             |
| git reset [commit] \| HEAD[~n]          | 해당 커밋으로 되돌린 후<br/>이후의 커밋, 스테이징 초기화                                                                                                                                                                                                                   |
| git reset \-\-soft [commit] \| HEAD[~n] | 해당 커밋으로 되돌린 후<br/>이후의 커밋 초기화                                                                                                                                                                                                                             |
| git revert [commit]                     | 해당 커밋의 수정사항 취소 후 새 커밋 생성                                                                                                                                                                                                                                  |
| git revert [commit]..[commit]           | 해당 범위의 수정사항 취소 후 새 커밋 생성                                                                                                                                                                                                                                  |
| git rebase -i [commit] \| HEAD[~n]      | p: 커밋 그냥 사용, 재정렬 및 삭제 가능<br/>r: 커밋 메시지 수정<br/>e: 커밋 메시지 및 내용 수정<br/>\*_HEAD가 해당 커밋으로 이동, 추가 작업 가능_<br/>\*_git rebase \-\-continue (작업 종료)_<br/>\*_git rebase \-\-abort (작업 중단)_<br/>s: squash merge<br/>d: 커밋 삭제 |

## 8) 임시 저장

| Command                       | Details                                                                                       |
| ----------------------------- | --------------------------------------------------------------------------------------------- |
| git stash (-u)                | 임시 저장 후 직전 커밋 상태로 되돌아감 (새 파일도)<br/>\*_한 번 이상 스테이징 한 파일만 가능_ |
| git stash list                | 임시 저장 목록 보기                                                                           |
| git stash apply (stash@{[n]}) | 최근(해당) 임시 저장 상태로 돌아가기                                                          |
| git stash drop (stash@{[n]})  | 최근(해당) 임시 저장 상태 지우기                                                              |
| git stash pop                 | 최근 임시 저장 상태 apply 후 drop                                                             |

## 9) 브랜치

| Command                         | Details                                      |
| ------------------------------- | -------------------------------------------- |
| git branch (-a)                 | 브랜치 목록 보기 (원격 목록도)               |
| git branch [branch]             | 브랜치 생성                                  |
| git branch -d [branch]          | 해당 브랜치 삭제                             |
| git branch -m [branch] [branch] | 브랜치명 바꾸기                              |
| git checkout [branch]           | 브랜치 전환                                  |
| git checkout -b [branch]        | 브랜치 생성 후 전환                          |
| git merge [branch] (\-\-squash) | 현재 브랜치에 해당 브랜치 병합 (스쿼시 병합) |
| git rebase [branch]             | 현재 브랜치에 해당 브랜치 이어 붙이기        |

## 10) 삭제

| Command                            | Details                     |
| ---------------------------------- | --------------------------- |
| git rm (\-\-cached) [file]         | 해당 파일 삭제 (원격에서만) |
| git rm -r (\-\-cached) [directory] | 해당 폴더 삭제 (원격에서만) |
| git fetch \-\-all \-\-prune        | 원격 브랜치 흔적 삭제       |

## Etc

### 1) .gitignore

| List                | Details                    |
| ------------------- | -------------------------- |
| example.xxx         | 해당 파일명 전부 제외      |
| /example.xxx        | 현재 폴더의 해당 파일 제외 |
| example/            | 해당 폴더와 하위 경로 제외 |
| example/example.xxx | 해당 폴더의 해당 파일 제외 |
| \*.xxx              | 특정 확장자 파일 전부 제외 |
| !example.xxx        | 예외 파일명 (버전 관리 ON) |

### 2) SSH 등록

1. ssh-keygen으로 ~/.ssh/에 id_rsa.pub(공개키)와 id_rsa(개인키) 생성
2. 공개키를 Github의 Settings/SSH and GPG keys에 등록

### 3) Github 계정 오류

- 키체인 접근 -> github.com
