<script setup>
const leafColors = [
  ["#78b942", "#2e6532"],
  ["#59a83a", "#214f2b"],
  ["#9ccb46", "#456f31"],
  ["#4f9d39", "#1f4d2a"],
  ["#73b842", "#2e6330"],
  ["#add24d", "#567733"],
  ["#63ad3d", "#27582d"],
  ["#8fc642", "#3b692d"],
];

const leafPositions = [
  "3%",
  "88%",
  "46%",
  "15%",
  "71%",
  "32%",
  "96%",
  "57%",
  "8%",
  "79%",
  "39%",
  "63%",
];

const leafFallDuration = 32;

const leaves = Array.from({ length: leafPositions.length }, (_, index) => {
  const [color, accent] = leafColors[index % leafColors.length];
  const direction = index % 2 === 0 ? 1 : -1;
  const phase = leafFallDuration * (index / leafPositions.length);

  return {
    x: leafPositions[index],
    delay: `-${phase.toFixed(2)}s`,
    duration: `${leafFallDuration}s`,
    size: `${28 + (index % 7) * 3}px`,
    mid: `${direction * (44 + (index % 4) * 14)}px`,
    end: `${direction * (10 + (index % 3) * 8)}px`,
    spin: `${-46 + ((index * 31) % 96)}deg`,
    color,
    accent,
  };
});

const grassColors = [
  ["#7cc142", "#2f7d33"],
  ["#5baa37", "#23652b"],
  ["#9ccc46", "#44782f"],
  ["#438f35", "#195423"],
  ["#6dbb3c", "#2b7430"],
  ["#a7d653", "#527f34"],
];

const grassBladeCount = 72;

const grassBlades = Array.from({ length: grassBladeCount }, (_, index) => {
  const [color, shadow] = grassColors[index % grassColors.length];
  const row = index % 4;

  return {
    x: `${((index / (grassBladeCount - 1)) * 100).toFixed(2)}%`,
    bottom: `${-18 + row * 6}px`,
    depth: `${1 + row}`,
    width: `${7 + ((index * 5) % 7)}px`,
    height: `${62 + row * 16 + ((index * 19) % 64)}px`,
    lean: `${-12 + ((index * 17) % 25)}deg`,
    sway: `${7 + ((index * 11) % 9)}deg`,
    duration: `${2.25 + ((index * 7) % 10) / 10}s`,
    delay: `-${((index * 13) % 28) / 10}s`,
    color,
    shadow,
  };
});
</script>

