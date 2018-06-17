<template>
  <div id="app">
    <div class="flex">
      <div v-show="loading" class="flex justify-center h-screen items-center w-full">
        <div class="font-sans text-5xl font-black">
          <span class="text-green-light">Loa</span><span class="text-blue-light">ding ...</span>
        </div>
      </div>
      <div v-show="!loading" class="w-1/2 border-r-4 border-green-light flex justify-center h-auto bg-green-light">
        <div class="flex flex-wrap pl-2 pr-1 w-full z-20 h-full">
          <a v-for="vue in vuejs" :href="vue.html_url" target="_blank" class="-mr-2">
            <img class="h-8 w-8 rounded-full border-4 hover:border-green border-white shadow bg-green-light" :src="vue.avatar_url" alt="">
          </a>
        </div>
        <div class="fixed flex justify-center items-center mt-8 z-50">
          <a href="https://github.com/vuejs/vue" target="__blank" class="no-underline py-2 px-6 flex flex-col hover:bg-green-light items-center border-4 border-green-dark bg-white text-grey-darker shadow">
            <span class="text-sm flex items-center font-sans">
              <svg class="h-6 w-6" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 261.8 226.7">
                <path d="M161.15-.011l-30.267 52.4-30.266-52.4H-.05l130.933 226.666L261.817-.01H161.15z" fill="#4dba87"></path>
                <path d="M161.15-.011l-30.267 52.4-30.266-52.4H52.35l78.533 136 78.534-136H161.15z" fill="#435466"></path>
              </svg>
              Support VueJs
            </span>
            <span class="flex items-center text-lg">
              <svg class="fill-current text-grey-darker h-4 w-4 mr-1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M10 15l-5.878 3.09 1.123-6.545L.489 6.91l6.572-.955L10 0l2.939 5.955 6.572.955-4.756 4.635 1.123 6.545z"
                />
              </svg>
              {{vuestart }}
            </span>
          </a>
        </div>
      </div>
      <div v-show="!loading" class="w-1/2 h-auto border-l-4 border-blue-light flex justify-center bg-blue-light">
        <div class="flex flex-wrap pl-2 pr-1 justify-start w-full z-30">
          <a v-for="reacter in reacters" :href="reacter.html_url" target="_blank" class="-mr-2">
            <img class="h-8 w-8 rounded-full border-4 hover:border-blue border-white shadow bg-blue-light" :src="reacter.avatar_url"
              alt="">
          </a>
        </div>
        <div class="fixed flex justify-center items-center mt-8 z-50">
          <a href="https://github.com/facebook/react" class="no-underline py-2 px-6 flex flex-col hover:bg-blue-light items-center border-4 border-blue-dark bg-white text-grey-darker shadow">
            <span class="text-sm flex items-center font-sans">
              <svg class="h-6 w-6" id="Layer_2_1_" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 490.6 436.9"><path fill="#61dafb" d="M490.6 218.5c0-32.5-40.7-63.3-103.1-82.4 14.4-63.6 8-114.2-20.2-130.4-6.5-3.8-14-5.6-22.3-5.6V0c-27.5 0-63.5 19.6-99.9 53.6C208.7 19.8 172.7.4 145.2.4v.1c-8.4 0-16 1.8-22.6 5.6-28.1 16.2-34.4 66.7-19.9 130.1C40.5 155.4 0 186.1 0 218.5c0 32.5 40.7 63.3 103.1 82.4-14.4 63.6-8 114.2 20.2 130.4 6.5 3.8 14.1 5.6 22.5 5.6 27.5 0 63.5-19.6 99.9-53.6 36.4 33.8 72.4 53.2 99.9 53.2 8.4 0 16-1.8 22.6-5.6 28.1-16.2 34.4-66.7 19.9-130.1 62-19.1 102.5-49.9 102.5-82.3zM344.9 22.3c4.6.1 8.3 1 11.4 2.7 13.6 7.8 19.5 37.5 14.9 75.7-1.1 9.4-2.9 19.3-5.1 29.4-19.6-4.8-41-8.5-63.5-10.9-13.5-18.5-27.5-35.3-41.6-50 32.5-30.3 63.1-46.8 83.9-46.9zM156.7 269.7c4.7 8 9.5 15.8 14.4 23.4-14.2-2.1-27.9-4.7-41-7.9 3.7-12.9 8.3-26.2 13.5-39.5 4.1 8 8.4 16 13.1 24zm-26.9-117.9c13.1-3.1 26.9-5.8 41.2-7.9-4.9 7.7-9.8 15.6-14.4 23.7-4.6 8-8.9 16-13 24-5.4-13.4-10-26.8-13.8-39.8zm25.5 67c6.2-13.4 13.2-26.8 20.7-39.9 7.8-13.5 15.8-26.3 24.1-38.2 14.9-1.3 30-2 45.2-2 15.1 0 30.2.7 45 1.9 8.3 11.9 16.4 24.6 24.2 38 7.6 13.1 14.5 26.4 20.8 39.8-6.3 13.4-13.2 26.8-20.7 39.9-7.8 13.5-15.8 26.3-24.1 38.2-14.9 1.3-30 2-45.2 2-15.1 0-30.2-.7-45-1.9-8.3-11.9-16.4-24.6-24.2-38-7.6-13.1-14.5-26.4-20.8-39.8zm178.6 50.6c4.6-8 8.9-16.1 13-24.1 5.4 13.4 10 26.8 13.8 39.8-13.1 3.2-26.9 5.9-41.2 8 4.9-7.7 9.8-15.6 14.4-23.7zm-.1-102.1c-4.6-8-9.5-15.8-14.4-23.4 14.2 2.1 27.9 4.7 41 7.9-3.7 12.9-8.3 26.2-13.5 39.5-4.1-8-8.4-16-13.1-24zm-61-50.3c-9-.4-18.2-.7-27.5-.7-9.4 0-18.7.2-27.8.7 9-11.7 18.3-22.4 27.5-32 9.3 9.6 18.6 20.3 27.8 32zM133.7 25.4c3-1.8 6.9-2.6 11.5-2.6v-.1c20.7 0 51.4 16.5 84 46.6-14 14.7-28 31.4-41.3 49.9-22.6 2.4-44 6.1-63.6 11-2.3-10-4-19.7-5.2-29-4.7-38.2 1.1-67.9 14.6-75.8zm-25.2 253.9c-9.9-3.1-19.3-6.5-28-10.2-35.4-15.1-58.3-34.9-58.3-50.6s22.9-35.6 58.3-50.6c8.6-3.7 18-7 27.7-10.1 5.7 19.6 13.2 40 22.5 60.9-9.2 20.8-16.6 41.1-22.2 60.6zm37.1 135.4c-4.5-.1-8.3-1-11.3-2.7-13.6-7.8-19.5-37.5-14.9-75.7 1.1-9.4 2.9-19.3 5.1-29.4 19.6 4.8 41 8.5 63.5 10.9 13.5 18.5 27.5 35.3 41.6 50-32.6 30.3-63.2 46.9-84 46.9zm99.9-62.7c-9.3-9.6-18.6-20.3-27.8-32 9 .4 18.2.7 27.5.7 9.4 0 18.7-.2 27.8-.7-9 11.7-18.3 22.4-27.5 32zm111.4 59.6c-3 1.8-6.9 2.6-11.5 2.6-20.7 0-51.4-16.5-84-46.6 14-14.7 28-31.4 41.3-49.9 22.6-2.4 44-6.1 63.6-11 2.3 10.1 4.1 19.8 5.2 29.1 4.7 38.2-1.1 67.9-14.6 75.8zM410 269.1c-8.6 3.7-18 7-27.7 10.1-5.7-19.6-13.2-40-22.5-60.9 9.2-20.8 16.6-41.1 22.2-60.6 9.9 3.1 19.3 6.5 28.1 10.2 35.4 15.1 58.3 34.9 58.3 50.6-.1 15.7-23 35.6-58.4 50.6z" class="st0"></path><circle fill="#61dafb" cx="245.2" cy="218.5" r="45.7" class="st0"></circle></svg>
              Support ReactJs
            </span>
            <span class="flex items-center text-lg">
              <svg class="fill-current text-grey-darker h-4 w-4 mr-1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M10 15l-5.878 3.09 1.123-6.545L.489 6.91l6.572-.955L10 0l2.939 5.955 6.572.955-4.756 4.635 1.123 6.545z"
                />
              </svg>
              {{ reactstart }}
            </span>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
    name: 'app',
    components: {},
    data() {
      return {
        reacters: [],
        vuejs: [],
        page: 1,
        loading : true,
        reactstart : '',
        vuestart : ''
      }
    },
    async mounted() {
      await this.starts()
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.page += 1;
      await this.fetch();
      this.loading = false

    },
    methods: {
      async starts() {
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
      async fetch() {
        await axios.get('https://api.github.com/repos/facebook/react/stargazers?page=' + this.page)
          .then(({
            data
          }) => {
            this.reacters.push(...data);
            return data;
          })
        await axios.get('https://api.github.com/repos/vuejs/vue/stargazers?page=' + this.page)
          .then(({
            data
          }) => {
            this.vuejs.push(...data);
            return data;
          })
      }
    }
  }
</script>

<style>
</style>