# WXM 사이트 마스터 스펙

> 배포 URL: `https://jaymtwoo-ai.github.io/`  
> 저장소: `jaymtwoo-ai.github.io`  
> 최종 갱신: 2025-06-11 (v5 — **1차 push 준비**, 로컬 구현·문서 동기화)  
> 상태: **확정 사항 정리 #001 ~ #007 통합본** + **와이어프레임 동기화 완료**

> **문서 표기 안내:** 본문의 `---` 는 마크다운 **섹션 구분선**입니다. 내용이 아니라 목차 사이를 나누는 선입니다.

---

## 문서 이력

| 번호 | 제목 | 상태 |
|------|------|------|
| #001 | 5단 구조 + HEADER/FOOTER | ✅ 확정 (v2: 네비·액션밴드·푸터 보강) |
| #002 | HERO 높이 + 모바일 액션밴드/FOOTER | ✅ 확정 (v2: 수치 규격 명시) |
| #003 | 페이지 유형 [A][B][C][D][E] | ✅ 확정 (v2: [E] 설명·coming-soon 목록) |
| #004 | 카드 색상 2모드 (select / content) | ✅ 확정 |
| #005 | CONTACT/Q&A 3단 연결 + 용어 정리 | ✅ 확정 (v2: pill/카드/CTA 설명) |
| #006 | 페이지·연결 마스터 표 + push 전략 | ✅ 본 문서 (v2: push 순서 재검토) |
| #007 | 디자인 시스템 (폰트·컬러·컴포넌트) | ✅ 확정 — `css/common.css` |

---

# #001 — 페이지 표준 구조 (5단)

| 순서 | 작업 용어 | 코드 클래스 | 역할 |
|------|----------|------------|------|
| ① | **HEADER** | `.site-header` | 로고 + 글로벌 네비 (전 페이지 공통) |
| ② | **HERO** | `.hero` | 첫 화면 — 슬로건 + 골드바 + 설명문 |
| ③ | **MID SECTION** | `.roadmap` 등 | 브랜드·서비스 구조·설명 |
| ④ | **하단 액션 영역** | 아래 표 참고 | 페이지별 이름·버튼 수만 다름 |
| ⑤ | **FOOTER** | `.site-footer` | 브랜드·회사정보·언어·© |

---

## 하단 액션 영역 — 3종 (레이아웃 통일)

**공통 레이아웃 셸** (index / qube24 / seminar 동일):

```
┌─────────────────────────────────────────────┐
│  [골드 라벨]          │  [pill 버튼 1  →]   │
│  [그린 제안 제목]      │  [pill 버튼 2  →]   │
│  (선택: 부가 설명)     │  [pill 버튼 3/4 →]  │
└─────────────────────────────────────────────┘
  ← 왼쪽: 제안 문구          오른쪽: pill 세로 나열 →
```

| 페이지 | 영역명 | pill 수 | 왼쪽 문구 (확정) |
|--------|--------|---------|-----------------|
| `index.html` | **CONTACT BAND** | 3개 | 라벨 `CONTACT` / 제목 `WXM과 함께 새로운 가능성을 시작하세요.` |
| `qube24.html` | **QUBE24 CONTACT** (`#qube24-contact`) | 4개 | 라벨 `QUBE24 CONTACT` / 제목 `문의 유형을 선택해 주세요.` (또는 QUBE24용 제안문) |
| `seminar-event.html` | **INQUIRY BAND** | 3개 | 라벨 `INQUIRY` / 제목 `참석, 참여, 그리고 제안` |

> **와이어프레임 원본 vs 확정:** 원본 와이어프레임은 qube24 `#qube24-contact`을 **4카드 그리드**로 그렸으나, **index CONTACT BAND와 같은 셸(왼쪽 문구 + 오른쪽 pill)** 로 통일하기로 확정.

### qube24 — pill 4개 (오른쪽)

| # | pill 텍스트 | 연결 |
|---|------------|------|
| 1 | WXM 운영형 문의 | `wxm-managed-form.html` (미제작 시 `coming-soon.html`) |
| 2 | 파트너 운영형 문의 | `partner-managed-form.html` (미제작 시 `coming-soon.html`) |
| 3 | 비즈니스 제안 | `business-proposal-form.html` (미제작 시 `coming-soon.html`) |
| 4 | Q&A | `qube24-qa.html` ← **qa.html 허브 아님** |

### seminar — pill 3개 (오른쪽)

| # | pill 텍스트 | 연결 |
|---|------------|------|
| 1 | 세미나 참석 문의 | `seminar-apply.html` (미제작 시 `coming-soon.html`) |
| 2 | 이벤트 참여 문의 | `event-apply.html` (미제작 시 `coming-soon.html`) |
| 3 | 함께 제안하기 | `seminar-event-proposal.html` (미제작 시 `coming-soon.html`) |

---

## 액션밴드 디자인 규격 (첨부 이미지 없이 적용)

> 이후 구현·검수는 **아래 수치** 기준. 매번 이미지 재첨부 불필요.

### 공통 색상 토큰

| 토큰 | 값 | 용도 |
|------|-----|------|
| `--g` | `#1F4037` | 제안 제목, pill 텍스트·아이콘 |
| `--gold` | `#C9A978` | 섹션 라벨 (CONTACT / INQUIRY 등) |
| 배경 | `#F4F0E8` | 밴드 배경 (+ `images/bg-2.png` 선택) |
| pill 테두리 | `rgba(201,169,120,0.68)` | 골드 border |
| pill 배경 | `rgba(244,240,232,0.18)` | 반투명 아이보리 |

