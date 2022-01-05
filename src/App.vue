<template>
  <div class="container">
    <AddCounters />
  </div>
</template>

<script>
import AddCounters from "./components/AddCounters.vue";
export default {
  name: "App",
  components: {
    AddCounters,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@200;300;400;500;600;700&display=swap");
/* Global Styles */
/* CSS Reset */
/*
  1. Use a more-intuitive box-sizing model.
*/
*,
*::before,
*::after {
  box-sizing: border-box;
}
/*
  2. Remove default margin
*/
* {
  margin: 0;
}
/*
  3. Allow percentage-based heights in the application
*/
html,
body {
  height: 100%;
}
/*
  Typographic tweaks!
  4. Add accessible line-height
  5. Improve text rendering
*/
body {
  touch-action: manipulation;
  font-family: "Inter", sans-serif;
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}
/*
  6. Improve media defaults
*/
img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
}
/*
  7. Remove built-in form typography styles
*/
input,
button,
textarea,
select {
  font: inherit;
}
/*
  8. Avoid text overflows
*/
p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
}
/*
  9. Create a root stacking context
*/
#root {
  isolation: isolate;
}
/* End reset */
:root {
  --colored-text: #36454f;
  --box-shadow: 0 2px 2px #ccc;
}

.container {
  max-width: 1128px;
  margin: 0 auto;
}
</style>
