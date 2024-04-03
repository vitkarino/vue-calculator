<template>
  <header>
    <nav>
      <router-link to="/" class="link" id="logo">Viktor's Vue Calculator</router-link>
      <router-link to="/" class="link">Home</router-link>
      <router-link to="/about" class="link">About</router-link>
    </nav>
  </header>
</template>

<style scoped lang="scss">
@import '/src/assets/main.scss';

header {
  position: absolute;
  width: 100%;
  top: 2vh;
  left: 0;
  text-align: center;
  display: flex;
  justify-content: center;
  font-weight: 500;
  font-style: normal;

  color: $primary;

  nav {
    display: flex;
    list-style: none;

    #logo {
      color: $primary;
    }

    .link {
      color: $text-light;
      margin-left: 16px;
      transition: 0.1s ease-in-out;

      &:hover {
        filter: brightness(1.3);
        cursor: pointer;
      }
    }
  }
}
</style>
