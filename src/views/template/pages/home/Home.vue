<template>
  <div class="home">
    <img alt="Vue logo" src="src/assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/views/template/pages/home/HelloWorld.vue"

export default {
  name: "Home",
  components: {
    HelloWorld
  }
}
</script>
