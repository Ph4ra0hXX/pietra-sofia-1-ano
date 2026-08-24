<script setup>
const leafColors = [
  ['#78b942', '#2e6532'],
  ['#59a83a', '#214f2b'],
  ['#9ccb46', '#456f31'],
  ['#4f9d39', '#1f4d2a'],
  ['#73b842', '#2e6330'],
  ['#add24d', '#567733'],
  ['#63ad3d', '#27582d'],
  ['#8fc642', '#3b692d'],
]

const leafPositions = [
  '3%',
  '88%',
  '46%',
  '15%',
  '71%',
  '32%',
  '96%',
  '57%',
  '8%',
  '79%',
  '39%',
  '63%',
]

const leafFallDuration = 32

const leaves = Array.from({ length: leafPositions.length }, (_, index) => {
  const [color, accent] = leafColors[index % leafColors.length]
  const direction = index % 2 === 0 ? 1 : -1
  const phase = leafFallDuration * (index / leafPositions.length)

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
  }
})
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
          <path
            class="falling-leaf__stem"
            d="M31 75C30 84 27 90 21 94"
          />
          <path
            class="falling-leaf__body"
            d="M33 5C49 13 59 30 58 47C57 67 44 82 31 86C18 80 6 66 6 48C6 30 17 13 33 5Z"
          />
          <path
            class="falling-leaf__shine"
            d="M24 18C15 27 11 39 12 50C13 62 20 72 29 78C21 69 17 57 18 45C19 34 22 25 24 18Z"
          />
          <path
            class="falling-leaf__vein"
            d="M33 12C31 30 30 50 31 78"
          />
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

    <div class="name-bone" role="img" aria-label="Osso com o nome Pietra Sofia">
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
  </main>
</template>

<style scoped>
@font-face {
  font-family: "Pietra Sofia";
  src: url("/font.ttf") format("truetype");
  font-display: swap;
  font-style: normal;
  font-weight: normal;
}

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
  background-image: url("/watermelon-pattern.svg");
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

.name-bone {
  position: absolute;
  z-index: 3;
  top: clamp(12px, 3vw, 32px);
  left: 50%;
  width: min(88vw, 760px);
  animation: bone-shake 4s cubic-bezier(0.45, 0, 0.55, 1) infinite;
  transform: translateX(-50%);
  transform-box: border-box;
  transform-origin: 50% 50%;
  filter: drop-shadow(0 12px 0 rgb(77 32 12 / 18%));
  will-change: transform;
}

@keyframes bone-shake {
  0%,
  100% {
    transform: translateX(-50%) rotate(-1deg);
  }

  50% {
    transform: translateX(-50%) rotate(1deg);
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
  fill: #9fca3d;
  font-family: "Pietra Sofia", cursive;
  font-size: 70px;
  font-weight: normal;
  letter-spacing: -2px;
  paint-order: stroke;
  stroke: #000000;
  stroke-width: 12px;
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

  .name-bone {
    width: 94vw;
  }

  .name-bone__text {
    font-size: 80px;
  }
}

@media (prefers-reduced-motion: reduce) {
  .name-bone {
    animation: none;
  }

  .falling-leaf {
    animation-duration: 34s;
  }
}
</style>
