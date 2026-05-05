# CLAUDE.md

이 파일은 이 저장소에서 작업할 때 Claude Code(claude.ai/code)에게 제공되는 안내 문서입니다.

## 프로젝트 목표

John Kim의 개인 소개(포트폴리오/이력서) 웹페이지 — 프레임워크, 빌드 단계, 외부 의존성 없음.

## 인물 정보 (`mycareer.md` 기반)

- **이름**: John Kim
- **경력**: 인사(HR) 8년, 사업개발 3년 (총 11년)
- **학력**: 고려대학교 학사, University of Hong Kong 석사

## 로컬 실행

```powershell
# Python
python -m http.server 8080

# Node.js
npx serve .
```

또는 브라우저에서 `index.html`을 직접 열어도 됩니다.

## 페이지 구조

`index.html` 하나에 모든 코드가 담겨 있으며, 다음 섹션으로 구성됩니다.

| 섹션 | id | 내용 |
|---|---|---|
| 내비게이션 | — | 스티키 frosted glass 바, 각 섹션 앵커 링크 |
| 히어로 | — | 이름·직함·태그·CTA 버튼, 아바타 |
| 통계 | `#stats` | HR 8년 / 사업개발 3년 / 학위 2개 숫자 카드 |
| 경력 | `#experience` | 타임라인 카드 2개 (사업개발, HR) |
| 학력 | `#education` | 학교별 카드 (고려대, HKU) |
| 역량 | `#skills` | 스킬 바 카드 6개 |
| 연락하기 | `#contact` | 그라데이션 CTA 박스 |

## 아키텍처

**CSS** — `:root` 커스텀 프로퍼티로 디자인 토큰 관리 (`--accent`, `--surface`, `--border` 등). 색상 변경은 여기서만 수정.

**JS** — 두 가지 역할만 담당:
1. `skills` 배열 → `#skills-grid`에 카드 동적 렌더링
2. `IntersectionObserver` → 스크롤 시 `.timeline-item`, `.edu-card`에 `.visible` 클래스 추가(등장 애니메이션) + 스킬 바 `width` 트랜지션 트리거

**애플 디자인 원칙** — SF Pro 시스템 폰트, `#0071e3` 액센트 블루, 흰 카드 + 미세 그림자, frosted glass 내비게이션, `border-radius: 980px` pill 버튼.

## 콘텐츠 수정 가이드

- **경력 추가/수정**: `<div class="timeline">` 안에 `.timeline-item` 블록 복사·편집
- **학력 추가**: `<div class="edu-grid">` 안에 `.edu-card` 블록 복사·편집
- **스킬 수정**: JS 상단 `skills` 배열의 `name`과 `pct`(0–100) 값 수정
- **연락처 이메일**: `.contact-btn`의 `href="mailto:..."` 수정
