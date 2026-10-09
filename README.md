<!DOCTYPE html> 
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jardín de Girasoles con Estrellas Fugaces</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;1,400&display=swap" rel="stylesheet">
    <style>
      
*,
*::after,
*::before {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

:root {
  --dark-color: #000;
  --fl-speed: 0.8s;
  --speed-leaf: 2s;
}

body {
  display: flex;
  align-items: flex-end;
  justify-content: center;
  min-height: 100vh;
  background-color: var(--dark-color);
  overflow: hidden;
  perspective: 1000px;
}

.night {
  position: fixed;
  left: 50%;
  top: 0;
  transform: translateX(-50%);
  width: 100%;
  height: 100%;
  filter: blur(0.1vmin);
  background-image: radial-gradient(
      ellipse at top,
      transparent 0%,
      var(--dark-color)
    ),
    radial-gradient(
      ellipse at bottom,
      var(--dark-color),
      rgba(145, 233, 255, 0.2)
    ),
    repeating-linear-gradient(
      220deg,
      rgb(0, 0, 0) 0px,
      rgb(0, 0, 0) 19px,
      transparent 19px,
      transparent 22px
    ),
    repeating-linear-gradient(
      189deg,
      rgb(0, 0, 0) 0px,
      rgb(0, 0, 0) 19px,
      transparent 19px,
      transparent 22px
    ),
    repeating-linear-gradient(
      148deg,
      rgb(0, 0, 0) 0px,
      rgb(0, 0, 0) 19px,
      transparent 19px,
      transparent 22px
    ),
    linear-gradient(90deg, rgb(0, 255, 250), rgb(240, 240, 240));
}

.shooting-stars {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
}

.shooting-star {
  position: absolute;
  width: 4px;
  height: 4px;
  background: #fff;
  border-radius: 50%;
  box-shadow: 0 0 6px 2px rgba(255, 255, 255, 0.8);
  opacity: 0;
  animation: shootingStar 3s linear infinite;
}

.shooting-star::before {
  content: '';
  position: absolute;
  top: 50%;
  right: 0;
  transform: translateY(-50%);
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 100%);
  animation: shootingStarTail 3s linear infinite;
}

.shooting-star:nth-child(1) { top: 5%; left: -10%; animation-delay: 0s; animation-duration: 2.5s; }
.shooting-star:nth-child(2) { top: 15%; left: -10%; animation-delay: 2s; animation-duration: 3s; }
.shooting-star:nth-child(3) { top: 25%; left: -10%; animation-delay: 4s; animation-duration: 2.8s; }
.shooting-star:nth-child(4) { top: 0%; left: -10%; animation-delay: 6s; animation-duration: 3.2s; }
.shooting-star:nth-child(5) { top: 35%; left: -10%; animation-delay: 8s; animation-duration: 2.7s; }
.shooting-star:nth-child(6) { top: 8%; left: -10%; animation-delay: 10s; animation-duration: 3.1s; }
.shooting-star:nth-child(7) { top: 45%; left: -10%; animation-delay: 12s; animation-duration: 2.9s; }
.shooting-star:nth-child(8) { top: 3%; left: -10%; animation-delay: 14s; animation-duration: 3.3s; }

@keyframes shootingStar {
  0% { opacity: 0; transform: translateX(0) translateY(0) rotate(45deg); }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { opacity: 0; transform: translateX(120vw) translateY(50vh) rotate(10deg); }
}

@keyframes shootingStarTail {
  0% { width: 0; }
  30% { width: 100px; }
  100% { width: 0; }
}

.flowers {
  position: relative;
  transform: scale(0.7);
  z-index: 2;
}

.flower {
  position: absolute;
  bottom: 15vmin;
  transform-origin: bottom center;
  z-index: 50;
}

.flower--1 { animation: moving-flower-1 4s linear infinite; }
.flower--1 .flower__line { height: 70vmin; animation-delay: 0.3s; }
.flower--1 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 1.6s backwards; }
.flower--1 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 1.4s backwards; }
.flower--1 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 1.2s backwards; }
.flower--1 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 1s backwards; }

