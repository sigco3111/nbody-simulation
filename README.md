# N-Body Gravity Simulation

> 50개의 형광색 천체가 서로의 중력에 이끌려 복잡한 궤도를 그리고, 클릭하면 블랙홀이 생성되어 주변을 빨아들이는 고성능 물리학 시뮬레이션.
> 단일 HTML 파일, 의존성 없음, 캔버스 한 번이면 끝.

![status](https://img.shields.io/badge/status-scaffold-blue)
![model](https://img.shields.io/badge/built%20with-opencode%20%2B%20MiniMax--M3-purple)

---

## 🇰🇷 한국어

### 개요

어두운 우주 공간에서 **서로 다른 질량을 가진 50개의 형광색 천체**들이 서로의 중력에 이끌려
복잡한 궤도를 그리며 회전합니다. 각 천체가 지나간 자리에는 **긴 잔상(Trail)**이 남아
아름다운 곡선을 만들고, **마우스를 클릭하면 새로운 블랙홀**이 생성되어 주변 천체들을
강력하게 빨아들입니다.

### 구현 결정 사항 (How)

| 결정 | 선택 | 이유 |
| --- | --- | --- |
| 렌더링 | **HTML5 Canvas 2D** | 단일 파일·의존성 0·고성능 잔상 FX에 최적 |
| 잔상 효과 | `ctx.fillRect(... rgba(0,0,0,0.1))` 매 프레임 | `clearRect` 대신 반투명 검정 사각형으로 페이드 |
| 물리 적분 | **Velocity Verlet** (p-로 symplectic) | 에너지 보존이 Euler보다 안정적, 50체 N-body 충분 |
| 충돌 | 완전 비탄성 합체(conservation 보정) | 직관적이면서 시각적으로 만족스러운 클러스터 형성 |
| 단일 파일 | 모든 코드를 1개 `index.html`에 인라인 | CDN 외부 의존성 0, 오프라인 동작 |
| 입력 | `mousedown` / `touchstart` — 매 프레임 5N 가속도 흡입 | 블랙홀은 흡입 + 질량 누적 |

### 사용법

```bash
# 1) 저장소를 클론하고
git clone https://github.com/sigco3111/nbody-simulation.git
cd nbody-simulation

# 2) index.html을 브라우저로 열기 (또는)
open index.html   # macOS

# 3) 호스팅이 필요하면
python3 -m http.server 8000
# → http://localhost:8000
```

### 조작

- **클릭** — 클릭한 위치에 블랙홀 생성 (질량은 누적됨, 흡입력 비례)
- **드래그** — 블랙홀 위치 미세 이동 (옵션)
- **`R`** — 모든 천체 리셋, 블랙홀 초기화
- **`스페이스바`** — 일시정지 / 재개
- **`H`** — HUD(물리 정보·체 수) 토글

### 커스터마이즈 (코드에서 직접)

`index.html` 상단 `CONFIG` 객체에서 다음을 조정할 수 있습니다.

```js
const CONFIG = {
  BODY_COUNT: 50,          // 천체 수 (10~200 권장)
  G: 0.5,                  // 중력 상수 (클수록 끌림 강함)
  TRAIL_FADE: 0.1,         // 잔상 페이드 알파 (작을수록 길게 남음)
  MAX_SPEED: 6,            // 천체 속도 상한 (블랙홀 과열 방지)
  BLACK_HOLE_PULL: 5,      // 클릭 흡입력
  SOFTENING: 20,           // Plummer softening ε (충돌 특이점 회피)
  // ...
};
```

### 로드맵

- [x] 1단계: 50개 천체 N-body + 잔상
- [x] 2단계: 클릭으로 블랙홀 생성
- [ ] 3단계: 다양한 프리셋 (은하 충돌 / 태양계 / 이중성)
- [ ] 4단계: Web Worker로 적분 오프로드 (대규모 N)

---

## 🇺🇸 English

### Overview

A high-performance N-body gravity simulation rendered on HTML5 Canvas.

**50 fluorescent celestial bodies** with different masses orbit each other,
leaving **long glowing trails** in dark space. **Click anywhere** to spawn a
black hole that devours everything nearby.

### Implementation Notes

| Decision | Choice | Why |
| --- | --- | --- |
| Renderer | **HTML5 Canvas 2D** | Single-file, no deps, fast trail FX |
| Trail effect | `ctx.fillRect(... rgba(0,0,0,0.1))` per frame | Semi-transparent black fades old pixels |
| Integrator | **Velocity Verlet** | Symplectic — preserves energy over Euler |
| Collision | Inelastic merge w/ momentum conservation | Forms visible clusters over time |
| Distribution | All code inlined in `index.html` | Zero CDN, runs offline |
| Input | `mousedown` / `touchstart` → black hole + suction | Click = continuous pull, mass accumulates |

### Controls

- **Click** — Spawn black hole (mass stacks with each click)
- **R** — Reset bodies & black holes
- **Space** — Pause / resume
- **H** — Toggle HUD

### Customize

Edit the `CONFIG` object at the top of `index.html`:

```js
const CONFIG = {
  BODY_COUNT: 50,
  G: 0.5,
  TRAIL_FADE: 0.1,
  MAX_SPEED: 6,
  BLACK_HOLE_PULL: 5,
  SOFTENING: 20,
};
```

### Roadmap

- [x] **Stage 1:** 50-body N-body + trails
- [x] **Stage 2:** Click-to-spawn black hole
- [ ] **Stage 3:** Presets — galaxy collision / solar system / binary
- [ ] **Stage 4:** Web Worker integrator for large-N

---

## 🛠 Built With

This project was scaffolded using **[opencode](https://opencode.ai)** running the
**MiniMax-M3** model. The following prompt generated the simulation in
`index.html`:

> HTML5 Canvas를 사용하여 어두운 우주 공간에서 서로 다른 질량을 가진 50개의 형광색 천체들이 서로의 중력에 이끌려(N-body simulation) 복잡한 궤도를 그리며 회전하는데, 각 천체가 지나간 자리에 긴 잔상(Trail)이 남아 아름다운 곡선을 만들고 마우스로 클릭하면 새로운 블랙홀이 생성되어 주변 천체들을 강력하게 빨아들이는 고성능 물리학 시뮬레이션을 단일 파일로 만들어줘.
>
> **Implementation Advice:** Use HTML5 Canvas. For the "Trails" effect, instead of clearing the canvas completely each frame (`ctx.clearRect`), draw a semi-transparent black rectangle (`ctx.fillStyle = 'rgba(0,0,0,0.1)'; ctx.fillRect(...)`) to create a fading trail effect. 모든 의존관계의 코드를 하나의 HTML에 담는 형태로 코드 작성.

## 📜 License

MIT — do whatever, but attribution appreciated.
