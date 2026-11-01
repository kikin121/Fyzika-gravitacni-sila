# Fyzika-gravitacni-sila


<!DOCTYPE html>
<html lang="cs">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Gravitační a tíhová síla</title>
<style>
  * { box-sizing: border-box; }
  body { margin: 0; min-height: 100vh; background: #1d1a2e; color: #f4efe6; font-family: "Trebuchet MS", "Segoe UI", Arial, sans-serif; }
  .app { width: min(1400px, 100%); margin: 0 auto; padding: 20px; }
  header { display: flex; justify-content: space-between; align-items: baseline; gap: 12px; margin-bottom: 14px; }
  h1 { margin: 0; font-size: clamp(18px, 2.4vw, 26px); }
  header span { font-size: 13px; color: #b9b2cc; }
  .deck { width: 100%; aspect-ratio: 16/9; background: #000; border: 3px solid #141036; border-radius: 12px; overflow: hidden; box-shadow: 8px 8px 0 #ff6fa5; }
  .deck:fullscreen { border: 0; border-radius: 0; box-shadow: none; aspect-ratio: auto; width: 100vw; height: 100vh; }
  canvas { display: block; width: 100%; height: 100%; object-fit: contain; }
  .bar { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; justify-content: space-between; margin-top: 22px; }
  .nav { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; }
  button, select { font: inherit; font-size: 14px; padding: 10px 14px; border-radius: 10px; border: 2px solid #141036; background: #f4efe6; color: #141036; cursor: pointer; }
  button:hover, select:hover { background: #fff; }
  button:disabled { opacity: .4; cursor: not-allowed; }
  button:focus-visible, select:focus-visible { outline: 3px solid #ffd54a; outline-offset: 2px; }
  .primary { background: #ffd54a; font-weight: 700; box-shadow: 4px 4px 0 #ff6fa5; }
  .primary:hover { background: #ffe07a; }
  #counter { min-width: 56px; text-align: center; font-size: 14px; color: #d8d2e8; }
  select { max-width: min(340px, 70vw); }
  #status { min-height: 20px; margin: 14px 0 0; font-size: 13px; color: #b9b2cc; }
  @media (max-width: 640px) { .app { padding: 10px; } .nav { width: 100%; } select { flex: 1; min-width: 0; } .primary { width: 100%; } }
</style>
</head>
<body>
<main class="app">
  <header><h1>Gravitační a tíhová síla</h1><span>Fyzika · střední škola · 13 snímků</span></header>
  <div class="deck" id="deck"><canvas id="slide" width="1920" height="1080" role="img" aria-label="Snímek prezentace"></canvas></div>
  <div class="bar">
    <div class="nav">
      <button id="prev" type="button">← Zpět</button>
      <span id="counter" aria-live="polite"></span>
      <button id="next" type="button">Dále →</button>
      <select id="picker" aria-label="Vybrat snímek"></select>
      <button id="full" type="button">Celá obrazovka</button>
    </div>
    <button id="download" class="primary" type="button">Stáhnout PowerPoint (.pptx)</button>
  </div>
  <p id="status" role="status">Snímky přepínáš šipkami. V PowerPointu jsou texty editovatelné, ilustrace jsou vložené jako obrázek na pozadí.</p>
</main>

<script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script>
<script>
"use strict";
const W = 1600, H = 900, INK = "#141036";

/* ---------- písma ---------- */
const FONTS = {
  H: { css: '"Arial Black","Segoe UI Black","Helvetica Neue",Arial,sans-serif', ppt: "Arial Black", w: 900, b: 0 },
  B: { css: '"Trebuchet MS","Segoe UI",Arial,sans-serif', ppt: "Trebuchet MS", w: 700, b: 1 },
  S: { css: '"Segoe Print","Bradley Hand","Comic Sans MS","Marker Felt",cursive', ppt: "Segoe Print", w: 400, b: 0 }
};
let EXPORT = null; // při exportu se texty sbírají místo kreslení

/* ---------- barevné motivy ---------- */
const dk = (bg, blob) => ({ bg, blob, tx: "#FFF4E0", kick: "#FFD54A", star: "#FFD54A", star2: "#4DE1C1", pink: "#FF6FA5", sq: "#FFD54A", sbg: "#FFD54A", sfg: "#1B1650", ssh: "#FF6FA5", dash: "#FFF4E0" });
const lt = (bg, blob, extra) => Object.assign({ bg, blob, tx: "#1B1650", kick: "#7A3BFF", star: "#FF6FA5", star2: "#7A3BFF", pink: "#FFB02E", sq: "#FF6FA5", sbg: "#7A3BFF", sfg: "#FFF4E0", ssh: "#141036", dash: "#1B2A5A", light: true }, extra || {});
const TH = {
  violet: dk("#2A1B6B", "#3A2A8E"),
  navy: dk("#13214F", "#1E3377"),
  plum: dk("#4A1D63", "#68307F"),
  teal: dk("#0E3A4A", "#16566A"),
  cream: lt("#FFF1D6", "#FFD9A8"),
  sky: lt("#D9E9FF", "#FFE08A"),
  paper: lt("#FFFDF4", "#FFE6F0", { grid: true })
};

/* ---------- obsah ---------- */
const slides = [
  { th: "violet", art: "intro", kick: "od jablka k oběžné dráze", title: "Úvod – gravitace kolem nás", bullets: ["Přitahuje každá dvě tělesa.", "Udržuje atmosféru, Měsíc i planety.", "Na Zemi ji vnímáme při pádu těles."], st: "Stejný zákon platí na Zemi i ve vesmíru." },
  { th: "navy", art: "newton", kick: "jak silné je přitahování?", title: "Newtonův gravitační zákon", bullets: ["Větší hmotnosti → větší síla.", "Dvojnásobná vzdálenost → čtvrtinová síla.", "Síly působí na obě tělesa stejně velké."], st: "F = G · m₁m₂ / r²", big: true },
  { th: "plum", art: "field", kick: "prostor, kde působí síla", title: "Gravitační pole a siločáry", bullets: ["Každé těleso vytváří gravitační pole.", "Siločáry míří k tělesu.", "Hustší siločáry značí silnější pole."], st: "Pole existuje i bez zkušebního tělesa." },
  { th: "cream", art: "fall", kick: "volný pád", title: "Gravitační zrychlení", bullets: ["Určuje, jak rychle roste rychlost pádu.", "Na povrchu Země přibližně 9,81 m/s².", "S rostoucí vzdáleností od Země klesá."], st: "g₀ = GM / r²", big: true },
  { th: "teal", art: "weight", kick: "podobné pojmy, jiný význam", title: "Tíhová síla, tíha a tíhové pole", bullets: ["Tíhová síla působí na těleso.", "Tíha je síla tělesa na podložku či závěs.", "Ve volném pádu může být tíha nulová."], st: "Na neotáčející se Zemi: F ≈ m · g" },
  { th: "violet", art: "rotation", kick: "rovník ≠ pól", title: "Tíhové pole Země a její rotace", bullets: ["Rotace mění výslednou tíhovou sílu.", "Na rovníku je účinek rotace největší.", "Roli hraje i zploštění Země."], st: "Tíhové zrychlení není všude stejné." },
  { th: "navy", art: "motion", kick: "pád, vrh a oběh", title: "Pohyb těles v gravitačním poli", bullets: ["Při pádu těleso zrychluje k Zemi.", "Vodorovný vrh má zakřivenou dráhu.", "Družice stále padá, ale míjí Zemi."], st: "Oběžná dráha = volný pád kolem Země." },
  { th: "sky", art: "kepler", kick: "pravidla pohybu planet", title: "Keplerovy zákony", bullets: ["Planety obíhají po elipsách.", "Průvodič opíše za stejný čas stejnou plochu.", "Vzdálenější planeta obíhá pomaleji."], st: "T² / a³ = konstanta", big: true },
  { th: "plum", art: "speeds", kick: "jak opustit Zemi", title: "Kosmické rychlosti", bullets: ["1. kosmická: přibližně 7,9 km/s.", "2. kosmická: přibližně 11,2 km/s.", "Ideální hodnoty bez odporu vzduchu."], st: "Oběžná dráha × únik ze Země" },
  { th: "teal", art: "tides", kick: "Měsíc hýbe oceány", title: "Příliv a odliv", bullets: ["Rozhoduje rozdíl gravitačního působení.", "Na opačných stranách vznikají přílivové vyvýšeniny.", "Přispívá také Slunce."], st: "Většina míst zažívá zhruba dva přílivy denně." },
  { th: "violet", art: "worlds", kick: "stejná hmotnost, jiná tíha", title: "Gravitační pole dalších vesmírných těles", bullets: ["Měsíc: g ≈ 1,62 m/s².", "Mars: g ≈ 3,71 m/s².", "Země: g ≈ 9,81 m/s²."], st: "Hmotnost zůstává, tíha se mění." },
  { th: "paper", art: "calc", kick: "dosaď a porovnej", title: "Praktické výpočty", bf: "S", bullets: ["Člověk o hmotnosti 60 kg na Zemi.", "F = m · g = 60 · 9,81 ≈ 589 N", "Na Měsíci: F = 60 · 1,62 ≈ 97 N"], st: "Ve vzdálenosti 2r od středu Země: g₀ / 4" },
  { th: "navy", art: "summary", kick: "co si zapamatovat", title: "Zajímavosti a shrnutí", bullets: ["Gravitace působí mezi všemi tělesy.", "Tíha není totéž co hmotnost.", "Jedna síla vysvětluje pád, oběh i příliv."], st: "Od jablka až po pohyb planet." }
];

/* ---------- text ---------- */
function measure(c, o) {
  const F = FONTS[o.f || "B"];
  c.save(); c.font = `${F.w} ${o.s}px ${F.css}`;
  const lines = []; let cur = "";
  for (const w of o.t.split(" ")) {
    const n = cur ? cur + " " + w : w;
    if (cur && c.measureText(n).width > o.w) { lines.push(cur); cur = w; } else cur = n;
  }
  lines.push(cur);
  const widest = Math.max(...lines.map(l => c.measureText(l).width));
  const lh = o.lh || Math.round(o.s * 1.25);
  c.restore();
  return { lines, widest, lh, h: lines.length * lh, F };
}
function T(c, o) {
  const m = measure(c, o), align = o.a || "l";
  const cx = o.x + o.w / 2, cy = o.y + m.h / 2;
  if (EXPORT) { EXPORT.push({ o, m, align, cx, cy }); return m; }
  c.save();
  c.font = `${m.F.w} ${o.s}px ${m.F.css}`; c.fillStyle = o.c; c.textBaseline = "middle";
  c.textAlign = align === "c" ? "center" : "left";
  c.translate(cx, cy); if (o.r) c.rotate(o.r * Math.PI / 180);
  m.lines.forEach((l, i) => c.fillText(l, align === "c" ? 0 : -o.w / 2, -m.h / 2 + m.lh * (i + .5)));
  c.restore();
  return m;
}

/* ---------- kreslicí pomůcky ---------- */
function fillStroke(c, fill, lw = 5) {
  if (fill) { c.fillStyle = fill; c.fill(); }
  if (lw) { c.strokeStyle = INK; c.lineWidth = lw; c.lineJoin = "round"; c.lineCap = "round"; c.stroke(); }
}
function circle(c, x, y, r, fill, lw = 5) { c.beginPath(); c.arc(x, y, r, 0, Math.PI * 2); fillStroke(c, fill, lw); }
function rrect(c, x, y, w, h, r, fill, lw = 5) { c.beginPath(); c.roundRect(x, y, w, h, r); fillStroke(c, fill, lw); }
function blob(c, x, y, s, pts) {
  const n = pts.length, P = pts.map(p => [x + p[0] * s, y + p[1] * s]);
  c.beginPath();
  c.moveTo((P[n - 1][0] + P[0][0]) / 2, (P[n - 1][1] + P[0][1]) / 2);
  for (let i = 0; i < n; i++) { const a = P[i], b = P[(i + 1) % n]; c.quadraticCurveTo(a[0], a[1], (a[0] + b[0]) / 2, (a[1] + b[1]) / 2); }
  c.closePath();
}
function sparkle(c, x, y, r, col) {
  c.fillStyle = col; c.beginPath(); c.moveTo(x, y - r);
  c.quadraticCurveTo(x + r * .14, y - r * .14, x + r, y); c.quadraticCurveTo(x + r * .14, y + r * .14, x, y + r);
  c.quadraticCurveTo(x - r * .14, y + r * .14, x - r, y); c.quadraticCurveTo(x - r * .14, y - r * .14, x, y - r); c.fill();
}
function plus(c, x, y, r, col) { c.save(); c.strokeStyle = col; c.lineWidth = 5; c.lineCap = "round"; c.beginPath(); c.moveTo(x - r, y); c.lineTo(x + r, y); c.moveTo(x, y - r); c.lineTo(x, y + r); c.stroke(); c.restore(); }
function dash(c, col, lw, fn, pat = [2, 14], al = 1) { c.save(); c.globalAlpha = al; c.setLineDash(pat); c.lineCap = "round"; c.lineWidth = lw; c.strokeStyle = col; c.beginPath(); fn(); c.stroke(); c.restore(); }
function thickLine(c, x1, y1, x2, y2, w, fill) { c.save(); c.lineCap = "round"; c.beginPath(); c.moveTo(x1, y1); c.lineTo(x2, y2); c.strokeStyle = INK; c.lineWidth = w + 10; c.stroke(); c.strokeStyle = fill; c.lineWidth = w; c.stroke(); c.restore(); }
function blockArrow(c, x1, y1, x2, y2, w, fill) {
  const L = Math.hypot(x2 - x1, y2 - y1), hl = w * 1.2;
  c.save(); c.translate(x1, y1); c.rotate(Math.atan2(y2 - y1, x2 - x1));
  c.beginPath(); c.moveTo(0, -w / 2); c.lineTo(L - hl, -w / 2); c.lineTo(L - hl, -w); c.lineTo(L, 0); c.lineTo(L - hl, w); c.lineTo(L - hl, w / 2); c.lineTo(0, w / 2); c.closePath();
  fillStroke(c, fill, 4); c.restore();
}
function doodleArrow(c, x1, y1, cx, cy, x2, y2, col, lw = 4) {
  c.save(); c.strokeStyle = col; c.lineWidth = lw; c.lineCap = "round"; c.lineJoin = "round";
  c.beginPath(); c.moveTo(x1, y1); c.quadraticCurveTo(cx, cy, x2, y2); c.stroke();
  const a = Math.atan2(y2 - cy, x2 - cx);
  c.beginPath(); c.moveTo(x2 - 20 * Math.cos(a - .5), y2 - 20 * Math.sin(a - .5)); c.lineTo(x2, y2); c.lineTo(x2 - 20 * Math.cos(a + .5), y2 - 20 * Math.sin(a + .5)); c.stroke();
  c.restore();
}
function chip(c, t, cx, cy, o = {}) {
  const s = o.s || 26, f = o.f || "B", r = o.r || 0;
  const m = measure(c, { t, w: 900, s, f });
  const w = m.widest + 38, h = m.h + 18;
  c.save(); c.translate(cx, cy); c.rotate(r * Math.PI / 180);
  rrect(c, -w / 2 + 5, -h / 2 + 5, w, h, h / 2.2, INK, 0);
  rrect(c, -w / 2, -h / 2, w, h, h / 2.2, o.bg || "#FFD54A", 4);
  c.restore();
  T(c, { t, x: cx - (m.widest + 8) / 2, y: cy - m.h / 2, w: m.widest + 8, s, f, c: o.fg || INK, a: "c", r });
}
function G(cx, cy, deg, x, y) { const a = deg * Math.PI / 180; return [cx + x * Math.cos(a) - y * Math.sin(a), cy + x * Math.sin(a) + y * Math.cos(a)]; }

/* ---------- objekty ---------- */
function planet(c, x, y, r, base, detail) {
  c.save(); c.beginPath(); c.arc(x, y, r, 0, 7); c.fillStyle = base; c.fill(); c.clip();
  if (detail) detail(c, x, y, r);
  c.beginPath(); c.arc(x, y, r + 2, 0, 7); c.arc(x - r * .2, y - r * .2, r + 2, 0, 7); c.fillStyle = "rgba(10,8,50,.22)"; c.fill("evenodd");
  c.beginPath(); c.ellipse(x - r * .5, y - r * .55, r * .14, r * .07, -.7, 0, 7); c.fillStyle = "rgba(255,255,255,.5)"; c.fill();
  c.restore();
  circle(c, x, y, r, null, 5);
}
const earthDetail = (c, x, y, r) => {
  c.fillStyle = "#5BCB7B";
  blob(c, x, y, r, [[-.55, -.4], [-.2, -.65], [.15, -.5], [.05, -.2], [-.25, -.05], [-.55, -.12]]); c.fill();
  blob(c, x, y, r, [[.2, .05], [.6, -.05], [.8, .25], [.6, .6], [.25, .65], [.1, .35]]); c.fill();
  blob(c, x, y, r, [[-.7, .35], [-.4, .3], [-.3, .6], [-.55, .75]]); c.fill();
  c.fillStyle = "rgba(255,255,255,.85)";
  blob(c, x, y, r, [[-.1, .0], [.12, -.1], [.3, -.02], [.2, .1], [0, .12]]); c.fill();
  blob(c, x, y, r, [[-.65, -.75], [-.4, -.85], [-.2, -.75], [-.4, -.65]]); c.fill();
};
const moonDetail = (c, x, y, r) => {
  c.fillStyle = "#B3B7D6";
  [[-.35, -.3, .22], [.3, -.1, .16], [-.1, .4, .2], [.45, .45, .1], [-.6, .2, .09]].forEach(k => { c.beginPath(); c.arc(x + k[0] * r, y + k[1] * r, k[2] * r, 0, 7); c.fill(); });
};
const marsDetail = (c, x, y, r) => {
  c.fillStyle = "#C8472A";
  [[-.3, -.2, .2], [.35, .15, .15], [-.1, .45, .17], [.5, -.4, .09]].forEach(k => { c.beginPath(); c.arc(x + k[0] * r, y + k[1] * r, k[2] * r, 0, 7); c.fill(); });
  c.fillStyle = "#fff"; c.beginPath(); c.ellipse(x, y - r * .95, r * .4, r * .2, 0, 0, 7); c.fill();
};
function sun(c, x, y, r) {
  c.save(); c.translate(x, y); c.beginPath();
  for (let i = 0; i < 12; i++) {
    const a = i * Math.PI / 6;
    c.moveTo(Math.cos(a - .17) * r * 1.1, Math.sin(a - .17) * r * 1.1);
    c.lineTo(Math.cos(a) * r * 1.55, Math.sin(a) * r * 1.55);
    c.lineTo(Math.cos(a + .17) * r * 1.1, Math.sin(a + .17) * r * 1.1);
    c.closePath();
  }
  fillStroke(c, "#FFB02E", 4); c.restore();
  circle(c, x, y, r, "#FFD23F", 5);
}
function apple(c, x, y, r) {
  c.save(); c.translate(x, y); c.scale(r / 50, r / 50);
  c.lineCap = "round";
  c.beginPath(); c.moveTo(0, -38); c.quadraticCurveTo(4, -60, 16, -68); c.strokeStyle = INK; c.lineWidth = 14; c.stroke(); c.strokeStyle = "#8B5A2B"; c.lineWidth = 6; c.stroke();
  c.beginPath(); c.moveTo(8, -52); c.quadraticCurveTo(30, -82, 62, -66); c.quadraticCurveTo(44, -40, 8, -52); c.closePath(); fillStroke(c, "#5BCB7B", 4);
  blob(c, 0, 0, 50, [[0, -.72], [.55, -.9], [1, -.3], [.85, .5], [.35, 1], [0, .85], [-.35, 1], [-.85, .5], [-1, -.3], [-.55, -.9]]); fillStroke(c, "#FF4D5E", 5);
  c.beginPath(); c.ellipse(-26, -14, 6, 12, .5, 0, 7); c.fillStyle = "rgba(255,255,255,.6)"; c.fill();
  c.restore();
}
function satellite(c, x, y, s, rot = 0) {
  c.save(); c.translate(x, y); c.rotate(rot * Math.PI / 180); c.scale(s, s);
  for (const sx of [-1, 1]) {
    thickLine(c, sx * 34, 0, sx * 58, 0, 8, "#C9CCE0");
    const px = sx < 0 ? -146 : 56;
    rrect(c, px, -26, 90, 52, 5, "#3C7BFF", 5);
    c.strokeStyle = "rgba(255,255,255,.85)"; c.lineWidth = 2.5; c.beginPath();
    for (let k = 1; k < 3; k++) { c.moveTo(px + k * 30, -26); c.lineTo(px + k * 30, 26); }
    c.moveTo(px, 0); c.lineTo(px + 90, 0); c.stroke();
  }
  thickLine(c, 0, -36, 0, -62, 5, "#C9CCE0"); circle(c, 0, -66, 8, "#FF4D5E", 4);
  rrect(c, -38, -38, 76, 76, 14, "#FFD54A", 5); circle(c, 0, 0, 16, "#FF6FA5", 4);
  c.restore();
}
function rocket(c, x, y, s, rot = 0) {
  c.save(); c.translate(x, y); c.rotate(rot * Math.PI / 180); c.scale(s, s);
  c.beginPath(); c.moveTo(-18, 88); c.quadraticCurveTo(0, 190, 18, 88); c.closePath(); fillStroke(c, "#FFB02E", 5);
  c.beginPath(); c.moveTo(-9, 88); c.quadraticCurveTo(0, 142, 9, 88); c.closePath(); fillStroke(c, "#FFE066", 0);
  c.beginPath(); c.moveTo(-34, 30); c.lineTo(-68, 100); c.lineTo(-30, 86); c.closePath(); fillStroke(c, "#FF6FA5", 5);
  c.beginPath(); c.moveTo(34, 30); c.lineTo(68, 100); c.lineTo(30, 86); c.closePath(); fillStroke(c, "#FF6FA5", 5);
  c.beginPath(); c.moveTo(0, -118); c.bezierCurveTo(56, -64, 44, 40, 34, 92); c.lineTo(-34, 92); c.bezierCurveTo(-44, 40, -56, -64, 0, -118); c.closePath(); fillStroke(c, "#F1F3FF", 5);
  c.beginPath(); c.moveTo(0, -118); c.bezierCurveTo(26, -92, 38, -70, 44, -52); c.lineTo(-44, -52); c.bezierCurveTo(-38, -70, -26, -92, 0, -118); c.closePath(); fillStroke(c, "#FF4D5E", 5);
  circle(c, 0, -6, 22, "#2B2D7A", 5); circle(c, -6, -12, 6, "rgba(255,255,255,.6)", 0);
  c.restore();
}
function astronaut(c, x, y, s, rot = 0) {
  c.save(); c.translate(x, y); c.rotate(rot * Math.PI / 180); c.scale(s, s);
  rrect(c, -72, 40, 144, 130, 24, "#C9CCE0", 5);
  rrect(c, -46, 180, 40, 110, 16, "#F1F3FF", 5); rrect(c, 6, 180, 40, 110, 16, "#F1F3FF", 5);
  rrect(c, -54, 268, 52, 32, 12, "#FF6FA5", 5); rrect(c, 2, 268, 52, 32, 12, "#FF6FA5", 5);
  rrect(c, -56, 56, 112, 140, 30, "#F1F3FF", 5);
  rrect(c, -30, 86, 60, 40, 8, "#FFD54A", 4); circle(c, -12, 106, 6, "#FF4D5E", 3); circle(c, 12, 106, 6, "#3FA9F5", 3);
  thickLine(c, -48, 84, -98, 150, 34, "#F1F3FF"); circle(c, -100, 156, 20, "#FF6FA5", 5);
  thickLine(c, 48, 84, 104, 22, 34, "#F1F3FF"); circle(c, 108, 12, 20, "#FF6FA5", 5);
  circle(c, 0, 0, 72, "#F1F3FF", 5);
  rrect(c, -50, -36, 100, 70, 32, "#2B2D7A", 5);
  c.beginPath(); c.ellipse(-24, -14, 14, 8, -.5, 0, 7); c.fillStyle = "rgba(255,255,255,.55)"; c.fill();
  c.restore();
}

/* ---------- ilustrace jednotlivých snímků ---------- */
const ART = {
  intro(c, th) {
    dash(c, th.dash, 4, () => c.arc(1250, 650, 350, 0, 7), [2, 14], .6);
    planet(c, 1250, 650, 265, "#2E86E0", earthDetail);
    planet(c, 930, 470, 48, "#D7DAEE", moonDetail);
    satellite(c, 1510, 416, .55, 25);
    c.save(); c.strokeStyle = th.star; c.lineWidth = 6; c.lineCap = "round";
    [-34, 0, 34].forEach(d => { c.beginPath(); c.moveTo(1180 + d, 70); c.lineTo(1180 + d, 125 + Math.abs(d) * .3); c.stroke(); }); c.restore();
    apple(c, 1180, 235, 46);
    dash(c, th.dash, 4, () => { c.moveTo(1180, 300); c.lineTo(1180, 372); }, [2, 12], .8);
    T(c, { t: "jablko padá!", x: 1235, y: 170, w: 260, s: 30, f: "S", c: th.star, a: "c", r: -5 });
    doodleArrow(c, 1275, 215, 1260, 240, 1232, 250, th.tx, 4);
    T(c, { t: "Měsíc", x: 860, y: 530, w: 140, s: 26, f: "S", c: th.tx, a: "c" });
  },
  newton(c, th) {
    planet(c, 1020, 440, 135, "#2E86E0", earthDetail);
    planet(c, 1440, 440, 72, "#D7DAEE", moonDetail);
    blockArrow(c, 1168, 440, 1262, 440, 24, th.pink);
    blockArrow(c, 1366, 440, 1272, 440, 24, th.star);
    chip(c, "F", 1215, 385, { bg: th.pink, fg: INK });
    chip(c, "F", 1320, 385, { bg: th.star, fg: INK });
    chip(c, "m₁", 1020, 630, { bg: "#FFF4E0" });
    chip(c, "m₂", 1440, 580, { bg: "#FFF4E0" });
    dash(c, th.dash, 3, () => { c.moveTo(1020, 700); c.lineTo(1440, 700); }, [10, 10], .8);
    c.save(); c.strokeStyle = th.dash; c.lineWidth = 4; c.beginPath(); c.moveTo(1020, 685); c.lineTo(1020, 715); c.moveTo(1440, 685); c.lineTo(1440, 715); c.stroke(); c.restore();
    chip(c, "r", 1230, 700, { bg: "#4DE1C1", s: 28 });
    T(c, { t: "2× dál → síla ¼", x: 1060, y: 740, w: 340, s: 30, f: "S", c: th.star, a: "c", r: -2 });
  },
  field(c, th) {
    [235, 335].forEach(r => dash(c, th.dash, 3, () => c.arc(1180, 450, r, 0, 7), [3, 13], .4));
    for (let k = 0; k < 12; k++) {
      const a = k * Math.PI / 6, x1 = 1180 + Math.cos(a) * 345, y1 = 450 + Math.sin(a) * 345, x2 = 1180 + Math.cos(a) * 172, y2 = 450 + Math.sin(a) * 172;
      doodleArrow(c, x1, y1, (x1 + x2) / 2, (y1 + y2) / 2, x2, y2, th.star, 5);
    }
    planet(c, 1180, 450, 140, "#2E86E0", earthDetail);
    circle(c, 1405, 580, 16, th.pink, 4);
    T(c, { t: "zkušební těleso", x: 1290, y: 616, w: 230, s: 26, f: "S", c: th.tx, a: "c" });
    T(c, { t: "siločáry", x: 1380, y: 80, w: 200, s: 32, f: "S", c: th.tx, a: "c", r: 4 });
    doodleArrow(c, 1470, 128, 1490, 170, 1434, 200, th.tx, 4);
  },
  fall(c, th) {
    dash(c, th.dash, 3, () => { c.moveTo(1010, 150); c.lineTo(1010, 640); }, [2, 14], .6);
    planet(c, 1200, 1140, 440, "#2E86E0", earthDetail);
    const ys = [150, 204, 366, 635], lab = ["t = 0 s", "1 s · 9,8 m/s", "2 s · 19,6 m/s", "3 s · 29,4 m/s"];
    ys.forEach((y, i) => {
      c.save(); if (i === 0) c.globalAlpha = .5; apple(c, 1010, y, 36); c.restore();
      T(c, { t: lab[i], x: 1075, y: y - 20, w: 380, s: 30, f: "S", c: th.tx });
    });
    blockArrow(c, 900, 170, 900, 610, 30, th.pink);
    chip(c, "zrychluje", 900, 668, { bg: th.sbg, fg: th.sfg, s: 24 });
  },
  weight(c, th) {
    rrect(c, 860, 724, 600, 36, 12, "#8E6BE8", 5);
    rrect(c, 950, 650, 360, 74, 24, "#C9CCE0", 5);
    rrect(c, 1070, 667, 120, 40, 8, "#1B2A3A", 4);
    T(c, { t: "49 N", x: 1070, y: 670, w: 120, s: 26, f: "B", c: "#9DFFB0", a: "c" });
    rrect(c, 1010, 490, 240, 160, 10, "#E8A24A", 5);
    c.save(); c.strokeStyle = INK; c.lineWidth = 5; c.beginPath(); c.moveTo(1010, 490); c.lineTo(1250, 650); c.moveTo(1250, 490); c.lineTo(1010, 650); c.stroke(); c.restore();
    chip(c, "m = 5 kg", 1130, 570, { bg: "#FFF4E0", s: 28 });
    blockArrow(c, 900, 490, 900, 640, 30, th.pink);
    chip(c, "tíhová síla", 900, 445, { bg: th.pink, s: 24 });
    dash(c, th.tx, 3, () => { c.moveTo(1312, 700); c.lineTo(1362, 700); }, [6, 8], .8);
    blockArrow(c, 1380, 675, 1380, 780, 30, th.star);
    chip(c, "tíha", 1380, 825, { bg: th.star, s: 24 });
    T(c, { t: "ve volném pádu → 0 N", x: 1020, y: 300, w: 420, s: 32, f: "S", c: th.star, a: "c", r: -3 });
    doodleArrow(c, 1230, 345, 1200, 400, 1190, 460, th.tx, 4);
  },
  rotation(c, th) {
    const cx = 1180, cy = 470, tilt = .26;
    c.save(); c.translate(cx, cy); c.rotate(tilt);
    dash(c, th.dash, 4, () => { c.moveTo(0, -290); c.lineTo(0, 290); }, [10, 10], .8);
    planet(c, 0, 0, 200, "#2E86E0", earthDetail);
    dash(c, th.star, 5, () => c.ellipse(0, 0, 200, 56, 0, 0, 7), [14, 10]);
    c.strokeStyle = th.pink; c.lineWidth = 9; c.lineCap = "round"; c.beginPath(); c.arc(0, 0, 255, -2.7, -.7); c.stroke();
    const tx = Math.cos(-.7) * 255, ty = Math.sin(-.7) * 255, a = -.7 + Math.PI / 2;
    c.beginPath(); c.moveTo(tx - 28 * Math.cos(a - .5), ty - 28 * Math.sin(a - .5)); c.lineTo(tx, ty); c.lineTo(tx - 28 * Math.cos(a + .5), ty - 28 * Math.sin(a + .5)); c.stroke();
    c.restore();
    chip(c, "pól · 9,83 m/s²", 1290, 130, { bg: th.star, s: 26 });
    chip(c, "rovník · 9,78 m/s²", 1400, 690, { bg: th.pink, s: 26 });
    doodleArrow(c, 1400, 655, 1415, 600, 1378, 545, th.tx, 4);
    T(c, { t: "rotace", x: 880, y: 250, w: 200, s: 34, f: "S", c: th.tx, a: "c", r: -5 });
    doodleArrow(c, 990, 290, 1030, 270, 1060, 240, th.tx, 4);
  },
  motion(c, th) {
    dash(c, th.pink, 5, () => c.arc(1230, 900, 490, 0, 7), [2, 16]);
    planet(c, 1230, 900, 380, "#2E86E0", earthDetail);
    dash(c, th.star, 6, () => { c.moveTo(1300, 410); c.quadraticCurveTo(1390, 380, 1440, 583); }, [14, 12]);
    dash(c, th.star, 6, () => { c.moveTo(1300, 410); c.quadraticCurveTo(1500, 360, 1580, 752); }, [14, 12]);
    c.beginPath(); c.moveTo(1095, 548); c.lineTo(1230, 436); c.lineTo(1365, 548); c.closePath(); fillStroke(c, "#8B6B4A", 5);
    c.save(); c.translate(1236, 418); c.rotate(-.1); rrect(c, -8, -15, 70, 30, 8, "#3A3A5A", 5); c.restore();
    circle(c, 1232, 432, 17, "#E8A24A", 5);
    satellite(c, 884, 554, .5, 40);
    chip(c, "1", 1372, 545, { bg: "#FFF4E0", s: 26 });
    chip(c, "2", 1488, 628, { bg: "#FFF4E0", s: 26 });
    chip(c, "3", 1050, 446, { bg: th.pink, s: 26 });
    T(c, { t: "větší rychlost → dál", x: 830, y: 230, w: 380, s: 32, f: "S", c: th.star, a: "c", r: -4 });
    doodleArrow(c, 1030, 280, 1130, 300, 1205, 392, th.tx, 4);
  },
  kepler(c, th) {
    const cx = 1200, cy = 450, a = 330, b = 210, cc = Math.sqrt(a * a - b * b), sx = cx + cc, sy = cy;
    const P = E => [cx + a * Math.cos(E), cy + b * Math.sin(E)];
    const sector = (e1, e2, n, col) => { c.beginPath(); c.moveTo(sx, sy); for (let k = 0; k <= n; k++) { const p = P(e1 + (e2 - e1) * k / n); c.lineTo(p[0], p[1]); } c.closePath(); fillStroke(c, col, 3); };
    sector(-.5, .5, 24, "rgba(255,111,165,.75)");
    sector(Math.PI - .0735, Math.PI + .0735, 6, "rgba(122,59,255,.65)");
    c.beginPath(); c.ellipse(cx, cy, a, b, 0, 0, 7); c.strokeStyle = INK; c.lineWidth = 5; c.stroke();
    const A = P(.5), B = P(Math.PI - .0735);
    planet(c, A[0], A[1], 22, "#2E86E0", earthDetail);
    planet(c, B[0], B[1], 22, "#2E86E0", earthDetail);
    sun(c, sx, sy, 44);
    chip(c, "Slunce", sx, 200, { bg: "#FFD23F", s: 26 });
    doodleArrow(c, sx, 235, sx + 12, 280, sx, 322, th.tx, 4);
    chip(c, "rychle", 1380, 735, { bg: th.pink, s: 26 });
    doodleArrow(c, 1400, 700, 1450, 650, 1480, 585, th.tx, 4);
    chip(c, "pomalu", 950, 360, { bg: th.sbg, fg: th.sfg, s: 26 });
    doodleArrow(c, 930, 392, 910, 420, 890, 440, th.tx, 4);
    T(c, { t: "stejný čas = stejná plocha", x: 1000, y: 410, w: 260, s: 28, f: "S", c: th.tx, a: "c", r: -3 });
  },
  speeds(c, th) {
    dash(c, th.dash, 4, () => c.arc(1200, 800, 380, 0, 7), [2, 14], .6);
    planet(c, 1200, 800, 300, "#2E86E0", earthDetail);
    dash(c, th.star, 6, () => { c.moveTo(1130, 505); c.bezierCurveTo(1100, 250, 1250, 200, 1360, 215); }, [14, 12]);
    satellite(c, 1491, 556, .5, 50);
    rocket(c, 1420, 215, .8, 78);
    chip(c, "oběh · 7,9 km/s", 1010, 380, { bg: th.pink, s: 26 });
    chip(c, "únik · 11,2 km/s", 1130, 110, { bg: th.star, s: 26 });
    T(c, { t: "pryč ze Země!", x: 1340, y: 335, w: 230, s: 30, f: "S", c: th.tx, a: "c", r: -5 });
  },
  tides(c, th) {
    c.beginPath(); c.ellipse(1100, 450, 218, 168, 0, 0, 7); fillStroke(c, "#8FE3FF", 5);
    planet(c, 1100, 450, 148, "#2E86E0", earthDetail);
    planet(c, 1500, 450, 68, "#D7DAEE", moonDetail);
    blockArrow(c, 1332, 450, 1424, 450, 26, "#FFB02E");
    chip(c, "Měsíc", 1500, 555, { bg: "#FFF4E0", s: 26 });
    chip(c, "příliv", 905, 625, { bg: th.star, s: 26 });
    doodleArrow(c, 905, 592, 895, 540, 893, 490, th.tx, 4);
    chip(c, "příliv", 1300, 625, { bg: th.star, s: 26 });
    doodleArrow(c, 1300, 592, 1305, 545, 1300, 495, th.tx, 4);
    chip(c, "odliv", 1100, 205, { bg: th.pink, s: 26 });
    doodleArrow(c, 1100, 237, 1100, 255, 1100, 278, th.tx, 4);
    chip(c, "odliv", 1100, 715, { bg: th.pink, s: 26 });
    doodleArrow(c, 1100, 683, 1100, 660, 1100, 625, th.tx, 4);
    sun(c, 1480, 130, 38);
    T(c, { t: "Slunce taky", x: 1380, y: 200, w: 200, s: 26, f: "S", c: th.tx, a: "c", r: 3 });
  },
  worlds(c, th) {
    const base = 745, k = 26;
    c.save(); c.strokeStyle = th.tx; c.lineWidth = 5; c.lineCap = "round"; c.beginPath(); c.moveTo(850, base); c.lineTo(1540, base); c.stroke(); c.restore();
    const d = [
      { x: 960, n: "Měsíc", g: 1.62, col: "#9AA0C8", r: 58, base: "#D7DAEE", det: moonDetail },
      { x: 1195, n: "Mars", g: 3.71, col: "#FF7A4D", r: 74, base: "#F0663A", det: marsDetail },
      { x: 1430, n: "Země", g: 9.81, col: "#3FA9F5", r: 96, base: "#2E86E0", det: earthDetail }
    ];
    d.forEach(w => {
      const h = w.g * k;
      rrect(c, w.x - 75, base - h, 150, h, 10, w.col, 5);
      planet(c, w.x, base - h - w.r - 14, w.r, w.base, w.det);
      T(c, { t: w.n, x: w.x - 100, y: 762, w: 200, s: 30, f: "B", c: th.tx, a: "c" });
      T(c, { t: String(w.g).replace(".", ",") + " m/s²", x: w.x - 110, y: 802, w: 220, s: 28, f: "S", c: th.star, a: "c" });
    });
  },
  calc(c, th) {
    const card = (cx, cy, deg, kind, disp, label) => {
      c.save(); c.translate(cx, cy); c.rotate(deg * Math.PI / 180);
      rrect(c, -142, -254, 300, 524, 22, INK, 0);
      rrect(c, -150, -262, 300, 524, 22, "#FFFFFF", 5);
      if (kind === "earth") planet(c, 0, -190, 58, "#2E86E0", earthDetail); else planet(c, 0, -190, 58, "#D7DAEE", moonDetail);
      astronaut(c, 0, -62, .42);
      rrect(c, -112, 64, 224, 58, 16, "#C9CCE0", 5); rrect(c, -52, 76, 104, 34, 8, "#1B2A3A", 4);
      c.restore();
      const p = G(cx, cy, deg, 0, 93);
      T(c, { t: disp, x: p[0] - 52, y: Math.round(p[1] - 16), w: 104, s: 24, f: "B", c: "#9DFFB0", a: "c", r: deg });
      const q = G(cx, cy, deg, 0, 160), z = G(cx, cy, deg, 0, 214);
      chip(c, "m = 60 kg", q[0], q[1], { bg: "#FFD54A", s: 22, r: deg });
      chip(c, label, z[0], z[1], { bg: "#E7E1FF", s: 21, r: deg });
    };
    card(985, 480, -2.5, "earth", "589 N", "Země · 9,81 m/s²");
    card(1340, 480, 2.5, "moon", "97 N", "Měsíc · 1,62 m/s²");
    T(c, { t: "≈ 6× menší tíha", x: 1000, y: 120, w: 340, s: 32, f: "S", c: th.kick, a: "c", r: -3 });
    doodleArrow(c, 1150, 170, 1170, 190, 1185, 215, th.kick, 4);
  },
  summary(c, th) {
    astronaut(c, 1200, 300, 1.45, -8);
    apple(c, 960, 260, 46);
    chip(c, "pád", 960, 340, { bg: th.pink, s: 28 });
    satellite(c, 1480, 300, .6, -20);
    chip(c, "oběh", 1480, 385, { bg: th.star, s: 28 });
    planet(c, 990, 690, 58, "#D7DAEE", moonDetail);
    chip(c, "příliv", 990, 785, { bg: "#4DE1C1", s: 28 });
    rocket(c, 1470, 650, .55, 20);
  }
};

/* ---------- vykreslení snímku ---------- */
const BLOB = [[0, -1], [.8, -.75], [1, .05], [.7, .85], [-.1, 1], [-.85, .6], [-1, -.2], [-.6, -.8]];
const DECOR = [[838, 120, 20], [1486, 92, 24], [1556, 300, 12], [1562, 626, 18], [884, 838, 13], [1336, 852, 20], [1030, 64, 10], [34, 330, 12], [50, 700, 16]];

function draw(i, c, k) {
  const s = slides[i], th = TH[s.th];
  c.save(); c.setTransform(k, 0, 0, k, 0, 0);
  c.fillStyle = th.bg; c.fillRect(0, 0, W, H);
  if (th.grid) {
    c.strokeStyle = "#CFE0F5"; c.lineWidth = 2; c.beginPath();
    for (let x = 0; x <= W; x += 50) { c.moveTo(x, 0); c.lineTo(x, H); }
    for (let y = 0; y <= H; y += 50) { c.moveTo(0, y); c.lineTo(W, y); }
    c.stroke();
    c.strokeStyle = "#FF9AB5"; c.lineWidth = 3; c.beginPath(); c.moveTo(60, 0); c.lineTo(60, H); c.stroke();
  }
  // organický flek za obrázkem
  c.save(); c.translate(1180, 450); c.rotate(i * .7); blob(c, 0, 0, 370, BLOB); c.fillStyle = th.blob; c.fill(); c.restore();
  c.save(); c.translate(1196, 466); c.rotate(i * .7); c.globalAlpha = .45; c.setLineDash([12, 12]); c.lineWidth = 3; c.strokeStyle = th.dash; blob(c, 0, 0, 370, BLOB); c.stroke(); c.restore();
  // hvězdy a čmáranice
  const cols = [th.star, th.pink, th.star2];
  DECOR.forEach((d, n) => sparkle(c, d[0], d[1], d[2], cols[(n + i) % 3]));
  [[1010, 100], [1535, 430], [820, 640], [1400, 878], [24, 520]].forEach((p, n) => { c.fillStyle = cols[(n + i + 1) % 3]; c.beginPath(); c.arc(p[0], p[1], 5, 0, 7); c.fill(); });
  plus(c, 1260, 66, 9, cols[(i + 2) % 3]); plus(c, 1566, 740, 10, cols[i % 3]);
  // ilustrace
  ART[s.art](c, th);
  // štítek s číslem + poznámka
  circle(c, 142, 120, 46, th.pink, 5);
  T(c, { t: String(i + 1).padStart(2, "0"), x: 92, y: 120 - 21, w: 100, s: 34, lh: 42, f: "H", c: INK, a: "c" });
  T(c, { t: s.kick, x: 205, y: 98, w: 560, s: 30, f: "S", c: th.kick, r: -1.5 });
  // nadpis
  let ts = 42;
  for (const z of [64, 58, 52, 46]) { if (measure(c, { t: s.title, w: 700, s: z, f: "H", lh: Math.round(z * 1.1) }).lines.length <= 2) { ts = z; break; } }
  const tm = T(c, { t: s.title, x: 90, y: 205, w: 700, s: ts, lh: Math.round(ts * 1.1), f: "H", c: th.tx });
  // vlnovka pod nadpisem
  const qy = 205 + tm.h + 16;
  c.save(); c.strokeStyle = th.sq; c.lineWidth = 7; c.lineCap = "round"; c.lineJoin = "round"; c.beginPath();
  for (let x = 0; x <= 240; x += 4) { const y = qy + Math.sin(x / 40 * Math.PI * 2) * 7; x === 0 ? c.moveTo(94 + x, y) : c.lineTo(94 + x, y); }
  c.stroke(); c.restore();
  // odrážky
  let y = qy + 46;
  const f = s.bf || "B", sz = f === "S" ? 30 : 31, lh = f === "S" ? 44 : 40;
  s.bullets.forEach((b, n) => {
    const m = T(c, { t: b, x: 140, y, w: 590, s: sz, lh, f, c: th.tx });
    sparkle(c, 104, y + lh / 2, 15, cols[n % 3]);
    y += m.h + 26;
  });
  // samolepka s vzorcem / hlavní myšlenkou
  const fs = s.big ? 42 : 29;
  const m0 = measure(c, { t: s.st, w: 640, s: fs, f: "B" });
  const sw = m0.widest + 60, sh = m0.h + 36, sy = Math.max(y - 12, H - 78 - sh), scx = 90 + sw / 2, scy = sy + sh / 2;
  c.save(); c.translate(scx, scy); c.rotate(-2 * Math.PI / 180);
  rrect(c, -sw / 2 + 9, -sh / 2 + 9, sw, sh, 18, th.ssh, 0);
  rrect(c, -sw / 2, -sh / 2, sw, sh, 18, th.sbg, 4);
  c.restore();
  T(c, { t: s.st, x: scx - (m0.widest + 8) / 2, y: scy - m0.h / 2, w: m0.widest + 8, s: fs, f: "B", c: th.sfg, a: "c", r: -2 });
  c.restore();
}

/* ---------- ovládání ---------- */
const canvas = document.getElementById("slide"), ctx = canvas.getContext("2d");
const picker = document.getElementById("picker"), statusEl = document.getElementById("status");
slides.forEach((s, i) => { const o = document.createElement("option"); o.value = i; o.textContent = `${i + 1}. ${s.title}`; picker.append(o); });
let current = 0;
function show(i) {
  current = Math.max(0, Math.min(slides.length - 1, i));
  draw(current, ctx, 1.2);
  picker.value = String(current);
  document.getElementById("counter").textContent = `${current + 1} / ${slides.length}`;
  document.getElementById("prev").disabled = current === 0;
  document.getElementById("next").disabled = current === slides.length - 1;
  canvas.setAttribute("aria-label", `Snímek ${current + 1}: ${slides[current].title}. ${slides[current].bullets.join(" ")}`);
}
document.getElementById("prev").onclick = () => show(current - 1);
document.getElementById("next").onclick = () => show(current + 1);
picker.onchange = () => show(Number(picker.value));
document.getElementById("full").onclick = () => { const d = document.getElementById("deck"); if (document.fullscreenElement) document.exitFullscreen(); else if (d.requestFullscreen) d.requestFullscreen(); };
document.addEventListener("keydown", e => {
  if (e.target instanceof HTMLSelectElement) return;
  if (["ArrowRight", "PageDown", " "].includes(e.key)) { e.preventDefault(); show(current + 1); }
  if (["ArrowLeft", "PageUp"].includes(e.key)) { e.preventDefault(); show(current - 1); }
});
(document.fonts && document.fonts.ready ? document.fonts.ready : Promise.resolve()).then(() => show(0));
show(0);

/* ---------- export do PPTX (obrázky na pozadí + editovatelné texty) ---------- */
const esc = s => String(s).replaceAll("&", "&amp;").replaceAll("<", "&lt;").replaceAll(">", "&gt;").replaceAll('"', "&quot;");
const emu = v => Math.round(v * 7620);
function textXml(it, id) {
  const { o, m, align, cx } = it, single = m.lines.length === 1;
  const bw = single ? Math.ceil(m.widest * 1.08 + 30) : o.w * 1.04;
  const bx = align === "c" ? cx - bw / 2 : o.x;
  const rot = Math.round((((o.r || 0) % 360) + 360) % 360 * 60000);
  const hex = o.c.replace("#", "");
  return `<p:sp><p:nvSpPr><p:cNvPr id="${id}" name="Text ${id}"/><p:cNvSpPr txBox="1"/><p:nvPr/></p:nvSpPr><p:spPr><a:xfrm${rot ? ` rot="${rot}"` : ""}><a:off x="${emu(bx)}" y="${emu(o.y)}"/><a:ext cx="${emu(bw)}" cy="${emu(m.h)}"/></a:xfrm><a:prstGeom prst="rect"><a:avLst/></a:prstGeom><a:noFill/></p:spPr><p:txBody><a:bodyPr wrap="${single ? "none" : "square"}" lIns="0" tIns="0" rIns="0" bIns="0" anchor="${single ? "ctr" : "t"}"><a:noAutofit/></a:bodyPr><a:lstStyle/><a:p><a:pPr algn="${align === "c" ? "ctr" : "l"}"><a:lnSpc><a:spcPts val="${Math.round(m.lh * 0.6 * 100)}"/></a:lnSpc></a:pPr><a:r><a:rPr lang="cs-CZ" sz="${Math.round(o.s * 60)}" b="${m.F.b}" dirty="0"><a:solidFill><a:srgbClr val="${hex}"/></a:solidFill><a:latin typeface="${m.F.ppt}"/><a:cs typeface="${m.F.ppt}"/></a:rPr><a:t>${esc(o.t)}</a:t></a:r></a:p></p:txBody></p:sp>`;
}
async function exportPptx() {
  const btn = document.getElementById("download");
  if (typeof JSZip === "undefined") { statusEl.textContent = "Export není dostupný: nepodařilo se načíst knihovnu JSZip."; return; }
  btn.disabled = true;
  try {
    const zip = new JSZip(), N = slides.length;
    const nsP = "http://schemas.openxmlformats.org/presentationml/2006/main", nsA = "http://schemas.openxmlformats.org/drawingml/2006/main", nsR = "http://schemas.openxmlformats.org/officeDocument/2006/relationships";
    const rel = "http://schemas.openxmlformats.org/package/2006/relationships", base = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/";
    const hdr = '<?xml version="1.0" encoding="UTF-8" standalone="yes"?>';
    zip.file("[Content_Types].xml", `${hdr}<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types"><Default Extension="rels" ContentType="application/vnd.openxmlformats-package.relationships+xml"/><Default Extension="xml" ContentType="application/xml"/><Default Extension="png" ContentType="image/png"/><Override PartName="/ppt/presentation.xml" ContentType="application/vnd.openxmlformats-officedocument.presentationml.presentation.main+xml"/><Override PartName="/ppt/slideMasters/slideMaster1.xml" ContentType="application/vnd.openxmlformats-officedocument.presentationml.slideMaster+xml"/><Override PartName="/ppt/slideLayouts/slideLayout1.xml" ContentType="application/vnd.openxmlformats-officedocument.presentationml.slideLayout+xml"/><Override PartName="/ppt/theme/theme1.xml" ContentType="application/vnd.openxmlformats-officedocument.theme+xml"/>${slides.map((_, i) => `<Override PartName="/ppt/slides/slide${i + 1}.xml" ContentType="application/vnd.openxmlformats-officedocument.presentationml.slide+xml"/>`).join("")}</Types>`);
    zip.file("_rels/.rels", `${hdr}<Relationships xmlns="${rel}"><Relationship Id="rId1" Type="${base}officeDocument" Target="ppt/presentation.xml"/></Relationships>`);
    zip.file("ppt/presentation.xml", `${hdr}<p:presentation xmlns:p="${nsP}" xmlns:a="${nsA}" xmlns:r="${nsR}"><p:sldMasterIdLst><p:sldMasterId id="2147483648" r:id="rId1"/></p:sldMasterIdLst><p:sldIdLst>${slides.map((_, i) => `<p:sldId id="${256 + i}" r:id="rId${i + 2}"/>`).join("")}</p:sldIdLst><p:sldSz cx="12192000" cy="6858000"/><p:notesSz cx="6858000" cy="9144000"/></p:presentation>`);
    zip.file("ppt/_rels/presentation.xml.rels", `${hdr}<Relationships xmlns="${rel}"><Relationship Id="rId1" Type="${base}slideMaster" Target="slideMasters/slideMaster1.xml"/>${slides.map((_, i) => `<Relationship Id="rId${i + 2}" Type="${base}slide" Target="slides/slide${i + 1}.xml"/>`).join("")}</Relationships>`);
    const tree = `<p:nvGrpSpPr><p:cNvPr id="1" name=""/><p:cNvGrpSpPr/><p:nvPr/></p:nvGrpSpPr><p:grpSpPr><a:xfrm><a:off x="0" y="0"/><a:ext cx="0" cy="0"/><a:chOff x="0" y="0"/><a:chExt cx="0" cy="0"/></a:xfrm></p:grpSpPr>`;
    zip.file("ppt/slideMasters/slideMaster1.xml", `${hdr}<p:sldMaster xmlns:p="${nsP}" xmlns:a="${nsA}" xmlns:r="${nsR}"><p:cSld><p:spTree>${tree}</p:spTree></p:cSld><p:clrMap bg1="lt1" tx1="dk1" bg2="lt2" tx2="dk2" accent1="accent1" accent2="accent2" accent3="accent3" accent4="accent4" accent5="accent5" accent6="accent6" hlink="hlink" folHlink="folHlink"/><p:sldLayoutIdLst><p:sldLayoutId id="2147483649" r:id="rId1"/></p:sldLayoutIdLst><p:txStyles><p:titleStyle><a:lvl1pPr><a:defRPr sz="4400"/></a:lvl1pPr></p:titleStyle><p:bodyStyle><a:lvl1pPr><a:defRPr sz="2800"/></a:lvl1pPr></p:bodyStyle><p:otherStyle><a:defPPr><a:defRPr/></a:defPPr></p:otherStyle></p:txStyles></p:sldMaster>`);
    zip.file("ppt/slideMasters/_rels/slideMaster1.xml.rels", `${hdr}<Relationships xmlns="${rel}"><Relationship Id="rId1" Type="${base}slideLayout" Target="../slideLayouts/slideLayout1.xml"/><Relationship Id="rId2" Type="${base}theme" Target="../theme/theme1.xml"/></Relationships>`);
    zip.file("ppt/slideLayouts/slideLayout1.xml", `${hdr}<p:sldLayout xmlns:p="${nsP}" xmlns:a="${nsA}" xmlns:r="${nsR}" type="blank" preserve="1"><p:cSld name="Prázdný"><p:spTree>${tree}</p:spTree></p:cSld><p:clrMapOvr><a:masterClrMapping/></p:clrMapOvr></p:sldLayout>`);
    zip.file("ppt/slideLayouts/_rels/slideLayout1.xml.rels", `${hdr}<Relationships xmlns="${rel}"><Relationship Id="rId1" Type="${base}slideMaster" Target="../slideMasters/slideMaster1.xml"/></Relationships>`);
    const fill3 = '<a:solidFill><a:schemeClr val="phClr"/></a:solidFill>'.repeat(3);
    const ln3 = [9525, 25400, 38100].map(w => `<a:ln w="${w}"><a:solidFill><a:schemeClr val="phClr"/></a:solidFill></a:ln>`).join("");
    zip.file("ppt/theme/theme1.xml", `${hdr}<a:theme xmlns:a="${nsA}" name="Vesmir"><a:themeElements><a:clrScheme name="Vesmir"><a:dk1><a:srgbClr val="141036"/></a:dk1><a:lt1><a:srgbClr val="FFFFFF"/></a:lt1><a:dk2><a:srgbClr val="2A1B6B"/></a:dk2><a:lt2><a:srgbClr val="FFF1D6"/></a:lt2><a:accent1><a:srgbClr val="FFD54A"/></a:accent1><a:accent2><a:srgbClr val="FF6FA5"/></a:accent2><a:accent3><a:srgbClr val="3FA9F5"/></a:accent3><a:accent4><a:srgbClr val="4DE1C1"/></a:accent4><a:accent5><a:srgbClr val="7A3BFF"/></a:accent5><a:accent6><a:srgbClr val="FF7A4D"/></a:accent6><a:hlink><a:srgbClr val="3FA9F5"/></a:hlink><a:folHlink><a:srgbClr val="7A3BFF"/></a:folHlink></a:clrScheme><a:fontScheme name="Vesmir"><a:majorFont><a:latin typeface="Arial Black"/><a:ea typeface=""/><a:cs typeface=""/></a:majorFont><a:minorFont><a:latin typeface="Trebuchet MS"/><a:ea typeface=""/><a:cs typeface=""/></a:minorFont></a:fontScheme><a:fmtScheme name="Vesmir"><a:fillStyleLst>${fill3}</a:fillStyleLst><a:lnStyleLst>${ln3}</a:lnStyleLst><a:effectStyleLst>${"<a:effectStyle><a:effectLst/></a:effectStyle>".repeat(3)}</a:effectStyleLst><a:bgFillStyleLst>${fill3}</a:bgFillStyleLst></a:fmtScheme></a:themeElements></a:theme>`);
    const off = document.createElement("canvas"); off.width = 2400; off.height = 1350; const oc = off.getContext("2d");
    for (let i = 0; i < N; i++) {
      statusEl.textContent = `Připravuji snímek ${i + 1} z ${N}…`;
      await new Promise(r => setTimeout(r, 0));
      oc.setTransform(1, 0, 0, 1, 0, 0); oc.clearRect(0, 0, 2400, 1350);
      EXPORT = [];
      try { draw(i, oc, 1.5); } finally { var items = EXPORT; EXPORT = null; }
      const blob = await new Promise(r => off.toBlob(r, "image/png"));
      if (!blob) throw new Error("Nepodařilo se vykreslit snímek.");
      zip.file(`ppt/media/slide${i + 1}.png`, blob);
      const bg = TH[slides[i].th].bg.replace("#", "");
      const texts = items.map((it, n) => textXml(it, n + 3)).join("");
      zip.file(`ppt/slides/slide${i + 1}.xml`, `${hdr}<p:sld xmlns:p="${nsP}" xmlns:a="${nsA}" xmlns:r="${nsR}"><p:cSld name="${esc(slides[i].title)}"><p:bg><p:bgPr><a:solidFill><a:srgbClr val="${bg}"/></a:solidFill><a:effectLst/></p:bgPr></p:bg><p:spTree>${tree}<p:pic><p:nvPicPr><p:cNvPr id="2" name="Ilustrace ${i + 1}"/><p:cNvPicPr><a:picLocks noChangeAspect="1"/></p:cNvPicPr><p:nvPr/></p:nvPicPr><p:blipFill><a:blip r:embed="rId2"/><a:stretch><a:fillRect/></a:stretch></p:blipFill><p:spPr><a:xfrm><a:off x="0" y="0"/><a:ext cx="12192000" cy="6858000"/></a:xfrm><a:prstGeom prst="rect"><a:avLst/></a:prstGeom></p:spPr></p:pic>${texts}</p:spTree></p:cSld><p:clrMapOvr><a:masterClrMapping/></p:clrMapOvr></p:sld>`);
      zip.file(`ppt/slides/_rels/slide${i + 1}.xml.rels`, `${hdr}<Relationships xmlns="${rel}"><Relationship Id="rId1" Type="${base}slideLayout" Target="../slideLayouts/slideLayout1.xml"/><Relationship Id="rId2" Type="${base}image" Target="../media/slide${i + 1}.png"/></Relationships>`);
    }
    statusEl.textContent = "Balím prezentaci…";
    const file = await zip.generateAsync({ type: "blob", compression: "DEFLATE", compressionOptions: { level: 4 } });
    const url = URL.createObjectURL(file), a = document.createElement("a");
    a.href = url; a.download = "Gravitacni_a_tihova_sila.pptx"; document.body.append(a); a.click(); a.remove();
    setTimeout(() => URL.revokeObjectURL(url), 60000);
    statusEl.textContent = "Hotovo. V PowerPointu jdou texty upravovat, ilustrace jsou obrázek na pozadí snímku.";
  } catch (e) {
    EXPORT = null; statusEl.textContent = `Export se nezdařil: ${e.message}`; console.error(e);
  } finally { btn.disabled = false; show(current); }
}
document.getElementById("download").onclick = exportPptx;
</script>
</body>
</html>
