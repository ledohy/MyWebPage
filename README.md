# 이동현 개인 소개 사이트

전북대학교 컴퓨터공학부 이동현의 개인 소개 사이트입니다.
[Hugo](https://gohugo.io/)와 [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 테마로 만들었고, `main`에 push하면 GitHub Actions가 GitHub Pages로 자동 배포합니다.

- 사이트: https://ledohy.github.io/MyWebPage/
- 저장소: https://github.com/ledohy/MyWebPage
- 배포 기록: https://github.com/ledohy/MyWebPage/actions

## 필요한 도구

| 도구 | 버전 | 용도 |
|---|---|---|
| Hugo extended | 0.158 이상 (배포는 0.167.0) | 사이트 빌드·미리보기 |
| Python | 3.10 이상 (배포는 3.12) | 배포와 같은 방식의 빌드 스크립트 실행 |
| Git | 2.x | 버전 관리, push |

macOS에서는 Homebrew로 설치할 수 있습니다.

```bash
brew install hugo
hugo version    # "extended"와 버전을 확인
```

## 로컬에서 실행하기

미리보기 서버 (파일을 저장하면 브라우저가 자동으로 새로고침됩니다):

```bash
git clone https://github.com/ledohy/MyWebPage.git
cd MyWebPage/site
hugo server --config pages.json --theme template --themesDir themes
```

브라우저에서 http://localhost:1313/MyWebPage/ 를 엽니다.

배포와 같은 방식으로 빌드하기 (저장소 루트에서 실행, 결과는 `public/`):

```bash
cd MyWebPage
python3 .github/pages_build.py --build
```

## 수정할 파일 위치

| 경로 | 내용 |
|---|---|
| `site/pages.json` | 사이트 설정: 제목, 언어, 주소(baseURL), 메뉴, 홈 프로필, GitHub 링크 |
| `site/content/_index.md` | 홈 페이지 |
| `site/content/about.md` | 소개 페이지 |
| `site/content/activities/` | 활동 페이지 (활동 하나당 `.md` 파일 하나) |
| `site/themes/template/` | PaperMod 테마 (빌드에 쓰는 사본) |
| `.github/workflows/hugo-pages.yml` | 배포 워크플로 (Hugo 버전 지정) |
| `.github/pages_build.py` | 빌드 스크립트 (하위 경로 `/MyWebPage/` 보정 포함) |

저장소 루트의 `layouts/`, `assets/`, `i18n/` 등은 내려받은 PaperMod 원본 파일입니다. 빌드에는 `site/themes/template/` 사본을 사용합니다.

## 수정하고 다시 배포하기

1. 위 파일을 수정하고 `hugo server` 화면에서 결과를 확인합니다.
2. 바꾼 파일만 골라 커밋하고 `main`에 push합니다.
   ```bash
   git add <수정한 파일>
   git commit -m "수정 내용 요약"
   git push origin main
   ```
3. 저장소 **Actions** 탭에서 `Deploy Hugo to GitHub Pages` 실행의 `build`와 `deploy`가 모두 성공했는지 확인합니다.
4. https://ledohy.github.io/MyWebPage/ 를 열어 변경이 반영됐는지 확인합니다. 예전 화면이 보이면 캐시 때문이므로 강력 새로고침(Cmd+Shift+R)하거나 시크릿 창으로 엽니다.

GitHub Pages 설정: Settings → Pages → Build and deployment → Source를 **GitHub Actions**로 둡니다.

## 출처와 라이선스

| 자료 | 구분 | 출처 | 이용 조건 |
|---|---|---|---|
| PaperMod 테마 (`site/themes/template/`, 저장소 루트의 원본 파일) | 외부 자료 | https://github.com/adityatelange/hugo-PaperMod | MIT License. 원본 [`LICENSE`](LICENSE)를 유지하고, 사이트 하단의 "Powered by Hugo & PaperMod" 표기를 유지합니다. |
| Hugo | 외부 도구 | https://gohugo.io/ | Apache License 2.0 |
| `prepare_github_pages.py`, `.github/pages_build.py`, `.github/workflows/hugo-pages.yml` | 외부 자료 | 초급프로젝트 수업 제공 스크립트 | 수업 과제용으로 제공받은 파일을 그대로 사용 |
| 설정(`site/pages.json`)과 글(`site/content/`) | 직접 작성 (AI 도움 포함) | 본인 | 설정·글 초안에 AI(Claude)를 사용했고, 내용 판단·수정·확인은 본인이 했습니다. |

테마 원본의 상세 안내는 [`site/themes/template/README.md`](site/themes/template/README.md)에 있습니다.