### 왼쪽 제안 문구

| 요소 | 데스크톱 | 모바일 |
|------|---------|--------|
| 라벨 (`.cb-label` 등) | 10px / bold / letter-spacing 0.28em / **골드** / UPPERCASE | 동일 |
| 제목 (`.cb-title` 등) | `clamp(28px, 2.45vw, 42px)` / **그린 `#1F4037`** / line-height 1.24 | 18~22px / **그린** |
| 부가 설명 (있을 때) | 15px / `rgba(23,24,21,0.72)` | 12~13px |

### pill 버튼 (`.cb-btn` / `.cs-btn` / `.iq-btn` 통일)

| 속성 | 데스크톱 | 모바일 |
|------|---------|--------|
| 형태 | `border-radius: 999px` (캡슐형) | 동일 |
| 테두리 | 1px solid 골드 68% | 동일 |
| 패딩 | 14px 24px | 14px 18px |
| 최소 높이 | 48px | 44px |
| 텍스트 | 13px bold / letter-spacing 0.12em / **그린** / UPPERCASE | 9~11px |
| 왼쪽 | 아이콘(20px) + 텍스트 | 아이콘(14px) + 텍스트 |
| 오른쪽 | `>` (chevron, 18px) | chevron 14px |
| 배치 | 오른쪽 열, **세로 나열**, gap 10px | 아래 블록, **가로 100%** (`width: 100%`) |

### 레이아웃 — 3열 / 1열이란?

| 환경 | 그리드 | 시각 구조 |
|------|--------|----------|
| **데스크톱 3열** | `0.42fr \| 0.34fr \| 0.42fr` | ①왼쪽=제안문구 ②가운데=빈 여백 ③오른쪽=pill 열 |
| **모바일 1열** | `1fr` (단일 열) | ①제안문구 **위** → ②pill 버튼 **아래** 세로 나열 |

> **"전체 너비"** = 모바일에서 각 pill이 화면 가로 **100%**를 차지한다는 뜻. 데스크톱은 오른쪽 열만 `min(420px, 100%)`.
>
> 모바일은 **2열(좌우 나란히) 아님**. 제안문구와 pill을 **위아래로 쌓는 1열**이 확정 (현재 `index.html` `#wxm-mobile-guaranteed` 기준).

---

## HEADER 네비 (확정 v2)

```
[WXM              → index.html]
[ABOUT            → index.html#about]
[BRANDS           → index.html#roadmap]     ← 네비 라벨만 변경 (ROADMAP → BRANDS)
[SEMINAR & EVENT  → seminar-event.html]   ← 문구 유지
[CONTACT US       → contact.html]         ← 문구 유지
[LOGIN            → login.html]
```

| 환경 | 표시 |
|------|------|
| 데스크톱 | 6개 모두 |
| 모바일 | **CONTACT US, LOGIN 숨김** / WXM·ABOUT·BRANDS·SEMINAR & EVENT 표시 |

> BRANDS = 메인 SERVICE ROADMAP 섹션 (QUBE24·02~05 브랜드 카드). "어떤 로드맵인지" 모호해서 **BRANDS** 로 명확화.

---

## FOOTER 고정 문구

| 클래스 | 고정 문구 |
|--------|----------|
| `.ft-logo` | `W X M` |
| `.ft-sub` | `WELLNESS × MECHANISM` |
| `.ft-tagline` | `We Design Wellness x Mechanism` |
| `.ft-company-name` | `더블유엑스엠 주식회사` |
| `.ft-company-info` | `사업자등록번호 155-81-03984 \| 대표 이지민` / `Contact 010-2580-4127 \| jimin@wxm.co.kr` |
| `.ft-lang` | `KR` `EN` `JP` `CN` (KR active) |
| `.ft-copy` | `© WXM Inc. All rights reserved.` |

### `W X M` / `×` / `x` — 헷갈리기 쉬운 부분

| 위치 | 실제 표기 | 설명 |
|------|----------|------|
| HEADER 로고 | `W X M` | **영문 알파벳 3글자 + 공백**. 곱하기(×)도 소문자 x도 **아님**. 그냥 **X** 라는 글자. |
| `.ft-sub` | `WELLNESS × MECHANISM` | **곱하기 기호 ×** (유니코드 multiplication sign) |
| HERO 슬로건, `.ft-tagline` | `Wellness x Mechanism` | **영문 소문자 x** |

→ 로고의 X는 브랜드 이니셜의 한 글자이고, 슬로건/푸터의 x·×는 문장 속 연결 기호로 **의도적으로 다르게** 씁니다.

### 모바일 FOOTER — 표시 문구 (3줄 + 언어 + ©)

**전 페이지 공통** (`css/mobile.css` + `css/common.css`). 페이지별 인라인 footer CSS로 덮어쓰지 않음.

| 표시 | 숨김 (모바일) |
|------|----------------|
| `W X M` / `WELLNESS × MECHANISM` / `We Design Wellness x Mechanism` / **`KR/EN/JP/CN`** / `© WXM Inc.` | 회사정보만 |

- 언어는 **한 줄** `KR/EN/JP/CN` (슬래시 구분, KR active)
- `qube24.html` 등 랜딩도 **index와 동일** compact footer
- 모든 HTML에 `<link rel="stylesheet" href="css/mobile.css">` 필수

모바일 표시:

```
1줄  W X M
2줄  WELLNESS × MECHANISM
3줄  We Design Wellness x Mechanism
4줄  KR/EN/JP/CN
     © WXM Inc. All rights reserved.
```