.flower--2 { left: 50%; transform: rotate(20deg); animation: moving-flower-2 4s linear infinite; }
.flower--2 .flower__line { height: 60vmin; animation-delay: 0.6s; }
.flower--2 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 1.9s backwards; }
.flower--2 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 1.7s backwards; }
.flower--2 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 1.5s backwards; }
.flower--2 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 1.3s backwards; }

.flower--3 { left: 50%; transform: rotate(-15deg); animation: moving-flower-3 4s linear infinite; }
.flower--3 .flower__line { animation-delay: 0.9s; }
.flower--3 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 2.5s backwards; }
.flower--3 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 2.3s backwards; }
.flower--3 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 2.1s backwards; }
.flower--3 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 1.9s backwards; }

.flower--4 { left: -25%; z-index: -6; transform: rotate(10deg); animation: moving-flower-4 3.5s linear infinite; }
.flower--4 .flower__line { height: 90vmin; animation-delay: 1.2s; }
.flower--4 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 2.8s backwards; }
.flower--4 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 2.6s backwards; }
.flower--4 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 2.4s backwards; }
.flower--4 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 2.2s backwards; }

.flower--5 { left: 75%; z-index: -7; transform: rotate(-25deg); animation: moving-flower-5 4.5s linear infinite; }
.flower--5 .flower__line { height: 85vmin; animation-delay: 1.9s; }
.flower--5 .flower__line__leaf--1 { animation: blooming-leaf-right var(--fl-speed) 2.7s backwards; }
.flower--5 .flower__line__leaf--2 { animation: blooming-leaf-right var(--fl-speed) 2.5s backwards; }
.flower--5 .flower__line__leaf--3 { animation: blooming-leaf-left var(--fl-speed) 2.3s backwards; }
.flower--5 .flower__line__leaf--4 { animation: blooming-leaf-left var(--fl-speed) 2.1s backwards; }

.flower__leafs { position: relative; animation: blooming-flower 2s backwards; }
.flower__leafs--1 { animation-delay: 1.1s; }
.flower__leafs--2 { animation-delay: 1.4s; }
.flower__leafs--3 { animation-delay: 1.7s; }
.flower__leafs--4 { animation-delay: 2.0s; }
.flower__leafs--5 { animation-delay: 2.0s; }

.flower__leafs::after {
  content: "";
  position: absolute;
  left: 0;
  top: 0;
  transform: translate(-50%, -100%);
  width: 8vmin;
  height: 8vmin;
  background-color: #6bf0ff;
  filter: blur(10vmin);
}

