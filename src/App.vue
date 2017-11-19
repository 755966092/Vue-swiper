<template>
  <div id="app">
    <Swiper :imgArr="imgArr" :time=1500 :autoPlay=true></Swiper>
  </div>
</template>

<script>
import Swiper from './components/Swiper.vue'
export default {
  name: 'app',
  components : {
    Swiper
  },
  data() {
    return {
      imgArr: [
        {
          src:require("./images/1.jpg"),
          title: '1.jpg'
        },
        {
          src:require("./images/2.jpg"),
          title: '2.jpg'
        },
        {
          src:require("./images/3.jpg"),
          title: '3.jpg'
        },
        {
          src:require("./images/4.jpg"),
          title: '4.jpg'
        },
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
* {
  margin: 0;
  padding: 0;
}
a {
  text-decoration: none;
}
ul,li {
  list-style: none;
}
</style>
