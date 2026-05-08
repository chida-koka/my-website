<!DOCTYPE html>

<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>WOOD CREATER　建築士 知田末吉 | 木の声を聴く</title>
<link href="https://fonts.googleapis.com/css2?family=Zen+Antique+Soft&family=Noto+Serif+JP:wght@200;300;400;500&family=Shippori+Mincho:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #1a1208;
    --ink-light: #2e2010;
    --sumi: #3a2e20;
    --earth: #6b5640;
    --clay: #9c7d5e;
    --washi: #f2ead8;
    --washi-dark: #e8dcc4;
    --aged: #d4c4a0;
    --moss: #5c6645;
    --rust: #8b4513;
    --gold-old: #a08040;
  }

- { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }

body {
background: var(–washi);
color: var(–ink);
font-family: ‘Shippori Mincho’, ‘Noto Serif JP’, serif;
overflow-x: hidden;
}

/* 和紙テクスチャ */
body::before {
content: ‘’;
position: fixed;
inset: 0;
background-image:
url(“data:image/svg+xml,%3Csvg xmlns=‘http://www.w3.org/2000/svg’ width=‘400’ height=‘400’%3E%3Cfilter id=‘paper’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.65’ numOctaves=‘3’ stitchTiles=‘stitch’/%3E%3CfeColorMatrix type=‘saturate’ values=‘0’/%3E%3C/filter%3E%3Crect width=‘400’ height=‘400’ filter=‘url(%23paper)’ opacity=‘0.06’/%3E%3C/svg%3E”);
pointer-events: none;
z-index: 9999;
mix-blend-mode: multiply;
}

/* ── ナビ ── */
nav {
position: fixed;
top: 0; left: 0; right: 0;
z-index: 100;
padding: 20px 48px;
display: flex;
justify-content: space-between;
align-items: center;
background: linear-gradient(to bottom, rgba(242,234,216,0.97) 60%, transparent);
border-bottom: 1px solid rgba(107,86,64,0.12);
}

.nav-logo {
display: flex;
align-items: center;
gap: 12px;
text-decoration: none;
}

.nav-logo-kanji {
font-family: ‘Zen Antique Soft’, serif;
font-size: 1.8rem;
color: var(–ink);
line-height: 1;
letter-spacing: -0.02em;
}

.nav-logo-text {
font-size: 0.6rem;
letter-spacing: 0.15em;
color: var(–earth);
line-height: 1.8;
font-weight: 300;
}

.nav-links {
display: flex;
gap: 36px;
list-style: none;
}

.nav-links a {
font-size: 0.75rem;
letter-spacing: 0.2em;
color: var(–earth);
text-decoration: none;
transition: color 0.3s;
font-family: ‘Noto Serif JP’, serif;
font-weight: 300;
}

.nav-links a:hover { color: var(–rust); }

/* ── ヒーロー ── */
.hero {
min-height: 100vh;
display: flex;
align-items: stretch;
position: relative;
overflow: hidden;
padding-top: 72px;
}

/* 薄い縦罫線（便箋風） */
.hero::before {
content: ‘’;
position: absolute;
inset: 0;
background: repeating-linear-gradient(
90deg,
transparent,
transparent 80px,
rgba(107,86,64,0.06) 80px,
rgba(107,86,64,0.06) 81px
);
pointer-events: none;
}

.hero-inner {
display: grid;
grid-template-columns: 80px 1fr 1fr;
width: 100%;
position: relative;
z-index: 1;
}

/* 縦書きサイドバー */
.hero-side {
background: var(–ink);
display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
padding: 60px 0;
gap: 40px;
position: relative;
}

.hero-side::after {
content: ‘’;
position: absolute;
top: 0; bottom: 0; right: -1px;
width: 1px;
background: linear-gradient(to bottom, transparent, rgba(160,128,64,0.5) 30%, rgba(160,128,64,0.5) 70%, transparent);
}

.side-text {
writing-mode: vertical-rl;
font-family: ‘Zen Antique Soft’, serif;
font-size: 0.7rem;
letter-spacing: 0.3em;
color: rgba(242,234,216,0.4);
}

.side-dot {
width: 4px;
height: 4px;
border-radius: 50%;
background: rgba(160,128,64,0.5);
}

/* メインビジュアル */
.hero-visual {
background: var(–ink-light);
position: relative;
overflow: hidden;
display: flex;
align-items: center;
justify-content: center;
min-height: 80vh;
}

/* 水墨画風の背景 */
.hero-visual::before {
content: ‘’;
position: absolute;
inset: 0;
background:
radial-gradient(ellipse 120% 80% at 20% 80%, rgba(58,46,32,0.8) 0%, transparent 60%),
radial-gradient(ellipse 80% 60% at 80% 20%, rgba(92,70,48,0.4) 0%, transparent 50%),
radial-gradient(ellipse 60% 40% at 50% 50%, rgba(30,20,10,0.3) 0%, transparent 70%);
}

/* 刷毛目の装飾 */
.hero-visual::after {
content: ‘’;
position: absolute;
inset: 0;
background: repeating-linear-gradient(
170deg,
transparent,
transparent 30px,
rgba(255,255,255,0.012) 30px,
rgba(255,255,255,0.012) 31px
);
}

.hero-big-kanji {
font-family: ‘Zen Antique Soft’, serif;
font-size: clamp(10rem, 20vw, 16rem);
color: rgba(242,234,216,0.06);
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
user-select: none;
letter-spacing: -0.05em;
line-height: 1;
}

.hero-stamp {
position: absolute;
bottom: 60px;
right: 48px;
width: 72px;
height: 72px;
border: 2px solid rgba(139,69,19,0.7);
display: flex;
align-items: center;
justify-content: center;
z-index: 2;
}

.hero-stamp span {
font-family: ‘Zen Antique Soft’, serif;
font-size: 1.4rem;
color: rgba(139,69,19,0.8);
writing-mode: vertical-rl;
letter-spacing: 0.15em;
line-height: 1;
}

/* ヒーローテキスト */
.hero-text {
padding: 80px 60px 80px 72px;
display: flex;
flex-direction: column;
justify-content: center;
position: relative;
}

.hero-text::before {
content: ‘’;
position: absolute;
left: 0;
top: 10%;
bottom: 10%;
width: 1px;
background: linear-gradient(to bottom, transparent, rgba(107,86,64,0.25) 20%, rgba(107,86,64,0.25) 80%, transparent);
}

.hero-catch {
font-family: ‘Zen Antique Soft’, serif;
font-size: clamp(2.8rem, 5vw, 4.5rem);
line-height: 1.5;
color: var(–ink);
writing-mode: vertical-rl;
height: clamp(240px, 40vh, 360px);
opacity: 0;
animation: fadeInSlide 1.2s ease 0.6s forwards;
letter-spacing: 0.15em;
margin-bottom: 48px;
}

.hero-sub {
font-size: 0.8rem;
line-height: 2.5;
color: var(–earth);
font-weight: 300;
opacity: 0;
animation: fadeInSlide 1.2s ease 1s forwards;
max-width: 360px;
letter-spacing: 0.05em;
}

.hero-author {
margin-top: 48px;
opacity: 0;
animation: fadeInSlide 1.2s ease 1.3s forwards;
}

.hero-author-name {
font-family: ‘Zen Antique Soft’, serif;
font-size: 1.6rem;
color: var(–ink);
letter-spacing: 0.25em;
}

.hero-author-title {
font-size: 0.65rem;
letter-spacing: 0.25em;
color: var(–clay);
margin-top: 6px;
font-weight: 300;
}

/* 墨の染み風の装飾 */
.ink-blob {
position: absolute;
border-radius: 50%;
background: radial-gradient(ellipse, rgba(26,18,8,0.06) 0%, transparent 70%);
pointer-events: none;
}

.ink-blob-1 { width: 300px; height: 200px; top: 10%; right: 5%; transform: rotate(-15deg); }
.ink-blob-2 { width: 200px; height: 300px; bottom: 15%; left: 10%; transform: rotate(10deg); }

/* ── 区切り装飾 ── */
.divider {
display: flex;
align-items: center;
gap: 24px;
max-width: 1200px;
margin: 0 auto;
padding: 0 80px;
}

.divider-line { flex: 1; height: 1px; background: rgba(107,86,64,0.2); }
.divider-kanji {
font-family: ‘Zen Antique Soft’, serif;
font-size: 1rem;
color: var(–clay);
letter-spacing: 0.2em;
}

/* ── フィロソフィー ── */
.philosophy {
padding: 100px 80px;
max-width: 1200px;
margin: 0 auto;
position: relative;
}

.philosophy-inner {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 80px;
align-items: start;
margin-top: 60px;
}

.section-head {
display: flex;
align-items: center;
gap: 20px;
margin-bottom: 0;
}

.section-head-kanji {
font-family: ‘Zen Antique Soft’, serif;
font-size: 3rem;
color: var(–ink);
line-height: 1;
letter-spacing: -0.02em;
}

.section-head-en {
font-size: 0.55rem;
letter-spacing: 0.3em;
color: var(–clay);
writing-mode: vertical-rl;
text-orientation: mixed;
font-weight: 300;
}

.philosophy-quote {
position: relative;
padding: 40px 40px 40px 48px;
border-left: 3px solid var(–ink);
margin-bottom: 40px;
}

.philosophy-quote::before {
content: ‘『’;
position: absolute;
top: 20px;
left: 12px;
font-family: ‘Zen Antique Soft’, serif;
font-size: 2rem;
color: rgba(26,18,8,0.15);
}

.philosophy-quote p {
font-family: ‘Zen Antique Soft’, serif;
font-size: 1.2rem;
line-height: 2.2;
color: var(–ink);
letter-spacing: 0.08em;
}

.philosophy-body p {
font-size: 0.85rem;
line-height: 2.6;
color: var(–sumi);
font-weight: 300;
margin-bottom: 20px;
letter-spacing: 0.05em;
}

/* 落款イメージ */
.rakkan {
display: inline-flex;
flex-direction: column;
align-items: center;
gap: 8px;
margin-top: 24px;
}

.rakkan-box {
width: 48px;
height: 48px;
border: 1.5px solid rgba(139,69,19,0.5);
display: flex;
align-items: center;
justify-content: center;
font-family: ‘Zen Antique Soft’, serif;
font-size: 1.3rem;
color: rgba(139,69,19,0.7);
}

.rakkan-name {
font-size: 0.55rem;
letter-spacing: 0.15em;
color: var(–clay);
}

/* ── 作品集 ── */
.works {
padding: 80px 0 100px;
background: var(–washi-dark);
position: relative;
overflow: hidden;
}

.works::before {
content: ‘’;
position: absolute;
inset: 0;
background: repeating-linear-gradient(
0deg,
transparent,
transparent 80px,
rgba(107,86,64,0.04) 80px,
rgba(107,86,64,0.04) 81px
);
}

.works-title-wrap {
text-align: center;
padding: 0 80px;
margin-bottom: 60px;
position: relative;
z-index: 1;
}

.works-title-ja {
font-family: ‘Zen Antique Soft’, serif;
font-size: clamp(3rem, 6vw, 5rem);
color: var(–ink);
letter-spacing: 0.3em;
line-height: 1;
display: block;
}

.works-title-en {
font-size: 0.6rem;
letter-spacing: 0.4em;
color: var(–clay);
display: block;
margin-top: 12px;
font-weight: 300;
}

.works-title-line {
width: 1px;
height: 48px;
background: linear-gradient(to bottom, rgba(107,86,64,0.4), transparent);
margin: 20px auto 0;
}

/* 巻物風グリッド */
.works-scroll-wrap {
overflow-x: auto;
padding: 0 80px 40px;
-webkit-overflow-scrolling: touch;
scrollbar-width: thin;
scrollbar-color: rgba(107,86,64,0.3) transparent;
position: relative;
z-index: 1;
}

.works-scroll {
display: flex;
gap: 24px;
width: max-content;
}

.work-card {
width: 280px;
flex-shrink: 0;
cursor: pointer;
transition: transform 0.4s ease;
}

.work-card:hover { transform: translateY(-8px); }

.work-visual {
height: 360px;
position: relative;
overflow: hidden;
border: 1px solid rgba(107,86,64,0.2);
display: flex;
align-items: center;
justify-content: center;
}

/* 作品ごとに異なる墨調 */
.w1 { background: linear-gradient(160deg, #f2ead8 0%, #c8b898 40%, #8b7050 100%); }
.w2 { background: linear-gradient(140deg, #e8dcc4 0%, #b09070 50%, #6b4a28 100%); }
