<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <AllDirectMessages />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import AllDirectMessages from '@/components/AllDirectMessages.vue'

export default {
  name: 'Home',
  components: {
    AllDirectMessages
  }
}
</script>
