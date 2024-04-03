<template>
  <div>
    <HeaderComponent />
    <CalculatorComponent />
  </div>
</template>

<script>
import CalculatorComponent from '../components/CalculatorComponent.vue'
import HeaderComponent from '../components/HeaderComponent.vue'

export default {
  name: 'HomeView',
  components: {
    CalculatorComponent,
    HeaderComponent
  }
}
</script>