<template>
  <main
    class="birthday-background"
    aria-label="Fundo decorativo laranja com sementes pretas"
  >
    <div class="birthday-background__texture" aria-hidden="true"></div>
    <div class="falling-leaves" aria-hidden="true">
      <span
        v-for="(leaf, index) in leaves"
        :key="index"
        class="falling-leaf"
        :style="{
          '--x': leaf.x,
          '--delay': leaf.delay,
          '--duration': leaf.duration,
          '--size': leaf.size,
          '--mid': leaf.mid,
          '--end': leaf.end,
          '--spin': leaf.spin,
          '--leaf-color': leaf.color,
          '--leaf-accent': leaf.accent,
        }"
      >
        <svg
          class="falling-leaf__graphic"
          viewBox="0 0 64 96"
          xmlns="http://www.w3.org/2000/svg"
          aria-hidden="true"
        >
          <path class="falling-leaf__stem" d="M31 75C30 84 27 90 21 94" />
          <path
            class="falling-leaf__body"
            d="M33 5C49 13 59 30 58 47C57 67 44 82 31 86C18 80 6 66 6 48C6 30 17 13 33 5Z"
          />
          <path
            class="falling-leaf__shine"
            d="M24 18C15 27 11 39 12 50C13 62 20 72 29 78C21 69 17 57 18 45C19 34 22 25 24 18Z"
          />
          <path class="falling-leaf__vein" d="M33 12C31 30 30 50 31 78" />
          <path
            class="falling-leaf__vein falling-leaf__vein--left"
            d="M31 39C23 35 17 30 13 24"
          />
          <path
            class="falling-leaf__vein falling-leaf__vein--left"
            d="M30 55C22 53 16 49 11 43"
          />
          <path
            class="falling-leaf__vein falling-leaf__vein--right"
            d="M32 34C42 30 49 24 53 17"
          />
          <path
            class="falling-leaf__vein falling-leaf__vein--right"
            d="M31 58C42 55 49 49 54 41"
          />
        </svg>
      </span>
    </div>

    <section class="party-header" aria-label="Informacoes da festa">
      <div
        class="name-bone"
        role="img"
        aria-label="Osso com o nome Pietra Sofia"
      >
        <div class="name-bone__motion">
          <svg
            class="name-bone__shape"
            viewBox="0 0 760 300"
            xmlns="http://www.w3.org/2000/svg"
            aria-hidden="true"
          >
            <path
              class="name-bone__shadow"
              d="M105 59C67 38 19 65 21 109C22 132 35 148 55 158C34 170 22 189 23 212C25 253 71 276 106 256C123 246 131 231 139 214C151 190 169 184 199 184H561C591 184 609 190 621 214C629 231 637 246 654 256C689 276 735 253 737 212C738 189 726 170 705 158C725 148 738 132 739 109C741 65 693 38 655 59C637 69 628 85 620 102C609 124 590 130 561 130H199C170 130 151 124 140 102C132 85 123 69 105 59Z"
            />
            <path
              class="name-bone__body"
              d="M105 47C67 26 19 53 21 97C22 120 35 136 55 146C34 158 22 177 23 200C25 241 71 264 106 244C123 234 131 219 139 202C151 178 169 172 199 172H561C591 172 609 178 621 202C629 219 637 234 654 244C689 264 735 241 737 200C738 177 726 158 705 146C725 136 738 120 739 97C741 53 693 26 655 47C637 57 628 73 620 90C609 112 590 118 561 118H199C170 118 151 112 140 90C132 73 123 57 105 47Z"
            />
            <text class="name-bone__text" x="380" y="133" text-anchor="middle">
              1 ANO
            </text>

            <text class="name-bone__text" x="380" y="203" text-anchor="middle">
              PIETRA SOFIA
            </text>
          </svg>
        </div>
      </div>

      <div
        class="event-details"
        aria-label="Outubro, dia 04, as 14 horas e 30 minutos"
      >
        <span class="event-details__item">Outubro </span>
        <span class="event-details__number">04</span>
        <span class="event-details__item">às 14:30</span>
      </div>

      <div class="party-actions" aria-label="Acoes da festa">
        <button class="party-actions__button" type="button">
          <span class="party-actions__button-label">
            Confirmar presen&ccedil;a
          </span>
        </button>
        <button class="party-actions__button" type="button">
          <span class="party-actions__button-label">
            Localiza&ccedil;&atilde;o da festa
          </span>
        </button>
        <button class="party-actions__button" type="button">
          <span class="party-actions__button-label"> Dicas de presentes </span>
        </button>
      </div>
    </section>

    <footer class="grass-footer" aria-hidden="true">
      <div class="grass-footer__field">
        <span
          v-for="(blade, index) in grassBlades"
          :key="index"
          class="grass-footer__blade"
          :style="{
            '--grass-x': blade.x,
            '--grass-bottom': blade.bottom,
            '--grass-depth': blade.depth,
            '--grass-width': blade.width,
            '--grass-height': blade.height,
            '--grass-lean': blade.lean,
            '--grass-sway': blade.sway,
            '--grass-duration': blade.duration,
            '--grass-delay': blade.delay,
            '--grass-color': blade.color,
            '--grass-shadow': blade.shadow,
          }"
        ></span>
      </div>
    </footer>
  </main>
</template>

<style scoped>
.birthday-background {
  position: relative;
  min-height: 100svh;
  overflow: hidden;
  background-color: #ff914d;
  isolation: isolate;
}

.birthday-background__texture {
  position: absolute;
  inset: -45px;
  background-image: url("./assets/watermelon-pattern.svg");
  background-position: center top;
  background-size: 310px 310px;
  transform: rotate(-0.4deg) scale(1.02);
}

.falling-leaves {
  position: absolute;
  inset: 0;
  z-index: 2;
  overflow: hidden;
  pointer-events: none;
}

.falling-leaf {
  position: absolute;
  display: block;
  top: -110px;
  left: var(--x);
  width: min(var(--size), 10vw);
  opacity: 0;
  transform: translate3d(0, -18vh, 0);
  animation: leaf-fall var(--duration) linear infinite;
  animation-delay: var(--delay);
  will-change: transform, opacity;
}

.falling-leaf__graphic {
  display: block;
  width: 100%;
  overflow: visible;
  filter: drop-shadow(0 7px 5px rgb(73 31 14 / 18%));
  transform: rotate(var(--spin));
  transform-origin: 50% 50%;
  animation: leaf-flutter 2.8s ease-in-out infinite alternate;
  animation-delay: var(--delay);
  will-change: transform;
}

