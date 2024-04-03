<template>
  <div>
    <HeaderComponent />
    <p>
      Hello, I'm Viktor Kysil - creator of this app! Thank you for trying out my project and don't
      forget to check out my <a href="https://github.com/vitkarino">github</a> to find new projects
      I made!
    </p>
  </div>
</template>

<script>
import HeaderComponent from '../components/HeaderComponent.vue'

export default {
  name: 'AboutView',
  components: {
    HeaderComponent
  }
}
</script>

<style scoped lang="scss">
@import '/src/assets/main.scss';

p {
  color: $text-light;
  width: 50vh;
}

a {
  text-decoration: none;
  color: $primary;
  transition: 0.1s ease-in-out;

  &:hover {
    filter: brightness(1.3);
    cursor: pointer;
  }
}
</style>
