<template>
  <nav role="navigation" class="w-full m-2 p-2 inline-block">
    <div class="w-full lg:w-auto block lg:inline-block" v-for="item in navConfig.dropdowns" :key="item.title">
    <t-dropdown  class="w-full" >
      <div
        slot="trigger"
        slot-scope="{
          mousedownHandler,
          focusHandler,
          blurHandler,
          keydownHandler,
          isShown
        }"
      >
        <button
          class="flex text-md  p-2 m-1 mx-2 text-gray-100 items-center pr-3 bg-transparent focus:outline-none focus:shadow-solid transition duration-150 ease-in-out border-2 border-gray-200"
          :class="{ 'border-gray-300 bg-gray-500 text-white ': isShown }"
          aria-label="User menu"
          aria-haspopup="true"
          @mousedown="mousedownHandler"
          @focus="focusHandler"
          @blur="blurHandler"
          @keydown="keydownHandler"
        >

            <span class="px-2">{{item.title}}</span> <i class="fas fa-caret-down "></i>
        </button>
      </div>

      <div slot-scope="{ hide, blurHandler }" class="origin-top-right absolute right-0 w-56 shadow-lg text-md bg-gray-900 text-white">

        <a
        :href="row.url"
        v-for="row in item.rows"
        target="_blank"
        :key="row.title"
        class="block w-full px-4 py-2   leading-5   hover:bg-gray-600 focus:outline-none focus:bg-gray-100 transition duration-150 ease-in-out"
        role="menuitem"
        @blur="blurHandler"
        >
          {{ row.title }}
        </a>


      </div>
    </t-dropdown>
  </div>

</nav>
</template>


<script>
 
export default {
  name: 'UpperNav',
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
