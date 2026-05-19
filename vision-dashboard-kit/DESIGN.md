# 비전코칭 대시보드 — 디자인 시스템

> dashboard.html에 적용된 디자인 토큰·컴포넌트·애니메이션 명세

---

## 컬러 체계

### 배경 계층
```
--bg-void:     #0f1117     (보이드)
--bg-primary:  #141926     (메인 배경)
--bg-raised:   #1a2035     (서피스/네비/사이드바)
--surface-1:   rgba(255,255,255, 0.06)  (글래스 카드)
--surface-2:   rgba(255,255,255, 0.09)  (호버)
--surface-3:   rgba(255,255,255, 0.13)  (활성)
```

### 텍스트 계층
```
--text-primary:   #eef2ff
--text-secondary: #b8c5d6
--text-muted:     #8899ae
--text-disabled:  rgba(255,255,255, 0.30)
```

### 브랜드 악센트 — 스카이블루
```
--accent:       #38bdf8
--accent-dark:  #0284c7
--accent-light: #7dd3fc
--accent-rgb:   56, 189, 248
```

### 시맨틱 4색
```
완료/성공:  #22c55e (그린)
활성/진행:  #3b82f6 (블루)
대기/경고:  #f59e0b (앰버)
에러/위험:  #ef4444 (레드)
```

### 8단계 고유 색상
```
1단계: #6366f1 (인디고)    5단계: #06b6d4 (시안)
2단계: #8b5cf6 (퍼플)      6단계: #3b82f6 (블루)
3단계: #ec4899 (핑크)      7단계: #22c55e (그린)
4단계: #f59e0b (앰버)      8단계: #f97316 (오렌지)
```

### 카테고리별 색상
```
Diagnosis:      #6366f1 (인디고)
Core Framework: #8b5cf6 (퍼플)
Applied Toolkit:#ec4899 (핑크)
Prescription:   #22c55e (그린)
Meta-Interview: #f59e0b (앰버)
Data Backbone:  #06b6d4 (시안)
Foresight:      #f97316 (오렌지)
```

---

## 타이포그래피

### 폰트 스택
```css
--font-ui:   'Pretendard Variable', 'Inter', -apple-system, 'Noto Sans KR', sans-serif;
--font-code: 'JetBrains Mono', 'D2Coding', monospace;
```

### CDN
```
https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/variable/pretendardvariable.min.css
```

### 스케일
```
히어로 타이틀: clamp(30px, 5.5vw, 48px)  weight: 800
섹션 헤더:    14~15px                       weight: 600~700
스킬 라벨:    11px                          weight: 400~500
캡션/카운트:  9~10px                        weight: 600~700
```

### 한글 최적화
```css
word-break: keep-all;
-webkit-font-smoothing: antialiased;
```

---

## 스페이싱 (4px 기반)

```
--space-1: 4px     --space-2: 8px     --space-3: 12px
--space-4: 16px    --space-5: 20px    --space-6: 24px
--space-8: 32px    --space-10: 40px   --space-12: 48px
```

---

## Border Radius

```
--radius-sm:   6px      (뱃지, 태그, 버튼 내부)
--radius-md:   10px     (버튼, 입력폼, 카드)
--radius-lg:   12px     (글래스 카드, 패널)
--radius-xl:   20px     (모달)
--radius-full: 9999px   (원형 뱃지, 토글)
```

---

## 그림자

```css
--shadow-sm:   0 1px 3px rgba(0,0,0,0.3);
--shadow-md:   0 4px 16px rgba(0,0,0,0.3);
--shadow-lg:   0 8px 32px rgba(0,0,0,0.4);
--shadow-xl:   0 24px 64px rgba(0,0,0,0.5);
--shadow-glow: 0 0 24px rgba(56,189,248, 0.2);
```

---

## 핵심 컴포넌트

### 글래스모피즘 카드
```css
background: rgba(255, 255, 255, 0.03~0.06);
backdrop-filter: blur(16px);
border: 1px solid rgba(255, 255, 255, 0.08~0.12);
border-radius: 12px;
```

### 토글 스위치 (3종)
```
일반 스킬:   32x18px   OFF=surface-3, ON=accent
서브스킬:    24x14px   OFF=surface-3, ON=accent
단계 토글:   32x18px   OFF=surface-3, PARTIAL=accent 40%, ON=accent
```

### 사이드바 컨트롤
```
전체 펼치기/접기 버튼: surface-1 배경, 10px 폰트, 호버 시 surface-2
안내 문구: accent 색상, opacity 0.7, 하단 보더
아코디언 열림 상태: 스킬 토글 시에도 유지 (sbOpenState 객체로 관리)
초기 상태: 모든 단계 접힘
```

