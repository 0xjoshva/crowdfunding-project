<template>
  <router-view />
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Commissioner:wght@100;200;300;400;500;600;700;800;900&display=swap');
*,
*::before,
*::after {
  box-sizing: border-box;
}
* {
  margin: 0;
}
html,
body {
  height: 100%;
  font-family: 'Commissioner', sans-serif;
}
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}
img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
}
input,
button,
textarea,
select {
  font: inherit;
}
p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
}
#root,
#__next {
  isolation: isolate;
}

:root {
  /* primary */
  --moderatecyan: hsl(176, 50%, 47%);
  --darkcyan: hsl(176, 72%, 28%);

  /* neutral */
  --black: hsl(0, 0%, 0%);
  --darkgray: hsl(0, 0%, 48%);
}
</style>
