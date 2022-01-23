<template>
  <img alt="Vue logo" :src="imgUrl">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import {Storage} from "aws-amplify";

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      imgUrl: ''
    }
  },
  async created() {
    const photos_public = await Storage.list('', { level: 'public' });
    // const photos_private = await Storage.list('', { level: 'private' });
    console.log(photos_public);
    // console.log(photos_private);

    this.imgUrl = await Storage.get('test_public.png');
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
