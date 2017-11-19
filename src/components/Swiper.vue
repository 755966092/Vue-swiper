<template>
  <div class="hello" @mouseover="clearTime" @mouseout="setTime">
    <div class="swiper">
      <img :src="imgArr[currentNum].src" alt="" >
      
      <div>
        <p>{{imgArr[currentNum].title}}</p>
        <span @click="switchImg(nextNum)"><a href="javascripe:;">&lt;</a></span>
        <ul>
          <li @click="switchImg(index)" v-for="(item, index) in imgArr">
            <a href="javascripe:;">{{ index + 1 }}</a>
          </li>
        </ul>
        <span @click="switchImg(preNum)"><a href="javascripe:;">&gt;</a></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Swiper',
  props: {
    imgArr: {
      type: Array,
      default: []
    },
    time: {
      type: Number,
      default: 1000
    },
    autoPlay: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {
      currentNum:0
    }
  },
  methods: {
    switchImg(index) {
      this.currentNum = index;
    },
    interval() {
      this.inv = setInterval(() => {
        this.switchImg(this.preNum);
      },this.time)
    },
    clearTime() {
      clearInterval(this.inv)
    },
    setTime() {
      if(this.autoPlay) {
        this.interval();
      } 
    }
  },
  computed: {
    nextNum() {
      if (this.currentNum === 0) {
        return this.imgArr.length-1
      } else {
        return this.currentNum - 1
      }
    },
    preNum() {
      if (this.currentNum  === this.imgArr.length-1) {
        return 0
      } else {
        return this.currentNum + 1
      }
    }
  },
  created() {
    if(this.autoPlay) {
      this.interval();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  img {
    display: inline-block;
    width: 550px;
    height: 320px;
  }
  ul,li {
    display: inline-block;
  }
  li {
    padding: 0 3px;
  }
</style>