.flower__leaf {
  position: absolute;
  bottom: 0;
  left: 50%;
  width: 23vmin;
  height: 6vmin;
  border-radius: 60% 40% 60% 40%;
  background-color: #ffd700;
  background-image: linear-gradient(to top, #ff8c00, #ffd700, #ffff00);
  transform-origin: bottom center;
  opacity: 0.95;
  box-shadow: inset 0 0 1vmin rgba(255, 255, 255, 0.7), 
              0 0 3vmin rgba(255, 215, 0, 0.4);
  z-index: 2;
}

.flower__white-circle {
  position: absolute;
  left: -4vmin;
  top: -4vmin;
  width: 10vmin;
  height: 10vmin;
  border-radius: 50%;
  background-color: #8b4513;
  background-image: radial-gradient(circle at 30% 30%, #654321, #8b4513, #2f1b14);
  box-shadow: inset 0 0 2vmin rgba(0, 0, 0, 0.8),
              0 0 1vmin rgba(139, 69, 19, 0.6);
}

.flower__white-circle::after {
  content: "";
  position: absolute;
  left: 46%;
  top: 31%;
  transform: translate(-50%, -50%);
  width: 80%;
  height: 80%;
  z-index: 3;
  border-radius: inherit;
  background-image: repeating-conic-gradient(
      from 0deg,
      #2f1b14 0deg 15deg,
      #654321 15deg 30deg
    ),
    radial-gradient(circle at center, #8b4513, #654321);
}

.flower__line {
  height: 55vmin;
  width: 2vmin;
  background-image: linear-gradient(
      to left,
      rgba(0, 0, 0, 0.3),
      transparent,
      rgba(255, 255, 255, 0.2)
    ),
    linear-gradient(to top, transparent 10%, #2d5016, #4a7c23, #6b8e23);
  box-shadow: inset 0 0 2px rgba(0, 0, 0, 0.7);
  animation: grow-flower-tree 4s backwards;
}

.flower__line__leaf {
  --w: 8vmin;
  --h: calc(var(--w) + 3vmin);
  position: absolute;
  top: 20%;
  left: 90%;
  width: var(--w);
  height: var(--h);
  border-top-right-radius: var(--h);
  border-bottom-left-radius: var(--h);
  background-image: linear-gradient(
    to top,
    rgba(45, 80, 22, 0.6),
    #4a7c23,
    #6b8e23
  );
  box-shadow: inset 0 0 1vmin rgba(0, 0, 0, 0.3);
}

.flower__line__leaf--1 { transform: rotate(70deg) rotateY(30deg); }
.flower__line__leaf--2 { top: 45%; transform: rotate(70deg) rotateY(30deg); }
.flower__line__leaf--3,
.flower__line__leaf--4 {
  border-top-right-radius: 0;
  border-bottom-left-radius: 0;
  border-top-left-radius: var(--h);
  border-bottom-right-radius: var(--h);
  left: -460%;
  top: 12%;
  transform: rotate(-70deg) rotateY(30deg);
}
.flower__line__leaf--4 { top: 40%; }

.flower__light {
  position: absolute;
  bottom: 0vmin;
  width: 0.8vmin;
  height: 0.8vmin;
  background-color: #8b4513;
  border-radius: 50%;
  filter: blur(0.1vmin);
  animation: sunflower-seeds 6s linear infinite backwards;
  box-shadow: 0 0 1vmin rgba(139, 69, 19, 0.8);
}

.flower__light:nth-child(odd) { background-color: #654321; }
.flower__light--1 { left: -2vmin; animation-delay: 1s; }
.flower__light--2 { left: 3vmin; animation-delay: 0.5s; }
.flower__light--3 { left: -6vmin; animation-delay: 0.3s; }
.flower__light--4 { left: 6vmin; animation-delay: 0.9s; }
.flower__light--5 { left: -1vmin; animation-delay: 1.5s; }
.flower__light--6 { left: -4vmin; animation-delay: 3s; }
.flower__light--7 { left: 3vmin; animation-delay: 2s; }
.flower__light--8 { left: -6vmin; animation-delay: 3.5s; }

.special-text {
  font-family: 'Playfair Display', serif;
  font-size: 1.8rem;
  color: #fffaf0;
  text-align: center;
  text-shadow: 0 0 8px #ff99cc, 0 0 16px #ff66cc;
  padding: 15px;
  position: fixed;
  top: 5%;
  left: 50%;
  transform: translateX(-50%);
  width: 90%;
  max-width: 800px;
  box-sizing: border-box;
  line-height: 1.4;
  z-index: 1000;
  opacity: 0;
  animation: fadeIn 3s 1s forwards;
}

/* Oculta el reproductor de iframe de YouTube fuera de vista */
.youtube-player {
  position: fixed;
  top: -100px;
  left: -100px;
  width: 1px;
  height: 1px;
  opacity: 0;
  pointer-events: none;
}

/* Botón flotante para activar la música */
.audio-btn {
  position: fixed;
  bottom: 20px;
  right: 20px;
  z-index: 2000;
  background: rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.4);
  color: #fff;
  padding: 10px 18px;
  border-radius: 25px;
  font-family: Arial, sans-serif;
  font-size: 0.9rem;
  cursor: pointer;
  backdrop-filter: blur(5px);
  box-shadow: 0 0 10px rgba(255, 153, 204, 0.5);
  transition: all 0.3s ease;
}

.audio-btn:hover {
  background: rgba(255, 255, 255, 0.4);
  transform: scale(1.05);
}

@media (max-width: 600px) {
  .special-text {
    font-size: 1.4rem;
    padding: 10px;
    top: 3%;
  }
}

.not-loaded * {
  animation-play-state: paused !important;
}

/* KEYFRAMES */
@keyframes fadeIn {
  to { opacity: 1; }
}

@keyframes sunflower-seeds {
  0% { opacity: 0; transform: translateY(0vmin) rotate(0deg); }
  20% { opacity: 1; transform: translateY(-3vmin) translateX(-1vmin) rotate(45deg); }
  40% { opacity: 1; transform: translateY(-8vmin) translateX(1vmin) rotate(90deg); }
  60% { transform: translateY(-12vmin) translateX(-1vmin) rotate(135deg); }
  80% { transform: translateY(-16vmin) translateX(2vmin) rotate(180deg); opacity: 0.5; }
  100% { transform: translateY(-25vmin) rotate(225deg); opacity: 0; }
}

@keyframes moving-flower-1 { 0%, 100% { transform: rotate(2deg); } 50% { transform: rotate(-2deg); } }
@keyframes moving-flower-2 { 0%, 100% { transform: rotate(18deg); } 50% { transform: rotate(14deg); } }
@keyframes moving-flower-3 { 0%, 100% { transform: rotate(-18deg); } 50% { transform: rotate(-20deg) rotateY(-10deg); } }
@keyframes moving-flower-4 { 0%, 100% { transform: rotate(9deg); } 50% { transform: rotate(12deg) rotateY(9deg); } }
@keyframes moving-flower-5 { 0%, 100% { transform: rotate(-5deg); } 50% { transform: rotate(-11deg) rotateY(5deg); } }

@keyframes blooming-leaf-right {
  0% { transform-origin: left; transform: rotate(70deg) rotateY(30deg) scale(0); }
}

@keyframes blooming-leaf-left {
  0% { transform-origin: right; transform: rotate(-70deg) rotateY(30deg) scale(0); }
}

@keyframes grow-flower-tree {
  0% { height: 0; border-radius: 1vmin; }
}

@keyframes blooming-flower {
  0% { transform: scale(0); }
}

    </style>
</head>

<body class="not-loaded">
  
  <div class="night"></div>
  
  <div class="special-text">"Solo paso por aquí a desearte un feliz cumpleaños, espero la estés pasando hermoso en tu día donde tú mandas y yo obedezco cualquier cosa solo por tu día especial" 💕🥰</div>

  <!-- Botón para iniciar el video/música -->
  <button id="musicToggle" class="audio-btn">🎵 Toca aquí para la música</button>

  <!-- Contenedor del Iframe de YouTube API -->
  <div class="youtube-player">
    <div id="player"></div>
  </div>

  <div class="shooting-stars">
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
    <div class="shooting-star"></div>
  </div>
  
  <div class="flowers">
    <!-- Flor 1 -->
    <div class="flower flower--1">
      <div class="flower__leafs flower__leafs--1">
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
        <div class="flower__white-circle"></div>
        <div class="flower__light flower__light--1"></div>
        <div class="flower__light flower__light--2"></div>
        <div class="flower__light flower__light--3"></div>
        <div class="flower__light flower__light--4"></div>
        <div class="flower__light flower__light--5"></div>
        <div class="flower__light flower__light--6"></div>
        <div class="flower__light flower__light--7"></div>
        <div class="flower__light flower__light--8"></div>
      </div>
      <div class="flower__line">
        <div class="flower__line__leaf flower__line__leaf--1"></div>
        <div class="flower__line__leaf flower__line__leaf--2"></div>
        <div class="flower__line__leaf flower__line__leaf--3"></div>
        <div class="flower__line__leaf flower__line__leaf--4"></div>
      </div>
    </div>

    <!-- Flor 2 -->
    <div class="flower flower--2">
      <div class="flower__leafs flower__leafs--2">
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
        <div class="flower__white-circle"></div>
      </div>
      <div class="flower__line">
        <div class="flower__line__leaf flower__line__leaf--1"></div>
        <div class="flower__line__leaf flower__line__leaf--2"></div>
        <div class="flower__line__leaf flower__line__leaf--3"></div>
        <div class="flower__line__leaf flower__line__leaf--4"></div>
      </div>
    </div>

    <!-- Flor 3 -->
    <div class="flower flower--3">
      <div class="flower__leafs flower__leafs--3">
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
        <div class="flower__white-circle"></div>
      </div>
      <div class="flower__line">
        <div class="flower__line__leaf flower__line__leaf--1"></div>
        <div class="flower__line__leaf flower__line__leaf--2"></div>
        <div class="flower__line__leaf flower__line__leaf--3"></div>
        <div class="flower__line__leaf flower__line__leaf--4"></div>
      </div>
    </div>
    
    <!-- Flor 4 -->
    <div class="flower flower--4">
      <div class="flower__leafs flower__leafs--4">
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
        <div class="flower__white-circle"></div>
      </div>
      <div class="flower__line">
        <div class="flower__line__leaf flower__line__leaf--1"></div>
        <div class="flower__line__leaf flower__line__leaf--2"></div>
        <div class="flower__line__leaf flower__line__leaf--3"></div>
        <div class="flower__line__leaf flower__line__leaf--4"></div>
      </div>
    </div>

    <!-- Flor 5 -->
    <div class="flower flower--5">
      <div class="flower__leafs flower__leafs--5">
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(0deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(30deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(60deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(90deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(120deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(150deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(180deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(210deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(240deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(270deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(300deg);"></div>
        <div class="flower__leaf" style="transform: translate(-50%, -10%) rotate(330deg);"></div>
        <div class="flower__white-circle"></div>
      </div>
      <div class="flower__line">
        <div class="flower__line__leaf flower__line__leaf--1"></div>
        <div class="flower__line__leaf flower__line__leaf--2"></div>
        <div class="flower__line__leaf flower__line__leaf--3"></div>
        <div class="flower__line__leaf flower__line__leaf--4"></div>
      </div>
    </div>
  </div>

  <!-- API IFrame de YouTube -->
  <script src="https://www.youtube.com/iframe_api"></script>
  <script>
    let player;
    let isPlaying = false;

    // ID del video de YouTube (puedes cambiarlo si deseas otro video)
    // ID actual: "nl629vLpF9A" (Feliz Cumpleaños)
    const YOUTUBE_VIDEO_ID = "MP1G8wnLpSM";

    function onYouTubeIframeAPIReady() {
      player = new YT.Player('player', {
        height: '1',
        width: '1',
        videoId: YOUTUBE_VIDEO_ID,
        playerVars: {
          'autoplay': 0,
          'controls': 0,
          'loop': 1,
          'playlist': YOUTUBE_VIDEO_ID
        },
        events: {
          'onReady': onPlayerReady
        }
      });
    }

    function onPlayerReady(event) {
      const musicBtn = document.getElementById('musicToggle');

      // Función para iniciar la reproducción
      const startVideo = () => {
        if (!isPlaying) {
          player.playVideo();
          isPlaying = true;
          musicBtn.textContent = "🔊 Pausar Música";
        }
      };

      // Inicia el video al presionar cualquier parte de la pantalla la primera vez
      const handleFirstInteraction = () => {
        startVideo();
        document.removeEventListener('click', handleFirstInteraction);
      };

      document.addEventListener('click', handleFirstInteraction);

      // Botón manual de Play / Pausa
      musicBtn.addEventListener('click', (e) => {
        e.stopPropagation();
        if (isPlaying) {
          player.pauseVideo();
          isPlaying = false;
          musicBtn.textContent = "🔈 Reproducir Música";
        } else {
          player.playVideo();
          isPlaying = true;
          musicBtn.textContent = "🔊 Pausar Música";
        }
      });
    }

    onload = () => {
      // Activa las animaciones CSS
      const c = setTimeout(() => {
        document.body.classList.remove("not-loaded");
        clearTimeout(c);
      }, 1000);
    };
  </script>
</body>
</html>