| 요소 | 모바일 크기 (index 기준) |
|------|------------------------|
| 1줄 | 8px / bold / letter-spacing 0.20em / `#F4F0E8` |
| 2줄 | 6px / bold / letter-spacing 0.10em / `rgba(244,240,232,0.35)` |
| 3줄 | 7px / `rgba(244,240,232,0.28)` |
| © | 6~7px / `rgba(244,240,232,0.25)` |

---

# #002 — HERO + 모바일 액션밴드/FOOTER

### HERO 높이 · 배경 · 슬로건 (3그룹 — 혼동 주의)

| 그룹 | 페이지 | 배경 | 높이 | 슬로건 |
|------|--------|------|------|--------|
| **메인** | `index.html` | `images/bg-1.png` + 얕은 오버레이 | HEADER+HERO ≈ **100vh** (스크롤 후 MID·밴드·FOOTER) | `We Design` / `Wellness x` / `Mechanism` (3줄 타이포) |

### index HERO 슬로건 — 모바일 3줄 고정 (브라우저 구도 유지)

데스크톱·모바일 **동일 3줄**. 모바일에서 줄이 합쳐지면 안 됨.

| 줄 | HTML | 금지 예 |
|----|------|---------|
| 1 | `We Design` (`.hero-line-design`) | `We Design Wellness x` 한 줄에 합침 |
| 2 | `Wellness x` (`.hero-line-wellness`) | — |
| 3 | `Mechanism` (`.hero-line-mechanism`, italic) | `Mechanism`만 둘째 줄에 단독 |

**모바일 CSS 필수**

```css
.hero-title { display:flex; flex-direction:column; align-items:flex-start; width:max-content; }
.hero-line   { display:block; white-space:nowrap; width:max-content; }
.hero-line-wellness { display:inline-flex; align-items:baseline; }
```

- `.hero-title`에 `width:100%` + `white-space:normal`만 주면 3줄이 깨짐 → **사용 금지**
- 크기만 `clamp`로 줄이고 **줄바꿈 구조는 유지**
| **랜딩형** | `qube24.html`, `seminar-event.html` | **그라데이션** (bg-1 없음) | **서로 동일** `min-height: 520px` (모바일 `auto`) | qube24: Better Moment / Better You · seminar: **index와 동일 3줄 슬로건** |
| **예외 [C]** | `coming-soon.html`, `login.html` | coming-soon: 그라데이션 / login: cream 본문 | **HEADER+본문+FOOTER = 100vh, 스크롤 없음** (`body.page-type-c`) | coming-soon: Coming Soon 타이틀 |

```
메인 진입 화면 = HEADER + HERO = 100vh
구현: index hero 높이 = 100vh - header높이 (데스크톱 patch min-height 720px)
스크롤해야 MID SECTION·액션밴드·FOOTER가 보임

랜딩형(qube24·seminar)은 풀스크린 아님 — 랜딩끼리 HERO 셸(배경·높이) 통일
seminar 슬로건 타이포만 index 기준, HERO 배경·높이는 qube24 기준
```

| 그룹 | 페이지 | 규칙 |
|------|--------|------|
| 메인 기준 | `index.html` | 풀스크린 HERO · bg-1.png |
| 랜딩형 통일 | `qube24.html`, `seminar-event.html` | 그라데이션 HERO · 높이 통일 · seminar 슬로건=index |
| 허브형 통일 | `contact.html`, `qa.html` | PAGE HEADER 높이 통일 |
| 예외 [C] | `coming-soon.html`, `login.html` | 풀스크린 HERO 없음. **`body.page-type-c`** — HEADER + 본문 + FOOTER가 스크롤 없이 한 화면 |

### index CONTACT BAND — 모바일 확정 문구

```
CONTACT                          ← 골드 라벨
WXM과 함께                       ← 그린 #1F4037
새로운 가능성을
시작하세요.

[📤 CONTACT US  →]               ← pill
[❓ Q & A       →]
[⬆ BACK TO TOP  →]
```

### coming-soon 오른쪽 설명문 (확정)

```
WXM은 지금 다음 서비스를 설계하고 있습니다.

공간과 이용자의 리듬을 연결하는
새로운 웰니스 경험을 준비하고 있습니다.

곧 더 정밀하고 자연스러운 방식으로 찾아뵙겠습니다.
```

### 로컬 구현 완료 · push 대기 (v5)

| 파일 | 반영 내용 |
|------|----------|
| `index.html` | bg-1 HERO · 5열 roadmap · CONTACT bg-2 · BRANDS 네비 · 모바일 guaranteed |
| `qube24.html` | 랜딩 HERO · MID 크기 index 정렬 · `#qube24-contact` pill 4개 · `common.css` 셸 (인라인 override 제거) |
| `seminar-event.html` | 랜딩 HERO(qube24 셸) · index 슬로건 타이포 · INQUIRY pill index 규격 · `contact-band` |
| `coming-soon.html` | `page-type-c` 한 화면 · 설명문 수정 |
| `login.html` | `page-type-c` 한 화면 |
| `css/common.css` | 액션밴드 통일 · `.page-type-c` [C] 레이아웃 |

> **주의:** `qube24`·`seminar`는 `<style>` 인라인 CSS가 `common.css`를 덮어쓰면 UI가 어긋남. 액션밴드·pill은 **common.css에 위임**하고 페이지별 인라인은 HERO·MID만 유지.

### 로컬 준비됨 · 아직 미 push

