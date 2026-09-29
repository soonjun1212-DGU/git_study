# 1주차 - 조정민

## 🎯 미션

**1. 뭘 했나요?** (한 줄)
- progit 자료를 보며 궁금한 점을 LLM과 함께 공부했다

**2. 어떤 명령어를 쳤나요?** (터미널에 친 거 그대로 복붙!)
```bash
PS C:\dev\git_study> git pull origin main
From https://github.com/soonjun1212-DGU/git_study
 * branch            main       -> FETCH_HEAD
Already up to date.
PS C:\dev\git_study> git switch week01/jeongmin 
fatal: invalid reference: week01/jeongmin
PS C:\dev\git_study> git switch -c week01/jeongmin
Switched to a new branch 'week01/jeongmin'
PS C:\dev\git_study> cd weeks
PS C:\dev\git_study\weeks> cd week01
PS C:\dev\git_study\weeks\week01> touch jeongmin.md
```

**3. 해보니까 어땠나요?**
- touch는 리눅스 명령어라 윈도우같은 powershell 터미널에서는 동작하지 않는다 따라서 WSL2를 설치해야 겠다고 생각헀다. 노트북에는 설치돼 있지만 데스크탑은 설치를 안해놔서 그렇다.

## 💡 새로 안 것

**1. Modified / Staged / Committed는 "세 개의 공간"에 붙은 이름표였다**

Pro Git에 나오는 워킹 트리·Staging Area·Git 디렉토리가 별개 개념인 줄 알았는데, 3단계 상태와 같은 얘기였다. 파일이 어느 공간에 있느냐에 따라 상태 이름이 붙는 것뿐이다.

| 공간 | 그 파일의 상태 | 옮기는 명령어 |
|---|---|---|
| 워킹 트리 (지금 편집 중인 폴더) | Modified | |
| Staging Area (= Index) | Staged | `git add` |
| Git 디렉토리 (`.git` 폴더) | Committed | `git commit` |

**2. 이 세 단계는 전부 로컬(내 개인 컴퓨터)에서 일어난다**

`git push` 전까지는 GitHub에 아무것도 올라가지 않는다. 커밋을 100번 하든 메시지에 오타를 내든 내 컴퓨터 안의 일이라, 되돌리기도 자유롭다. 인터넷 없이도 커밋까지 가능한 이유.

**3. Staging Area는 "파일"이 아니라 "변경된 줄"을 담는 곳이다**

이번 주에 제일 헷갈렸던 부분. 생각의 흐름은 이랬다.

1. 커밋은 의미 단위로 잘게 쪼개는 게 좋다고 한다
2. 그런데 한 파일 안에서 버그 수정도 하고 신기능도 만들었으면? → 이게 오히려 더 흔한 상황 아닌가?
3. `git add`는 **파일 단위**로 고르는 건데, 그럼 그 파일을 add하는 순간 두 작업이 통째로 같이 올라가는 거 아닌가?
4. 그럼 쪼개는 게 애초에 불가능한 거 아닌가?

결론은 **3번의 전제가 틀렸다**는 것.
`git add 파일명`이라고 쓰다 보니 "파일을 담는 바구니"로 착각했는데,
Staging Area는 사실 **변경된 줄(diff) 단위**로 담기는 곳이다.
파일 단위 add는 그중 제일 자주 쓰는 한 가지 방법일 뿐이었다.

그래서 한 파일 안에서도 이렇게 쪼갤 수 있다.

```bash
git add -p main.js      # 바뀐 부분을 하나씩 보여주며 y/n로 고르게 함
```

VS Code에서는 더 쉽다. 소스 제어 탭에서 파일을 열고, 바뀐 줄 위에 마우스를 올리면
나오는 **Stage Change** 버튼을 누르면 그 부분만 스테이징된다.

> 정리하면: "커밋을 쪼개라"는 말이 성립하는 이유가 바로 이것 때문.
> 파일 단위로만 담긴다면 쪼개라는 조언 자체가 자주 불가능했을 것.

**4. Untracked = Git이 존재 자체를 모르는 새 파일**

한 번도 커밋된 적 없는 파일. `.gitignore`가 무시할 수 있는 건 이 상태의 파일뿐이다.

**5. 이미 커밋된 파일은 `.gitignore`에 적어도 계속 추적된다**

한 번 추적이 시작된 파일은 `.gitignore`보다 추적이 우선이다. 실수로 커밋한 `.env` 같은 파일을 뒤늦게 숨기려 할 때 반드시 마주치는 상황. 해결은 추적 목록에서만 빼주면 된다.

```bash
git rm --cached abc      # 내 컴퓨터의 파일은 그대로, 추적만 해제
git commit -m "chore: abc 추적 제외"
```

`--cached`가 핵심. 이걸 빼면 실제 파일까지 지워진다.

> 순준님이 이번 주에 물어본 "`.gitignore`는 add 안 해도 동작하나?"의 짝이 되는 이야기예요.(참고로 깃에 푸쉬안해도 동작하냐 라고 하신다면 동작은 하지만 개인 로컬에서만 동작해서 저도 쓰려면 깃에 푸쉬를 해주셔야 합니다)
> **아직 커밋 안 된 파일** → `.gitignore`가 바로 먹힘
> **이미 커밋된 파일** → `.gitignore`에 적어도 안 먹힘, `git rm --cached` 필요

## ❓ 질문

순준님은 git add를 할때 git add . 로 전부 담으시나요 아니면 파일을 골라서 담으시나요?
전 습관적으로 .으로 전부 다 담는데 스테이징 영역이 원래 골라 담으라고 만든걸 알고 좀 반성했습니다
