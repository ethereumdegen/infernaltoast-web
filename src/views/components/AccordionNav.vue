<template>
  <nav role="navigation" class="w-full m-2 p-2 inline-block">
    <div class="w-full lg:w-auto block lg:inline-block" v-for="item in navConfig.dropdowns" :key="item.title">



      <t-dropdown
        tag-name="nav"
        :classes="{}"
        :fixed-classes="{}"
        class="bg-blue-800"
      >
        <div
          slot="trigger"
          slot-scope="{
            mousedownHandler,
            focusHandler,
            blurHandler,
            keydownHandler,
            isShown
          }"
          class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8"
        >
          <div class="flex justify-between h-16">
            <div class="flex ml-auto">
              <div class="-ml-2 mr-2 flex items-center lg:hidden">
                <!-- Mobile menu button -->
                <div class="flex-shrink-0 flex items-center text-white">
                    <span class="px-2">{{item.title}}</span>
                </div>
                <button
                  class="inline-flex items-center justify-center p-2 rounded-md text-blue-400 hover:text-white hover:bg-blue-700 focus:outline-none focus:bg-blue-700 focus:text-white transition duration-150 ease-in-out"
                  aria-label="Main menu"
                  aria-expanded="false"
                  @mousedown="mousedownHandler"
                  @blur="blurHandler"
                  @keydown="keydownHandler"
                >
                  <svg
                    :class="{ 'hidden': isShown, 'block': !isShown}"
                    class="h-6 w-6"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                  </svg>
                  <svg
                    :class="{ 'hidden': !isShown, 'block': isShown}"
                    class="h-6 w-6"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
                  </svg>
                </button>
              </div>


            </div>
          </div>
        </div>

        <div class="lg:hidden">
          <div class="px-2 pt-2 pb-3 sm:px-3">
            <a
            v-for="row in item.rows"
            :key="row.title"
            :href="row.url"
            target="_blank"
            class="block px-3 py-2 my-2 rounded-md text-base font-medium text-white bg-blue-900 hover:bg-blue-500 focus:outline-none focus:text-white focus:bg-blue-700 transition duration-150 ease-in-out">
            {{row.title}}
          </a>
           </div>
        </div>
      </t-dropdown>







  </div>

</nav>
</template>


<script>
 
export default {
  name: 'AccordionNav',
  props: [],
  data() {
    return {
      navConfig: null
    }
  },
  created(){

    this.navConfig = Config;
  },
  methods: {

  }
}
</script>
