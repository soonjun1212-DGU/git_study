# 🚀 매주 PR 가이드

`XX`만 매주 주차 숫자로 바꿔서 순서대로 따라 하면 돼요. (예: `week02`)

## 📋 순서

**① main 최신으로 받기**
```powershell
cd ~/dev/git_study
git switch main
git pull
```

**② 매 주 브랜치 만들기**
```powershell
git switch -c weekXX/soonjun
```
✅ VS Code 왼쪽 아래가 `weekXX/soonjun`으로 바뀌면 OK

**③ 정리 파일 작성**

`weeks/_note.md`(정리 틀)를 복사해서 `weeks/weekXX/soonjun.md`로 이름을 바꾸고 작성해요 → [마크다운 가이드](./docs/markdown-guide.md) 참고

> [!NOTE]
> 정리 틀은 **직접 복사**해야 해요. VS Code에서 파일을 만들어도 자동으로 채워지지 않아요.

**④ 커밋하고 올리기**
```Terminal
git add .
git commit -m "docs: X주차 정리 추가"
git push -u origin weekXX/soonjun
```

**⑤ PR 열기**

GitHub → 노란 **Compare & pull request** → PR 설명 작성 → **Reviewers**에 상대방 지정 → **Create pull request**

> [!NOTE]
> **GitHub 웹사이트의 PR 작성 화면**에서는 설명 칸에 PR 양식이 자동으로 채워져 있어요. 빈칸만 채우면 돼요.

> [!TIP]
> 내용을 보충하고 싶으면 같은 브랜치에서 수정 → `add` → `commit` → `push`만 하면 기존 PR에 자동으로 붙어요. 새 PR은 안 만들어도 돼요!

**⑥ 머지 후 정리** (화요일 미팅에서 머지 → Delete branch 후)
```powershell
git switch main
git pull
git branch -d weekXX/soonjun
```

---

## 💾 커밋 메시지

`docs: 무엇을 했는지` 형식으로 짧고 구체적으로!

- `docs: 2주차 정리 추가`
- `docs: 내용 보충`
- `docs: 용어집에 HEAD 추가`

---

## 💬 리뷰하기

**Files changed** 탭 → 줄 옆 파란 `+` 로 코멘트 → **Review changes** → **Approve** 또는 **Comment**

> [!IMPORTANT]
> **좋았던 점 1개 + 질문 1개** 는 꼭 남겨요!

---

## 🆘 막혔을 때

| 상황 | 해결 |
|---|---|
| 어느 브랜치인지 모르겠어요 | `git status` 첫 줄 확인 |
| main에서 작업했어요 (커밋 전) | `git switch -c weekXX/soonjun` 하면 수정 내용 그대로 옮겨져요 |
| 커밋 메시지 오타 (push 전) | `git commit --amend -m "고친 메시지"` |
| push가 rejected 돼요 | `git pull` 후 다시 `git push` |
| 충돌이 났어요 | VS Code에서 **Accept Both Changes** → `git add .` → `git commit` → `git push` |
| 전혀 모르겠어요 | `git status` 캡처해서 Discord에 올리고 기다리기 😅 |

---

## 📌 자주 쓰는 명령어

| 명령어 | 하는 일 |
|---|---|
| `git status` | 지금 상태 확인 (제일 많이 씀!) |
| `git switch 브랜치명` | 브랜치 이동 |
| `git pull` | 최신 내용 받기 |
| `git add .` | 전부 스테이징 |
| `git commit -m "메시지"` | 커밋 |
| `git push` | GitHub에 올리기 |
| `git log --oneline --graph --all` | 기록 그림으로 보기 |
