# GSAP Showcase

브랜딩·에이전시 웹사이트(BlueGarage, Awwwards 류)에서 자주 쓰이는 **GSAP / ScrollTrigger 인터랙션 18종** 모음.

## 실행 방법
- `index.html`을 더블클릭 → 갤러리에서 원하는 데모 선택.
- 각 데모는 **CDN만 쓰는 독립 HTML** → 빌드/설치 없이 브라우저에서 바로 동작.
- 인터넷 연결 필요 (GSAP은 cdnjs에서 로드, 이미지는 picsum.photos).

## 데모 목록

### 핵심 패턴 (Core)
| # | 데모 | 핵심 기법 |
|---|------|-----------|
| 01 | Pin + Scrub Hero | `pin` + `scrub` 타임라인 — 고정한 채 스크롤 진행도로 텍스트 전환 |
| 02 | Height Scrub Accordion | `height: 0 → auto` 트윈을 `scrub` (BlueGarage "WHAT WE BUILD" 실측 재현) |
| 03 | Text Reveal | `overflow:hidden` 마스크 + `yPercent` 라인 등장 |
| 04 | Horizontal Scroll | 세로 스크롤 → `xPercent` 가로 이동, `pin` + `end: "+="` |
| 05 | Parallax Layers | 레이어별 `data-speed`로 `yPercent` 속도차 |
| 06 | Pinned Stacking Cards | CSS `sticky` + 다음 카드 진입 시 `scale` 다운 |
| 07 | Scroll Progress | `ScrollTrigger` `onUpdate`의 `self.progress`를 바/링에 매핑 |

### 텍스트 연출 (Typography)
| # | 데모 | 핵심 기법 |
|---|------|-----------|
| 08 | Split Text | 글자를 `<span>`으로 분할 후 `stagger` (유료 SplitText 없이) |
| 09 | Marquee | 2벌 복제 무한 루프 + `getVelocity()`로 `timeScale` 제어 |
| 10 | Word Fill | 단어 분할 + `pin` 구간에서 `color` stagger를 `scrub` |

### 이미지 / 미디어 (Media)
| # | 데모 | 핵심 기법 |
|---|------|-----------|
| 11 | Clip-path Reveal | `clip-path: inset()` + `scale` 동시 트윈 |
| 12 | Image Parallax Grid | 이미지를 컨테이너보다 크게 두고 `yPercent` 흐름 |
| 13 | Image Sequence | 캔버스 `drawImage`를 프레임 인덱스로 `scrub` (Apple AirPods 식) |
| 14 | Header Color Invert | 섹션 `data-theme`를 `onToggle`로 헤더 `color` 전환 |

### 고급 레이아웃 (Advanced)
| # | 데모 | 핵심 기법 |
|---|------|-----------|
| 15 | Horizontal Gallery | 가로 트랙 + `containerAnimation`으로 항목별 시차 |
| 16 | Flip Layout | `Flip.getState()` → DOM 변경 → `Flip.from()` 자동 보간 |
| 17 | Lenis Smooth Scroll | Lenis(무료) + `gsap.ticker`/`ScrollTrigger.update` 동기화 |
| 18 | ScrollTrigger.batch | 동시에 보이는 요소를 묶어 한 번에 stagger (대형 그리드) |

## 알아둘 점

- **ScrollSmoother는 유료**: BlueGarage가 쓰는 GSAP `ScrollSmoother`(관성 스크롤)는 GSAP Business 멤버십 전용입니다. 무료로 같은 느낌을 내려면 **17번 Lenis** 조합을 쓰세요.
- **`height: 'auto'` 트윈**은 GSAP가 픽셀로 자동 환산해 줍니다. CSS transition만으로는 불가능 — 02번 아코디언의 핵심.
- **React에서 쓸 때**는 `@gsap/react`의 `useGSAP({ scope })`로 감싸면 cleanup/revert가 자동 처리됩니다.
- **이미지 로드 후** 레이아웃이 바뀌면 트리거 위치가 틀어집니다 → `ScrollTrigger.refresh()` 호출.
- **`markers: true`**를 ScrollTrigger에 추가하면 start/end 위치가 화면에 표시되어 디버깅이 쉽습니다.

## 버전
- GSAP 3.12.5 (gsap, ScrollTrigger, Flip)
- Lenis 1.1.13
