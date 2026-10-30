[breaking-bad-portal (5).html](https://github.com/user-attachments/files/34181750/breaking-bad-portal.5.html)
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="Breaking Bad - Portal interactivo.">
  <title>Breaking Bad | Portal</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Oswald:wght@400;500;600;700&family=Source+Sans+3:wght@300;400;600&display=swap" rel="stylesheet">
  <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='80'>Br</text></svg>">
  <style>
:root {
  --void: #0a0c09;
  --lab: #111411;
  --panel: #181c17;
  --green-deep: #0d3b1e;
  --green: #1a5c32;
  --green-bright: #2d8f4e;
  --green-glow: rgba(45, 143, 78, 0.45);
  --element: #00a651;
  --element-bg: #006b3a;
  --sand: #c4a035;
  --sand-light: #e8c84a;
  --text: #d8d6c8;
  --muted: #8a8878;
  --line: #2a3228;
  --danger: #b33a3a;
  --font-title: 'Oswald', Impact, sans-serif;
  --font-body: 'Source Sans 3', system-ui, sans-serif;
}
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  font-family: var(--font-body);
  background: var(--void);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
  line-height: 1.55;
}
#bg-canvas {
  position: fixed; inset: 0; z-index: 0;
  pointer-events: none; opacity: 0.4;
}
.topbar {
  position: sticky; top: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0.6rem 1.4rem;
  background: rgba(10, 12, 9, 0.94);
  backdrop-filter: blur(14px);
  border-bottom: 1px solid var(--line);
}
/* TITULO ESTILO INTRO BREAKING BAD */
.bb-title {
  display: flex;
  align-items: center;
  gap: 2px;
  font-family: var(--font-title);
  font-weight: 700;
  font-size: 1.55rem;
  letter-spacing: 0.02em;
  text-transform: uppercase;
  color: var(--text);
  text-decoration: none;
  user-select: none;
}
.element {
  display: inline-flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 2.15em;
  height: 2.15em;
  background: var(--element-bg);
  border: 2px solid var(--element);
  color: #fff;
  line-height: 1;
  position: relative;
  box-shadow: 0 0 12px var(--green-glow);
}
.element .num {
  position: absolute;
  top: 3px; left: 4px;
  font-size: 0.45em;
  font-weight: 500;
  opacity: 0.9;
}
.element .sym {
  font-size: 1.05em;
  font-weight: 700;
  margin-top: 0.15em;
}
.bb-title .rest { padding: 0 0.08em; }
.nav-links { display: flex; gap: 0.15rem; }
.nav-links a {
  color: var(--muted);
  text-decoration: none;
  padding: 0.45rem 0.9rem;
  font-size: 0.88rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  border-radius: 4px;
  transition: 0.25s;
}
.nav-links a:hover,
.nav-links a.on {
  color: var(--sand-light);
  background: rgba(26, 92, 50, 0.35);
}
.burger {
  display: none;
  flex-direction: column; gap: 5px;
  background: none; border: none; cursor: pointer; padding: 5px;
}
.burger span {
  width: 22px; height: 2px; background: var(--green-bright);
}
.view {
  display: none;
  position: relative; z-index: 1;
  max-width: 1100px;
  margin: 0 auto;
  padding: 2rem 1.3rem 3.5rem;
  animation: in 0.45s ease;
}
#home.view {
  max-width: none;
  padding-left: 0;
  padding-right: 0;
  padding-top: 0;
  padding-bottom: 0;
}
#home .home-hero {
  margin: 0;
  width: 100%;
}
#home .home-content {
  max-width: 1100px;
  margin: 0 auto;
  padding-left: 1.5rem;
  padding-right: 1.5rem;
}

.view.on { display: block; }
@keyframes in {
  from { opacity: 0; transform: translateY(10px); }
  to   { opacity: 1; transform: translateY(0); }
}
.home-hero {
  position: relative;
  min-height: calc(100vh - 52px);
  display: flex;
  align-items: flex-end;
  border-radius: 0;
  overflow: hidden;
  margin: -2rem -1.3rem 0;
  width: calc(100% + 2.6rem);
}
.home-bg {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}
.home-bg img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 30%;
  display: block;
  filter: brightness(0.82) contrast(1.06);
  transform: scale(1.08);
  transform-origin: center center;
}
.home-overlay {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(to top, rgba(10,12,9,0.92) 0%, rgba(10,12,9,0.55) 32%, rgba(10,12,9,0.15) 58%, rgba(10,12,9,0.25) 100%),
    radial-gradient(ellipse at 50% 35%, transparent 25%, rgba(10,12,9,0.35) 100%);
  pointer-events: none;
}
.home-content {
  position: relative;
  z-index: 2;
  padding: 2.5rem 1.5rem 2.2rem;
  max-width: 640px;
  width: 100%;
}
.home-content h2 {
  font-family: var(--font-title);
  font-size: clamp(2.4rem, 6vw, 3.8rem);
  font-weight: 700;
  letter-spacing: 0.03em;
  line-height: 1.08;
  margin-bottom: 1rem;
  text-transform: uppercase;
  text-shadow: 0 2px 20px rgba(0,0,0,0.8);
}
.home-content h2 .hl {
  color: var(--green-bright);
  text-shadow: 0 0 30px var(--green-glow), 0 2px 12px rgba(0,0,0,0.6);
}
.home-content > p {
  color: var(--text);
  font-size: 1.05rem;
  max-width: 440px;
  margin-bottom: 1.5rem;
  opacity: 0.9;
  text-shadow: 0 1px 8px rgba(0,0,0,0.7);
}
.home-content .metrics {
  margin-top: 1.8rem;
  background: rgba(17, 20, 17, 0.75);
  backdrop-filter: blur(10px);
  border: 1px solid var(--line);
}
@media (max-width: 720px) {
  .home-hero {
    margin: -1.4rem -0.9rem 0;
    width: calc(100% + 1.8rem);
    min-height: 78vh;
  }
  .home-bg img { object-position: center 20%; }
}
@media (max-width: 420px) {
  .home-hero {
    margin: -1.4rem -0.9rem 0;
    width: calc(100% + 1.8rem);
  }
}
.home-copy h2 {
  font-family: var(--font-title);
  font-size: clamp(2.2rem, 5.5vw, 3.6rem);
  font-weight: 700;
  letter-spacing: 0.03em;
  line-height: 1.1;
  margin-bottom: 1rem;
  text-transform: uppercase;
}
.home-copy h2 .hl {
  color: var(--green-bright);
  text-shadow: 0 0 30px var(--green-glow);
}
.home-copy p {
  color: var(--muted);
  font-size: 1.05rem;
  max-width: 420px;
  margin-bottom: 1.6rem;
}
.actions { display: flex; flex-wrap: wrap; gap: 0.7rem; margin-bottom: 1.8rem; }
.credit { font-size: 0.82rem; color: var(--muted); }
.credit b { color: var(--sand); }
.emblem {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 0.6rem;
  flex-wrap: wrap;
}
.hero-wrap {
  width: 100%;
  max-width: 380px;
  margin: 0 auto;
  border-radius: 8px;
  overflow: hidden;
  border: 2px solid var(--green);
  box-shadow: 0 0 32px var(--green-glow), 0 12px 40px rgba(0,0,0,0.5);
  aspect-ratio: 2 / 2.55;
  background: var(--panel);
}
.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center 18%;
  display: block;
  /* crop bottom so logo/title is hidden */
  transform: scale(1.08);
  transform-origin: center top;
}
@media (max-width: 860px) {
  .hero-wrap { max-width: 280px; }
}