| 파일 | 변경 내용 |
|------|----------|
| `index.html` | 충돌 CSS 제거, `#wxm-mobile-guaranteed`, `mobile.css?v=7` |
| `qa.html` | 인라인 모바일 CSS |
| `contact.html` | 인라인 모바일 CSS |
| `qube24.html` | pill 4개 · MID·CONTACT index 정렬 |
| `seminar-event.html` | INQUIRY·HERO 정렬 |
| `coming-soon.html` | `page-type-c` · 문구 수정 |
| `login.html` | `page-type-c` |
| `css/common.css` | 액션밴드 · `page-type-c` |

---

# #003 — 페이지 유형 + MID SECTION

### 페이지 유형 정의

```
[A] 랜딩형
    HEADER → HERO(풀스크린) → MID SECTION → 액션밴드 → FOOTER
    예: index, qube24, seminar-event

[B] 허브형
    HEADER → PAGE HEADER → HUB LIST → FOOTER
    예: contact, qa (+ qube24-qa는 [B] 서브)

[C] 예외 단순형
    HEADER → 본문(또는 소형 HERO) → FOOTER
    스크롤 없이 한 화면. MID·액션밴드(④) 없음
    단, 간단한 액션 pill은 있을 수 있음 (아래 표)
    예: coming-soon, login

[D] 폼/캘린더형 (chapter3)
    HEADER → 폼 또는 캘린더 본문 → FOOTER
    허브·랜딩에서 pill 클릭 후 진입하는 "실행" 페이지

[E] 세부설명형 (chapter4)
    HEADER → PAGE HEADER → 본문 콘텐츠 → FOOTER
    ※ [B] 허브형과 동일 셸. 내용만 상세 설명으로 다름
```

### [C] 예외형 — 액션 pill + 한 화면 레이아웃

| 페이지 | 액션 pill | 연결 | 비고 |
|--------|----------|------|------|
| `coming-soon.html` | BACK TO MAIN | `index.html` | ✅ 구현 · 오른쪽 설명문 **「QUBE24를 시작으로,」 제거** (2025-06-11) |
| `login.html` | LOGIN 버튼 | (폼 제출) | ✅ 구현 · 계정 문의 → `contact.html` |

**[C] 한 화면 구현 (`css/common.css`):**

- `body.page-type-c` → `height: 100vh`, flex column, `overflow: hidden`
- `main` → `flex: 1`, `min-height: 0`
- `.site-footer` → `flex-shrink: 0`, 축소 패딩
- 모바일: footer 회사정보·언어 숨김 (3줄+©)

> **액션밴드(④)** = index/qube24/seminar 하단의 큰 밴드 영역.  
> **[C]의 pill** = 본문 안 간단 버튼. 밴드 구조 없음.

### [E] 세부설명형 — [B]와 같은 셸로 해도 되나?

**문제 없음. 확정.**

| 비교 | [B] 허브 | [E] 세부 |
|------|---------|---------|
| 셸 | PAGE HEADER + 리스트/본문 + FOOTER | **동일** |
| 차이 | 브랜드 **선택** 목록 | 한 주제 **상세** 설명 |
| 예 | contact.html (5개 브랜드 카드) | qube24-custom.html (맞춤 기준 상세) |

DETAIL HERO를 별도로 두지 않고, [B]의 PAGE HEADER 형식을 재사용.

### [E] 세부설명형 — 왜 필요한가?

| 항목 | 설명 |
|------|------|
| **언제 쓰나** | qube24 MID의 B2B 카드(01~04)를 **클릭했을 때** 들어가는 하위 페이지 |
| **[A]와 차이** | [A]는 브랜드 **랜딩**(첫인상+전체 구조), [E]는 **한 주제만 깊게** 설명 |
| **구성** | PAGE HEADER(소제목) → 본문 섹션(표·다이어그램) → FOOTER |
| **예시** | `qube24-custom.html` = B2B 01「맞춤 기준」상세 / `qube24-operation.html` = 04「운영 방식」상세 |
| **연결** | `qube24.html` MID 카드 클릭 → 해당 [E] 페이지 (미제작 시 `coming-soon.html`) |

### 전체 페이지 30개 — 마스터 목록

> 이전 "미제작 14개"는 **당장 chapter3·4에서 만들 페이지만** 센 숫자였습니다.  
> 사이트 **전체 계획**은 아래 **30개**입니다.

