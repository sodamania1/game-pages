# 정적 문서 사이트 계약

## 목적과 구현

- 여러 게임의 개인정보처리방침·지원 안내와 향후 이용약관·라이선스 등 공개 문서를 관리한다.
- HTML과 `assets/css/site.css`를 사용한다. 프레임워크·Node.js 빌드·외부 UI 라이브러리에 의존하지 않는다. JavaScript는 꼭 필요할 때만 최소한 사용한다.
- `.nojekyll`로 Jekyll 처리를 비활성화한다. 게임 코드·빌드·백엔드·데이터베이스·추적 코드·광고를 추가하지 않는다.
- 공통 header / main / footer, 상단 탐색, 시스템 폰트, 밝은 배경, 약 760~900px 본문 폭, 모바일 대응과 키보드 접근성을 유지한다.

## 구조와 URL

- 루트 `index.html`은 게임별 문서 허브, `privacy/index.html`은 정책 목록이다.
- 게임별 정책은 `privacy/<game-id>/index.html`에 두고 `/game-pages/privacy/<game-id>/` URL을 유지한다. 표시 이름이 바뀌어도 등록된 게임 ID 경로를 바꾸지 않는다.
- 일반 페이지의 내부 탐색·CSS는 각 깊이에 맞는 상대 경로를 사용한다. `404.html`은 깊은 잘못된 URL에서도 동작하도록 `/game-pages/` 기준 경로를 사용한다.
- 게임을 추가하면 루트와 Privacy 목록을 함께 갱신한다. 미제공 문서는 준비 상태를 표시하거나 실제 공통 페이지에 연결한다.
- `support/index.html`은 공통 지원 안내, `terms/index.html`은 아직 게시하지 않은 약관의 예약 페이지다.

## 개인정보 문서

- 실제 게임 구현·권한·SDK·서비스를 확인한 사실만 작성한다. 미확인 데이터 수집·전송·이용·공유·보관·아동 관련 사항과 연락처는 TODO로 남긴다.
- 기존 아홉 게임(abyss, vamplab, junkbots, lighthouse, diceforge, depot, animalstore, retrosaga, ast)은 확인 전 초안이며 독립 파일로 관리한다.
- Catbox는 게임 저장소의 확정 문서에서 가져온 한국어·영어 정책이다. 한국어 기본 경로는 `privacy/catbox/`, 영어는 `privacy/catbox/en/`이다. 두 언어의 탐색 링크와 언어 메타데이터를 유지한다.
- Catbox의 원본 경로·반영 커밋·작성일·시행일은 [README](../README.md#catbox-privacy-policy)에서 관리한다. 변경 시 원본과 공개 문서의 내용·날짜를 맞추고 출처 커밋을 갱신한다.
- 이 사이트가 언어별 문서를 제공한다는 사실은 모든 출시 국가의 법적 요건을 검증했다는 뜻이 아니다. 번역본은 동일한 정책 내용을 유지한다.
- 임의의 연락처·회사명·개발자 실명을 만들거나 노출하지 않는다. 확인된 게임별 연락처를 공통 연락처로 자동 적용하지 않는다.

## 검증과 배포

- 변경한 HTML의 기본 구조, viewport, 내부 링크, CSS, 깊은 경로의 공통 탐색과 언어 전환을 확인한다. URL 변경 시 `/game-pages/` 하위 실제 HTTP 경로로 검증한다.
- 공개 배포 대상은 `sodamania1/game-pages`, Pages 설정은 `main / (root)`이다. 다른 저장소 설정은 변경하지 않는다.
- 커밋·푸시·설정 변경은 사용자 요청과 실행 환경의 승인 정책을 따른다. 배포했다면 완료 상태와 실제 URL을 확인한다.
- 로컬 확인·Pages 설정·새 게임 추가 방법은 [README](../README.md)에 유지한다.

## 작업 기록 표준

- `work-history` 버전 `1.0`을 [배포본](work-history-standard.md)으로 채택한다.
- 중앙 원본은 `project-standards/standards/work-history-standard.md`이며 채택 시 중앙 커밋은 `1df8c1d2641a769629c04025364675668d45ebaa`다.
- 표준 본문은 변경하지 않는다. 프로젝트 보충 규칙은 이 계약과 루트 AGENTS에 유지한다.
- `docs/`와 AGENTS는 유지보수 문서다. 공개 저장소·정적 배포에서 읽힐 수 있으므로 공개 가능한 내용만 작성한다.