.big-element {
  width: 110px; height: 110px;
  background: var(--element-bg);
  border: 3px solid var(--element);
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  color: #fff;
  box-shadow: 0 0 28px var(--green-glow), inset 0 0 20px rgba(0,0,0,0.3);
  position: relative;
  animation: breathe 3s ease-in-out infinite;
}
.big-element .n {
  position: absolute; top: 8px; left: 10px;
  font-size: 0.75rem; opacity: 0.85;
}
.big-element .s {
  font-family: var(--font-title);
  font-size: 2.8rem; font-weight: 700;
  line-height: 1;
}
.big-element .name {
  font-size: 0.55rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  margin-top: 2px;
  opacity: 0.8;
}
@keyframes breathe {
  0%, 100% { box-shadow: 0 0 20px var(--green-glow), inset 0 0 20px rgba(0,0,0,0.3); }
  50% { box-shadow: 0 0 40px var(--green-glow), 0 0 60px rgba(0,166,81,0.2), inset 0 0 20px rgba(0,0,0,0.3); }
}
.metrics {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.8rem;
  margin-top: 2.2rem;
  padding: 1.2rem;
  background: var(--lab);
  border: 1px solid var(--line);
  border-radius: 6px;
}
.metric { text-align: center; }
.metric .v {
  font-family: var(--font-title);
  font-size: 1.9rem;
  color: var(--green-bright);
  letter-spacing: 0.04em;
}
.metric .l {
  font-size: 0.72rem;
  color: var(--muted);
  text-transform: uppercase;
  letter-spacing: 0.1em;
}
.btn {
  display: inline-flex; align-items: center; justify-content: center;
  padding: 0.7rem 1.4rem;
  border: none; border-radius: 4px;
  font-family: var(--font-body);
  font-size: 0.92rem; font-weight: 600;
  cursor: pointer; transition: 0.25s;
  text-decoration: none;
}
.btn-green {
  background: var(--green);
  color: #fff;
  box-shadow: 0 3px 14px var(--green-glow);
}
.btn-green:hover {
  background: var(--green-bright);
  transform: translateY(-1px);
}
.btn-outline {
  background: transparent;
  color: var(--sand-light);
  border: 1px solid var(--sand);
}
.btn-outline:hover { background: rgba(196, 160, 53, 0.12); }
.btn-sm { padding: 0.4rem 0.9rem; font-size: 0.82rem; }
.btn-red { background: #7a2222; color: #fff; }
.btn-red:hover { background: var(--danger); }
.head { text-align: center; margin-bottom: 1.8rem; }
.head h2 {
  font-family: var(--font-title);
  font-size: clamp(1.7rem, 4vw, 2.4rem);
  letter-spacing: 0.06em;
  text-transform: uppercase;
  margin-bottom: 0.3rem;
  color: var(--green-bright);
}
.head p { color: var(--muted); font-size: 0.92rem; }
.tools {
  display: flex; flex-wrap: wrap; gap: 0.65rem;
  justify-content: center; margin-top: 1rem;
}
.tools input,
.tools select {
  padding: 0.55rem 0.9rem;
  border-radius: 4px;
  border: 1px solid var(--line);
  background: var(--panel);
  color: var(--text);
  font-size: 0.88rem;
  min-width: 170px;
}
.tools input:focus,
.tools select:focus {
  outline: none;
  border-color: var(--green-bright);
  box-shadow: 0 0 0 2px var(--green-glow);
}
.wait { text-align: center; padding: 2.5rem; color: var(--muted); }
.spin {
  width: 42px; height: 42px;
  border: 3px solid var(--line);
  border-top-color: var(--green-bright);
  border-radius: 50%;
  margin: 0 auto 0.9rem;
  animation: rot 0.75s linear infinite;
}
@keyframes rot { to { transform: rotate(360deg); } }
.err {
  background: rgba(179, 58, 58, 0.12);
  border: 1px solid var(--danger);
  color: #e08080;
  padding: 0.9rem;
  border-radius: 4px;
  text-align: center;
  margin-bottom: 1.2rem;
}
.cast {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(155px, 1fr));
  gap: 1.1rem;
}
.card {
  background: var(--lab);
  border: 1px solid var(--line);
  border-radius: 6px;
  overflow: hidden;
  cursor: grab;
  transition: 0.28s;
  position: relative;
  user-select: none;
}
.card:hover {
  border-color: var(--green-bright);
  transform: translateY(-5px);
  box-shadow: 0 10px 26px var(--green-glow);
}
.card:active { cursor: grabbing; }
.card.focus { outline: 2px solid var(--sand); outline-offset: 2px; }
.card img {
  width: 100%; height: 195px;
  object-fit: cover;
  background: var(--panel);
  display: block;
}
.card .meta { padding: 0.75rem; }
.card .nm {
  font-weight: 600; font-size: 0.92rem;
  white-space: nowrap; overflow: hidden; text-overflow: ellipsis;
  margin-bottom: 0.15rem;
}
.card .rl {
  font-size: 0.72rem; color: var(--muted);
  text-transform: uppercase; letter-spacing: 0.06em;
}
.card .rl.main { color: var(--sand); }
.card .plus {
  position: absolute; top: 7px; right: 7px;
  width: 30px; height: 30px; border-radius: 50%;
  border: none;
  background: rgba(10, 12, 9, 0.85);
  color: var(--green-bright);
  font-size: 1.05rem; cursor: pointer;
  opacity: 0; transition: 0.25s;
  display: flex; align-items: center; justify-content: center;
}
.card:hover .plus { opacity: 1; }
.card .plus:hover { background: var(--green); color: #fff; }
.drop {
  min-height: 260px;
  background: var(--lab);
  border: 2px dashed var(--line);
  border-radius: 6px;
  padding: 1.3rem;
  transition: 0.25s;
}
.drop.over {
  border-color: var(--green-bright);
  background: rgba(26, 92, 50, 0.12);
  box-shadow: inset 0 0 28px var(--green-glow);
}
.hint {
  text-align: center; color: var(--muted);
  padding: 2rem; font-style: italic;
}
.crew-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(135px, 1fr));
  gap: 0.9rem;
}
.crew-item {
  background: var(--panel);
  border: 1px solid var(--green);
  border-radius: 5px;
  overflow: hidden;
  position: relative;
  animation: pop 0.3s ease;
}
@keyframes pop {
  from { opacity: 0; transform: scale(0.88); }
  to   { opacity: 1; transform: scale(1); }
}
.crew-item img { width: 100%; height: 140px; object-fit: cover; }
.crew-item .meta { padding: 0.5rem; text-align: center; }
.crew-item .nm { font-size: 0.82rem; font-weight: 600; }
.crew-item .x {
  position: absolute; top: 5px; right: 5px;
  width: 24px; height: 24px; border-radius: 50%;
  border: none; background: var(--danger); color: #fff;
  font-size: 0.85rem; cursor: pointer; opacity: 0.85;
}
.crew-item .x:hover { opacity: 1; transform: scale(1.08); }
/* ===== QUIZ / TRIVIA ===== */
.quiz-panel {
  background: var(--lab);
  border: 1px solid var(--line);
  border-radius: 8px;
  padding: 2rem 1.5rem;
  text-align: center;
  max-width: 620px;
  margin: 0 auto;
}
.quiz-icon { font-size: 2.8rem; margin-bottom: 0.6rem; }
.quiz-title {
  font-family: var(--font-title);
  font-size: 1.6rem;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  color: var(--green-bright);
  margin-bottom: 0.6rem;
}
.quiz-desc {
  color: var(--muted);
  font-size: 0.95rem;
  max-width: 420px;
  margin: 0 auto 1.2rem;
  line-height: 1.5;
}
.quiz-best {
  font-size: 0.88rem;
  color: var(--sand-light);
  margin-bottom: 1.3rem;
  letter-spacing: 0.03em;
}
.quiz-progress {
  display: flex;
  align-items: center;
  gap: 0.8rem;
  margin-bottom: 0.8rem;
}
.quiz-bar {
  flex: 1;
  height: 6px;
  background: var(--panel);
  border-radius: 3px;
  overflow: hidden;
}
.quiz-fill {
  height: 100%;
  width: 10%;
  background: var(--green-bright);
  border-radius: 3px;
  transition: width 0.35s ease;
  box-shadow: 0 0 10px var(--green-glow);
}
#quiz-step {
  font-size: 0.82rem;
  color: var(--muted);
  white-space: nowrap;
  font-weight: 600;
}
.quiz-score-live {
  font-size: 0.88rem;
  color: var(--muted);
  margin-bottom: 1.2rem;
}
.quiz-score-live strong {
  color: var(--green-bright);
  font-family: var(--font-title);
  font-size: 1.15rem;
}
.quiz-question {
  font-family: var(--font-title);
  font-size: 1.25rem;
  letter-spacing: 0.02em;
  line-height: 1.35;
  margin-bottom: 1.4rem;
  color: var(--text);
  text-align: left;
}
.quiz-options {
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
}
.quiz-opt {
  display: block;
  width: 100%;
  text-align: left;
  padding: 0.85rem 1.1rem;
  background: var(--panel);
  border: 1px solid var(--line);
  border-radius: 6px;
  color: var(--text);
  font-family: var(--font-body);
  font-size: 0.95rem;
  font-weight: 500;
  cursor: pointer;
  transition: 0.22s;
}
.quiz-opt:hover:not(:disabled) {
  border-color: var(--green-bright);
  background: rgba(26, 92, 50, 0.25);
  box-shadow: 0 0 14px var(--green-glow);
  transform: translateX(4px);
}
.quiz-opt.correct {
  border-color: var(--green-bright);
  background: rgba(45, 143, 78, 0.3);
  color: #fff;
}
.quiz-opt.wrong {
  border-color: var(--danger);
  background: rgba(179, 58, 58, 0.2);
  color: #e08080;
}
.quiz-opt:disabled { cursor: default; opacity: 0.85; }
.quiz-final-score {
  font-family: var(--font-title);
  font-size: 2.8rem;
  color: var(--green-bright);
  letter-spacing: 0.04em;
  margin: 0.4rem 0 0.6rem;
}
.quiz-rank {
  font-family: var(--font-title);
  font-size: 1.35rem;
  color: var(--sand-light);
  letter-spacing: 0.04em;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}