| # | 파일 | 유형 | 상태 | 비고 |
|---|------|------|------|------|
| 01 | `index.html` | [A] | ✅ | 기준 페이지 · push 전 폰 확인 |
| 02 | `qube24.html` | [A] | ✅ | pill 4개 · MID·CONTACT 정렬 완료 |
| 03 | `seminar-event.html` | [A] | ✅ | INQUIRY pill · HERO 정렬 완료 |
| 04 | `contact.html` | [B] | ⚠️ | Contact 허브 |
| 05 | `qa.html` | [B] | ⚠️ | Q&A 허브 |
| 06 | `qube24-qa.html` | [B] | ⚠️ | QUBE24 Q&A |
| 07 | `coming-soon.html` | [C] | ✅ | 공통 준비중 |
| 08 | `login.html` | [C] | ✅ | 파트너 로그인 |
| 09 | `wxm-managed-form.html` | [D] | ❌ | |
| 10 | `partner-managed-form.html` | [D] | ❌ | |
| 11 | `business-proposal-form.html` | [D] | ❌ | |
| 12 | `seminar-calendar.html` | [D] | ❌ | |
| 13 | `event-calendar.html` | [D] | ❌ | |
| 14 | `seminar-apply.html` | [D] | ❌ | |
| 15 | `event-apply.html` | [D] | ❌ | |
| 16 | `seminar-event-proposal.html` | [D] | ❌ | |
| 17 | `qube24-custom.html` | [E] | ❌ | B2B 01 상세 |
| 18 | `qube24-configuration.html` | [E] | ❌ | B2B 02 상세 |
| 19 | `qube24-space.html` | [E] | ❌ | B2B 03 상세 |
| 20 | `qube24-operation.html` | [E] | ❌ | B2B 04 상세 |
| 21 | `recovery-mode.html` | [A] | ❌ | ROADMAP 02 랜딩 (추후) |
| 22 | `body-check.html` | [A] | ❌ | ROADMAP 03 랜딩 (추후) |
| 23 | `inner-flow.html` | [A] | ❌ | ROADMAP 04 랜딩 (추후) |
| 24 | `connected-wellness.html` | [A] | ❌ | ROADMAP 05 랜딩 (추후) |
| 25 | `recovery-mode-qa.html` | [B] | ❌ | ROADMAP 02 Q&A (추후) |
| 26 | `body-check-qa.html` | [B] | ❌ | ROADMAP 03 Q&A (추후) |
| 27 | `inner-flow-qa.html` | [B] | ❌ | ROADMAP 04 Q&A (추후) |
| 28 | `connected-wellness-qa.html` | [B] | ❌ | ROADMAP 05 Q&A (추후) |
| 29 | `index-en.html` | 언어 | ❌ | EN → `coming-soon.html` |
| 30 | `index-jp.html` | 언어 | ❌ | JP → `coming-soon.html` |
| (+) | `index-cn.html` | 언어 | ❌ | CN → `coming-soon.html` (31번째) |

**집계**

| 구분 | 수 |
|------|-----|
| 현재 파일 존재 | **8** |
| 미제작 (09~30) | **22** |
| **확정 핵심 30** | KR 메인 기준 30페이지 (CN 포함 시 31) |

### `coming-soon.html` 연결 현황

**지금 live 코드에서 `coming-soon.html`로 연결되는 경로 (13곳):**

| 출발 페이지 | 버튼/카드 | 비고 |
|------------|----------|------|
| `index.html` | ROADMAP 02 | 미래 브랜드 |
| `index.html` | ROADMAP 03 | 미래 브랜드 |
| `index.html` | ROADMAP 04 | 미래 브랜드 |
| `index.html` | ROADMAP 05 | 미래 브랜드 |
| `contact.html` | 허브 02~05 | 4개 |
| `qa.html` | 허브 02~05 | 4개 |
| `seminar-event.html` | 세미나 캘린더 SCHEDULE | MID 카드 |
| `seminar-event.html` | 이벤트 캘린더 SCHEDULE | MID 카드 |
| `seminar-event.html` | INQUIRY — 세미나 참석 | pill |
| `seminar-event.html` | INQUIRY — 이벤트 참여 | pill |
| `seminar-event.html` | INQUIRY — 함께 제안하기 | pill |

**미제작 페이지 — 원칙: 완성 전까지 `coming-soon.html` 연결**

