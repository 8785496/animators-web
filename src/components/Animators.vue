<template>
  <ul>
    <li v-for="animator in animators" :key="animator.name">
      {{ animator.name }}
    </li>
  </ul>
</template>

<script>
import { environment } from '../environment'

export default {
  name: 'Animators',
  data() {
    return {
      animators: []
    }
  },
  mounted() {
    const api = environment.api;
    fetch(`${api}/animators`).then(res => {
      res.json().then(data => this.animators = data);
    })
  }
}
</script>

<style scoped>
ul {
  background: silver;
}
</style>
