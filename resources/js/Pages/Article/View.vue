<template>
  <Scaffold navbar-theme="light">
    <template v-slot:header>
      <title v-if="data">{{ data.title }}</title>
      <meta v-if="data" name="description" :content=" data.summary ">

    </template>
    <section class="flex justify-center pt-24">
      <div
          class="w-full   rounded-lg overflow-x-hidden  max-w-4xl  xs:mx-2 md:mx-4    blur-xs opacity-75 bg-white  backdrop-filter">
        <div v-if="$page.props.error_message" class="text-center flex flex-col font-bold p-4 text-danger  text-lg">
          <div class="text-gray-900">{{ $page.props.error_message }}</div>
          <Link :href="$page.props.error_link" class="my-4">{{ __('return') }}</Link>
        </div>
        <!--      main section-->

        <div v-else-if="data" class=" flex flex-col ">
          <div
              class="px-4 py-4 text-white   bg-[radial-gradient(ellipse_at_top_right,_var(--tw-gradient-stops))] from-emerald-500 to-lime-600">
            {{ data.title }}
          </div>
          <div v-if="data" class="      flex flex-col   ">

            <div class="grid grid-cols-1   items-center    h-64 w-full   relative">
              <div class="h-[inherit]">
                <Image :src="route('storage.articles')+`/${data.id}.jpg`"
                       classes="object-contain rounded-lg    h-[inherit]     w-full"/>
                <div
                    class="text-sm    absolute  top-0 start-0 w-full h-full  bg-primary-500 opacity-10  backdrop-blur">
                </div>
              </div>

            </div>

            <div v-if="data.owner" class="text-sm bg-gray-200 p-4 rounded flex flex-wrap">
              <span class="text-gray-500 ">{{ __('author') }}: </span>
              <span>{{ data.author }}</span>
              <span class="  border-s border-1   border-gray-400   mx-2">  </span>
              <span class="text-gray-500  ">{{ __('phone') }}: </span>
              <span>{{ data.owner.phone }}</span>
              <span class="  border-s border-1   border-gray-400   mx-2">  </span>
              <span class="text-gray-500  ">{{ __('view') }}: </span>
              <span>{{ data.view }}</span>
              <span class="  border-s border-1   border-gray-400   mx-2">  </span>
              <div class="flex justify-center items-center   ">

                <a v-if="$page.props.socials.whatsapp" target="_blank" :href="$page.props.socials.whatsapp"
                   class="mx-2 text-gray-700 dark:text-neutral-200">
                  <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-5 w-5  "
                      fill="currentColor"
                      viewBox="0 0 24 24">
                    <path
                        d="M.057 24l1.687-6.163c-1.041-1.804-1.588-3.849-1.587-5.946.003-6.556 5.338-11.891 11.893-11.891 3.181.001 6.167 1.24 8.413 3.488 2.245 2.248 3.481 5.236 3.48 8.414-.003 6.557-5.338 11.892-11.893 11.892-1.99-.001-3.951-.5-5.688-1.448l-6.305 1.654zm6.597-3.807c1.676.995 3.276 1.591 5.392 1.592 5.448 0 9.886-4.434 9.889-9.885.002-5.462-4.415-9.89-9.881-9.892-5.452 0-9.887 4.434-9.889 9.884-.001 2.225.651 3.891 1.746 5.634l-.999 3.648 3.742-.981zm11.387-5.464c-.074-.124-.272-.198-.57-.347-.297-.149-1.758-.868-2.031-.967-.272-.099-.47-.149-.669.149-.198.297-.768.967-.941 1.165-.173.198-.347.223-.644.074-.297-.149-1.255-.462-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.297-.347.446-.521.151-.172.2-.296.3-.495.099-.198.05-.372-.025-.521-.075-.148-.669-1.611-.916-2.206-.242-.579-.487-.501-.669-.51l-.57-.01c-.198 0-.52.074-.792.372s-1.04 1.016-1.04 2.479 1.065 2.876 1.213 3.074c.149.198 2.095 3.2 5.076 4.487.709.306 1.263.489 1.694.626.712.226 1.36.194 1.872.118.571-.085 1.758-.719 2.006-1.413.248-.695.248-1.29.173-1.414z"/>
                  </svg>
                </a>

                <a v-if="$page.props.socials.telegram" target="_blank" :href="$page.props.socials.telegram"
                   class="mx-2 text-gray-700 dark:text-neutral-200">
                  <svg
                      class="h-6 w-6"
                      fill="currentColor"
                      viewbox="0 0 24 24"
                      version="1.1"
                      xmlns="http://www.w3.org/2000/svg"
                      xmlns:xlink="http://www.w3.org/1999/xlink"
                      xml:space="preserve"
                      xmlns:serif="http://www.serif.com/"
                      style="fill-rule:evenodd;clip-rule:evenodd;stroke-linejoin:round;stroke-miterlimit:1.41421;">
          <path
              id="telegram-1"
              d="M18.384,22.779c0.322,0.228 0.737,0.285 1.107,0.145c0.37,-0.141 0.642,-0.457 0.724,-0.84c0.869,-4.084 2.977,-14.421 3.768,-18.136c0.06,-0.28 -0.04,-0.571 -0.26,-0.758c-0.22,-0.187 -0.525,-0.241 -0.797,-0.14c-4.193,1.552 -17.106,6.397 -22.384,8.35c-0.335,0.124 -0.553,0.446 -0.542,0.799c0.012,0.354 0.25,0.661 0.593,0.764c2.367,0.708 5.474,1.693 5.474,1.693c0,0 1.452,4.385 2.209,6.615c0.095,0.28 0.314,0.5 0.603,0.576c0.288,0.075 0.596,-0.004 0.811,-0.207c1.216,-1.148 3.096,-2.923 3.096,-2.923c0,0 3.572,2.619 5.598,4.062Zm-11.01,-8.677l1.679,5.538l0.373,-3.507c0,0 6.487,-5.851 10.185,-9.186c0.108,-0.098 0.123,-0.262 0.033,-0.377c-0.089,-0.115 -0.253,-0.142 -0.376,-0.064c-4.286,2.737 -11.894,7.596 -11.894,7.596Z">

          </path>
        </svg>
                </a>

              </div>

            </div>

            <div class="space-y-2 flex flex-col my-2   px-4">
              <p class="text-sm my-2">
                <span class="text-gray-500 ">{{ __('tags') }}: </span>
                <span>{{ data.tags }}</span>
              </p>
            </div>
            <div class="border-b my-2 border-primary-200"></div>
            <div v-if="data.content" class="container self-center space-y-2 flex flex-col my-2   px-4 ">
              <div v-html="data.content"></div>
            </div>

          </div>


        </div>
      </div>
    </section>
    <section v-if="false">
      <div class=" w-full px-3 my-8   flex  items-center justify-center">
        <PrimaryButton @click="$inertia.visit(route(($page.props.auth.user?'panel.article.create':'login')  ))"
                       class="mx-2 py-2  px-6  ">
          {{ __('register_article') }}
        </PrimaryButton>
      </div>
    </section>

  </Scaffold>
