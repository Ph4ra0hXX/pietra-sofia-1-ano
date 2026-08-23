<template>
  <main class="birthday-background" aria-label="Fundo decorativo laranja com sementes pretas">
    <div class="birthday-background__texture" aria-hidden="true"></div>
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
  background-image: url('/watermelon-pattern.svg');
  background-position: center top;
  background-size: 310px 310px;
  transform: rotate(-0.4deg) scale(1.02);
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
}
</style>