.quiz-msg {
  color: var(--muted);
  font-size: 0.95rem;
  max-width: 400px;
  margin: 0 auto 0.8rem;
  line-height: 1.5;
}
.quiz-phases-preview {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
  margin-bottom: 1.2rem;
}
.phase-tag {
  font-size: 0.78rem;
  font-weight: 600;
  letter-spacing: 0.04em;
  text-transform: uppercase;
  padding: 0.35rem 0.7rem;
  border-radius: 4px;
  border: 1px solid var(--line);
}
.phase-tag.phase-1 { color: var(--green-bright); border-color: var(--green); background: rgba(45,143,78,0.12); }
.phase-tag.phase-2 { color: var(--sand-light); border-color: var(--sand); background: rgba(196,160,53,0.12); }
.phase-tag.phase-3 { color: #e08080; border-color: var(--danger); background: rgba(179,58,58,0.12); }
.quiz-phase-badge {
  display: inline-block;
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  padding: 0.3rem 0.75rem;
  border-radius: 4px;
  margin-bottom: 0.9rem;
  border: 1px solid var(--line);
}
.quiz-phase-badge.p1 { color: var(--green-bright); border-color: var(--green); background: rgba(45,143,78,0.15); }
.quiz-phase-badge.p2 { color: var(--sand-light); border-color: var(--sand); background: rgba(196,160,53,0.15); }
.quiz-phase-badge.p3 { color: #e08080; border-color: var(--danger); background: rgba(179,58,58,0.15); }
.quiz-exit-btn {
  margin-top: 1.4rem;
  opacity: 0.75;
  width: 100%;
  max-width: 220px;
}
.quiz-exit-btn:hover { opacity: 1; }
.info-panel {
  margin-top: 1.6rem;
  background: var(--lab);
  border: 1px solid var(--line);
  border-radius: 6px;
  padding: 1.3rem;
}
.info-panel h3 {
  font-family: var(--font-title);
  font-size: 1.15rem;
  letter-spacing: 0.05em;
  color: var(--green-bright);
  margin-bottom: 0.7rem;
  text-transform: uppercase;
}
#show-info { color: var(--muted); font-size: 0.93rem; line-height: 1.65; }
#show-info b { color: var(--text); }
.overlay {
  position: fixed; inset: 0; z-index: 200;
  display: flex; align-items: center; justify-content: center;
  padding: 1rem;
}
.overlay[hidden] { display: none; }
.overlay .shade {
  position: absolute; inset: 0;
  background: rgba(0,0,0,0.8);
  backdrop-filter: blur(5px);
}
.overlay .box {
  position: relative;
  background: var(--lab);
  border: 1px solid var(--green);
  border-radius: 10px;
  max-width: 460px; width: 100%;
  max-height: 90vh; overflow-y: auto;
  box-shadow: 0 12px 40px rgba(0,0,0,0.6), 0 0 35px var(--green-glow);
  animation: modalIn 0.28s ease;
}
@keyframes modalIn {
  from { opacity: 0; transform: scale(0.94) translateY(16px); }
  to   { opacity: 1; transform: scale(1) translateY(0); }
}
.overlay .close {
  position: absolute; top: 10px; right: 12px;
  width: 34px; height: 34px; border-radius: 50%;
  border: none; background: var(--panel); color: var(--text);
  font-size: 1.3rem; cursor: pointer; z-index: 2;
}
.overlay .close:hover { background: var(--danger); color: #fff; }
.overlay .body { padding: 1.4rem; }
.overlay .body img {
  width: 100%; max-height: 270px; object-fit: cover;
  border-radius: 6px; margin-bottom: 0.9rem;
}
.overlay .body h3 {
  font-family: var(--font-title);
  font-size: 1.55rem; letter-spacing: 0.03em;
  margin-bottom: 0.3rem;
}
.overlay .badge {
  display: inline-block;
  padding: 0.18rem 0.55rem;
  background: var(--green);
  border-radius: 3px;
  font-size: 0.72rem;
  margin-bottom: 0.7rem;
}
.overlay .body p { color: var(--muted); font-size: 0.93rem; }
.toasts {
  position: fixed; bottom: 1.3rem; right: 1.3rem;
  z-index: 300; display: flex; flex-direction: column; gap: 0.45rem;
}
.toast {
  background: var(--panel);
  border: 1px solid var(--green);
  color: var(--text);
  padding: 0.8rem 1.1rem;
  border-radius: 5px;
  box-shadow: 0 6px 20px rgba(0,0,0,0.5);
  animation: slide 0.3s ease;
  font-size: 0.88rem;
}
.toast.ok { border-color: var(--green-bright); }
.toast.no { border-color: var(--danger); }
@keyframes slide {
  from { opacity: 0; transform: translateX(36px); }
  to   { opacity: 1; transform: translateX(0); }
}
.foot {
  text-align: center;
  padding: 1.8rem 1rem;
  border-top: 1px solid var(--line);
  color: var(--muted);
  font-size: 0.82rem;
  position: relative; z-index: 1;
}
.foot a { color: var(--green-bright); text-decoration: none; }
.foot a:hover { text-decoration: underline; }
@media (max-width: 720px) {
  .nav-links {
    display: none;
    position: absolute; top: 100%; left: 0; right: 0;
    flex-direction: column;
    background: rgba(10,12,9,0.98);
    padding: 0.8rem;
    border-bottom: 1px solid var(--line);
  }
  .nav-links.open { display: flex; }
  .burger { display: flex; }
  .cast { grid-template-columns: repeat(auto-fill, minmax(135px, 1fr)); }
  .metrics { grid-template-columns: 1fr; gap: 1rem; }
  .big-element { width: 90px; height: 90px; }
  .big-element .s { font-size: 2.2rem; }
}
@media (max-width: 420px) {
  .topbar { padding: 0.5rem 0.9rem; }
  .bb-title { font-size: 1.25rem; }
  .view { padding: 1.4rem 0.9rem 3rem; }
  .actions { flex-direction: column; }
  .btn { width: 100%; }
}

.ep-list {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}
.ep-card {
  display: grid;
  grid-template-columns: 56px 120px 1fr auto;
  gap: 1rem;
  align-items: center;
  background: var(--lab);
  border: 1px solid var(--line);
  border-radius: 6px;
  padding: 0.7rem 1rem;
  cursor: pointer;
  transition: 0.25s;
}
.ep-card:hover {
  border-color: var(--green-bright);
  box-shadow: 0 6px 20px var(--green-glow);
  transform: translateY(-2px);
}
.ep-rank {
  font-family: var(--font-title);
  font-size: 1.5rem;
  color: var(--sand);
  text-align: center;
  font-weight: 700;
}
.ep-rank.gold { color: #e8c84a; }
.ep-rank.silver { color: #c0c0c0; }
.ep-rank.bronze { color: #cd7f32; }
.ep-card img {
  width: 120px;
  height: 68px;
  object-fit: cover;
  border-radius: 4px;
  background: var(--panel);
}
.ep-info .title {
  font-weight: 600;
  font-size: 1rem;
  margin-bottom: 0.15rem;
}
.ep-info .meta {
  font-size: 0.78rem;
  color: var(--muted);
  letter-spacing: 0.04em;
}
.ep-info .blurb {
  font-size: 0.8rem;
  color: var(--muted);
  margin-top: 0.25rem;
  line-height: 1.35;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
@media (max-width: 640px) {
  .ep-info .blurb { display: none; }
}

.ep-score {
  font-family: var(--font-title);
  font-size: 1.55rem;
  color: var(--green-bright);
  white-space: nowrap;
}
.ep-score span {
  font-size: 0.75rem;
  color: var(--muted);
  font-family: var(--font-body);
}
@media (max-width: 640px) {
  .ep-card {
    grid-template-columns: 40px 1fr auto;
  }
  .ep-card img { display: none; }
  .ep-rank { font-size: 1.2rem; }
  .ep-score { font-size: 1.25rem; }
}
:focus-visible { outline: 2px solid var(--green-bright); outline-offset: 2px; }
.card.drag { opacity: 0.45; transform: scale(0.96); }
  </style>
</head>
<body>
  <canvas id="bg-canvas"></canvas>

  <header class="topbar">
    <a href="#home" class="bb-title" id="logo-home">
      <span class="element"><span class="num">35</span><span class="sym">Br</span></span>
      <span class="rest">eaking</span>
      <span class="element"><span class="num">56</span><span class="sym">Ba</span></span>
      <span class="rest">d</span>
    </a>
    <nav class="nav-links" id="nav">
      <a href="#home" class="on" data-v="home">Inicio</a>
      <a href="#cast" data-v="cast">Elenco</a>
      <a href="#episodes" data-v="episodes">Episodios</a>
      <a href="#quiz" data-v="quiz">Trivia</a>
    </nav>
    <button class="burger" id="burger" aria-label="Menú"><span></span><span></span><span></span></button>
  </header>

  <main>
    <section id="home" class="view on">
      <div class="home-hero">
        <div class="home-bg">
          <!-- PONÉ ACÁ TU IMAGEN GRANDE: cambiá solo el src -->
          <img src="https://images5.alphacoders.com/287/thumb-1920-287897.jpg" alt="Breaking Bad" id="hero-img">
        </div>
        <div class="home-overlay"></div>
        <div class="home-content">
          <h2>Yo soy el que<br><span class="hl">llama a la puerta</span></h2>
          <p>Explora el elenco de la serie, descubre los episodios mejor valorados en IMDb y poné a prueba tus conocimientos con la trivia. Bienvenido al laboratorio.</p>
          <div class="actions">
            <button class="btn btn-green" id="go-cast">Ver el elenco</button>
            <button class="btn btn-outline" id="go-eps">Ver episodios</button>
          </div>
          <div class="metrics">
            <div class="metric"><span class="v" id="m-cast">—</span><span class="l">Personajes</span></div>
            <div class="metric"><span class="v" id="m-top">—</span><span class="l">Top IMDb</span></div>
            <div class="metric"><span class="v">62</span><span class="l">Episodios</span></div>
          </div>
        </div>
      </div>
    </section>

    <section id="cast" class="view">
      <div class="head">
        <h2>El Elenco</h2>
        <p>Clic para detalles · Flechas del teclado</p>
        <div class="tools">
          <input type="text" id="q" placeholder="Buscar..." autocomplete="off">
          <select id="filter">
            <option value="all">Todos</option>
            <option value="Main">Principales</option>
            <option value="Supporting">Secundarios</option>
          </select>
          <button class="btn btn-green btn-sm" id="reload">Recargar</button>
        </div>
      </div>
      <div class="wait" id="wait">
        <div class="spin"></div>
        <p>Cargando elenco desde TVMaze...</p>
      </div>
      <div class="err" id="err" hidden></div>
      <div class="cast" id="cast-grid"></div>
    </section>

    <section id="episodes" class="view">
      <div class="head">
        <h2>Episodios por IMDb</h2>
        <p>Ordenados de mayor a menor puntuación · Clic para detalles</p>
        <div class="tools">
          <select id="ep-season">
            <option value="all">Todas las temporadas</option>
            <option value="1">Temporada 1</option>
            <option value="2">Temporada 2</option>
            <option value="3">Temporada 3</option>
            <option value="4">Temporada 4</option>
            <option value="5">Temporada 5</option>
          </select>
          <button class="btn btn-green btn-sm" id="ep-reload">Recargar</button>
        </div>
      </div>
      <div class="wait" id="ep-wait">
        <div class="spin"></div>
        <p>Cargando episodios...</p>
      </div>
      <div class="err" id="ep-err" hidden></div>
      <div class="ep-list" id="ep-list"></div>
    </section>

    <section id="quiz" class="view">
      <div class="head">
        <h2>Trivia del Laboratorio</h2>
        <p>33 preguntas · 3 fases de 11 · Fácil → Intermedio → Difícil · v10</p>
      </div>

      <!-- Pantalla de inicio -->
      <div id="quiz-start" class="quiz-panel">
        <div class="quiz-icon">🧪</div>
        <h3 class="quiz-title">¿Estás listo?</h3>
        <p class="quiz-desc">33 preguntas en 3 fases. Completa la fase Fácil para desbloquear el Intermedio, y luego el Difícil.</p>
        <div class="quiz-phases-preview">
          <span class="phase-tag phase-1">1. Fácil · 11</span>
          <span class="phase-tag phase-2">2. Intermedio · 11</span>
          <span class="phase-tag phase-3">3. Difícil · 11</span>
        </div>
        <div class="quiz-best" id="quiz-best">Mejor puntaje: —</div>
        <button class="btn btn-green" id="quiz-begin">Comenzar Fase Fácil</button>
      </div>

      <!-- Pantalla de pregunta -->
      <div id="quiz-play" class="quiz-panel" hidden>
        <div class="quiz-phase-badge" id="quiz-phase">Fase 1 · Fácil</div>
        <div class="quiz-progress">
          <div class="quiz-bar"><div class="quiz-fill" id="quiz-fill"></div></div>
          <span id="quiz-step">1 / 11</span>
        </div>
        <div class="quiz-score-live">Puntos totales: <strong id="quiz-score">0</strong></div>
        <h3 class="quiz-question" id="quiz-q"></h3>
        <div class="quiz-options" id="quiz-opts"></div>
        <button type="button" class="btn btn-outline btn-sm quiz-exit-btn" id="quiz-exit">Salir de la trivia</button>
      </div>

      <!-- Pantalla entre fases -->
      <div id="quiz-phase-end" class="quiz-panel" hidden>
        <div class="quiz-icon" id="quiz-phase-icon">✅</div>
        <h3 class="quiz-title" id="quiz-phase-title">Fase completada</h3>
        <p class="quiz-desc" id="quiz-phase-msg">Pasas a la siguiente etapa.</p>
        <div class="quiz-final-score" style="font-size:1.8rem" id="quiz-phase-score">0 / 11</div>
        <button class="btn btn-green" id="quiz-next-phase">Continuar</button>
        <button type="button" class="btn btn-outline btn-sm quiz-exit-btn" id="quiz-exit-phase" style="margin-top:0.8rem">Salir de la trivia</button>
      </div>

      <!-- Pantalla de resultado final -->
      <div id="quiz-end" class="quiz-panel" hidden>
        <div class="quiz-icon" id="quiz-end-icon">🏆</div>
        <h3 class="quiz-title" id="quiz-end-title">Resultado final</h3>
        <div class="quiz-final-score" id="quiz-final">0 / 33</div>
        <p class="quiz-rank" id="quiz-rank"></p>
        <p class="quiz-msg" id="quiz-msg"></p>
        <div class="quiz-best" id="quiz-best-end"></div>
        <div class="actions" style="justify-content:center;margin-top:1.4rem">
          <button class="btn btn-green" id="quiz-retry">Reintentar</button>
          <button class="btn btn-outline" id="quiz-home">Volver al inicio</button>
        </div>
      </div>

    </section>
  </main>

  <div class="overlay" id="modal" hidden>
    <div class="shade"></div>
    <div class="box">
      <button class="close" id="m-close">&times;</button>
      <div class="body" id="m-body"></div>
    </div>
  </div>

  <div class="toasts" id="toasts"></div>

  <footer class="foot">
    <p>Breaking Bad · Episodios por IMDb · Trivia del Laboratorio</p>
    <p style="margin-top:0.3rem;font-size:0.78rem">Datos: <a href="https://www.tvmaze.com" target="_blank" rel="noopener">TVMaze API</a></p>
  </footer>

  <script>
(() => {
  'use strict';
  const SHOW = 169;
  const API = 'https://api.tvmaze.com';
  // Ratings IMDb aproximadas (fuente: TVRankd / IMDb, pueden variar ligeramente)
  const IMDB = {
    '1-1': 9.0, '1-2': 8.6, '1-3': 8.7, '1-4': 8.2, '1-5': 8.2, '1-6': 9.3, '1-7': 8.8,
    '2-1': 8.6, '2-2': 9.3, '2-3': 8.3, '2-4': 8.2, '2-5': 8.2, '2-6': 8.8, '2-7': 8.6,
    '2-8': 9.2, '2-9': 9.2, '2-10': 8.4, '2-11': 8.9, '2-12': 9.3, '2-13': 9.2,
    '3-1': 8.4, '3-2': 8.6, '3-3': 8.3, '3-4': 8.1, '3-5': 8.5, '3-6': 9.3, '3-7': 9.6,
    '3-8': 8.7, '3-9': 8.3, '3-10': 7.9, '3-11': 8.4, '3-12': 9.5, '3-13': 9.6,
    '4-1': 9.2, '4-2': 8.2, '4-3': 7.9, '4-4': 8.5, '4-5': 8.6, '4-6': 8.4, '4-7': 8.8,
    '4-8': 9.3, '4-9': 8.9, '4-10': 9.6, '4-11': 9.7, '4-12': 9.5, '4-13': 9.8,
    '5-1': 9.2, '5-2': 8.8, '5-3': 8.8, '5-4': 8.7, '5-5': 9.6, '5-6': 9.0, '5-7': 9.6,
    '5-8': 9.5, '5-9': 9.4, '5-10': 9.2, '5-11': 9.6, '5-12': 9.1, '5-13': 9.7,
    '5-14': 9.9, '5-15': 9.7, '5-16': 9.9
  };
  const SUM = {
    '1-1': 'Un profesor de química recibe un diagnóstico que cambia su vida y decide usar sus conocimientos de una forma inesperada.',
    '1-2': 'Walt y Jesse enfrentan las consecuencias de su primera operación y deben actuar con rapidez.',
    '1-3': 'Walt se enfrenta a una decisión moral mientras la presión familiar y policial aumenta.',
    '1-4': 'Walt comparte una noticia devastadora con su familia mientras el negocio empieza a tomar forma.',
    '1-5': 'Ante una oferta legítima y una intervención familiar, Walt reconsidera su camino.',
    '1-6': 'Walt da un paso decisivo y se presenta ante un peligroso contacto con una nueva identidad.',
    '1-7': 'La operación se expande y Walt y Jesse se ven obligados a conseguir insumos de forma arriesgada.',
    '2-1': 'Walt y Jesse intentan deshacerse de un socio volátil mientras la tensión familiar crece.',
    '2-2': 'Walt y Jesse quedan atrapados con un peligroso aliado; sus familias buscan desesperadamente respuestas.',
    '2-3': 'Tras un encuentro violento, Walt y Jesse deben cubrir rastros mientras la DEA avanza.',
    '2-4': 'Walt intenta reconectar con su familia; Jesse se encuentra sin hogar y sin rumbo.',
    '2-5': 'Jesse organiza una red de distribución; Hank lidia con las secuelas de un enfrentamiento.',
    '2-6': 'Jesse interviene en un robo y descubre una realidad mucho más dura de lo esperado.',
    '2-7': 'El negocio se expande; Hank se adapta a un nuevo destino y Skyler retoma su carrera.',
    '2-8': 'Un arresto obliga a Walt y Jesse a buscar ayuda legal de un abogado muy particular.',
    '2-9': 'Tras una revisión médica, Walt y Jesse se encierran en el desierto para una producción intensiva.',
    '2-10': 'Walt intenta volver a una vida normal, pero viejos hábitos y nuevas tentaciones lo persiguen.',
    '2-11': 'Nuevas alianzas y oportunidades aparecen mientras la salud de Walt da un giro inesperado.',
    '2-12': 'Jesse se acerca a alguien especial; Walt enfrenta las consecuencias de sus decisiones.',
    '2-13': 'Una tragedia sacude a todos; Walt debe enfrentar tanto su secreto como el dolor familiar.',
    '3-1': 'Walt enfrenta una nueva amenaza y una relación familiar cada vez más deteriorada.',
    '3-2': 'Walt busca recuperar el control de su vida mientras fuerzas externas se acercan.',
    '3-3': 'Skyler toma una decisión firme; Walt se ve forzado a redefinir su posición en el negocio.',
    '3-4': 'Walt consigue un nuevo rol; Hank se acerca peligrosamente a una pista clave.',
    '3-5': 'Walt se adapta a un entorno más profesional; las tensiones con Jesse aumentan.',
    '3-6': 'Walt y Jesse deben eliminar evidencia antes de que la investigación de Hank dé frutos.',
    '3-7': 'Un acto impulsivo de Hank genera consecuencias graves; una amenaza silenciosa se acerca.',
    '3-8': 'Una crisis familiar lleva a todos al hospital mientras el negocio continúa en segundo plano.',
    '3-9': 'Jesse busca un propósito más allá del laboratorio; Walt lidia con nuevas dinámicas de poder.',
    '3-10': 'Una molestia aparentemente menor obliga a Walt y Jesse a pasar una noche larga en el laboratorio.',
    '3-11': 'Jesse se acerca a alguien del pasado; Walt y Gus ajustan su relación de trabajo.',
    '3-12': 'Walt y Jesse se enfrentan a un dilema moral que pone a prueba su alianza.',
    '3-13': 'Con el futuro del laboratorio en juego, Walt y Jesse deben tomar una decisión definitiva.',
    '4-1': 'Tras un golpe devastador, Walt y Jesse esperan el veredicto de Gus en el laboratorio.',
    '4-2': 'Jesse busca independencia; Walt se siente cada vez más vulnerable ante Gus.',
    '4-3': 'Marie lidia con un problema personal; Walt intenta fortalecer su posición.',
    '4-4': 'Hank recibe una pista importante; Walt y Jesse ajustan su dinámica de trabajo.',
    '4-5': 'Jesse gana confianza en el laboratorio; Walt sospecha que lo están reemplazando.',
    '4-6': 'Walt se siente acorralado y reacciona de forma impredecible ante la presión.',
    '4-7': 'Jesse enfrenta un dilema moral; las tensiones entre Walt y Gus se intensifican.',
    '4-8': 'El pasado de Gus sale a la luz; la DEA intensifica su investigación.',
    '4-9': 'Jesse y Walt chocan; las alianzas dentro del imperio de Gus se tambalean.',
    '4-10': 'Un viaje al sur pone a prueba lealtades; Walt queda en una posición crítica.',
    '4-11': 'Walt se ve obligado a actuar con desesperación para proteger a su familia.',
    '4-12': 'La tensión alcanza su punto máximo mientras todos preparan su próximo movimiento.',
    '4-13': 'Walt pone en marcha un plan arriesgado para cambiar el equilibrio de poder de una vez por todas.',
    '5-1': 'Tras un cambio radical de escenario, Walt, Jesse y Mike deben eliminar rastros peligrosos.',
    '5-2': 'Nuevas oportunidades de negocio aparecen; Lydia entra en escena con sus propios temores.',
    '5-3': 'Walt, Jesse y Mike montan una nueva operación; la vida doméstica de Walt se complica.',
    '5-4': 'Walt celebra un cumpleaños significativo mientras las grietas en su familia se profundizan.',
    '5-5': 'El equipo planea un golpe ambicioso para conseguir un recurso esencial.',
    '5-6': 'Aparece una oferta tentadora para salir del negocio; Walt se niega a ceder el control.',
    '5-7': 'Walt consolida su autoridad de una forma que deja claras las nuevas reglas del juego.',
    '5-8': 'Con el negocio en su punto más alto, Walt contempla un retiro que parece cada vez más cercano.',
    '5-9': 'Una revelación sacude a Hank; el pasado de Walt vuelve para enfrentarlo.',
    '5-10': 'Walt toma medidas para proteger su secreto mientras Hank inicia una investigación personal.',
    '5-11': 'Confesiones y grabaciones cambian el tablero; Jesse se enfrenta a una verdad devastadora.',
    '5-12': 'Jesse busca justicia por su cuenta; Walt y Hank preparan movimientos opuestos.',
    '5-13': 'Una confrontación en el desierto pone a todos en el límite de lo irreversible.',
    '5-14': 'Las consecuencias de años de mentiras y violencia se desatan de forma brutal.',
    '5-15': 'Walt se esconde lejos de todo mientras su familia enfrenta un nuevo orden en casa.',
    '5-16': 'Walt regresa a Albuquerque para cerrar cuentas pendientes y enfrentar el final de su imperio.',
  };

  // 33 preguntas: 11 por fase (Fácil → Intermedio → Difícil)
  const QUIZ = [
    // ===== FASE 1: FÁCIL (11) =====
    { q: '¿En qué ciudad se desarrolla principalmente Breaking Bad?', opts: ['Phoenix', 'Las Vegas', 'Albuquerque', 'El Paso'], a: 2, phase: 1 },
    { q: '¿Qué enfermedad le diagnostican a Walter White al comienzo de la serie?', opts: ['Cáncer de páncreas', 'Cáncer de pulmón', 'Leucemia', 'Cáncer de hígado'], a: 1, phase: 1 },
    { q: '¿Cómo se llama el alter ego de Walter White?', opts: ['Señor White', 'Heisenberg', 'El Cocinero', 'Cielo Azul'], a: 1, phase: 1 },
    { q: '¿De qué color es la metanfetamina que produce Heisenberg?', opts: ['Blanca pura', 'Azul cristalina', 'Verde neón', 'Amarilla'], a: 1, phase: 1 },
    { q: '¿Qué actor interpreta a Walter White?', opts: ['Aaron Paul', 'Bryan Cranston', 'Bob Odenkirk', 'Dean Norris'], a: 1, phase: 1 },
    { q: '¿Quién es el socio y exalumno de Walt?', opts: ['Saul Goodman', 'Mike Ehrmantraut', 'Jesse Pinkman', 'Gus Fring'], a: 2, phase: 1 },
    { q: '¿Cómo se llama la esposa de Walter White?', opts: ['Marie', 'Jane', 'Skyler', 'Andrea'], a: 2, phase: 1 },
    { q: '¿En qué canal de televisión se emitió originalmente Breaking Bad?', opts: ['HBO', 'Netflix', 'AMC', 'FX'], a: 2, phase: 1 },
    { q: '¿Cuántas temporadas tiene Breaking Bad?', opts: ['4', '5', '6', '7'], a: 1, phase: 1 },
    { q: '¿Quién es el cuñado de Walt y agente de la DEA?', opts: ['Steve Gomez', 'Hank Schrader', 'Mike Ehrmantraut', 'Tuco Salamanca'], a: 1, phase: 1 },
    { q: '¿Cuál es la profesión de Walt al inicio de la serie?', opts: ['Médico', 'Abogado', 'Profesor de química', 'Policía'], a: 2, phase: 1 },

    // ===== FASE 2: INTERMEDIO (11) =====
    { q: '¿Cómo se llama el restaurante de pollo frito de Gus Fring?', opts: ['Los Pollos Locos', 'El Pollo Feliz', 'Los Pollos Hermanos', 'Pollo Express'], a: 2, phase: 2 },
    { q: '¿Quién dice la frase "Mejor llama a Saul"?', opts: ['Mike Ehrmantraut', 'Saul Goodman', 'Hank Schrader', 'Tuco Salamanca'], a: 1, phase: 2 },
    { q: '¿Cuál es el apodo de Walter White Jr.?', opts: ['Junior', 'Flynn', 'Waltito', 'Buddy'], a: 1, phase: 2 },
    { q: '¿Quién es el hombre de confianza de Gus Fring y expolicía?', opts: ['Victor', 'Tyrus', 'Mike Ehrmantraut', 'Gale Boetticher'], a: 2, phase: 2 },
    { q: '¿Cómo se llama la hermana de Skyler?', opts: ['Jane', 'Marie', 'Lydia', 'Andrea'], a: 1, phase: 2 },
    { q: '¿Quién es el primer gran narco con el que tratan Walt y Jesse?', opts: ['Gus Fring', 'Tuco Salamanca', 'Don Eladio', 'Jack Welker'], a: 1, phase: 2 },
    { q: '¿Cómo se llama la novia de Jesse que muere por sobredosis?', opts: ['Andrea', 'Jane Margolis', 'Wendy', 'Lydia'], a: 1, phase: 2 },
    { q: '¿Qué usa Héctor Salamanca para comunicarse?', opts: ['Una pizarra', 'Un timbre', 'Lenguaje de señas', 'Una tableta'], a: 1, phase: 2 },
    { q: '¿Qué actor interpreta a Jesse Pinkman?', opts: ['Bryan Cranston', 'Aaron Paul', 'RJ Mitte', 'Jesse Plemons'], a: 1, phase: 2 },
    { q: '¿Cómo se llama el lavadero de autos que compra Walt?', opts: ['A1A Car Wash', 'Lavadero Cielo Azul', 'White Clean', 'Desierto Auto'], a: 0, phase: 2 },
    { q: '¿Quién es el químico brillante que Gus contrata para reemplazar a Walt?', opts: ['Todd Alquist', 'Gale Boetticher', 'Victor', 'Huell'], a: 1, phase: 2 },

    // ===== FASE 3: DIFÍCIL (11) =====
    { q: '¿Quién activa la bomba que mata a Gustavo Fring?', opts: ['Jesse Pinkman', 'Mike Ehrmantraut', 'Héctor Salamanca', 'Walt con un control remoto'], a: 2, phase: 3 },
    { q: '¿Cómo se llama la empresa que Walt cofundó y después abandonó?', opts: ['Química Cielo Azul', 'Gray Matter', 'Madrigal Electromotive', 'A1A Car Wash'], a: 1, phase: 3 },
    { q: '¿Qué nombre falso usa Walt cuando le compra un arma a Lawson?', opts: ['Señor Mayhew', 'Señor Lambert', 'Señor White', 'Señor Heisenberg'], a: 1, phase: 3 },
    { q: '¿En qué episodio Hank descubre que Walt es Heisenberg al encontrar un libro?', opts: ['Confesiones', 'Dinero sangriento', 'Deslizándome sobre todo', 'Ozymandias'], a: 1, phase: 3 },
    { q: '¿Cómo se llama la ejecutiva de Madrigal obsesionada con el té de manzanilla?', opts: ['Francesca', 'Lydia Rodarte-Quayle', 'Skyler', 'Marie'], a: 1, phase: 3 },
    { q: '¿Quién lidera la banda neonazi que traiciona a Walt?', opts: ['Todd Alquist', 'Jack Welker', 'Kenny', 'Declan'], a: 1, phase: 3 },
    { q: '¿Qué libro le dedica Gale a Walt y termina delatándolo?', opts: ['Hojas de hierba de Walt Whitman', 'El alquimista', 'Química orgánica', 'Moby Dick'], a: 0, phase: 3 },
    { q: '¿Cómo muere Mike Ehrmantraut?', opts: ['En una explosión', 'Walt le dispara junto al río', 'Lo mata Gus', 'Muere en el desierto'], a: 1, phase: 3 },
    { q: '¿Cuál es el nombre real de Saul Goodman?', opts: ['Jimmy McGill', 'James Morgan', 'Saul Goodman es su nombre real', 'Robert Sackheim'], a: 0, phase: 3 },
    { q: '¿En qué episodio Walt dice "Yo soy el que llama a la puerta"?', opts: ['Espacio de arrastre', 'Arrinconado', 'Hermanos', 'Escopeta'], a: 1, phase: 3 },
    { q: '¿A quién le da Walt la ricina al final de la serie?', opts: ['A Jack en el café', 'A Lydia en el té de manzanilla', 'A Todd en una cerveza', 'A Jesse en un cigarrillo'], a: 1, phase: 3 }
  ];
  const PHASE_NAMES = { 1: 'Fácil', 2: 'Intermedio', 3: 'Difícil' };
  const PHASE_NEXT = { 1: 'Intermedio', 2: 'Difícil', 3: null };

const BIOS = {
    'walter white': 'Profesor de química con cáncer de pulmón. Se convierte en Heisenberg, construye un imperio de metanfetamina y destruye todo a su alrededor por ego y poder.',
    'heisenberg': 'El alter ego de Walter White. Frío, calculador y despiadado. El nombre que impone miedo en el suroeste de Estados Unidos.',
    'jesse pinkman': 'Exalumno de Walter. Cocina metanfetamina, sufre manipulaciones constantes y termina siendo tanto víctima como cómplice de Heisenberg.',
    'skyler white': 'Esposa de Walter. Descubre el secreto, intenta proteger a su familia, lava dinero y se ve arrastrada al crimen contra su voluntad.',
    'hank schrader': 'Cuñado de Walter y agente de la DEA. Persigue a Heisenberg sin saber que lo tiene en su propia familia. Su investigación define el final de la serie.',
    'marie schrader': 'Esposa de Hank. Apoya a su marido y a la familia White; lidia con el trauma y el color púrpura es su sello.',
    'walter white jr.': 'Hijo de Walter y Skyler. Vive con parálisis cerebral; es una de las motivaciones de Walt y también testigo del colapso familiar.',
    'flynn': 'Apodo de Walter White Jr. Quiere a su padre y no entiende del todo el mundo criminal que lo rodea.',
    'saul goodman': 'Abogado criminalista de dudosa ética. Conecta a Walt y Jesse con el bajo mundo, lava dinero y siempre tiene una salida. “¡Mejor llama a Saul!”',
    'gustavo fring': 'Dueño de Los Pollos Hermanos y capo de la droga. Elegante, metódico y letal. Construye un imperio paralelo hasta que Heisenberg y Héctor lo eliminan.',
    'gus fring': 'Dueño de Los Pollos Hermanos y capo de la droga. Elegante, metódico y letal. Muere en una explosión planeada por Walt con ayuda de Héctor Salamanca.',
    'mike ehrmantraut': 'Expolicía y hombre de confianza de Gus. Profesional, de pocas palabras. Protege el negocio y paga caro su lealtad. “No más medias tintas.”',
    'tuco salamanca': 'Narco violento y errático del cartel. Primera gran amenaza para Walt y Jesse; su caos obliga a buscar nuevos socios.',
    'hector salamanca': 'Patriarca del cartel Salamanca. Mudo y en silla de ruedas, se comunica con un timbre. Odia a Gus desde décadas atrás y, aliado con Walt, activa la bomba que mata a Gustavo Fring.',
    'héctor salamanca': 'Patriarca del cartel Salamanca. Mudo y en silla de ruedas, se comunica con un timbre. Odia a Gus desde décadas atrás y, aliado con Walt, activa la bomba que mata a Gustavo Fring.',
    'todd alquist': 'Miembro de la banda de Jack. Tranquilo por fuera, despiadado por dentro. Mata sin dudar y participa en los actos más oscuros del final de la serie.',
    'lydia rodarte-quayle': 'Ejecutiva de Madrigal. Obsesionada con la pureza del producto y el té de manzanilla. Socio de Heisenberg en la expansión internacional; termina envenenada.',
    'jane margolis': 'Vecina y novia de Jesse. Artista con adicción. Su muerte —que Walt podría haber evitado— marca un punto de no retorno para Jesse y para Heisenberg.',
    'andrea cantillo': 'Interés romántico de Jesse y madre de Brock. Su vínculo con Jesse la pone en la mira del entorno criminal con un final trágico.',
    'brock cantillo': 'Hijo de Andrea. Envenenado en un plan de Walter para manipular a Jesse y enfrentarlos a Gus.',
    'huell babineaux': 'Guardaespaldas y “mano” de Saul. Especialista en quitar cosas sin que te des cuenta; clave en varios engaños de la serie.',
    'badger': 'Amigo de Jesse. Torpe, leal y siempre metido en líos menores de la calle. Sirve de puente con el mundo callejero.',
    'skinny pete': 'Amigo de Jesse. Músico aficionado y parte del círculo cercano en las calles de Albuquerque. Leal hasta el final.',
    'combo': 'Amigo de Jesse. Muere temprano tras un enfrentamiento por territorio, lo que empuja a Jesse más profundo en el negocio.',
    'gretchen schwartz': 'Exnovia de Walter y socia de Gray Matter. Representa el éxito y el resentimiento que alimentan la transformación de Walt.',
    'elliott schwartz': 'Excompañero de Walter y fundador de Gray Matter. Ofrece ayuda económica que Walt rechaza por orgullo herido.',
    'steven gomez': 'Compañero de Hank en la DEA. Leal y profesional. Su destino queda ligado a la cacería de Heisenberg.',
    'gomey': 'Compañero de Hank en la DEA. Leal y profesional. Su destino queda ligado a la cacería de Heisenberg.',
    'ted beneke': 'Jefe de Skyler. Se ve envuelto en problemas fiscales y en el plan de lavado de dinero de los White.',
    'jack welker': 'Líder de una banda de neo-nazis. Aliado temporal de Walter que termina traicionándolo, matando a Hank y esclavizando a Jesse.',
    'gale boetticher': 'Químico brillante y educado. Asistente de Gus en el laboratorio. Su muerte a manos de Jesse dispara la guerra abierta entre Walt y Gus.',
    'victor': 'Hombre de confianza de Gus. Eficiente y silencioso. Gus lo ejecuta frente a Walt y Jesse como advertencia tras un error en el laboratorio.',
    'tyrus kitt': 'Hombre de confianza de Gus. Vigilante y ejecutor; muere junto a Gus en la explosión del geriátrico.',
    'carmen molina': 'Directora de la escuela donde enseña Walter. Representa su vida “normal” antes de Heisenberg.',
    'wendy': 'Prostituta de la zona. Aparece en tramas menores ligadas a Jesse y al bajo mundo de Albuquerque.',
    'don eladio': 'Jefe del cartel mexicano. Controla el negocio desde el otro lado de la frontera; Gus lo elimina en una jugada maestra durante “Salud”.',
    'eladio vuente': 'Jefe del cartel mexicano. Controla el negocio desde el otro lado de la frontera; Gus lo elimina en una jugada maestra durante “Salud”.',
    'juan bolsa': 'Alto mando del cartel. Intermediario entre el cartel y las operaciones en Albuquerque; representa la vieja guardia que Gus desprecia.',
    'marco salamanca': 'Primo de los Salamanca. Sicario implacable que, junto a su hermano, llega a Albuquerque a vengar a Tuco y atacar a Hank.',
    'leonel salamanca': 'Primo de los Salamanca. Sicario casi silencioso; junto a Marco intenta matar a Hank en un ataque brutal.',
    'the cousins': 'Los primos Salamanca. Sicarios del cartel enviados a vengar a Tuco; su ataque a Hank cambia el rumbo de la investigación de la DEA.',
    'gonzo': 'Brazo derecho de Tuco. Su desaparición y muerte generan sospechas tempranas en la DEA y complican el rastro de Heisenberg.',
    'no-doz': 'Hombre de Tuco. Muere en el primer enfrentamiento serio de Walt y Jesse con el cartel callejero.',
    'krazy-8': 'Distribuidor que Walt y Jesse capturan en los primeros episodios. Walt debe decidir si matarlo o no; esa elección marca el inicio de Heisenberg.',
    'emilio koyama': 'Primo de Krazy-8 y socio inicial. Muere en el primer cocinado de Walt y Jesse, desencadenando toda la cadena de violencia.',
    'spooge': 'Adicto que roba a la red de Jesse. Su historia con su pareja y su hijo muestra el lado más sórdido de la calle.',
    'sky blue': 'Pareja de Spooge. Aparece en la trama de “Peekaboo”, donde Jesse se enfrenta a las consecuencias humanas del negocio.',
    'clovis': 'Dueño del desguace. Ayuda a Jesse y Walt a deshacerse del RV; es un contacto práctico del mundo ilegal.',
    'group leader': 'Líder del grupo de rehabilitación al que asiste Jesse. Representa el intento de Jesse de redimirse.',
    'chris mara': 'Hombre de Mike. Participa en operaciones de limpieza y seguridad del imperio de Gus.',
    'dennis markowski': 'Encargado de la lavandería industrial que oculta el superlaboratorio de Gus.',
    'duane chow': 'Dueño de una empresa de contenedores. Gus lo usa y luego lo elimina cuando ya no le sirve.',
    'kaylee ehrmantraut': 'Nieta de Mike. La razón por la que Mike trabaja y ahorra; humaniza al personaje más frío del entorno de Gus.',
    'stacey ehrmantraut': 'Nuera de Mike y madre de Kaylee. Parte de la vida familiar que Mike intenta proteger.',
    'francesca liddy': 'Secretaria de Saul Goodman. Cínica y leal a su sueldo; sobrevive al caos del bufete.',
    'kuby': 'Hombre de Saul. Ayuda en trabajos sucios y engaños, como el plan con Ted Beneke.',
    'patrick kuby': 'Hombre de Saul. Ayuda en trabajos sucios y engaños, como el plan con Ted Beneke.',
    'lawson': 'Traficante de armas. Le vende a Walt el revolver que usa en momentos clave del final.',
    'declan': 'Narco de Arizona. Compite y negocia con el imperio de Heisenberg en la última temporada.',
    'uncle jack': 'Jack Welker. Líder de la banda neo-nazi que traiciona a Walt, mata a Hank y secuestra a Jesse.',
    'kenny': 'Miembro de la banda de Jack. Participa en la masacre del desierto y en el cautiverio de Jesse.',
    'matt': 'Miembro de la banda de Jack. Forma parte del grupo que cambia el final de Walt y Jesse.',
    'fran': 'Enfermera del geriátrico de Héctor. Aparece en la trama final de Gus y el timbre.',
    'gretchen': 'Exnovia de Walter y socia de Gray Matter. Representa el éxito y el resentimiento que alimentan a Heisenberg.',
    'elliott': 'Excompañero de Walter y fundador de Gray Matter. Ofrece ayuda que Walt rechaza por orgullo.',
    'bogdan': 'Dueño del lavadero de autos donde Walt trabaja al principio. Walt lo compra más tarde con dinero del negocio.',
    'carmen': 'Directora de la escuela. Representa la vida normal de Walt antes de convertirse en Heisenberg.',
    'louis': 'Compañero de trabajo de Skyler en Beneke. Aparece en tramas de la vida “legal” de los White.',
    'dr. cruz': 'Médico que trata a Walt. Sus diagnósticos marcan giros importantes en la motivación de Heisenberg.',
    'holly white': 'Hija pequeña de Walter y Skyler. Símbolo de la familia que Walt dice proteger y que termina usando como rehén.',
    'holly': 'Hija pequeña de Walter y Skyler. Símbolo de la familia que Walt dice proteger y que termina usando como rehén.'
  };



const EXTRA_CAST = [
    { id: 9001, name: 'Hector Salamanca', actor: 'Mark Margolis', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/2/6798.jpg', role: 'Supporting', url: '#' },
    { id: 9002, name: 'Tuco Salamanca', actor: 'Raymond Cruz', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/188/470706.jpg', role: 'Supporting', url: '#' },
    { id: 9003, name: 'Leonel Salamanca', actor: 'Daniel Moncada', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/164/412471.jpg', role: 'Supporting', url: '#' },
    { id: 9004, name: 'Marco Salamanca', actor: 'Luis Moncada', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/164/412473.jpg', role: 'Supporting', url: '#' },
    { id: 9005, name: 'Don Eladio', actor: 'Steven Bauer', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/4/10217.jpg', role: 'Supporting', url: '#' },
    { id: 9006, name: 'Jane Margolis', actor: 'Krysten Ritter', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/158/395985.jpg', role: 'Supporting', url: '#' }
  ];

  function getBio(name) {
    if (!name) return 'Personaje del universo de Breaking Bad. Forma parte de la historia de Albuquerque y del imperio de Heisenberg.';
    const key = name.toLowerCase().trim();
    if (BIOS[key]) return BIOS[key];
    for (const k of Object.keys(BIOS)) {
      if (key.includes(k) || k.includes(key)) return BIOS[k];
    }
    return 'Personaje del universo de Breaking Bad. Intervienen en la trama criminal, familiar o policial que rodea a Walter White.';
  }

  let cast = [], list = [], focus = -1, episodes = [], epList = [];
  const $ = s => document.querySelector(s);
  const $$ = s => document.querySelectorAll(s);
  const grid = $('#cast-grid');
  const wait = $('#wait');
  const err = $('#err');
  const modal = $('#modal');
  const mBody = $('#m-body');
  const toasts = $('#toasts');
  const canvas = $('#bg-canvas');
  const ctx = canvas.getContext('2d');
  const pts = [];

  function sizeCanvas() {
    canvas.width = innerWidth;
    canvas.height = innerHeight;
  }
  function seed() {
    pts.length = 0;
    for (let i = 0; i < 50; i++) {
      pts.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        r: Math.random() * 1.8 + 0.3,
        vx: (Math.random() - 0.5) * 0.3,
        vy: (Math.random() - 0.5) * 0.3,
        a: Math.random() * 0.4 + 0.08,
        c: Math.random() > 0.4 ? '45,143,78' : '196,160,53'
      });
    }
  }
  function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    pts.forEach(p => {
      p.x += p.vx; p.y += p.vy;
      if (p.x < 0) p.x = canvas.width;
      if (p.x > canvas.width) p.x = 0;
      if (p.y < 0) p.y = canvas.height;
      if (p.y > canvas.height) p.y = 0;
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(${p.c},${p.a})`;
      ctx.fill();
    });
    requestAnimationFrame(draw);
  }

  async function loadCast() {
    wait.hidden = false;
    err.hidden = true;
    grid.innerHTML = '';
    try {
      const res = await fetch(`${API}/shows/${SHOW}/cast`);
      if (!res.ok) throw new Error('HTTP ' + res.status);
      const data = await res.json();
      cast = (data || []).map((it, i) => ({
        id: it.person?.id || i,
        name: it.character?.name || it.person?.name || '?',
        actor: it.person?.name || '',
        image: it.person?.image?.medium || '',
        role: i < 6 ? 'Main' : 'Supporting',
        url: it.person?.url || '#'
      }));
      const seen = new Set();
      cast = cast.filter(c => {
        const k = c.name.toLowerCase();
        if (seen.has(k)) return false;
        seen.add(k);
        return true;
      });
      // Añadir personajes clave de la trama si faltan en la API
      EXTRA_CAST.forEach(ex => {
        const k = ex.name.toLowerCase();
        if (!seen.has(k)) {
          cast.push(ex);
          seen.add(k);
        }
      });
      list = [...cast];
      render();
      $('#m-cast').textContent = cast.length;
      toast(cast.length + ' personajes cargados', 'ok');
    } catch (e) {
      err.hidden = false;
      err.textContent = 'Error API: ' + e.message + ' · Usando respaldo';
      cast = fallback();
      const seen = new Set(cast.map(c => c.name.toLowerCase()));
      EXTRA_CAST.forEach(ex => {
        const k = ex.name.toLowerCase();
        if (!seen.has(k)) { cast.push(ex); seen.add(k); }
      });
      list = [...cast];
      render();
      $('#m-cast').textContent = cast.length + '*';
    } finally {
      wait.hidden = true;
    }
  }

  async function loadEpisodes() {
    const epWait = $('#ep-wait');
    const epErr = $('#ep-err');
    const epListEl = $('#ep-list');
    epWait.hidden = false;
    epErr.hidden = true;
    epListEl.innerHTML = '';
    try {
      const res = await fetch(`${API}/shows/${SHOW}/episodes`);
      if (!res.ok) throw new Error('HTTP ' + res.status);
      const data = await res.json();
      episodes = (data || []).filter(e => e.type === 'regular').map(e => {
        const key = e.season + '-' + e.number;
        return {
          id: e.id,
          name: e.name,
          season: e.season,
          number: e.number,
          airdate: e.airdate,
          image: e.image?.medium || '',
          summary: (e.summary || '').replace(/<[^>]+>/g, ''),
          imdb: IMDB[key] || (e.rating?.average ? +(e.rating.average + 0.7).toFixed(1) : 8.0),
          blurb: SUM[key] || 'Episodio de Breaking Bad.',
          url: e.url || '#'
        };
      });
      episodes.sort((a, b) => b.imdb - a.imdb || a.season - b.season || a.number - b.number);
      filterEps();
      if (episodes.length) {
        $('#m-top').textContent = episodes[0].imdb.toFixed(1);
      }
      toast(episodes.length + ' episodios cargados', 'ok');
    } catch (e) {
      epErr.hidden = false;
      epErr.textContent = 'Error al cargar episodios: ' + e.message;
    } finally {
      epWait.hidden = true;
    }
  }

  function filterEps() {
    const season = $('#ep-season').value;
    epList = season === 'all'
      ? [...episodes]
      : episodes.filter(e => String(e.season) === season);
    renderEps();
  }

  function renderEps() {
    const el = $('#ep-list');
    el.innerHTML = '';
    if (!epList.length) {
      el.innerHTML = '<p style="text-align:center;color:var(--muted);padding:2rem">Sin episodios.</p>';
      return;
    }
    epList.forEach((ep, i) => {
      const rank = i + 1;
      let rankCls = '';
      if (rank === 1) rankCls = 'gold';
      else if (rank === 2) rankCls = 'silver';
      else if (rank === 3) rankCls = 'bronze';
      const card = document.createElement('article');
      card.className = 'ep-card';
      card.innerHTML = `
        <div class="ep-rank ${rankCls}">#${rank}</div>
        <img src="${ep.image}" alt="${ep.name}" loading="lazy" onerror="this.src='https://via.placeholder.com/120x68/181c17/2d8f4e?text=Br'">
        <div class="ep-info">
          <div class="title">${ep.name}</div>
          <div class="meta">T${ep.season} · E${ep.number} · ${ep.airdate || ''}</div>
          <div class="blurb">${ep.blurb}</div>
        </div>
        <div class="ep-score">${ep.imdb.toFixed(1)} <span>/10</span></div>`;
      card.onclick = () => openEp(ep);
      el.appendChild(card);
    });
  }

  function openEp(ep) {
    mBody.innerHTML = `
      ${ep.image ? `<img src="${ep.image}" alt="${ep.name}" onerror="this.style.display='none'">` : ''}
      <h3>${ep.name}</h3>
      <span class="badge">T${ep.season} · Episodio ${ep.number}</span>
      <p style="margin-bottom:0.4rem"><b>IMDb:</b> <span style="color:var(--green-bright);font-weight:700">${ep.imdb.toFixed(1)}/10</span></p>
      <p style="margin-bottom:0.5rem;color:var(--muted);font-size:0.85rem">${ep.airdate || ''}</p>
      <p style="margin-bottom:0.85rem;line-height:1.55">${ep.blurb || 'Sin sinopsis disponible.'}</p>
      <a class="btn btn-outline btn-sm" href="${ep.url}" target="_blank" rel="noopener">Ver en TVMaze</a>`;
    modal.hidden = false;
    document.body.style.overflow = 'hidden';
  }

  async function loadShow() {
    const el = $('#show-info');
    try {
      const res = await fetch(`${API}/shows/${SHOW}`);
      if (!res.ok) throw 0;
      const d = await res.json();
      const sum = (d.summary || '').replace(/<[^>]+>/g, '').slice(0, 280);
      el.innerHTML = `<p><b>${d.name}</b></p>
        <p>⭐ ${d.rating?.average || '—'} · 62 episodios · ${d.status}</p>
        <p>${(d.genres || []).join(' · ')} · ${d.network?.name || 'AMC'}</p>
        <p style="margin-top:0.5rem">${sum}...</p>`;
    } catch {
      el.innerHTML = '<p><b>Breaking Bad</b> (2008–2013)</p><p>Un profesor de química con cáncer se mete en el mundo de la metanfetamina junto a un exalumno.</p>';
    }
  }

  function fallback() {
    return [
      { id: 1, name: 'Walter White', actor: 'Bryan Cranston', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2400.jpg', role: 'Main', url: '#' },
      { id: 2, name: 'Jesse Pinkman', actor: 'Aaron Paul', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2401.jpg', role: 'Main', url: '#' },
      { id: 3, name: 'Skyler White', actor: 'Anna Gunn', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2402.jpg', role: 'Main', url: '#' },
      { id: 4, name: 'Hank Schrader', actor: 'Dean Norris', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2403.jpg', role: 'Main', url: '#' },
      { id: 5, name: 'Marie Schrader', actor: 'Betsy Brandt', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2404.jpg', role: 'Main', url: '#' },
      { id: 6, name: 'Walter White Jr.', actor: 'RJ Mitte', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2405.jpg', role: 'Main', url: '#' },
      { id: 7, name: 'Saul Goodman', actor: 'Bob Odenkirk', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2406.jpg', role: 'Main', url: '#' },
      { id: 8, name: 'Gustavo Fring', actor: 'Giancarlo Esposito', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2407.jpg', role: 'Main', url: '#' },
      { id: 9, name: 'Mike Ehrmantraut', actor: 'Jonathan Banks', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2408.jpg', role: 'Main', url: '#' },
      { id: 10, name: 'Hector Salamanca', actor: 'Mark Margolis', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2410.jpg', role: 'Supporting', url: '#' },
      { id: 11, name: 'Tuco Salamanca', actor: 'Raymond Cruz', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2411.jpg', role: 'Supporting', url: '#' },
      { id: 12, name: 'Jane Margolis', actor: 'Krysten Ritter', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2412.jpg', role: 'Supporting', url: '#' },
      { id: 13, name: 'Gale Boetticher', actor: 'David Costabile', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2413.jpg', role: 'Supporting', url: '#' },
      { id: 14, name: 'Todd Alquist', actor: 'Jesse Plemons', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2414.jpg', role: 'Supporting', url: '#' },
      { id: 15, name: 'Lydia Rodarte-Quayle', actor: 'Laura Fraser', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2415.jpg', role: 'Supporting', url: '#' },
      { id: 16, name: 'Jack Welker', actor: 'Michael Bowen', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2416.jpg', role: 'Supporting', url: '#' },
      { id: 17, name: 'Andrea Cantillo', actor: 'Emily Rios', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2417.jpg', role: 'Supporting', url: '#' },
      { id: 18, name: 'Huell Babineaux', actor: 'Lavell Crawford', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2418.jpg', role: 'Supporting', url: '#' },
      { id: 19, name: 'Badger', actor: 'Matt Jones', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2419.jpg', role: 'Supporting', url: '#' },
      { id: 20, name: 'Skinny Pete', actor: 'Charles Baker', image: 'https://static.tvmaze.com/uploads/images/medium_portrait/0/2420.jpg', role: 'Supporting', url: '#' }
    ];
  }

  function render() {
    grid.innerHTML = '';
    if (!list.length) {
      grid.innerHTML = '<p style="grid-column:1/-1;text-align:center;color:var(--muted)">Sin resultados.</p>';
      return;
    }
    list.forEach((c, i) => {
      const el = document.createElement('article');
      el.className = 'card';
      el.tabIndex = 0;
      el.dataset.i = i;
      el.innerHTML = `
        <img src="${c.image}" alt="${c.name}" loading="lazy" onerror="this.src='https://via.placeholder.com/200x280/181c17/2d8f4e?text=Br'">
        <div class="meta">
          <div class="nm">${c.name}</div>
          <div class="rl ${c.role === 'Main' ? 'main' : ''}">${c.role === 'Main' ? 'Principal' : 'Secundario'}</div>
        </div>`;
      el.addEventListener('click', () => open(c));
      el.addEventListener('keydown', e => {
        if (e.key === 'Enter' || e.key === ' ') { e.preventDefault(); open(c); }
      });
      grid.appendChild(el);
    });
    focus = -1;
  }

  function open(c) {
    const bio = getBio(c.name);
    mBody.innerHTML = `
      <img src="${c.image}" alt="${c.name}" onerror="this.src='https://via.placeholder.com/400x280/181c17/2d8f4e?text=Br'">
      <h3>${c.name}</h3>
      <span class="badge">${c.role === 'Main' ? 'Principal' : 'Secundario'}</span>
      ${c.actor ? `<p style="margin-bottom:0.5rem"><b>Actor:</b> ${c.actor}</p>` : ''}
      <p style="margin-bottom:0.85rem;line-height:1.55"><b>En la serie:</b> ${bio}</p>
      <a class="btn btn-outline btn-sm" href="${c.url}" target="_blank" rel="noopener">Ver más</a>`;
    modal.hidden = false;
    document.body.style.overflow = 'hidden';
  }

  function close() {
    modal.hidden = true;
    document.body.style.overflow = '';
  }

  function toast(msg, type) {
    const t = document.createElement('div');
    t.className = 'toast ' + (type || '');
    t.textContent = msg;
    toasts.appendChild(t);
    setTimeout(() => {
      t.style.opacity = '0';
      t.style.transition = 'opacity .3s';
      setTimeout(() => t.remove(), 300);
    }, 2600);
  }

  /* ===== QUIZ LOGIC v7 ===== */
  var QSTATE = {
    idx: 0,
    order: [],
    results: [],
    locked: false,
    best: 0,
    currentPhase: 1,
    phaseHits: { 1: 0, 2: 0, 3: 0 }
  };

  // Cargar mejor puntaje al iniciar (localStorage + sessionStorage + memoria)
  (function loadBest() {
    var v = 0;
    try { v = parseInt(localStorage.getItem('bb_quiz_best') || '0', 10) || 0; } catch (e1) {}
    if (!v) {
      try { v = parseInt(sessionStorage.getItem('bb_quiz_best') || '0', 10) || 0; } catch (e2) {}
    }
    QSTATE.best = v;
  })();

  function getBest() {
    return QSTATE.best || 0;
  }
  function setBest(n) {
    n = parseInt(n, 10) || 0;
    if (n > (QSTATE.best || 0)) {
      QSTATE.best = n;
      try { localStorage.setItem('bb_quiz_best', String(n)); } catch (e1) {}
      try { sessionStorage.setItem('bb_quiz_best', String(n)); } catch (e2) {}
      return true;
    }
    return false;
  }
  function showBest() {
    var b = getBest();
    var total = QUIZ.length;
    var txt = b > 0 ? ('Mejor puntaje: ' + b + '/' + total) : 'Mejor puntaje: —';
    var el = document.getElementById('quiz-best');
    if (el) el.textContent = txt;
  }
  function currentScore() {
    var s = 0;
    for (var i = 0; i < QSTATE.results.length; i++) {
      if (QSTATE.results[i] === true) s++;
    }
    return s;
  }
  function shuffle(arr) {
    var a = arr.slice();
    for (var i = a.length - 1; i > 0; i--) {
      var j = Math.floor(Math.random() * (i + 1));
      var t = a[i]; a[i] = a[j]; a[j] = t;
    }
    return a;
  }
  // Mezclar solo dentro de la fase actual
  function buildPhaseOrder(phaseNum) {
    var indices = [];
    for (var i = 0; i < QUIZ.length; i++) {
      if ((QUIZ[i].phase || 1) === phaseNum) indices.push(i);
    }
    return shuffle(indices);
  }
  function phaseQuestionCount(phaseNum) {
    var n = 0;
    for (var i = 0; i < QUIZ.length; i++) {
      if ((QUIZ[i].phase || 1) === phaseNum) n++;
    }
    return n;
  }
  function phaseScore(phaseNum) {
    // Contar aciertos solo de esta fase (usando results alineados con order)
    // results se acumulan en orden de juego; guardamos phaseResults por fase
    return QSTATE.phaseHits[phaseNum] || 0;
  }
  function hideAllQuizPanels() {
    document.getElementById('quiz-start').hidden = true;
    document.getElementById('quiz-play').hidden = true;
    document.getElementById('quiz-phase-end').hidden = true;
    document.getElementById('quiz-end').hidden = true;
  }
  function quizStart() {
    QSTATE.idx = 0;
    QSTATE.results = [];
    QSTATE.locked = false;
    QSTATE.currentPhase = 1;
    QSTATE.phaseHits = { 1: 0, 2: 0, 3: 0 };
    QSTATE.order = buildPhaseOrder(1);
    hideAllQuizPanels();
    document.getElementById('quiz-play').hidden = false;
    document.getElementById('quiz-score').textContent = '0';
    renderQuestion();
  }
  function renderQuestion() {
    QSTATE.locked = false;
    var q = QUIZ[QSTATE.order[QSTATE.idx]];
    var phase = QSTATE.currentPhase;
    var phaseTotal = QSTATE.order.length;

    document.getElementById('quiz-step').textContent = (QSTATE.idx + 1) + ' / ' + phaseTotal;
    document.getElementById('quiz-fill').style.width = (((QSTATE.idx + 1) / phaseTotal) * 100) + '%';
    document.getElementById('quiz-q').textContent = q.q;
    document.getElementById('quiz-score').textContent = String(currentScore());

    var badge = document.getElementById('quiz-phase');
    badge.textContent = 'Fase ' + phase + ' · ' + (PHASE_NAMES[phase] || '');
    badge.className = 'quiz-phase-badge p' + phase;

    // Mezclar el orden de las opciones al azar
    var indices = [];
    for (var k = 0; k < q.opts.length; k++) indices.push(k);
    for (var s = indices.length - 1; s > 0; s--) {
      var j = Math.floor(Math.random() * (s + 1));
      var tmp = indices[s];
      indices[s] = indices[j];
      indices[j] = tmp;
    }
    // Posición donde quedó la respuesta correcta después del shuffle
    var shuffledCorrect = 0;
    for (var c = 0; c < indices.length; c++) {
      if (indices[c] === q.a) {
        shuffledCorrect = c;
        break;
      }
    }
    QSTATE.currentCorrect = shuffledCorrect;

    var opts = document.getElementById('quiz-opts');
    opts.innerHTML = '';
    for (var i = 0; i < indices.length; i++) {
      (function (displayIndex, originalIndex) {
        var btn = document.createElement('button');
        btn.type = 'button';
        btn.className = 'quiz-opt';
        btn.textContent = q.opts[originalIndex];
        btn.onclick = function () { answer(displayIndex); };
        opts.appendChild(btn);
      })(i, indices[i]);
    }
  }
  function answer(choice) {
    if (QSTATE.locked) return;
    QSTATE.locked = true;

    var correct = QSTATE.currentCorrect;
    var isRight = (choice === correct);
    QSTATE.results.push(isRight);
    if (isRight) {
      QSTATE.phaseHits[QSTATE.currentPhase] = (QSTATE.phaseHits[QSTATE.currentPhase] || 0) + 1;
    }

    var btns = document.getElementById('quiz-opts').children;
    for (var i = 0; i < btns.length; i++) {
      btns[i].disabled = true;
      btns[i].onclick = null;
      if (i === correct) btns[i].className = 'quiz-opt correct';
      else if (i === choice) btns[i].className = 'quiz-opt wrong';
    }

    document.getElementById('quiz-score').textContent = String(currentScore());

    setTimeout(function () {
      QSTATE.idx = QSTATE.idx + 1;
      if (QSTATE.idx >= QSTATE.order.length) {
        showPhaseEnd();
      } else {
        renderQuestion();
      }
    }, 800);
  }
  function showPhaseEnd() {
    var phase = QSTATE.currentPhase;
    var hits = QSTATE.phaseHits[phase] || 0;
    var total = QSTATE.order.length;
    var next = PHASE_NEXT[phase];

    hideAllQuizPanels();
    document.getElementById('quiz-phase-end').hidden = false;
    document.getElementById('quiz-phase-icon').textContent = phase === 3 ? '🏆' : '✅';
    document.getElementById('quiz-phase-title').textContent = 'Fase ' + PHASE_NAMES[phase] + ' completada';
    document.getElementById('quiz-phase-score').textContent = hits + ' / ' + total;

    if (next) {
      document.getElementById('quiz-phase-msg').textContent =
        'Acertaste ' + hits + ' de ' + total + '. Ahora pasas a la fase ' + next + '.';
      document.getElementById('quiz-next-phase').textContent = 'Ir a fase ' + next;
      document.getElementById('quiz-next-phase').onclick = function () {
        startNextPhase();
      };
    } else {
      document.getElementById('quiz-phase-msg').textContent =
        'Acertaste ' + hits + ' de ' + total + ' en la fase final. Mira tu resultado.';
      document.getElementById('quiz-next-phase').textContent = 'Ver resultado final';
      document.getElementById('quiz-next-phase').onclick = function () {
        quizFinish();
      };
    }
  }
  function startNextPhase() {
    QSTATE.currentPhase = QSTATE.currentPhase + 1;
    QSTATE.idx = 0;
    QSTATE.locked = false;
    QSTATE.order = buildPhaseOrder(QSTATE.currentPhase);
    hideAllQuizPanels();
    document.getElementById('quiz-play').hidden = false;
    renderQuestion();
  }
  function quizFinish() {
    var score = currentScore();
    var total = QUIZ.length;
    var isNew = setBest(score);
    var bestNow = getBest();

    hideAllQuizPanels();
    document.getElementById('quiz-end').hidden = false;
    document.getElementById('quiz-final').textContent = score + ' / ' + total;

    var rank, msg, icon;
    // Umbrales sobre 33 preguntas
    if (score >= 28) {
      rank = 'Eres Heisenberg';
      msg = 'Dominas las tres fases del laboratorio. Nadie te llama a la puerta... tu eres el que llama.';
      icon = '👑';
    } else if (score >= 22) {
      rank = 'Eres un cocinero profesional';
      msg = 'Superaste las fases con nivel alto. Gus estaria impresionado.';
      icon = '⚗️';
    } else if (score >= 15) {
      rank = 'Eres un distribuidor de calle';
      msg = 'Pasaste las fases, pero te falta purificar el producto. Sigue cocinando.';
      icon = '📦';
    } else if (score >= 8) {
      rank = 'Eres un simple distribuidor';
      msg = 'Completaste el recorrido, pero apenas. Mejor llama a Saul.';
      icon = '🚗';
    } else {
      rank = 'Eres un civil inocente';
      msg = 'Las fases te superaron. Vuelve a Albuquerque y presta mas atencion.';
      icon = '🏠';
    }
    document.getElementById('quiz-end-icon').textContent = icon;
    document.getElementById('quiz-rank').textContent = rank;
    document.getElementById('quiz-msg').textContent = msg;

    var detail = 'Fácil: ' + (QSTATE.phaseHits[1] || 0) + '/11 · Intermedio: ' + (QSTATE.phaseHits[2] || 0) + '/11 · Difícil: ' + (QSTATE.phaseHits[3] || 0) + '/11';
    if (isNew) {
      document.getElementById('quiz-best-end').textContent = 'Nuevo record! ' + bestNow + '/' + total + '  ·  ' + detail;
    } else {
      document.getElementById('quiz-best-end').textContent = 'Tu puntaje: ' + score + '/' + total + '  ·  Mejor: ' + bestNow + '/' + total + '  ·  ' + detail;
    }
    var startBest = document.getElementById('quiz-best');
    if (startBest) startBest.textContent = 'Mejor puntaje: ' + bestNow + '/' + total;

    if (isNew) toast('Nuevo record: ' + bestNow + '/' + total, 'ok');
  }
  function quizReset() {
    hideAllQuizPanels();
    document.getElementById('quiz-start').hidden = false;
    var b = getBest();
    var total = QUIZ.length;
    var startBest = document.getElementById('quiz-best');
    if (startBest) {
      startBest.textContent = b > 0 ? ('Mejor puntaje: ' + b + '/' + total) : 'Mejor puntaje: —';
    }
  }

  function go(id) {
    $$('.view').forEach(v => v.classList.remove('on'));
    $$('.nav-links a').forEach(a => a.classList.remove('on'));
    const s = document.getElementById(id);
    if (s) s.classList.add('on');
    const a = $(`.nav-links a[data-v="${id}"]`);
    if (a) a.classList.add('on');
    $('#nav').classList.remove('open');
  }

  function filter() {
    const q = $('#q').value.trim().toLowerCase();
    const f = $('#filter').value;
    list = cast.filter(c => {
      const okN = c.name.toLowerCase().includes(q) || (c.actor || '').toLowerCase().includes(q);
      const okR = f === 'all' || c.role === f;
      return okN && okR;
    });
    render();
  }

  function keys(e) {
    if ($('#cast').classList.contains('on')) {
      const cards = $$('.card');
      if (!cards.length) return;
      if (e.key === 'ArrowRight' || e.key === 'ArrowDown') {
        e.preventDefault();
        focus = Math.min(focus + 1, cards.length - 1);
        cards[focus].focus();
        cards.forEach(c => c.classList.remove('focus'));
        cards[focus].classList.add('focus');
      }
      if (e.key === 'ArrowLeft' || e.key === 'ArrowUp') {
        e.preventDefault();
        focus = Math.max(focus - 1, 0);
        cards[focus].focus();
        cards.forEach(c => c.classList.remove('focus'));
        cards[focus].classList.add('focus');
      }
    }
    if (e.key === 'Escape' && !modal.hidden) close();
  }

  function init() {
    sizeCanvas(); seed(); draw();
    addEventListener('resize', () => { sizeCanvas(); seed(); });
    $$('.nav-links a').forEach(a => {
      a.addEventListener('click', e => { e.preventDefault(); go(a.dataset.v); });
    });
    $('#logo-home').addEventListener('click', e => { e.preventDefault(); go('home'); });
    $('#burger').onclick = () => $('#nav').classList.toggle('open');
    $('#go-cast').onclick = () => go('cast');
    const goEps = $('#go-eps');
    if (goEps) goEps.onclick = () => go('episodes');
    $('#q').oninput = filter;
    $('#filter').onchange = filter;
    $('#reload').onclick = loadCast;
    $('#ep-season').onchange = filterEps;
    $('#ep-reload').onclick = loadEpisodes;
    $('#m-close').onclick = close;
    modal.querySelector('.shade').onclick = close;
    // Quiz
    $('#quiz-begin').onclick = quizStart;
    $('#quiz-retry').onclick = quizStart;
    $('#quiz-home').onclick = function () { quizReset(); go('home'); };
    var exitBtn = document.getElementById('quiz-exit');
    if (exitBtn) exitBtn.onclick = function () { quizReset(); };
    var exitPhaseBtn = document.getElementById('quiz-exit-phase');
    if (exitPhaseBtn) exitPhaseBtn.onclick = function () { quizReset(); };
    showBest();
    document.addEventListener('keydown', keys);
    loadCast();
    loadEpisodes();
  }
  if (document.readyState === 'loading') document.addEventListener('DOMContentLoaded', init);
  else init();
})();
</script>
</body>
</html>
