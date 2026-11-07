# 송경찬 개인 포트폴리오

Hugo와 Noesis 테마로 만든 개인 소개 웹사이트입니다.
`main` 브랜치에 push하면 GitHub Actions가 사이트를 빌드해 GitHub Pages에 자동으로 배포합니다.

| 항목 | 주소 |
|---|---|
| 공개 사이트 | https://song-kyeong-chan.github.io/myhomepage/ |
| 저장소 | https://github.com/Song-kyeong-chan/myhomepage |
| 배포 기록 | https://github.com/Song-kyeong-chan/myhomepage/actions |

## 폴더 구조

```text
.
├── site/                      ← 실제 사이트 (여기만 수정)
│   ├── hugo.toml              ← 사이트 설정 (제목, 언어, 소셜 링크)
│   ├── pages.json             ← 배포용 설정 (baseURL, 테마 위치)
│   ├── content/               ← 글과 페이지
│   ├── layouts/               ← 테마 템플릿을 덮어쓴 파일 (한국어화 등)
│   ├── assets/css/override.css← 테마 스타일 보정
│   ├── assets/js/core.js      ← 모바일 메뉴 스크립트 (한국어 버튼 이름)
│   └── themes/template/       ← Noesis 테마 사본 (원본 README·라이선스 포함, 수정하지 않음)
├── .github/workflows/hugo-pages.yml ← 자동 빌드·배포 워크플로
├── .github/pages_build.py     ← 워크플로가 실행하는 빌드 스크립트
├── layouts/, assets/, exampleSite/ … ← 테마 원본 보관용 (빌드에 사용하지 않음)
├── LICENSE.md                 ← 테마 라이선스 (MIT)
└── THIRD_PARTY_NOTICES.md     ← 테마에 포함된 외부 자료 고지
```

## 실행 환경

| 도구 | 버전 | 용도 |
|---|---|---|
| Hugo extended | 0.169.0 (로컬) / 0.167.0 (Actions) | 사이트 빌드 |
| Git | 2.39 | 버전 관리 |
| macOS | Darwin 24 (Apple Silicon) | 작업 환경 |

Actions에서 쓰는 Hugo 버전은 `.github/workflows/hugo-pages.yml`의 `HUGO_VERSION`에 고정되어 있습니다.

## 설치

```bash
# Hugo extended 설치 (macOS, Homebrew)
brew install hugo
hugo version          # 출력에 "+extended"가 있는지 확인

# 저장소 받기
git clone https://github.com/Song-kyeong-chan/myhomepage.git
cd myhomepage
```

## 로컬 미리보기

```bash
cd site
hugo server --config hugo.toml,pages.json --renderToMemory
```

브라우저에서 http://localhost:1313/myhomepage/ 를 엽니다. 파일을 저장하면 화면이 자동으로 새로고침됩니다.

- `--config hugo.toml,pages.json`: 사이트 설정과 배포 설정을 함께 읽습니다. 빠뜨리면 테마를 찾지 못합니다.
- `--renderToMemory`: 결과물을 디스크에 쓰지 않아 `site/public/`이 생기지 않습니다.
- `site/assets/` 아래에 **새 폴더**를 만들었다면 서버를 `Ctrl + C`로 끄고 다시 실행해야 반영됩니다.

## 빌드만 확인하기

```bash
cd site
hugo --config hugo.toml,pages.json
```

결과물은 `site/public/`에 생기며 `.gitignore`로 제외되어 커밋되지 않습니다.

## 내용 수정하기

| 바꾸고 싶은 것 | 파일 |
|---|---|
| 사이트 제목, 소셜 링크(GitHub·Instagram·메일) | `site/hugo.toml` |
| 홈 화면 제목·소개·프로필 사진 | `site/content/_index.md`, `site/content/myface.jpeg` |
| 소개 페이지 (학력, 관심 분야, 학습 목표, 기술) | `site/content/about/index.md` |
| 성과 페이지 설명과 자격증 표 | `site/content/posts/_index.md` |
| LifeSync 활동 글과 캡처 | `site/content/posts/lifesync/` |
| 화면 스타일 보정 | `site/assets/css/override.css` |
| 메뉴·홈·목록·404 등 화면 문구 | `site/layouts/` 아래 같은 이름의 파일 |

### 새 활동 글 추가

```text
site/content/posts/새-글-이름/
├── index.md       ← 글 본문 (front matter에 title, date, description)
└── image.jpg      ← 글에 쓰는 이미지 (영문 소문자 파일명)
```

본문에서 이미지는 `![이미지 설명](image.jpg)`로 넣습니다. 대괄호 안의 설명이 대체 텍스트(alt)가 됩니다.

## 배포하기

```bash
git add <수정한 파일>
git commit -m "무엇을 왜 바꿨는지"
git push
```

`main`에 push하면 워크플로가 자동으로 실행됩니다.

1. `.github/pages_build.py --dependencies`: 빌드에 필요한 준비
2. `.github/pages_build.py --build`: `site/`를 빌드해 루트 `public/`에 결과물 생성
3. GitHub Pages에 결과물 배포

## 배포 확인

1. 저장소의 **Actions** 탭에서 방금 push한 커밋 이름의 실행을 엽니다.
2. `build`와 `deploy`가 모두 초록색 체크인지 확인합니다. 빨간색이면 실패한 단계를 눌러 로그를 확인합니다.
3. 공개 사이트를 열어 변경 내용을 확인합니다. 예전 화면이 보이면 `Cmd + Shift + R`로 강력 새로고침합니다.

터미널에서 확인할 수도 있습니다 (GitHub CLI 필요).

```bash
gh run list -L 3
```

## 출처와 라이선스

### 외부 자료

| 자료 | 출처 | 라이선스 |
|---|---|---|
| Noesis Hugo 테마 | https://github.com/josephhutch/noesis (Joe Hutchinson) | MIT, `LICENSE.md` |
| KaTeX, normalize.css | 테마에 포함 | MIT, `THIRD_PARTY_NOTICES.md` |
| Source Sans 3 글꼴 | 테마에 포함 | SIL OFL 1.1 |
| GitHub Pages 배포 스크립트 | 수업 제공 `prepare_github_pages.py`로 생성 | 수업 자료 |

### 직접 만든 자료

- 소개·학력·자격증·활동 글의 내용과 사실 정보
- 프로필 사진 (`site/content/myface.jpeg`)
- LifeSync 활동 글 및 앱 실행 화면 캡처
- 메뉴 구성, 성과 페이지 구역 나누기 등 사이트 구성 결정

### AI 도움을 받은 부분

AI 도구 Claude Code를 사용했으며, 모든 결과는 직접 검토하고 미리보기와 공개 사이트에서 확인한 뒤 커밋했습니다.

| 부분 | AI가 한 일 | 본인이 한 일 |
|---|---|---|
| 화면 문구 한국어화 (i18n) | 바꿀 문구 위치와 명령 제안 | 적용, 화면 확인 |
| 스타일 보정 (`override.css`) | 사진 잘림·표 넘침 원인 분석과 CSS 제안 | 적용 여부 결정, 화면 폭별 확인 |
| 화면 조정(반응형) | 1440·768·390px 화면 폭별 자동 점검으로 모바일 표 넘침 발견, 줄바꿈 CSS 제안 | 적용, 화면 폭별 재확인 |
| README | 초안 작성 | 명령 실행으로 검증, 수정 |

