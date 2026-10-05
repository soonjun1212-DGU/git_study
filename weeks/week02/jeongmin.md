# 2주차 - 조정민

## 🎯 미션

**1. 뭘 했나요?** (한 줄)
- restore 로 파일 수정을 되돌리기
- restore --staged 로 잘못 add 한거 빼기 
- git commit --amend로 최근 커밋 메시지 고치기
- git log를 그래프로 우리 레포기록 구경하기

**2. 어떤 명령어를 쳤나요?** (터미널에 친 거 그대로 복붙!)
```bash
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ git status
On branch week02/jeongmin
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   ../../README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ./

no changes added to commit (use "git add" and/or "git commit -a")
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ git restore README.md
error: pathspec 'README.md' did not match any file(s) known to git
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ cd ..
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks$ cd ..
youngb0@DESKTOP-1MGL7IV:~/projects/git_study$ git restore README.md
youngb0@DESKTOP-1MGL7IV:~/projects/git_study$ git status
On branch week02/jeongmin
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        weeks/week02/

nothing added to commit but untracked files present (use "git add" to track)
```

```bash
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ git add jeongmin.md
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ git status
On branch week02/jeongmin
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   jeongmin.md

youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ git restore --staged jeongmin.md
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ git status
On branch week02/jeongmin
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ./

nothing added to commit but untracked files present (use "git add" to track)
youngb0@DESKTOP-1MGL7IV:~/projects/git_study/weeks/week02$ 
```

```bash
youngb0@DESKTOP-1MGL7IV:~/projects/git_study$ git log --oneline --graph --all
* 2601405 (origin/week01/jeongmin) docs: 1주차 정리 추가
* 9c72982 (HEAD -> week02/jeongmin, origin/main, origin/HEAD, main) docs: 1주
차 정리 및 용어집 추가 (#3)
| * e4998e2 (origin/week01/soonjun) docs: 1주차 용어집 추가
| * f66a34a docs: 1주차 정리 추가
|/  
* 3adb013 docs: PR 가이드, 마크다운 가이드 추가 및 README·템플릿·용어집 개편 (#2)
*   47a5d74 Merge pull request #1 from soonjun1212-DGU/week00/soonjun
|\  
| * ad59b7c (origin/week00/soonjun) docs:자기소개 추가
|/  
* 62ec4f7 Create pull_request_template.md
* 82ad46d Create .gitkeep
* 43626bd Update README.md
* 3a7086d Update README.md
* 4f911f2 Update README.md
```

**3. 해보니까 어땠나요?**
- 로컬 내에서 수정한 내역을 되돌릴수 있고, 스테이징 영역에서 add한 파일을 뺄수 있으며, 최근 커밋을 고칠수 있다는걸 알았다. 생각보다 깃이 체계적인 명령어 들로 구성돼 있다는걸 알았다. 또한 git log를 사용하면 우리 레포의 기록을 볼수있어서 신기했다 심지어 옵션도 다양했다. 그중 기억에 남는건 git log --oneline 이다. 자주 쓴다니 좀 염두를 해두는게 좋을것 같았다.

## 💡 새로 안 것

**몰랐는데 이번에 알게 된 것** 
- `git log` 명령어로 커밋 히스토리를 조회할수 있다. 나가려면 `q`.
- `git log --oneline`: 한줄에 커밋 하나 (현업에서 자주씀)
- `git log --graph --oneline --all`: 브랜치가 갈라지고 합쳐지는 모양을 그림으로
- `git log -p`: 각 커밋에서 뭐가 바뀌어는지 diff 까지
- `git log --stat`: 어떤 파일이 몇줄 바뀌었는지만 요약
- 마지막 커밋을 고칠수 있다. `git commit --amend` 주로 커밋 메시지 오타, 파일 하나 빠뜨렸을때 쓴다.
- 스테이징 취소를 할수있다. `git add`를 잘못했을때 파일 내용은 그대로 두고 스테이징만 뺄수있다. `git restore --staged 파일명` 
- 로컬의 수정 내역을 버릴수 있다. 마지막 스테이징 영역 상태로 파일을 되돌리는 방법은, `git restore 파일명`. 단 복구가 불가능 하기에 진짜버려도 될때만 쓰기.

## ❓ 질문

**궁금하거나 헷갈린 것** (하나면 충분, 화요일에 같이 이야기해요)
- PR을 리뷰하고 머지할때 Merge commit방식이 있고 Squash and merge 방식이 있습니다. 어떤 차이인지 한번 같이 생각해 보면 좋을것 같습니다. 
