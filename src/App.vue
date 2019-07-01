<template>
  <div id="app">
    <transition @enter="enter" @leave="leave" :css="false">
    	<img alt="Vue logo" src="./assets/logo.png" v-if="show">
    </transition>
    <HelloWorld msg="Welcome to Your Vue.js App" v-if="show"/>
    <button @click="show = !show">Toggle Content</button> 
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  data() {
  	return {
  		show: false,
  	}
  },
  components: {
    HelloWorld
  },
  methods: {
  	enter(el, done) {
  		console.log("enter hello world called", el)
  		TweenMax.from(el, 2, { opacity: 0, xPercent: 100, onComplete: done })
  	},
  	leave(el, done) {
  		console.log("leave hello world called", el)
  		TweenMax.to(el, 2, { opacity: 0, xPercent: 100, onComplete: done })
  	},
  }
}
</script>

<style lang="less">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
