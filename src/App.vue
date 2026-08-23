<template>
  <main class="birthday-background" aria-label="Fundo decorativo laranja com sementes pretas">
    <div class="birthday-background__texture" aria-hidden="true"></div>

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
        <text class="name-bone__text" x="380" y="153" text-anchor="middle">PIETRA SOFIA</text>
      </svg>
    </div>
  </main>
</template>

<style scoped>
@font-face {
  font-family: 'Pietra Sofia';
  src: url('/font.ttf') format('truetype');
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
  background-image: url('/watermelon-pattern.svg');
  background-position: center top;
  background-size: 310px 310px;
  transform: rotate(-0.4deg) scale(1.02);
}

.name-bone {
  position: absolute;
  z-index: 1;
  top: clamp(12px, 3vw, 32px);
  left: 50%;
  width: min(88vw, 760px);
  transform: translateX(-50%) rotate(-2deg);
  filter: drop-shadow(0 12px 0 rgb(77 32 12 / 18%));
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
  fill: #080808;
  font-family: 'Pietra Sofia', cursive;
  font-size: 70px;
  font-weight: normal;
  letter-spacing: -2px;
  paint-order: stroke;
  stroke: #fff9e8;
  stroke-width: 12px;
}

/* Uma granulação quase imperceptível tira o aspecto excessivamente digital. */
.birthday-background::after {
  position: absolute;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 180 180' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.18'/%3E%3C/svg%3E");
  content: '';
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
</style>
