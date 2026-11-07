# 공개 사이트 기능 검증 기록

- 대상: https://ledohy.github.io/MyWebPage/
- 검사일: 2026-11-07 (KST)
- 검사 기준 배포: 커밋 `4f323ca` → Actions 실행 #8
- 브라우저: Chrome (시크릿 창, 기기 모드), Safari (개인정보 보호 창). 버전은 보고서에 적는다.

| ID | 영역 (기준) | 대상·환경·시각 | 확인 동작 / 예상 | 실제 결과 | 근거 |
|---|---|---|---|---|---|
| T01 | 배포 (P03·P04·P05) | Actions 실행 #8, Safari, 17:13 | main push 후 워크플로가 자동으로 시작되고 build·deploy가 성공할 것 | 성공. Triggered via push, 커밋 4f323ca, build 30s → deploy 10s, Success | [t01-actions.png](t01-actions.png) |
| T02 | 경로·자산 (P11·P13·P24·P25) | /about/ 직접 입력, Chrome 시크릿 + Disable cache, 17:26 | 캐시 없이 접속해도 CSS·아이콘 요청이 모두 성공할 것 | 성공. 요청 6개 모두 200, 4xx 없음 (첫 검사 17:15는 캐시 사용 상태여서 다시 검사함) | [t02-about-nocache.png](t02-about-nocache.png), [t02-network.png](t02-network.png) |
| T02 | 잘못된 주소 (P23) | /no-such-page/, Chrome 시크릿, 17:17 | 404 안내 화면과 홈 링크가 보일 것 | 성공. 문서는 404(의도한 결과), "Page not found" 화면, Back to home으로 홈 이동, CSS·아이콘 200 | [t02-404.png](t02-404.png) |
| T03 | 메뉴·링크 (P21·P22·P26·P27) | 공개 사이트, 17:31 | 메뉴·목차·뒤로 가기·로고·GitHub 링크가 맞는 곳으로 이동할 것 | 성공. About 이동, 목차에서 #skills 도착, 뒤로 가기, Activities에서 BRL 글 이동, 로고로 홈 이동, GitHub 새 탭 | [t03-anchor.png](t03-anchor.png), [t03-activities.png](t03-activities.png) |
| T04 | 반응형 (P31·P32·P33·P34) | Chrome 기기 모드 1440·390·768, 17:35~17:38 | 가로 넘침·겹침 없이 읽히고, 390px에서 메뉴를 쓸 수 있을 것 | 성공. 모든 폭에서 가로 넘침 없음. 390px에서 표가 폭 안에 들어가고 메타 정보가 목록으로 표시됨. 관찰: 390px About에서 "맨 위로" 버튼이 표 마지막 칸 위에 뜨지만 글자는 가리지 않음 | [t04-fig-1440-home.png](t04-fig-1440-home.png), [t04-fig-390-about.png](t04-fig-390-about.png), [t04-fig-390-activity.png](t04-fig-390-activity.png), [t04-768-activities.png](t04-768-activities.png) |
| T05 | 키보드 (P41·P42·P43) | /about/, Safari, 17:43~17:45 | 첫 Tab에 본문 바로가기가 보이고, Enter로 본문 이동, 이후 초점 테두리가 보일 것 | 성공. 첫 Tab에 "Skip to main content" 표시, Enter 후 주소 #main, 다음 Tab에서 목차 링크에 초점 테두리 표시 (다크 모드에서 검사) | [t05-skiplink.png](t05-skiplink.png), [t05-focus.png](t05-focus.png) |

## 남은 문제

- Chrome(Mac)에서는 Tab이 링크를 건너뛰고 버튼(테마 전환)에만 간다. Safari와 Linux Chromium에서는 정상이어서 브라우저·OS 환경 문제로 판단했다. 원인(확장 프로그램 여부 등)은 확인하지 못했다.
- 390px About에서 "맨 위로" 버튼이 표 위에 겹쳐 뜬다. 현재는 내용을 가리지 않는다.