.falling-leaf:nth-child(3n) .falling-leaf__graphic {
  animation-duration: 3.5s;
}

.falling-leaf:nth-child(4n) .falling-leaf__graphic {
  animation-duration: 2.3s;
}

.falling-leaf__body {
  fill: var(--leaf-color);
  stroke: #111111;
  stroke-linejoin: round;
  stroke-width: 2.8;
}

.falling-leaf__shine {
  fill: rgb(255 255 255 / 20%);
}

.falling-leaf__stem,
.falling-leaf__vein {
  fill: none;
  stroke: var(--leaf-accent);
  stroke-linecap: round;
  stroke-linejoin: round;
  stroke-width: 3.2;
}

.falling-leaf__stem {
  stroke: #193b20;
  stroke-width: 4;
}

.falling-leaf__vein--left,
.falling-leaf__vein--right {
  stroke-width: 2.4;
  opacity: 0.65;
}

@keyframes leaf-fall {
  0% {
    opacity: 0;
    transform: translate3d(0, -22vh, 0);
  }

  2%,
  98% {
    opacity: 0.95;
  }

  24% {
    transform: translate3d(var(--mid), 24vh, 0);
  }

  50% {
    transform: translate3d(0, 55vh, 0);
  }

  76% {
    transform: translate3d(var(--mid), 84vh, 0);
  }

  100% {
    opacity: 0;
    transform: translate3d(var(--end), 122vh, 0);
  }
}

@keyframes leaf-flutter {
  0% {
    transform: rotate(var(--spin)) rotateY(0deg);
  }

  50% {
    transform: rotate(18deg) rotateY(42deg);
  }

  100% {
    transform: rotate(-24deg) rotateY(-24deg);
  }
}

.party-header {
  position: absolute;
  z-index: 3;
  top: clamp(12px, 3vw, 32px);
  left: 50%;
  width: min(88vw, 760px);
  transform: translateX(-50%);
}

.name-bone {
  filter: drop-shadow(0 12px 0 rgb(77 32 12 / 18%));
}

.name-bone__motion {
  animation: bone-shake 4.6s ease-in-out infinite;
  display: block;
  transform-origin: 50% 50%;
  will-change: transform;
}

@keyframes bone-shake {
  0%,
  100% {
    transform: translate3d(0, 0, 0) rotate(-1.1deg);
  }

  50% {
    transform: translate3d(0, 2px, 0) rotate(1.1deg);
  }
}

.name-bone__shape {
  display: block;
  width: 100%;
  overflow: visible;
}

.name-bone__shadow {
  fill: #080808;
}

.name-bone__body {
  fill: #fff9e8;
  stroke: #080808;
  stroke-width: 8;
  stroke-linejoin: round;
}

.name-bone__text {
  fill: #ed008e;
  font-family: "Pietra Sofia Title", cursive;
  font-size: 70px;
  font-weight: normal;
  letter-spacing: 0;
  paint-order: stroke;
  stroke: #000000;
  stroke-width: 12px;
}

.event-details {
  display: grid;
  grid-template-columns: minmax(0, 1fr) auto minmax(0, 1fr);
  align-items: center;
  column-gap: clamp(8px, 3.5vw, 40px);
  margin-top: clamp(-8px, -1.2vw, 4px);
  color: #fff;
  font-family: "Pietra Sofia", cursive;
  text-align: center;
  text-transform: uppercase;
  filter: drop-shadow(0 5px 0 rgb(0 0 0 / 16%));
}

.event-details__item {
  display: grid;
  min-width: 0;
  gap: clamp(8px, 1.8vw, 13px);
  justify-items: center;
  font-size: 30px;
  line-height: 0.9;
  letter-spacing: 0;
  overflow-wrap: anywhere;
  paint-order: stroke;
  -webkit-text-stroke: clamp(4px, 0.35vw, 3px) #000000;
}

.event-details__item::before,
.event-details__item::after {
  display: block;
  width: min(100%, 242px);
  height: clamp(3px, 0.65vw, 6px);
  border-radius: 999px;
  background: #fff;
  content: "";
}

.event-details__number {
  color: #ed008e;
  font-size: clamp(82px, 16vw, 164px);
  line-height: 0.74;
  letter-spacing: 0;
  paint-order: stroke;
  -webkit-text-stroke: clamp(4px, 0.75vw, 7px) #fff;
  text-shadow: 0 4px 0 rgb(0 0 0 / 18%);
}

