<template>
  <div id="app">
    <div class="container mx-auto">
    <div class="flex h-screen justify-center items-center">
      <div class="w-1/3 flex flex-col justify-start">
       <transition
          enter-active-class="animated shake"
          leave-active-class="animated swing"
        >
        <svg v-show="vue" class="h-64" v-bind:style="winner == 'react' ? 'transform: rotate(-200deg)' : ''" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 261.8 226.7"><path d="M161.15-.011l-30.267 52.4-30.266-52.4H-.05l130.933 226.666L261.817-.01H161.15z" fill="#4dba87"></path><path d="M161.15-.011l-30.267 52.4-30.266-52.4H52.35l78.533 136 78.534-136H161.15z" fill="#435466"></path></svg>
       </transition>
          <!-- <svg width="14" height="16" aria-hidden="true" class="octicon octicon-star"><path fill="#333" fill-rule="evenodd" d="M14 6l-4.9-.64L7 1 4.9 5.36 0 6l3.6 3.26L2.67 14 7 11.67 11.33 14l-.93-4.74L14 6z"></path></svg> -->
        <transition
          enter-active-class="animated bounceInDown"
        >
        <h1 v-show="winner === 'vue' && !start" class="text-blue-light text-xl md:text-5xl font-bold text-center">WINNER</h1>        
        </transition>
      </div>
      <div class="w-1/3 flex flex-col justify-center">
        <button v-show="!initing" @click="init" type="button" class="shadow-lg text-white font-sans border hover:bg-grey-light text-base md:text-5xl p-3 rounded flex justify-center items-center w-full">
          <div class="text-green-light sm:px-1 md:px-3">
            Vuejs 
          </div>
          <span class="px-1 text-black font-semibold underline text-base">VS</span>  
          <div class="sm:px-1 md:px-3" style="color:#61dafb;">          
              React
          </div>
        </button>
         <transition
          enter-active-class="animated shake"
          leave-active-class="animated swing"          
        >
        <span v-show="fighting" class="text-black font-thin text-xl md:text-3xl flex flex-col justify-center items-center">
          <svg class="text-grey-darker h-24 w-24 mb-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M4.34 15.66A7.97 7.97 0 0 0 9 17.94V10H5V8h4V5.83a3 3 0 1 1 2 0V8h4v2h-4v7.94a7.97 7.97 0 0 0 4.66-2.28l-1.42-1.42h5.66l-2.83 2.83a10 10 0 0 1-14.14 0L.1 14.24h5.66l-1.42 1.42zM10 4a1 1 0 1 0 0-2 1 1 0 0 0 0 2z"/></svg>
          <!-- FIGHTING ... -->
        </span>
         </transition>
        <transition
          enter-active-class="animated zoomIn"
        >
        <span v-show="winner === 'react' && !start" class="text-black font-thin text-3xl flex flex-col justify-center items-center">
          <svg class="h-8" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 490.6 436.9"><path fill="#61dafb" d="M490.6 218.5c0-32.5-40.7-63.3-103.1-82.4 14.4-63.6 8-114.2-20.2-130.4-6.5-3.8-14-5.6-22.3-5.6V0c-27.5 0-63.5 19.6-99.9 53.6C208.7 19.8 172.7.4 145.2.4v.1c-8.4 0-16 1.8-22.6 5.6-28.1 16.2-34.4 66.7-19.9 130.1C40.5 155.4 0 186.1 0 218.5c0 32.5 40.7 63.3 103.1 82.4-14.4 63.6-8 114.2 20.2 130.4 6.5 3.8 14.1 5.6 22.5 5.6 27.5 0 63.5-19.6 99.9-53.6 36.4 33.8 72.4 53.2 99.9 53.2 8.4 0 16-1.8 22.6-5.6 28.1-16.2 34.4-66.7 19.9-130.1 62-19.1 102.5-49.9 102.5-82.3zM344.9 22.3c4.6.1 8.3 1 11.4 2.7 13.6 7.8 19.5 37.5 14.9 75.7-1.1 9.4-2.9 19.3-5.1 29.4-19.6-4.8-41-8.5-63.5-10.9-13.5-18.5-27.5-35.3-41.6-50 32.5-30.3 63.1-46.8 83.9-46.9zM156.7 269.7c4.7 8 9.5 15.8 14.4 23.4-14.2-2.1-27.9-4.7-41-7.9 3.7-12.9 8.3-26.2 13.5-39.5 4.1 8 8.4 16 13.1 24zm-26.9-117.9c13.1-3.1 26.9-5.8 41.2-7.9-4.9 7.7-9.8 15.6-14.4 23.7-4.6 8-8.9 16-13 24-5.4-13.4-10-26.8-13.8-39.8zm25.5 67c6.2-13.4 13.2-26.8 20.7-39.9 7.8-13.5 15.8-26.3 24.1-38.2 14.9-1.3 30-2 45.2-2 15.1 0 30.2.7 45 1.9 8.3 11.9 16.4 24.6 24.2 38 7.6 13.1 14.5 26.4 20.8 39.8-6.3 13.4-13.2 26.8-20.7 39.9-7.8 13.5-15.8 26.3-24.1 38.2-14.9 1.3-30 2-45.2 2-15.1 0-30.2-.7-45-1.9-8.3-11.9-16.4-24.6-24.2-38-7.6-13.1-14.5-26.4-20.8-39.8zm178.6 50.6c4.6-8 8.9-16.1 13-24.1 5.4 13.4 10 26.8 13.8 39.8-13.1 3.2-26.9 5.9-41.2 8 4.9-7.7 9.8-15.6 14.4-23.7zm-.1-102.1c-4.6-8-9.5-15.8-14.4-23.4 14.2 2.1 27.9 4.7 41 7.9-3.7 12.9-8.3 26.2-13.5 39.5-4.1-8-8.4-16-13.1-24zm-61-50.3c-9-.4-18.2-.7-27.5-.7-9.4 0-18.7.2-27.8.7 9-11.7 18.3-22.4 27.5-32 9.3 9.6 18.6 20.3 27.8 32zM133.7 25.4c3-1.8 6.9-2.6 11.5-2.6v-.1c20.7 0 51.4 16.5 84 46.6-14 14.7-28 31.4-41.3 49.9-22.6 2.4-44 6.1-63.6 11-2.3-10-4-19.7-5.2-29-4.7-38.2 1.1-67.9 14.6-75.8zm-25.2 253.9c-9.9-3.1-19.3-6.5-28-10.2-35.4-15.1-58.3-34.9-58.3-50.6s22.9-35.6 58.3-50.6c8.6-3.7 18-7 27.7-10.1 5.7 19.6 13.2 40 22.5 60.9-9.2 20.8-16.6 41.1-22.2 60.6zm37.1 135.4c-4.5-.1-8.3-1-11.3-2.7-13.6-7.8-19.5-37.5-14.9-75.7 1.1-9.4 2.9-19.3 5.1-29.4 19.6 4.8 41 8.5 63.5 10.9 13.5 18.5 27.5 35.3 41.6 50-32.6 30.3-63.2 46.9-84 46.9zm99.9-62.7c-9.3-9.6-18.6-20.3-27.8-32 9 .4 18.2.7 27.5.7 9.4 0 18.7-.2 27.8-.7-9 11.7-18.3 22.4-27.5 32zm111.4 59.6c-3 1.8-6.9 2.6-11.5 2.6-20.7 0-51.4-16.5-84-46.6 14-14.7 28-31.4 41.3-49.9 22.6-2.4 44-6.1 63.6-11 2.3 10.1 4.1 19.8 5.2 29.1 4.7 38.2-1.1 67.9-14.6 75.8zM410 269.1c-8.6 3.7-18 7-27.7 10.1-5.7-19.6-13.2-40-22.5-60.9 9.2-20.8 16.6-41.1 22.2-60.6 9.9 3.1 19.3 6.5 28.1 10.2 35.4 15.1 58.3 34.9 58.3 50.6-.1 15.7-23 35.6-58.4 50.6z" class="st0"></path><circle fill="#61dafb" cx="245.2" cy="218.5" r="45.7" class="st0"></circle></svg>
          <p class="mt-4 flex items-center text-base">
          <svg class="-mr-1" width="20" height="16" aria-hidden="true"><path fill="#333" fill-rule="evenodd" d="M14 6l-4.9-.64L7 1 4.9 5.36 0 6l3.6 3.26L2.67 14 7 11.67 11.33 14l-.93-4.74L14 6z"></path></svg>
           {{ reactstart }}
          </p>
        </span>   
        </transition>
        <transition
          enter-active-class="animated zoomIn"
        >        
        <span v-show="winner === 'vue' && !start" class="text-black font-thin text-3xl flex flex-col justify-center items-center">
          <svg class="h-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 261.8 226.7"><path d="M161.15-.011l-30.267 52.4-30.266-52.4H-.05l130.933 226.666L261.817-.01H161.15z" fill="#4dba87"></path><path d="M161.15-.011l-30.267 52.4-30.266-52.4H52.35l78.533 136 78.534-136H161.15z" fill="#435466"></path></svg>
          <p class="mt-4 flex items-center text-sm">
          <svg class="-mr-1" width="20" height="16" aria-hidden="true"><path fill="#333" fill-rule="evenodd" d="M14 6l-4.9-.64L7 1 4.9 5.36 0 6l3.6 3.26L2.67 14 7 11.67 11.33 14l-.93-4.74L14 6z"></path></svg>
           {{ vuestart }}
          </p>
        </span>  
        </transition>
        <button v-show="!start && winner !== ''" @click="init" class="apperance-none underline text-center text-grey-darker text-lg mt-6">Retry</button>
      </div>
      <div class="w-1/3 flex flex-col justify-end">
        <transition
          enter-active-class="animated shake"
          leave-active-class="animated swing"
        >
        <svg v-show="react" class="h-64" v-bind:style="winner == 'vue' ? 'transform: rotate(-200deg)' : ''" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 490.6 436.9"><path fill="#61dafb" d="M490.6 218.5c0-32.5-40.7-63.3-103.1-82.4 14.4-63.6 8-114.2-20.2-130.4-6.5-3.8-14-5.6-22.3-5.6V0c-27.5 0-63.5 19.6-99.9 53.6C208.7 19.8 172.7.4 145.2.4v.1c-8.4 0-16 1.8-22.6 5.6-28.1 16.2-34.4 66.7-19.9 130.1C40.5 155.4 0 186.1 0 218.5c0 32.5 40.7 63.3 103.1 82.4-14.4 63.6-8 114.2 20.2 130.4 6.5 3.8 14.1 5.6 22.5 5.6 27.5 0 63.5-19.6 99.9-53.6 36.4 33.8 72.4 53.2 99.9 53.2 8.4 0 16-1.8 22.6-5.6 28.1-16.2 34.4-66.7 19.9-130.1 62-19.1 102.5-49.9 102.5-82.3zM344.9 22.3c4.6.1 8.3 1 11.4 2.7 13.6 7.8 19.5 37.5 14.9 75.7-1.1 9.4-2.9 19.3-5.1 29.4-19.6-4.8-41-8.5-63.5-10.9-13.5-18.5-27.5-35.3-41.6-50 32.5-30.3 63.1-46.8 83.9-46.9zM156.7 269.7c4.7 8 9.5 15.8 14.4 23.4-14.2-2.1-27.9-4.7-41-7.9 3.7-12.9 8.3-26.2 13.5-39.5 4.1 8 8.4 16 13.1 24zm-26.9-117.9c13.1-3.1 26.9-5.8 41.2-7.9-4.9 7.7-9.8 15.6-14.4 23.7-4.6 8-8.9 16-13 24-5.4-13.4-10-26.8-13.8-39.8zm25.5 67c6.2-13.4 13.2-26.8 20.7-39.9 7.8-13.5 15.8-26.3 24.1-38.2 14.9-1.3 30-2 45.2-2 15.1 0 30.2.7 45 1.9 8.3 11.9 16.4 24.6 24.2 38 7.6 13.1 14.5 26.4 20.8 39.8-6.3 13.4-13.2 26.8-20.7 39.9-7.8 13.5-15.8 26.3-24.1 38.2-14.9 1.3-30 2-45.2 2-15.1 0-30.2-.7-45-1.9-8.3-11.9-16.4-24.6-24.2-38-7.6-13.1-14.5-26.4-20.8-39.8zm178.6 50.6c4.6-8 8.9-16.1 13-24.1 5.4 13.4 10 26.8 13.8 39.8-13.1 3.2-26.9 5.9-41.2 8 4.9-7.7 9.8-15.6 14.4-23.7zm-.1-102.1c-4.6-8-9.5-15.8-14.4-23.4 14.2 2.1 27.9 4.7 41 7.9-3.7 12.9-8.3 26.2-13.5 39.5-4.1-8-8.4-16-13.1-24zm-61-50.3c-9-.4-18.2-.7-27.5-.7-9.4 0-18.7.2-27.8.7 9-11.7 18.3-22.4 27.5-32 9.3 9.6 18.6 20.3 27.8 32zM133.7 25.4c3-1.8 6.9-2.6 11.5-2.6v-.1c20.7 0 51.4 16.5 84 46.6-14 14.7-28 31.4-41.3 49.9-22.6 2.4-44 6.1-63.6 11-2.3-10-4-19.7-5.2-29-4.7-38.2 1.1-67.9 14.6-75.8zm-25.2 253.9c-9.9-3.1-19.3-6.5-28-10.2-35.4-15.1-58.3-34.9-58.3-50.6s22.9-35.6 58.3-50.6c8.6-3.7 18-7 27.7-10.1 5.7 19.6 13.2 40 22.5 60.9-9.2 20.8-16.6 41.1-22.2 60.6zm37.1 135.4c-4.5-.1-8.3-1-11.3-2.7-13.6-7.8-19.5-37.5-14.9-75.7 1.1-9.4 2.9-19.3 5.1-29.4 19.6 4.8 41 8.5 63.5 10.9 13.5 18.5 27.5 35.3 41.6 50-32.6 30.3-63.2 46.9-84 46.9zm99.9-62.7c-9.3-9.6-18.6-20.3-27.8-32 9 .4 18.2.7 27.5.7 9.4 0 18.7-.2 27.8-.7-9 11.7-18.3 22.4-27.5 32zm111.4 59.6c-3 1.8-6.9 2.6-11.5 2.6-20.7 0-51.4-16.5-84-46.6 14-14.7 28-31.4 41.3-49.9 22.6-2.4 44-6.1 63.6-11 2.3 10.1 4.1 19.8 5.2 29.1 4.7 38.2-1.1 67.9-14.6 75.8zM410 269.1c-8.6 3.7-18 7-27.7 10.1-5.7-19.6-13.2-40-22.5-60.9 9.2-20.8 16.6-41.1 22.2-60.6 9.9 3.1 19.3 6.5 28.1 10.2 35.4 15.1 58.3 34.9 58.3 50.6-.1 15.7-23 35.6-58.4 50.6z" class="st0"></path><circle fill="#61dafb" cx="245.2" cy="218.5" r="45.7" class="st0"></circle></svg>
        </svg>
        </transition>
        <!-- <svg width="14" height="16" aria-hidden="true" class="octicon octicon-star"><path fill="#333" fill-rule="evenodd" d="M14 6l-4.9-.64L7 1 4.9 5.36 0 6l3.6 3.26L2.67 14 7 11.67 11.33 14l-.93-4.74L14 6z"></path></svg> -->
        <transition
          enter-active-class="animated bounceInDown"
        >
        <h1 v-show="winner === 'react' && !start" class="text-blue-light text-xl md:text-5xl font-bold text-center">WINNER</h1>        
        </transition>
      </div>

    </div>
    </div>
  
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'app',
  components: {
  },
  data() {
    return {
      vue : true,
      react : true,
      fighting : false,
      vuestart : 0,
      reactstart : 0,
      winner : '',
      start : false,
      initing : false
    }
  },
  methods : {
    async init() {
      this.initing = true
      this.start = true
      this.winner = ''
      await this.Start();
      if(this.vuestart > this.reactstart)
      {
        this.winner = "vue"
      }
      if(this.vuestart < this.reactstart)
      {
        this.winner = "react"
      }
      if(this.vuestart == this.reactstart)
      {
        this.winner = "draft"
      }
      this.start = false
    },
    async Start() {
      this.fighting = true
      await this.vueAnimate()
      this.fighting = false             
      await this.reactAnimate()
      this.fighting = true       
      await this.vueAnimate()
      this.fighting = false       
      await this.fetch()      
      await this.reactAnimate()      
      this.fighting = true       
      await this.vueAnimate()
      this.fighting = false       
      await this.reactAnimate() 
      this.fighting = false            
      await this.vueAnimate()
      this.fighting = false 
    },
    async vueAnimate() {
      await this.sleep(500);      
      this.vue = false;    
      await this.sleep(500);
      this.vue = true;   
      return;
    },
    async reactAnimate() {
      await this.sleep(500);      
      this.react = false;     
      await this.sleep(500);
      this.react = true;   
      return;
    },
    async fetch() {
      let react = axios.get('https://api.github.com/repos/facebook/react')
          .then(({data}) => {
            this.reactstart = data.stargazers_count
          })
      let vue = axios.get('https://api.github.com/repos/vuejs/vue')
          .then(({data}) => {
            this.vuestart = data.stargazers_count
          })
      return [react,vue];
    },
    sleep(time) {
      return new Promise((resolve) => {
        setTimeout(() => {
        resolve('revoled')
      },time)
      })
    }
  }
}
</script>

<style>

</style>
