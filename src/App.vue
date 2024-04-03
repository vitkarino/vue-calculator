<script>
import HeaderComponent from './components/HeaderComponent.vue'
export default {
  name: 'App',
  components: {
    HeaderComponent
  }
}
</script>

<template>
  <div id="app">
    <HeaderComponent />
    <!-- <transition name="router"><router-view /></transition> -->
    <router-view v-slot="{ Component }"
      ><transition name="router" mode="out-in"><component :is="Component" /></transition
    ></router-view>
  </div>
</template>