| 미제작 페이지 | 임시 연결 출발지 |
|-------------|----------------|
| 폼 3종 (#09~11) | qube24 pill 1~3 |
| 캘린더 2종 (#12~13) | seminar MID 카드 |
| 신청/제안 3종 (#14~16) | seminar INQUIRY pill |
| qube24 세부 4종 (#17~20) | qube24 B2B MID 카드 |
| 브랜드 랜딩 4종 (#21~24) | index ROADMAP 02~05 (현재 coming-soon) |
| 브랜드 Q&A 4종 (#25~28) | qa 허브 02~05 (현재 coming-soon) |
| EN / JP / CN (#29~30) | footer 언어 링크 → **`coming-soon.html`** |

### MID SECTION 카드 모드 (#004 연동)

| 모드 | 적용 | 규칙 |
|------|------|------|
| **select** | `index.html` 만 | ON 1개(그린) + OFF(골드 숫자+회색) |
| **content** | qube24, seminar 등 | 전 카드 ON(그린), OFF 없음 |

---

# #004 — 카드 색상 규칙

### select 모드 (`index` 로드맵)

| 요소 | ON (01 QUBE24) | OFF (02~05) |
|------|----------------|-------------|
| 숫자 | 그린 `#1F4037` | 골드 `rgba(201,169,120,0.78)` |
| 타이틀 | 그린 | 어두운 회색 |
| 설명 | 그린 톤 | 회색 |
| dot/라인 | 그린 | 연한 회색 |
| 뱃지 | FIRST STEP | NEXT STEP |

### content 모드 (qube24 MID, seminar 카드 등)

- 전 카드 **ON(그린)** — OFF(회색 비활성) 없음
- 숫자/라벨: 골드 / 타이틀: `#1F4037` / 본문: `#4D5A56`

---

# #005 — CONTACT / Q&A 연결 + 용어

## 용어 사전

| 용어 | 뜻 | 어디에 쓰이나 |
|------|-----|-------------|
| **pill** | 둥근 캡슐형 **액션 버튼** (icon + 텍스트 + `>`) | CONTACT BAND, QUBE24 CONTACT, INQUIRY BAND |
| **카드 (MID)** | MID SECTION의 **설명 박스** (번호·제목·본문·화살표) | index ROADMAP, qube24 B2B 01~04, seminar SEM CARD |
| **허브** | 브랜드 **목록 페이지** (contact / qa) | 1단 — "어느 브랜드?" 선택 |
| **CTA** | Call To Action = 페이지 **하단 행동 유도 영역** | `qube24-qa.html` Q&A 아래 "QUBE24 문의하기" 밴드 |

> **pill ≠ 카드.** qube24 `#qube24-contact`의 WXM운영형·파트너운영형·비즈니스제안·Q&A **4가지는 모두 오른쪽 pill 버튼**이 맞습니다. (와이어프레임 원본의 4카드 그리드 → pill 셸로 변경 확정)

---

## 3단 연결 구조

```
[1단] 브랜드 허브        contact.html / qa.html
         ↓
[2단] 브랜드별 진입      qube24.html#qube24-contact / qube24-qa.html
         ↓
[3단] 실제 폼·Q&A 페이지   wxm-managed-form.html 등
```

### CONTACT 연결표

| 출발 | 동작 | 목표 URL | 현재 | 상태 |
|------|------|---------|------|------|
| index CONTACT BAND | CONTACT US pill | `contact.html` | ✅ | OK |
| index CONTACT BAND | Q&A pill | `qa.html` | ✅ | OK |
| contact 허브 | QUBE24 | `qube24.html#qube24-contact` | ✅ | OK |
| contact 허브 | 02~05 | `coming-soon.html` | ✅ | OK |
| qube24 #qube24-contact | WXM 운영형 pill | `wxm-managed-form.html` | ✅ → coming-soon | OK (임시) |
| qube24 #qube24-contact | 파트너 운영형 pill | `partner-managed-form.html` | ✅ → coming-soon | OK (임시) |
| qube24 #qube24-contact | 비즈니스 제안 pill | `business-proposal-form.html` | ✅ → coming-soon | OK (임시) |
| qube24 #qube24-contact | Q&A pill | `qube24-qa.html` | ✅ | OK |

**Q&A 연결 정리 (헷갈리기 쉬운 부분):**

| 경로 | 목적지 | 이유 |
|------|--------|------|
| index → Q&A pill | `qa.html` (전체 허브) | WXM 전체 Q&A 목록 |
| qa 허브 → QUBE24 | `qube24-qa.html` | QUBE24 **전용** Q&A |
| qube24 #qube24-contact → Q&A pill | `qube24-qa.html` | 같은 QUBE24 FAQ (허브 거치지 않음) |
| ~~qube24 → qa.html~~ | ❌ 사용 안 함 | 메인 허브로 돌아가면 안 됨 |

### qube24-qa 하단 CTA — 왜 contact로 가나?

`qube24-qa.html` Q&A를 다 읽은 뒤:

```
[CTA 밴드]
  "더 궁금한 점이 있으신가요?"
  [QUBE24 문의하기 →]  →  qube24.html#qube24-contact
  [Q&A 목록으로 →]     →  qa.html (전체 허브로 복귀)
```

- **CTA** = Q&A 아래 "다음에 뭘 할지" 안내하는 밴드
- **문의하기** → qube24 페이지 **문의 섹션**(pill 4개)으로 이동 — 폼 작성 전 유형 선택 단계
- Q&A만 보다가 직접 문의하고 싶을 때 쓰는 **바로가기**

### Q&A 연결 (전체)

| 출발 | 목표 | 상태 |
|------|------|------|
| index Q&A pill | `qa.html` | ✅ |
| qa 허브 QUBE24 | `qube24-qa.html` | ✅ |
| qa 허브 02~05 | `coming-soon.html` | ✅ |

### qube24.html 목표 구조

```
HEADER
HERO — 현재 qube24.html 형식 유지
  ├─ 왼쪽: QUBE24 라벨 + 슬로건 (Better Moment / Better You)
  └─ 오른쪽: 골드 세로바 + 설명 문구 (B2B SYSTEM 소개)
  ※ 와이어프레임 원본의 OAK/DARK/WHITE 큐브 3종 비주얼은 적용 안 함
  ※ HERO 안에 문의 pill 없음 (문의는 #qube24-contact에서)
MID SECTION — QUBE24 B2B SYSTEM (카드 4개 → [E] 세부페이지)
#qube24-contact — QUBE24 CONTACT
  └─ 왼쪽 문구 + 오른쪽 pill 4개
      ├ WXM 운영형 문의    → wxm-managed-form.html
      ├ 파트너 운영형 문의  → partner-managed-form.html
      ├ 비즈니스 제안      → business-proposal-form.html
      └ Q&A               → qube24-qa.html
FOOTER
```

---

# #006 — 전체 페이지 마스터 표

## A. 구현 현황

| 상태 | 수 | 대상 |
|------|-----|------|
| ✅ 구조 OK | 4 | coming-soon, login, qube24, qube24-qa |
| ⚠️ 있음·최종 확인 | 4 | index, contact, qa, seminar-event (폰 실기기) |
| ❌ 미제작 | 22 | #09~#30 (아래 전체 표) |
| **전체 계획** | **30** | KR 기준 30페이지 (CN 포함 시 31) |

> **숫자 정리:** "미제작 14"는 chapter3·4 당장 만들 12개+언어 3개만 센 것.  
> 브랜드 랜딩 4 + 브랜드 Q&A 4를 더하면 **전체 30개**입니다.

## B. 사용자 동선 (QR) — 확인

```
QR → index.html
│
├─ CONTACT BAND [CONTACT US] → contact.html (허브)
│     └─ QUBE24 선택 → qube24.html#qube24-contact (pill 4개)
│           └─ 폼 / qube24-qa
│
├─ CONTACT BAND [Q&A] → qa.html (허브)
│     └─ QUBE24 선택 → qube24-qa.html
│
├─ BRANDS ROADMAP QUBE24 → qube24.html (전체 랜딩)
├─ HEADER SEMINAR & EVENT → seminar-event.html
└─ HEADER LOGIN → login.html
```

**위 두 경로 맞습니다:**
- CONTACT US → contact 허브 → `#qube24-contact` ✅
- Q&A → qa 허브 → `qube24-qa.html` ✅

## C. 연결 마스터 (요약)

| From | Element | To (목표) |
|------|---------|-----------|
| index | ROADMAP 01 | `qube24.html` |
| index | ROADMAP 02~05 | `coming-soon.html` |
| index | CB CONTACT US | `contact.html` |
| index | CB Q&A | `qa.html` |
| contact | QUBE24 | `qube24.html#qube24-contact` |
| qa | QUBE24 | `qube24-qa.html` |
| qube24 | B2B 01~04 | `qube24-*.html` → 미제작 시 coming-soon |
| qube24 | contact pill×4 | forms / `qube24-qa.html` |
| qube24-qa | CTA 문의하기 | `qube24.html#qube24-contact` |
| seminar | INQUIRY pill×3 | apply/proposal html → 미제작 시 coming-soon |

---

# push 전략 (검토용 코멘트)

## 질문: 모바일을 먼저 push해야 하나?

**결론: 두 가지 선택지가 있습니다. 구조를 먼저 잡고 싶다면 1차 push를 미루는 편이 낫습니다.**

### 선택지 A — 모바일 먼저 (기존 STEP 1)

| 장점 | 단점 |
|------|------|
| QR로 들어온 **폰 사용자가 바로** 레이아웃 개선 | 곧 네비(ROADMAP→BRANDS), qube24 구조 바꾸면 **또 push** |
| 변경 범위 작음 (3파일) | 구조 버그(qube24 잘못된 링크)는 그대로 |

**적합:** "폰에서 당장 깨지는 것만 빨리 고치고 싶다"

### 선택지 B — 구조 먼저, 모바일은 묶어서 1회 push (권장)

| 순서 | 작업 | 1차 push에 포함 |
|------|------|----------------|
| 1 | qube24 `#qube24-contact` pill 4개 + 링크 수정 | ✅ |
| 2 | HEADER 네비 BRANDS + SEMINAR & EVENT + CONTACT US 통일 | ✅ |
| 3 | 모바일 index/qa/contact | ✅ |
| 4 | FOOTER 문구·모바일 3줄 통일 | ✅ |

| 장점 | 단점 |
|------|------|
| **push 1회**로 QR 체감 대부분 해결 | 작업량 많아 첫 push까지 시간 더 걸림 |
| 문서 확정안과 live가 한 번에 맞음 | — |

**적합:** "매번 push하기 싫고, 문서대로 한 번에 맞추고 싶다" ← **현재 상황에 더 맞음**

### 선택지 C — 단계별 push (기존 STEP 1→7)

문서 작업 순서 그대로 여러 번 push. 변경 이력 추적은 쉽지만 배포 횟수 많음.

---

## 권장 push 플랜 (v2)

| 차수 | 내용 | 파일 예시 |
|------|------|----------|
| **1차** | 모바일 + qube24 pill + HEADER/FOOTER 통일 | index, qa, contact, qube24, (전 페이지 header) |
| **2차** | HERO 100vh-header | index, qube24, seminar |
| **3차** | MID 셸 + [D][E] 신규 페이지 | 단계별 |

### 1차 push 전 체크리스트

- [x] `qa.html` 소스에 `wxm-mobile-guaranteed` 존재
- [x] `mobile.css?v=7` 로드 (index, qa, contact)
- [x] qube24 Q&A pill → `qube24-qa.html` (not qa.html)
- [x] qube24 pill 4개 (운영형·파트너·제안·Q&A)
- [x] qube24·seminar 액션밴드 pill 크기 index 규격 (`common.css`)
- [x] qube24 MID 크기 index roadmap 규격
- [x] seminar HERO: qube24 랜딩 셸 + index 슬로건
- [x] HEADER: ABOUT / BRANDS / SEMINAR & EVENT / CONTACT US / LOGIN
- [x] 모바일 footer 3줄+© (회사·언어 숨김)
- [x] footer EN/JP/CN → `coming-soon.html`
- [x] coming-soon·login `page-type-c` 한 화면
- [x] coming-soon 설명문 QUBE24 문구 제거
- [x] 와이어프레임·SITE-MASTER v5 동기화
- [ ] 폰 실기기에서 index·qa·contact·qube24·seminar 최종 확인
- [ ] 사용자 **「push 해줘」** 승인 후 배포

---

# #007 — 디자인 시스템

> 구현 파일: **`css/common.css`** (전 페이지 `<link rel="stylesheet" href="css/common.css">`)  
> 페이지별 `<style>` = common 이후 로드, **덮어쓰기·추가만**

## 폰트 — Pretendard 확정 (SUIT 비교)

| | **Pretendard** ✅ 확정 | **SUIT** |
|---|---------------------|----------|
| 품질 | 둘 다 한글 UI용 **최상급** | 동급 |
| 체감 차이 | **거의 없음** (둘 다 깔끔한 산세리프) | Pretendard가 약간 둥글고, SUIT가 약간 각짐 |
| Figtree 궁합 | Inter 계열 → **Figtree와 잘 맞음** | 동일하게 무난 |
| 이 프로젝트 | index·qube24·seminar **이미 적용 중** | 전환 시 전 페이지 교체 비용만 발생 |
| CDN | `cdn.jsdelivr.net/.../pretendard.css` | `cdn.jsdelivr.net/gh/sunn-us/SUIT/fonts/...` |

**결론:** SUIT로 바꿔도 나쁘지 않지만 **체감 차이 미미** → 이미 쓰는 **Pretendard 유지**.

### 폰트 용도 규칙

| 용도 | 폰트 | CSS 변수 / 클래스 |
|------|------|------------------|
| 영문 라벨·네비·숫자·pill | **Figtree** | `var(--font-display)` / `.font-display` |
| 한글 제목·본문·설명 | **Pretendard** | `var(--font-body)` / `.font-body` |
| body 기본 | Figtree → Pretendard fallback | `font-family: var(--font-display)` |

```html
<!-- 전 페이지 head 공통 -->
<link href="...Figtree..." rel="stylesheet">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css">
<link rel="stylesheet" href="css/common.css">
```

---

## 컬러 토큰 (`:root`)

| 토큰 | 값 | 용도 |
|------|-----|------|
| `--g` | `#1F4037` | 브랜드 그린 — 제목·pill·카드 ON |
| `--gh` | `#102A24` | 다크 그린 — HEADER·FOOTER·PAGE HEADER |
| `--cream` | `#F4F0E8` | 페이지 배경 |
| `--card` | `#F8F5EE` | 카드·폼 배경 |
| `--gold` | `#C9A978` | 섹션 라벨·골드 악센트 |
| `--gold-soft` | `#D4B98D` | HERO kicker 등 |
| `--text` | `#171815` | 본문 |
| `--muted` | `#5F5A52` | 보조·Q&A 답변 |
| `--dis` | `#B4B2A9` | 비활성(ROADMAP OFF) |
| `--bc` | `rgba(201,169,120,0.25)` | 구분선 |
| `--pill-border` | `rgba(201,169,120,0.68)` | 액션밴드 pill 테두리 |
| `--pill-bg` | `rgba(244,240,232,0.18)` | pill 배경 |
| `--cream-text` | `#F4F0E8` | 다크 배경 위 텍스트 |

---

## 레이아웃 토큰

| 토큰 | 값 | 용도 |
|------|-----|------|
| `--max-site` | `1400px` | HEADER·FOOTER·PAGE HEADER |
| `--max-content` | `860px` | 허브·Q&A 본문 |
| `--header-h` | `60px` | HEADER 높이 (모바일 48px는 페이지별 override) |

---

## 고정 컴포넌트 (common.css)

| 컴포넌트 | 클래스 | 페이지 |
|----------|--------|--------|
| HEADER | `.site-header`, `.nav-link`, `.nav-pill` | 전체 |
| FOOTER | `.site-footer`, `.ft-*` | 전체 |
| PAGE HEADER | `.page-header`, `.ph-label`, `.ph-title` | [B][E] |
| [C] 한 화면 | `.page-type-c` | coming-soon, login |
| 섹션 라벨 | `.section-label` | MID·허브·Q&A |
| 허브 pill | `.hub-item` | contact, qa |
| 액션밴드 pill | `.cb-btn`, `.cs-btn`, `.iq-btn` | index, qube24, seminar |
| Q&A 아코디언 | `.qa-item`, `.qa-q`, `.qa-a` | qube24-qa |
| CTA 밴드 (다크) | `.cta-band`, `.cta-btn` | qube24-qa |

---

## 용도별 디자인 — 4종 pill/band

| 유형 | 배경 | 버튼 클래스 | 쓰는 곳 |
|------|------|------------|---------|
| **액션밴드** (밝음) | `--cream` | `.cb-btn` / `.cs-btn` / `.iq-btn` | index, qube24, seminar 하단 |
| **허브 pill** | transparent | `.hub-item` | contact, qa 목록 |
| **CTA 밴드** (어두움) | `--g` | `.cta-btn` | qube24-qa 하단 |
| **Q&A 아코디언** | `--cream` | (클릭 행 `.qa-q`) | qube24-qa 본문 |

### 액션밴드 pill — 공통 수치 (#001과 동일)

- `border-radius: 999px` / min-height 48px(데스크톱) · 44px(모바일)
- 텍스트 13px bold 그린 / 모바일 9~11px
- 데스크톱 3열 그리드 / 모바일 1열(문구 위 + pill 아래 100%)

### MID 카드 색상

→ **#004** select/content 모드 참고

---

## common.css 적용 현황

| 파일 | common.css | 인라인 CSS |
|------|------------|-----------|
| `qa.html`, `contact.html`, `qube24-qa.html`, `login.html` | ✅ 기본 위임 | 모바일·페이지만 |
| `index.html`, `qube24.html`, `seminar-event.html`, `coming-soon.html` | ✅ 링크 추가 | HERO·MID 등 페이지 전용 유지 |

---

# 부록

| 항목 | 값 |
|------|-----|
| Git remote | `origin` → `jaymtwoo-ai.github.io` |
| 모바일 CSS | `css/mobile.css`, `css/mobile-critical.css` |
| 공통 디자인 | `css/common.css` (#007) · `.page-type-c` [C] |
| **와이어프레임 (최신)** | `docs/WXM-WIREFRAME-BROWSER.html` (데스크톱) |
| | `docs/WXM-WIREFRAME-MOBILE.html` (모바일) |
| 마스터 스펙 | `docs/SITE-MASTER.md` (본 문서 v5) |
| 구 와이어프레임 | `docs/WXM-CURRENT-WIREFRAME.html` (참고용·통합본) |

---

*push는 승인 후 진행. 수정 요청은 `#001`~`#007` 번호로 지시해 주세요.*
