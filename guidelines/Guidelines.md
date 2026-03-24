# YOLO Bring IT - 웹 게임 애플리케이션 가이드라인

## 📱 해상도 최적화 기준

### 주요 타겟 해상도
- **모바일**: 320px × 568px (iPhone SE 기준)
- **데스크톱**: 1280px × 1080px (표준 데스크톱)

### rem 기반 단위 시스템
```css
/* 기본 설정: 1rem = 14px (globals.css에서 정의) */
/* 모든 크기는 rem 단위로 정의하여 접근성과 일관성 확보 */

/* 기본 spacing scale */
0.25rem  /* 4px equivalent - 미세 간격 */
0.5rem   /* 7px equivalent - 작은 간격 */
0.75rem  /* 10.5px equivalent - 보통 간격 */
1rem     /* 14px equivalent - 기본 단위 */
1.25rem  /* 17.5px equivalent - 중간 크기 */
1.5rem   /* 21px equivalent - 큰 간격 */
2rem     /* 28px equivalent - 더 큰 간격 */
3rem     /* 42px equivalent - 큰 요소 */
4rem     /* 56px equivalent - 매우 큰 요소 */
```

### 반응형 브레이크포인트
```css
/* Tailwind V4 기본 브레이크포인트 활용 */
/* Base: ~640px (모바일 우선) */
sm: 40rem    /* 640px - 작은 태블릿 */
md: 48rem    /* 768px - 태블릿 */
lg: 64rem    /* 1024px - 작은 데스크톱 */
xl: 80rem    /* 1280px - 표준 데스크톱 */
2xl: 96rem   /* 1536px - 대형 데스크톱 */
```

## 🎨 디자인 시스템

### 색상 팔레트
- **Primary Blue**: `#6dc4e8` (메인 브랜드 컬러)
- **Secondary Blue**: `#5ab4d8` (보조 브랜드 컬러)
- **Success Green**: `#10b981` (성공, 연결 상태)
- **Error Red**: `#ef4444` (오류, 실패 상태)
- **Warning Yellow**: `#f59e0b` (경고, 대기 상태)

### 타이포그래피 (rem 기반)
- **게임 제목**: `font-family: 'Bungee_Shade:Regular'`
- **UI 텍스트**: `font-family: 'BM_HANNA_TTF:Regular'`
- **기본 폰트 크기**: `1rem` (14px, globals.css에서 설정)

```css
/* Tailwind 텍스트 클래스와 rem 매핑 */
text-xs:   0.75rem   /* 10.5px */
text-sm:   0.875rem  /* 12.25px */
text-base: 1rem      /* 14px - 기본 */
text-lg:   1.125rem  /* 15.75px */
text-xl:   1.25rem   /* 17.5px */
text-2xl:  1.5rem    /* 21px */
text-3xl:  1.875rem  /* 26.25px */
text-4xl:  2.25rem   /* 31.5px */
```

### 컴포넌트 크기 시스템 (rem)
```css
/* 터치 친화적 최소 크기 */
--min-touch-target: 2.75rem;  /* 44px equivalent */

/* 버튼 크기 스케일 */
--btn-sm: 2rem;      /* 28px - 작은 버튼 */
--btn-md: 2.5rem;    /* 35px - 기본 버튼 */
--btn-lg: 3rem;      /* 42px - 큰 버튼 */
--btn-xl: 3.5rem;    /* 49px - 매우 큰 버튼 */

/* 아이콘 크기 스케일 */
--icon-xs: 1rem;     /* 14px */
--icon-sm: 1.25rem;  /* 17.5px */
--icon-md: 1.5rem;   /* 21px */
--icon-lg: 2rem;     /* 28px */
--icon-xl: 2.5rem;   /* 35px */
```

### 애니메이션 원칙
- **Duration**: 0.3s (빠른 피드백), 0.6s (표준), 1.2s (강조)
- **Easing**: `[0.23, 1, 0.32, 1]` (부드러운 커스텀 곡선)
- **Scale Effects**: `1.05` (호버), `0.95` (클릭)

## 🏗️ 컴포넌트 구조

### 레이아웃 원칙
- **Mobile First**: 모바일 우선 반응형 설계
- **rem 기반**: 모든 크기를 rem으로 정의하여 접근성 확보
- **Progressive Enhancement**: 큰 화면에서 기능 추가
- **Fixed Viewport**: 게임 화면은 스크롤 없는 전체 화면

### 버튼 설계 (rem)
```typescript
// 기본 버튼 크기 (터치 친화적)
className="w-8 h-8 sm:w-10 sm:h-10 lg:w-12 lg:h-12"
// rem equivalent: w-[2rem] h-[2rem] sm:w-[2.5rem] sm:h-[2.5rem] lg:w-[3rem] lg:h-[3rem]

// 텍스트 크기
className="text-sm sm:text-base lg:text-lg xl:text-xl"

// 패딩
className="p-3 sm:p-4 lg:p-6"
// rem equivalent: p-[0.75rem] sm:p-[1rem] lg:p-[1.5rem]
```

### 카드 컴포넌트 (rem)
```typescript
// 배경과 테두리
className="bg-gradient-to-br from-white/80 to-white/60 dark:from-gray-800/80 dark:to-gray-700/60 backdrop-blur-sm rounded-2xl border-2 border-[#6dc4e8]/30 shadow-lg"

// 내부 패딩 (rem 기반)
className="p-4 sm:p-6 lg:p-8"
// rem equivalent: p-[1rem] sm:p-[1.5rem] lg:p-[2rem]
```

