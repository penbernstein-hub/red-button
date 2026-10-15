<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Caught Red-Handed</title>
<meta property="og:title" content="So… you pushed the red button, huh?">
<meta property="og:description" content="Well, don't push… click this blue one.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter+Tight:wght@400;800&display=swap">
<style>
  :root {
    --ground: #FFFFFF;
    --ink: #111111;
    --blue-top: #3B6FF2;
    --blue-top-light: #6D95FF;
    --blue-top-dark: #2A56D6;
    --blue-side: #1E42B5;
    --blue-side-dark: #142F8A;
    --blue-side-edge: #0F2470;
  }

  html, body { height: 100%; }
  body {
    margin: 0;
    background: var(--ground);
    color: var(--ink);
    font-family: "Inter Tight", "Helvetica Neue", Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    display: flex;
    align-items: center;
    justify-content: center;
    padding-inline: 24px;
    padding-block: 48px;
    box-sizing: border-box;
  }

  main {
    width: 100%;
    max-width: 640px;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    gap: 24px;
  }

  p {
    margin: 0;
    font-weight: 400;
    line-height: 1.3;
    text-wrap: balance;
  }
  .lead { font-size: clamp(1.1rem, 3vw, 1.35rem); }
  .big  { font-size: clamp(1.7rem, 6vw, 2.6rem); }
  .next { font-size: clamp(1.2rem, 4vw, 1.7rem); }

  /* Game-show push button */
  .push {
    --w: 260px;
    --h: 150px;      /* height of the top ellipse */
    --depth: 42px;   /* thickness of the side wall */
    --press: 0px;
    position: relative;
    display: block;
    width: var(--w);
    height: calc(var(--h) + var(--depth) + 20px);
    margin-top: 24px;
    text-decoration: none;
    -webkit-tap-highlight-color: transparent;
    user-select: none;
  }
  .push:active { --press: 22px; }

  .push .shadow {
    position: absolute;
    left: 6%;
    right: 6%;
    top: calc(var(--depth) + 24px);
    height: var(--h);
    border-radius: 50%;
    background: radial-gradient(ellipse at center, rgba(0,0,0,0.22), rgba(0,0,0,0) 70%);
    filter: blur(6px);
  }
  .push .bottom {
    position: absolute;
    left: 0; right: 0;
    top: var(--depth);
    height: var(--h);
    border-radius: 50%;
    background: var(--blue-side-dark);
  }
  .push .wall {
    position: absolute;
    left: 0; right: 0;
    top: calc(var(--h) / 2 + var(--press));
    height: calc(var(--depth) - var(--press));
    background: linear-gradient(90deg,
      var(--blue-side-edge) 0%,
      var(--blue-side) 28%,
      var(--blue-side) 72%,
      var(--blue-side-edge) 100%);
  }
  .push .top {
    position: absolute;
    left: 0; right: 0;
    top: var(--press);
    height: var(--h);
    border-radius: 50%;
    background:
      radial-gradient(ellipse 70% 55% at 35% 30%, var(--blue-top-light) 0%, rgba(109,149,255,0) 60%),
      linear-gradient(180deg, var(--blue-top) 0%, var(--blue-top-dark) 100%);
    box-shadow: inset 0 -6px 14px rgba(0,0,0,0.18);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2px;
    color: #FFFFFF;
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 0.02em;
    line-height: 1;
    transition: top 90ms ease;
  }
  .push .wall { transition: top 90ms ease, height 90ms ease; }

  .push:focus-visible .top {
    outline: 3px solid var(--ink);
    outline-offset: 4px;
  }

  @media (prefers-reduced-motion: reduce) {
    .push .top, .push .wall { transition: none; }
  }
</style>
</head>
<body>
<main>
  <p class="lead">Well, well, well.</p>
  <p class="big">So… you pushed the red button, huh?</p>
  <p class="next">Well, don't push… click this blue one.</p>
  <a class="push" href="https://docs.google.com/forms/d/e/1FAIpQLScon4cT9QTO0mWIew_2ZL6kGa7aA9aRjlI4YaArKwk4H3nVLg/viewform" target="_blank" rel="noopener" aria-label="Click the blue button">
    <span class="shadow" aria-hidden="true"></span>
    <span class="bottom" aria-hidden="true"></span>
    <span class="wall" aria-hidden="true"></span>
    <span class="top" aria-hidden="true"></span>
  </a>
</main>
</body>
</html>
