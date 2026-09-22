git-study/
├── README.md
├── glossary.md                      # 공용 용어집
├── .github/
│   └── pull_request_template.md     # PR 템플릿
└── weeks/
    ├── week01/
    │   ├── jungmin.md
    │   └── teammate.md
    └── week02/
        └── ...

# 최신 main 받아오기
git switch main
git pull

# 이번 주 브랜치 만들기
git switch -c week01/이름

# 정리하고 저장하기
git add .
git commit -m "docs: 1주차 정리 추가"

# 올리기
git push -u origin week01/이름

# 지금 상태 그림으로 보기
git log --oneline --graph --all
