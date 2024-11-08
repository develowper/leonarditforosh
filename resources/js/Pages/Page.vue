<template>
  <Scaffold navbar-theme="light">
    <template v-slot:header>
      <title>{{page.title }}</title>

    </template>
    <div class="    container ">
      <div v-if="!page.id" class="mx-24">


        <div class="flex flex-col items-center p-4 shadow-lg rounded-lg mt-[30vh] w-full justify-center text-danger text-lg
        font-bold ">
          <ApplicationLogo class="w-14 h-14 fill-current text-primary-600"/>
          <div class="py-4"> {{ page.title }}</div>
          <Link :href="route('/')" class="py-4 text-primary-500"> {{ __('main_page') }}</Link>
        </div>
      </div>
      <div v-else class="mt-[15vh]">
        <div v-if="page.content" class="container self-center space-y-2 flex flex-col my-2   px-4 ">
          <div v-html="page.content"></div>
        </div>
      </div>
    </div>
  </Scaffold>
</template>

<script>
import Scaffold from "@/Layouts/Scaffold.vue";
import ApplicationLogo from "@/Components/ApplicationLogo.vue";
import {Head, Link} from '@inertiajs/vue3';
import heroImage from '@/../images/hero.jpg';
import {loadScript} from "vue-plugin-load-script";

export default {
  data() {
    return {
      page: this.$page.props.page
    }
  },
  props: [],
  components: {
    Scaffold,
    Head,
    ApplicationLogo,
    Link,
  },
  // mixins: [Mixin],
  setup(props) {

  }, mounted() {
    this.page = this.$page.props.page;
    // console.log(this.page.title)
  },

}
</script>
<style type="text/css">.turbo-progress-bar {
  position: fixed;
  display: block;
  top: 0;
  left: 0;
  height: 3px;
  background: #32CD32;
  z-index: 9999;
  transition: width 300ms ease-out,
  opacity 150ms 150ms ease-in;
  transform: translate3d(0, 0, 0);
}
</style>