### 8단계 빠른 선택 버튼 (3상태)
```
미선택:   rgba(색, 0.04) 배경, rgba(색, 0.15) 보더
부분선택: rgba(색, 0.08) 배경, rgba(색, 0.50) 보더 2px, 카운트 표시
전체선택: rgba(색, 0.15) 배경, 실색 보더 2px, box-shadow 글로우, scale(1.03)
```

### 네비바 버튼
```
코칭 시작 (비활성): rgba(255,255,255,0.08) 배경, text-disabled 색상
코칭 시작 (활성):   linear-gradient(135deg, #0284c7, #38bdf8), 글로우 애니메이션
리셋 버튼:          rgba(239,68,68,0.08) 배경, 레드 보더, 호버 시 강조
```

### 패키지 버튼 (pill)
```
기본: surface-1 배경, border 1px solid
활성: accent 0.15 배경, accent 보더, accent 텍스트
```

### 히어로 줌 버튼 (플로팅)
```
position: fixed, bottom-right
배경: rgba(20,25,38,0.85) + backdrop-filter blur
border-radius: 9999px (pill)
A- / 퍼센트 / A+ 구성
```

---

## 줌 시스템

### 방식: transform scale (전체 페이지 균일)
```css
#zoomWrap {
    transform-origin: top left;
    transform: scale(var);
    width: calc(100% / scale);
}
```

### 컨트롤
```
A- / A+ 버튼: 네비바 (대시보드) + 플로팅 (히어로)
Ctrl + 마우스 휠: window capture 단계에서 선점
범위: 80% ~ 150% (10% 단위)
레벨 표시: 네비바 + 히어로 동기화
```

---

## 애니메이션

### 이징
```css
--ease-spring:   cubic-bezier(0.22, 1, 0.36, 1);
--ease-standard: cubic-bezier(0.4, 0, 0.2, 1);
```

### 키프레임
```css
fadeUp:       translateY(16px) -> 0, opacity 0 -> 1  (0.4s spring)
pulse-glow:   box-shadow 8px -> 24px -> 8px          (2.5s infinite)
border-shift: background-position shift               (6s infinite, 이미지 링)
```

### 접근성
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## 레이아웃

### 전체 구조
```
<body>
  <div id="zoomWrap">         <!-- transform: scale() 줌 래퍼 -->
    <nav class="topnav">      <!-- sticky top, 45px, z-index:50 -->
    <div class="hero-page">   <!-- 첫 화면 -->
    <div class="dashboard-page"> <!-- 대시보드 -->
  </div>
</body>
```

### 대시보드 페이지 (2열)
```
┌─ 네비바 (sticky top, 45px, z-index:50) ──────────────┐
│ 로고|홈|스킬|spacer|줌|디바이스|API|리셋|선택N개|코칭시작 │
└───────────────────────────────────────────────────────┘
┌─ 사이드바 (280px, sticky) ─┐ ┌─ 메인 (flex:1, sticky) ──┐
│ 전체 펼치기/접기             │ │ 8단계 빠른 선택            │
│ 안내 문구                    │ │ 추천 패키지                │
│ 개별 스킬 65개               │ │ 선택된 스킬 목록           │
│ (8단계 아코디언+단계토글)     │ │                            │
└──────────────────────────────┘ └───────────────────────────┘
```

### 히어로 페이지 (중앙 정렬)
```
뱃지 -> 타이틀 -> 부제 -> CTA 버튼 -> 이미지 -> API 입력 -> 링크
max-width: 800px, text-align: center
플로팅 줌 버튼 (우측 하단)
```

### 디바이스 프리뷰 (dash-main 전체 적용)
```
Desktop:  제한 없음 (max-width: 1600px)
Tablet:   max-width: 768px, 중앙 정렬, 보더
Phone:    max-width: 390px, 사이드바 세로 배치, 보더
```

### 반응형
```
< 600px:  사이드바 전체폭, 메인 아래로 (세로 배치)
> 600px:  2열 병렬 (사이드바 280px + 메인 flex:1)
> 1200px: 사이드바 280px (변동 없음)
```

---

## 모달

```css
배경: rgba(0,0,0,0.6) + backdrop-filter: blur(6px)
콘텐츠: bg-raised, border, radius-xl, max-width 560~700px
애니메이션: fadeUp (0.4s spring)
```

종류:
- API 키 발급 안내
- 8단계 여정 타임라인
- 결과물 샘플 목록
- 개별 샘플 상세 보기

---

*이 디자인 시스템은 신교수님의 통합 디자인 DNA를 기반으로 합니다.*
