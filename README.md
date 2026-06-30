# 운영 대시보드

석유화학 운영 엔지니어를 위한 업무·프로젝트 관리 대시보드입니다.
단일 `index.html` 파일로 동작하는 정적 웹앱이며, 데이터는 Firebase Firestore에 저장됩니다.

## 주요 기능

- **업무 관리** — 1회성/반복 업무 등록, 중요도·기한·진행률 관리
- **텍스트 붙여넣기 등록** — 보고 텍스트를 붙여넣으면 업무 앞 번호(`1.`, `2.`)를 기준으로 자동 분리하고, `7.2(목)` 형식의 기한을 인식합니다. 중복 업무는 자동 제외됩니다.
- **프로젝트 추적** — 진행 중인 프로젝트와 마일스톤 관리
- **마감 임박 알림** — 임계일 기준 데스크톱 알림
- **실시간 동기화** — Firestore `onSnapshot` 기반 다중 기기 실시간 반영

## 기술 구성

- React 18 (UMD) + Babel Standalone (브라우저 내 JSX 트랜스파일)
- Firebase Firestore v12 (ESM CDN)
- Pretendard 한글 폰트

빌드 과정 없이 `index.html`을 브라우저에서 바로 열면 됩니다.

## Firebase 설정

`index.html` 안에 Firebase 웹 설정이 포함되어 있습니다. 웹 `apiKey`는 클라이언트 노출을 전제로 한 식별자이지만, **데이터 보호는 Firestore 보안 규칙으로 해야 합니다.** 공개 배포 시 반드시 Firestore 보안 규칙을 설정하세요.

Firestore 컬렉션 구조:

- `tasks` — 업무 문서
- `projects` — 프로젝트 문서
- `settings/main` — 알림 임계일 등 환경 설정