### 반응형 스페이싱 시스템
```typescript
// 간격 (gap)
className="gap-2 sm:gap-3 lg:gap-4 xl:gap-6"
// rem equivalent: gap-[0.5rem] sm:gap-[0.75rem] lg:gap-[1rem] xl:gap-[1.5rem]

// 마진
className="m-2 sm:m-4 lg:m-6 xl:m-8"
// rem equivalent: m-[0.5rem] sm:m-[1rem] lg:m-[1.5rem] xl:m-[2rem]

// 높이 (컨테이너)
className="h-16 sm:h-20 lg:h-24 xl:h-32"
// rem equivalent: h-[4rem] sm:h-[5rem] lg:h-[6rem] xl:h-[8rem]
```

## 🎮 게임 플로우

### 화면 전환 구조
1. **Landing** → Login/Register → **Lobby**
2. **Lobby** → GameJoin → GameWaitingRoom → **Game**
3. **Game** → RoundResult → **Game** (7라운드) → FinalResult → **Lobby**

### 상태 관리
- `currentScreen`: 현재 화면 상태
- `gameData`: 게임 진행 데이터 (플레이어, 점수, 라운드)
- `isLoggedIn`: 인증 상태 (개발용으로 true 기본값)

## 🔧 기술적 가이드라인

### rem 사용 원칙
```typescript
// 픽셀 단위 사용 금지
style={{ width: '240px', height: '180px' }}

// rem 단위 또는 Tailwind 클래스 사용
className="w-60 h-45" // Tailwind 클래스
style={{ width: '15rem', height: '11.25rem' }} // 직접 rem 사용
```

### 반응형 패턴 (rem 기반)
```typescript
// 크기: 모바일 → 데스크톱 (rem 기반)
className="text-sm sm:text-base md:text-lg lg:text-xl xl:text-2xl"
className="p-3 sm:p-4 md:p-5 lg:p-6 xl:p-8"
className="w-8 h-8 sm:w-10 sm:h-10 md:w-12 md:h-12 lg:w-14 lg:h-14"

// 간격 시스템
className="space-y-2 sm:space-y-3 md:space-y-4 lg:space-y-6"
className="gap-1 sm:gap-2 md:gap-3 lg:gap-4 xl:gap-6"
```

### Import 구조
```typescript
// 외부 라이브러리
import { motion, AnimatePresence } from "framer-motion";

// 컴포넌트
import { ComponentName } from "./components/ComponentName";

// 이미지 및 에셋
import imgName from "figma:asset/[hash].png";
```

## 📋 컴포넌트별 특수 요구사항

### LobbyScreen (rem 최적화)
- **데스크톱**: 3컬럼 그리드 (사이드바 + 메인 + 오른쪽 패널)
- **모바일**: 세로 스택, 오버레이 사이드바
- **웹캠 크기**: `h-32 sm:h-36 lg:h-44 xl:h-52` (rem 기반)
- **버튼 크기**: `w-8 h-8 sm:w-10 sm:h-10 lg:w-12 lg:h-12`

### GameJoinScreen (rem 최적화)
- **모바일**: 세로 배치, `h-32 sm:h-36` 가로형 카드
- **데스크톱**: 가로 배치, `aspect-square` 정사각형 카드
- **텍스트**: `text-lg sm:text-xl md:text-3xl lg:text-4xl xl:text-5xl`

### GameWaitingRoom (rem 최적화)
- **플레이어 그리드**: 2x3 배치, `w-20 h-20 sm:w-24 sm:h-24 lg:w-28 lg:h-28`
- **채팅 높이**: `h-80` (20rem) 고정
- **입력창**: `h-12` (3rem) 높이

## 🚀 성능 최적화

### rem 기반 최적화
- **일관된 스케일링**: rem 사용으로 모든 요소가 proportional하게 확대/축소
- **접근성**: 사용자 폰트 크기 설정 자동 반영
- **계산 효율성**: 브라우저 최적화된 rem 계산

### 애니메이션 최적화
- **GPU 가속**: `transform`, `opacity` 속성 우선 사용
- **rem 기반 애니메이션**: 일관된 스케일링 보장

## 📱 접근성 (Accessibility)

### 터치 인터페이스 (rem)
- **최소 터치 영역**: `2.75rem × 2.75rem` (44px equivalent)
- **충분한 여백**: `0.5rem` 이상 간격
- **피드백 제공**: 모든 인터랙션에 시각/햅틱 피드백

### 사용자 설정 존중
- **폰트 크기**: rem 사용으로 사용자 설정 자동 반영
- **확대/축소**: 모든 UI 요소가 proportional하게 스케일링
- **고대비 모드**: 색상 대비 WCAG 2.1 AA 기준 준수

### 키보드 네비게이션
- **Tab 순서**: 논리적 포커스 이동
- **포커스 표시**: `ring-2 ring-offset-2` 명확한 포커스 링

---

이 rem 기반 가이드라인을 따라 접근성이 뛰어나고 일관성 있는 웹 게임 애플리케이션을 개발하세요! 🎮✨