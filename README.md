# Game Pages

## Purpose

여러 게임의 개인정보처리방침, 지원 안내 및 향후 이용약관·오픈소스 라이선스 등 외부 공개 문서를 관리하는 GitHub Pages 전용 저장소입니다. 게임 코드나 빌드 결과물은 포함하지 않습니다.

사이트: https://sodamania1.github.io/game-pages/

HTML과 공통 CSS만 사용합니다. JavaScript, 외부 CDN, 패키지 설치 및 로컬 빌드가 필요하지 않습니다. `.nojekyll`은 Jekyll 처리를 비활성화합니다.

## Site structure

```text
game-pages/
├── .gitignore
├── .nojekyll
├── index.html                # 게임별 문서 허브
├── privacy/
│   ├── index.html            # 개인정보처리방침 목록
│   ├── abyss/index.html
│   ├── vamplab/index.html
│   ├── junkbots/index.html
│   ├── lighthouse/index.html
│   ├── diceforge/index.html
│   ├── depot/index.html
│   ├── animalstore/index.html
│   ├── retrosaga/index.html
│   ├── ast/index.html
│   └── catbox/
│       ├── index.html        # 고양이는 액체다 개인정보처리방침 (한국어)
│       └── en/index.html     # Cats Are Liquid Privacy Policy (English)
├── support/index.html        # 공통 지원 안내
├── terms/index.html          # 향후 약관용 예약 페이지
├── assets/css/site.css       # 모든 페이지의 공통 스타일
├── 404.html
└── README.md
```

게임별 개인정보처리방침은 독립된 파일입니다. 기존 아홉 게임은 동일한 초기 초안 템플릿을 사용하며, catbox는 게임 내 확정 문서를 바탕으로 작성했습니다. 한 게임의 확인된 사실을 다른 게임에 자동으로 적용하지 않습니다. 향후 게임별 지원 문서는 `support/<game-id>/index.html`, 기타 문서는 별도 디렉터리로 추가할 수 있습니다.

## Catbox privacy policy

고양이는 액체다(Cats Are Liquid)의 공개 개인정보처리방침입니다.

- 한국어: https://sodamania1.github.io/game-pages/privacy/catbox/
- English: https://sodamania1.github.io/game-pages/privacy/catbox/en/
- 작성일: 2026년 9월 30일
- 시행일: 2026년 11월 1일
- 원본: `sodamania1/catbox` 저장소의 `legal/privacy.html`, `legal/privacy.en.html`
- 반영한 원본 커밋: `a0f036bea07f9514e6eeb3169cd6d3e649e664bd`

두 언어의 본문과 날짜, 개발자명 및 개인정보 문의 이메일은 원본 확정 문서를 유지합니다. 공통 CSS, 사이트 탐색, 언어 전환과 언어별 메타데이터만 공개 사이트 형식에 맞췄습니다. 한국어 페이지를 기본 URL로 사용하며 영어 페이지와 서로 연결합니다.

문서 변경 시 게임 내 두 원본과 공개 페이지의 본문·날짜를 함께 맞추고 위 원본 커밋을 갱신합니다. 게임 구현이 바뀌면 원본에서 먼저 해당 사실을 확인합니다. `main`에 커밋하고 푸시하여 Pages 배포를 마친 뒤 공개 URL을 Play Console에 등록합니다.

## Local editing

HTML/CSS를 직접 수정하면 됩니다. 파일을 직접 열어 내용을 볼 수 있지만, 디렉터리 URL 탐색을 정확히 확인하려면 저장소 루트에서 다음을 실행합니다.

```bash
python3 -m http.server 8000
```

`http://localhost:8000/`에서 확인합니다. 일반 페이지는 상대 경로를 사용하므로 루트 및 `/game-pages/` 하위 배포에서 모두 동작합니다.

실제 Pages 하위 경로와 404 링크까지 확인하려면 저장소의 **상위 디렉터리**에서 다음을 실행하고 `http://localhost:8000/game-pages/`를 엽니다.

```bash
python3 -m http.server 8000
```

이 방식은 로컬 상위 디렉터리도 제공하므로 테스트 후 서버를 종료합니다. Python 기본 서버는 존재하지 않는 URL에 `404.html`을 자동으로 표시하지 않으므로 `/game-pages/404.html`을 직접 열어 확인합니다.

`404.html`은 어떤 깊이의 잘못된 URL에서도 CSS와 탐색이 유지되도록 `/game-pages/` 기준 경로를 사용합니다. 저장소 이름이나 사용자 지정 도메인의 배포 경로가 바뀌면 이 파일의 경로를 함께 수정합니다. 일반 페이지의 디렉터리 링크는 `file://` 환경에서 디렉터리로 보일 수 있습니다.

## GitHub Pages setup

대상 저장소는 `sodamania1/game-pages`입니다. GitHub 웹 UI에서 다음을 설정합니다.

**Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch: main → Folder: / (root) → Save**

`main`에 변경 사항을 커밋하고 푸시하면 Pages가 배포합니다. 별도 빌드 도구나 직접 작성한 Actions workflow는 필요하지 않습니다. 배포 상태는 저장소의 **Actions** 또는 **Settings → Pages**에서 확인합니다.

## Adding a new game

1. 기존 `privacy/<game-id>/index.html`을 새 `privacy/<new-game-id>/index.html`에 복사합니다.
2. 페이지 제목, 표시 이름, breadcrumb와 설명에 있는 게임 이름을 변경합니다. 복사한 정책 내용은 해당 게임 기준으로 다시 검증하고 미확인 항목은 TODO로 둡니다.
3. `privacy/index.html`과 루트 `index.html` 목록에 새 게임 링크를 추가합니다.
4. 새 페이지의 CSS와 Home / Privacy / Support / Terms 링크를 확인합니다.

표시 이름을 바꿀 때는 위 두 목록과 해당 게임 페이지의 `<title>`, breadcrumb, 게임 표시 이름을 수정합니다. 정식 게임명이 바뀌어도 이미 등록한 **게임 ID 디렉터리는 변경하지 않습니다**.

정책 URL은 `https://sodamania1.github.io/game-pages/privacy/<game-id>/`입니다. Google Play Console 등에 등록한 뒤에도 이 경로를 유지하고 문서 내용만 갱신합니다.

## Important

catbox 이외의 기존 아홉 게임 개인정보처리방침은 **확인 전 초안**입니다. 실제 정책으로 제출하기 전에 실제 게임 구현, 권한, SDK, 광고·분석·서버 서비스를 조사하고 TODO를 해결해야 합니다. 수집이 없다는 주장도 검증 없이 작성하지 않습니다. 공개 이메일, 회사명 또는 개인 이름을 추측하여 추가하지 않습니다.

게임별 확인 항목:

- 적용 범위와 책임 주체
- 데이터 수집·전송 여부, 데이터 종류, 출처, 권한, 수집 방식
- 데이터 이용 목적
- 실제 SDK와 제3자 서비스, 데이터 수신 여부, 확인된 정책 링크
- 데이터 저장 위치, 보관 기간, 삭제 절차
- 대상 연령과 아동 정보 처리 여부
- 정책 변경 공지 방법과 최종 수정일
- 개인정보 문의 및 관련 요청을 받을 공개 연락처

공통 `support/index.html`에도 실제 공개 지원 채널을 추가해야 합니다. 이용약관은 아직 게시하지 않았으며 `terms/index.html`은 예약 페이지입니다.