</template>

<script>

import Scaffold from "@/Layouts/Scaffold.vue";
import SecondaryButton from "@/Components/SecondaryButton.vue";
import PrimaryButton from "@/Components/PrimaryButton.vue";
import {Head, Link} from "@inertiajs/vue3";
import LoadingIcon from "@/Components/LoadingIcon.vue";
import Image from "@/Components/Image.vue";
import Article from "@/Components/Article.vue";
import {} from "@heroicons/vue/24/outline";
import {EyeIcon, CurrencyDollarIcon, UserIcon} from "@heroicons/vue/24/solid";

export default {
  data() {
    return {
      html: null,
      timer: 0,
      timerPercent: 0,
      auto_view: this.$page.props.auto_view,
      error: null,
      data: null,
      available_sites: 0,
      hiddenProp: null,
      intervalId: null,
      sites: [],
      loading: false,
      params: {
        page: 0,
        search: null,
        order_by: null,
        dir: null,
      }
    }
  },
  components: {
    Scaffold,
    Image,
    Link,
    EyeIcon,
    CurrencyDollarIcon,
    LoadingIcon,
    PrimaryButton,
    SecondaryButton,
    UserIcon,
    Article,
  },
  created() {
    // this.isLoading(true);

  },
  mounted() {

    this.data = this.$page.props.data;

    this.increaseView(this.data.id);
  },
  methods: {
    increaseView(id) {
      window.axios.post(route('article.view'), {id: id},);


    },
  },

}

</script>