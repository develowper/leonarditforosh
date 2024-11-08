<template>
  <div @click="toggleWidget" :class="toggle" id="animate-from-outside"
       class="z-[1065]    fixed hover:cursor-pointer  bottom-[20%] h-fit  bg-primary-600 text-white  shadow-xl p-2 px-4 rounded-e-lg">
    <div class="flex items-center">
      <div>
        <div>{{ __('counseling') }}</div>
        <div> {{ $page.props.socials.phone }}</div>
      </div>
      <span class="  border-s border-1 h-10 border-red   mx-2">  </span>

      <PhoneIcon class="w-10 h-10 border border-2 rounded-full p-1   text-white"/>
    </div>
  </div>
</template>

<script>
import {
  PhoneIcon,
} from "@heroicons/vue/24/outline";

export default {
  name: "FloatingWidget",
  props: ['minimize'],
  components: {
    PhoneIcon,
  },
  data() {
    return {
      toggle: 'close',
    }
  },
  mounted() {


  },
  methods: {
    toggleWidget() {
      if (this.toggle === 'open')
        this.toggle = 'close';
      else
        this.toggle = 'open';
    }
  }
}
</script>

<style scoped lang="scss">
#animate-from-outside {


  &.open {
    animation: opening 1s ease;
  }

  //
  &.close {
    animation: closing 1s ease forwards;
  }


}

@keyframes opening {
  from {
    transform: translate(-140px, 0);
  }
  to {
    transform: translate(0, 0);
  }
}

@keyframes closing {
  from {
    transform: translate(0px, 0);
  }
  to {
    transform: translate(-140px, 0px);
  }
}
</style>