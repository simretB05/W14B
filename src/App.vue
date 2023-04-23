<template>
  <div id="app">
  <get-joke-button></get-joke-button>
  <normal-joke-button></normal-joke-button>
  <snake-joke-button></snake-joke-button>
  <loud-joke-button></loud-joke-button>
  <display-joke></display-joke>
  </div>
</template>

<script>
//imported  components
import GetJokeButton from '@/components/GetJokeButton.vue';
import NormalJokeButton from './components/NormalJokeButton.vue';
import DisplayJoke from './components/DisplayJoke.vue';
import SnakeJokeButton from './components/SnakeJokeButton.vue';
import LoudJokeButton from './components/LoudJokeButton.vue';
export default {
  
  name: 'App',
  components: {
    // registered Components
    GetJokeButton,
    NormalJokeButton,
    DisplayJoke,
    SnakeJokeButton,
    LoudJokeButton
    
  },
 
    
    }
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
