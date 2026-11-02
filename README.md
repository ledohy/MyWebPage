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
