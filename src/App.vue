<template>
  <div id="app" class="overflow-x-hidden">
    <!-- medium to large screen nav -->
    <nav class="fixed top-0 inset-x-0 flex flex-row justify-between items-center bg-white px-4 py-2 z-40" id="nav">
      <div class="h-12 md:h-20 pt-3">
        <img class="hidden md:block h-full w-full object-cover" :src="require('@/assets/logo.jpeg')" alt="kenya airways logo">
        <!-- <img class="md:hidden h-full w-full object-cover" :src="require('@/assets/logo2.jpeg')" alt="kenya airways logo"> -->
        <p class="md:hidden"><span class="text-red-700">KQ</span>&nbsp;logo</p>
        <!-- logo -->
      </div>
      <button @click.prevent="showNav=true" class="md:hidden bg-transparent p-1 focus:outline-none" type="button">
        <fa-icon :icon="['fas', 'bars']" size="2x"/>
      </button>
      <ul class="hidden md:block">
        <li class="inline md:px-3 lg:px-6"><router-link :to="{name:'Home'}">Home</router-link></li>
        <li class="inline md:px-3 lg:px-6"><router-link :to="{name:'ContactUs'}">Contact&nbsp;Us</router-link></li>
        <li class="inline md:px-3 lg:px-6"><router-link :to="{name:'AboutUs'}">About&nbsp;Us</router-link></li>
      </ul>
    </nav>
    <!-- mobile navbar -->
    <router-view :showNav="showNav" />
    <!-- footer -->
    <footer class="text-xs text-white bg-gray-900 p-2 mt-4">
      <h3 class="py-2 md:py-5 font-medium text-sm md:text-xl">&copy; {{new Date().getFullYear()}} Kenya Airways Limited. All rights reserved.</h3>
    </footer>
  </div>
</template>

<script>
import {bus} from '@/main.js'
  export default{
    data(){
      return {
        showNav:false
      }
    },
    created(){
      bus.$on('closeNav', (data)=>{
        this.showNav = data
      })
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
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #D12626;
}

/* width */
::-webkit-scrollbar {
  width: 7px;
}
/* Track */
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px #E0CF35;
  border-radius: 5px;
}
/* Handle */
::-webkit-scrollbar-thumb {
  background-color: #000;
  border-radius: 5px;
}
/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background-color: #D12626;
}
</style>