.party-actions {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  align-items: stretch;
  gap: clamp(12px, 2vw, 20px);
  width: min(96vw, 960px);
  margin: clamp(16px, 2.6vw, 28px) auto 0;
}

.party-actions__button {
  appearance: none;
  position: relative;
  display: grid;
  place-items: center;
  min-width: min(100%, 280px);
  min-height: clamp(50px, 6vw, 64px);
  padding: 12px clamp(14px, 2vw, 22px) 13px;
  color: #ffffff;
  font-family: "Pietra Sofia Title", cursive;
  font-size: clamp(18px, 2.1vw, 25px);
  font-weight: normal;
  line-height: 1;
  letter-spacing: 0.4px;
  text-align: center;
  text-transform: uppercase;
  overflow-wrap: anywhere;
  background: #ed008e;
  border: 0;
  border-radius: 10px;
  box-shadow:
    0 6px 0 #9e005f,
    0 8px 0 rgb(0 0 0 / 10%);
  cursor: pointer;
  transform: translateY(0);
  transition:
    background-color 140ms ease,
    box-shadow 140ms ease,
    transform 140ms ease,
    filter 140ms ease;
}

.party-actions__button-label {
  position: relative;
  z-index: 1;
  display: block;
}

.party-actions__button:hover {
  background: #ff159e;
  filter: brightness(1.01);
  box-shadow:
    0 4px 0 #9e005f,
    0 6px 0 rgb(0 0 0 / 9%);
  transform: translateY(2px);
}

.party-actions__button:active {
  box-shadow:
    0 1px 0 #9e005f,
    0 2px 0 rgb(0 0 0 / 7%);
  transform: translateY(5px);
}

.party-actions__button:focus-visible {
  outline: 4px solid #ffffff;
  outline-offset: 4px;
}

.grass-footer {
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 4;
  height: clamp(128px, 24vh, 230px);
  overflow: hidden;
  pointer-events: none;
}

.grass-footer__field {
  position: absolute;
  inset: 0 -2% 0;
  transform-origin: bottom center;
}

.grass-footer__blade {
  position: absolute;
  bottom: var(--grass-bottom);
  left: var(--grass-x);
  z-index: var(--grass-depth);
  display: block;
  width: var(--grass-width);
  height: var(--grass-height);
  background: var(--grass-color);
  border-radius: 999px 999px 0 0;
  clip-path: polygon(50% 0, 100% 100%, 0 100%);
  transform: translateX(-50%) rotate(var(--grass-lean));
  transform-origin: 50% 100%;
  animation: grass-blade-sway var(--grass-duration) ease-in-out infinite
    alternate;
  animation-delay: var(--grass-delay);
  will-change: transform;
}

.grass-footer__blade:nth-child(2n) {
  background: var(--grass-shadow);
}

.grass-footer__blade:nth-child(3n) {
  width: calc(var(--grass-width) + 3px);
  opacity: 0.92;
}

@keyframes grass-blade-sway {
  0% {
    transform: translateX(-50%)
      rotate(calc(var(--grass-lean) - var(--grass-sway)));
  }

  100% {
    transform: translateX(-50%)
      rotate(calc(var(--grass-lean) + var(--grass-sway)));
  }
}

/* Uma granulação quase imperceptível tira o aspecto excessivamente digital. */
.birthday-background::after {
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.18'/%3E%3C/svg%3E");
  content: "";
  opacity: 0.035;
  pointer-events: none;
  mix-blend-mode: multiply;
}

@media (max-width: 600px) {
  .birthday-background__texture {
    background-size: 255px 255px;
  }

  .grass-footer {
    height: clamp(122px, 21vh, 190px);
  }

  .party-header {
    width: 94vw;
  }

  .name-bone__text {
    font-size: 80px;
  }

  .event-details {
    column-gap: 7px;
  }

  .party-actions {
    grid-template-columns: 1fr;
    gap: 10px;
    width: min(440px, 90vw);
    margin-top: 14px;
  }

  .party-actions__button {
    min-height: 60px;
    padding: 12px 16px 13px;
    font-size: clamp(18px, 5.2vw, 24px);
    box-shadow:
      0 6px 0 #9e005f,
      0 8px 0 rgb(0 0 0 / 10%);
  }
}

@media (prefers-reduced-motion: reduce) {
  .falling-leaf {
    animation-duration: 34s;
  }

  .grass-footer__blade {
    animation-duration: 8s;
  }
}
</style>
