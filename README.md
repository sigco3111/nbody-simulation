# 🌌 nbody-simulation

> HTML5 Canvas API 기반 N체 중력 시뮬레이션 — 50개의 형광색 천체가 어두운 우주에서 서로의 중력으로 궤도를 그리고, 클릭으로 블랙홀을 생성할 수 있습니다.

50개의 형광색 천체가 서로의 중력에 이끌려 복잡한 궤도를 그리고, 각 천체가 지나간 자리에는 **긴 발광 잔상(Trail)**이 남습니다. **마우스를 클릭하면 새로운 블랙홀**이 생성되어 주변 천체들을 강력하게 빨아들이고, 흡수 순간에는 제트·충격파·렌즈링·도플러 디스크 같은 시각 효과가 폭발합니다. 단일 HTML, 의존성 0.

[🇰🇷 한국어 (기본)](#) · [🇺🇸 English](#-english)

---

## 🎬 라이브 데모 (Live Demo)

> **👉 [https://nbody-simulation-five.vercel.app/](https://nbody-simulation-five.vercel.app/)** — 브라우저에서 바로 실행

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-7C3AED?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Fnbody--simulation-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/nbody-simulation) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-0-9CA3AF?style=flat-square) |

### 🎮 빠른 사용법
1. 위 데모 링크 클릭 → 브라우저에서 페이지 열기
2. **천체들이 서로의 중력으로 복잡한 궤도를 그리는 것을 관찰** — 잔상이 곡선을 만듭니다
3. **마우스 클릭** — 클릭한 위치에 블랙홀 생성, 주변 천체 흡입
4. **R** — 전체 리셋 · **Space** — 일시정지 · **H** — HUD 토글

---

## 🤖 생성 정보 (Attribution)

이 프로젝트의 코드는 아래 모델과 프롬프트를 이용해 **자동으로 생성**되었습니다.

