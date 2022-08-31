<template>
    <div class="am-header bg-teal-700 text-white md:pb-4 md:pt-4 md:flex md:justify-between md:content-center">
        <div class="headers flex items-center justify-between">
            <span v-if="!expanded" class="font-sans md:text-2xl ml-4">Techbox</span>
            <button v-if="mobile && !expanded" @click="toggle()" class="mr-2 pt-2">
                <span class="material-icons">dashboard</span>
            </button>
        </div>
        <div class="actions min-h-screen md:min-h-full p-4 md:max-h-36 md:p-0 md:flex md:flex-row md:items-center" v-if="!mobile || expanded">
            <button v-if="!mobile">
                <span class="material-icons">search</span>
            </button>

            <button v-if="mobile" @click="toggle()" class="float-right">
                <span class="material-icons">close</span>
            </button>

            <div class="body">
                <div class="body-header">
                    <input v-if="mobile" type="text" name="company-website" id="company-website"
                        class="w-full h-10 p-4 rounded-lg focus:outline-none" placeholder="Search">
                    <nav class="flex flex-col pt-4 items-start md:flex-row">
                        <router-link class="text-2xl font-semibold mb-4 md:text-lg mr-4" to="/tutorial">Tutorial</router-link>
                        <router-link class="text-2xl font-semibold mb-4 md:text-lg mr-4" to="/about">Tips</router-link>
                        <router-link class="text-2xl font-semibold mb-4 md:text-lg mr-4" to="/about">News</router-link>
                        <router-link class="text-2xl font-semibold mb-4 md:text-lg mr-4" to="/about">Technology</router-link>
                    </nav>
                </div>
                <div v-if="mobile" class="body-footer flex items-start flex-col">
                    <span class="text-4xl font-semibold mt-8">Trending</span>
                    <div class="feed mt-4">
                        <div v-for="notice in news" v-bind:key="notice">
                            <div class="max-w-sm mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-2xl mb-4">
                                <div class="flex flex-row items-center">
                                    <div class="md:shrink-0">
                                        <img class="object-cover md:h-full max-h-40 w-38" v-bind:src="notice.image"
                                            alt="Man looking at item at a store">
                                    </div>
                                    <div class="p-8">
                                        <div class="uppercase tracking-wide text-sm text-neutral-600 font-semibold">{{ notice.title }}</div>
                                        <div class="uppercase tracking-wide text-sm text-neutral-400 mt-4 font-semibold">{{ notice.date }}</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>
  
  <script>
  // @ is an alias to /src
  
  
  export default {
      name: 'AmHeader',
      components: {
          //
      },
      data() {
          return {
              mobile: false,
              expanded: false,
              news: [
                  {
                      title: 'Lorem ipsum dolor sit amet',
                      description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
                      image: 'https://picsum.photos/200/300?image=0',
                      date: '12/12/2019'
                  },
                  {
                      title: 'Lorem ipsum dolor sit amet',
                      description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.',
                      image: 'https://picsum.photos/200/300?image=1',
                      date: '12/12/2019'
                  },
              ],
          }
      },
      created() {
          (window.innerWidth < 768) ? this.mobile = true : this.mobile = false;
      },
      methods: {
          toggle() {
              this.expanded = !this.expanded;
          }
      }
  }
  </script>
  