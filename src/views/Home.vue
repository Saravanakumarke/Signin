<template>
  <div class="home">
    
    <Signin/>
  </div>
</template>

<script>
// @ is an alias to /src
import Signin from '@/components/Signin.vue'

export default {
  name: 'home',
  components: {
    Signin
  }
}
</script>