| 항목 | 값 |
|---|---|
| **모델** | MiniMax-M3 |
| **실행 환경** | OpenCode CLI |
| **저장소** | [`sigco3111/nbody-simulation`](https://github.com/sigco3111/nbody-simulation) |
| **라이선스** | MIT |
| **의존성** | 없음 (Vanilla JS, 단일 HTML) |

### 📝 사용된 프롬프트 (원문)

```
HTML5 Canvas를 사용하여 어두운 우주 공간에서 서로 다른 질량을 가진 50개의 형광색 천체들이
서로의 중력에 이끌려(N-body simulation) 복잡한 궤도를 그리며 회전하는데,
각 천체가 지나간 자리에 긴 잔상(Trail)이 남아 아름다운 곡선을 만들고
마우스로 클릭하면 새로운 블랙홀이 생성되어 주변 천체들을 강력하게 빨아들이는
고성능 물리학 시뮬레이션을 단일 파일로 만들어줘.

Implementation Advice: Use HTML5 Canvas. For the "Trails" effect,
instead of clearing the canvas completely each frame (ctx.clearRect),
draw a semi-transparent black rectangle
(ctx.fillStyle = 'rgba(0,0,0,0.1)'; ctx.fillRect(...)) to create
a fading trail effect. 모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.
```

---

## ✨ 주요 특징 (Features)

- 🌌 **50개 N-body 시뮬레이션** — 서로 다른 질량의 천체가 서로의 중력으로 상호작용
- 🔭 **Velocity Verlet 적분** — symplectic 적분으로 에너지를 안정적으로 보존
- ✨ **가산 발광 잔상** — `rgba(0,0,0,0.06)` 페이드로 형광 곡선 생성
- 🕳️ **클릭 → 블랙홀** — 5N 흡입 + 질량 누적 + 제트·충격파·렌즈링·도플러 디스크
- 💫 **중심 앵커 질량** — 화면 중앙에 고정 질량 → 50체가 안정적으로 공존
- ⚡ **60fps 안정** — `requestAnimationFrame` 루프 + DPR 캔버스
- 🌌 **우주 배경 FX** — 220개 트윙클 별 + 5개 네뷸라 + 비네팅
- 📦 **단일 HTML** — 외부 의존성 0개, 파일 하나만 열면 실행
- 🔒 **온디바이스** — 모든 물리·렌더링이 브라우저 안에서 처리됨

---

## 🚀 실행 방법 (Quick Start)

### 방법 1: 그냥 브라우저로 열기 (가장 간단)
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### 방법 2: 로컬 서버 (권장)
```bash
python3 -m http.server 8000
# → http://localhost:8000
```

### 방법 3: 라이브 데모 (Vercel)
이미 배포되어 있습니다 → [https://nbody-simulation-five.vercel.app/](https://nbody-simulation-five.vercel.app/)

---

## 🎮 조작법 (Controls)

| 입력 | 효과 |
|---|---|
| **마우스 클릭** | 클릭한 위치에 블랙홀 생성 (질량 누적, 흡입력 비례) |
| **R** | 모든 천체 + 블랙홀 리셋 |
| **Space** | 일시정지 / 재개 |
| **H** | HUD(물리 정보·체 수) 토글 |
| **ESC** (일부 브라우저) | 풀스크린 토글 |

---

## 🛠️ 기술 스택 (Tech Stack)

| 영역 | 사용 기술 |
|---|---|
| **렌더링** | HTML5 Canvas 2D Context (DPR-aware) |
| **물리** | Velocity Verlet 적분 + Plummer softening |
| **충돌** | 비탄성 합체 (운동량 보존) |
| **블랙홀 FX** | 제트 입자 + 충격파 + 렌즈링 + 도플러 디스크 |
| **색상** | 16색 형광 팔레트 + 가산 합성 (`globalCompositeOperation = 'lighter'`) |
| **루프** | `requestAnimationFrame` |
| **의존성** | 없음 (Vanilla JS) |

---

## 📂 프로젝트 구조

```
nbody-simulation/
├── index.html         # 단일 HTML (모든 코드 포함)
├── README.md          # 한국어 (기본)
└── LICENSE            # MIT
```

---

## 🎨 디자인 결정 (Design Choices)

브레인스토밍 단계에서 내린 결정 6가지:

| 결정 포인트 | 선택 | 이유 |
|---|---|---|
| **물리 적분기** | Velocity Verlet (symplectic) | Euler 대비 에너지 보존 우수, 50체 N-body에 충분한 안정성 |
| **충돌 처리** | 완전 비탄성 합체 (운동량 보정) | 직관적 — 가벼운 천체가 무거운 천체에 합쳐져 클러스터 형성 |
| **잔상 기법** | `fillRect(rgba(0,0,0,0.06))` 매 프레임 | `clearRect` 대신 반투명 사각형 → 자연스러운 형광 페이드 |
| **블랙홀 흡입** | 5N 가속도 + 질량 누적 + 제트/충격파 FX | 단순 흡입이 아닌 "사건의 지평선 통과" 느낌 강조 |
| **안정성** | 중심 앵커 질량 (1500) 고정 | 50체가 우주 공간으로 흩어지지 않고 궤도 영역에 머무름 |
| **시각 FX** | 가산 합성 + 렌즈링 + 도플러 디스크 | 형광 색상 겹침으로 진짜 발광감, 상대론적 시각 효과 |

### 직접 커스터마이즈하고 싶다면

`index.html` 상단에서 다음 상수를 조정하면 분위기를 바꿀 수 있어요:

```js
const CONFIG = {
  BODY_COUNT:       50,        // 천체 수 (10~200 권장)
  G:                0.5,       // 중력 상수 (클수록 끌림 강함)
  TRAIL_FADE:       0.06,      // 잔상 페이드 알파 (작을수록 길게 남음)
  MAX_SPEED:        8,         // 천체 속도 상한 (블랙홀 과열 방지)
  BLACK_HOLE_PULL:  5,         // 클릭 흡입력
  SOFTENING:        20,        // Plummer softening ε (충돌 특이점 회피)
  BH_BASE_MASS:     5000,      // 블랙홀 초기 질량
  CENTRAL_MASS:     1500,      // 중심 앵커 질량 (궤도 안정화)
  USE_ADDITIVE_GLOW: true,     // 'lighter' 합성으로 형광 발광
  LENSING_RINGS:    true,      // 블랙홀 주변 렌즈링 (arc)
  DOPPLER_DISK:     true,      // 강착원반 상대론적 색편이
  NEBULA_ENABLED:   true,      // 배경 네뷸라 활성화
  // ... 더 많은 옵션은 코드 내 주석 참조
};
```

고급 사용자용: 적분 루프를 RK4로 바꾸거나, Barnes-Hut 트리를 추가해 200~500체로 확장해볼 수도 있어요.

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

이 프로젝트는 [OpenCode CLI](https://opencode.ai) 환경의 **MiniMax-M3** 모델로 생성되었습니다. 프롬프트 엔지니어링과 디자인 결정은 저장소 소유자가 직접 수행했습니다.

---

## 🇺🇸 English

### Overview

A high-performance **N-body gravity simulation** rendered on HTML5 Canvas.
**50 fluorescent celestial bodies** of varying masses orbit one another,
leaving long glowing trails in dark space. **Click anywhere** to forge a
**black hole** that devours surrounding bodies — with jet particles, shockwaves,
lensing rings, and a relativistic Doppler accretion disk.

A single HTML file. Zero dependencies. Open it in a browser and it runs.

### Features

- 50-body N-body simulation with mutual gravity
- Velocity Verlet integrator (symplectic, energy-stable)
- Additive-blend fluorescent trails via `rgba(0,0,0,0.06)` fade
- Click-to-spawn black holes with mass accumulation + 5N pull
- Jet particles, shockwaves, lensing arcs, Doppler disk
- Central anchor mass (1500) for orbital stability
- 220 twinkling stars + 5 nebulae + corner vignette
- Single `index.html`, 60fps, on-device

### Controls

| Input | Effect |
|---|---|
| **Click** | Spawn black hole (mass stacks with each click) |
| **R** | Reset all bodies & black holes |
| **Space** | Pause / resume |
| **H** | Toggle HUD |

### Quick Start

```bash
open index.html                           # macOS
# or
python3 -m http.server 8000               # local server
# or
# Live demo: https://nbody-simulation-five.vercel.app/
```

### Design Decisions

| Decision | Choice | Why |
|---|---|---|
| Integrator | **Velocity Verlet** | Symplectic — preserves energy, 50-body stable |
| Collisions | **Inelastic merge** w/ momentum conservation | Forms visible clusters, intuitive |
| Trails | `fillRect(rgba(0,0,0,0.06))` per frame | Cleaner glow than `clearRect` |
| Black hole | 5N pull + mass stacking + FX | Feels like an event horizon, not a magnet |
| Stability | Central anchor mass (1500) | Prevents drift out of frame |
| Visuals | Additive blend + lensing + Doppler disk | Real fluorescence + relativistic feel |

### Customize

Edit the `CONFIG` object at the top of `index.html`:

```js
const CONFIG = {
  BODY_COUNT:       50,
  G:                0.5,
  TRAIL_FADE:       0.06,
  MAX_SPEED:        8,
  BLACK_HOLE_PULL:  5,
  SOFTENING:        20,
  BH_BASE_MASS:     5000,
  CENTRAL_MASS:     1500,
  USE_ADDITIVE_GLOW: true,
  LENSING_RINGS:    true,
  DOPPLER_DISK:     true,
  NEBULA_ENABLED:   true,
};
```

### License

MIT © 2026 sigco3111

Built with [OpenCode CLI](https://opencode.ai) + **MiniMax-M3**.
