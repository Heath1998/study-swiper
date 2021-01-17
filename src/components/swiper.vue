<template>
  <div class="all-swiper">
    <swiperItem v-for="(item, i) of arr" :key="i" :index="i" :curIndex="curIndex"  :nextPosition="nextPosition"  :activeIndex = "activeIndex" />
  </div>
</template>

<script>
import swiperItem from './swiperItem';
export default {
  components: {
    swiperItem
  },
  data() {
    return {
      arr: [1,2,3,4,5,6],
      activeIndex: 0,
      nextPosition: 0,
      lockAnimate: false,
      norepeat:false,
      curIndex: 0
    }
  },
  methods: {
    onmousewheel(event) {
      console.log(this.lockAnimate)
      if(this.lockAnimate) return ;
      if(event.wheelDelta > 0) {
        if(this.activeIndex === 0) {
          return ;
        } else {
          this.nextPosition = this.activeIndex - 1;
           this.lockAnimate = true;
        }
      } else {
        if(this.activeIndex === this.arr.length - 1) {
          return ;
        } else {
          this.nextPosition = this.activeIndex + 1;
           this.lockAnimate = true;
        }
      }
      this.activeIndex = -1;
    },
    removeOnMouseWheel() {
      this.lockAnimate = true;
      this.norepeat = false;
      console.log('remove');
    },
    addOnMouseWheel() {
      if (this.activeIndex === -1) {
        this.activeIndex = this.nextPosition;
        this.curIndex = this.nextPosition;
        this.norepeat = true;
        return ;
      }
      if (this.activeIndex !== -1 && !this.norepeat) {
        // document.addEventListener('mousewheel', this.onmousewheel);
        this.lockAnimate = false;
        this.norepeat = true;
        console.log('add' + this.lockAnimate);
      }
    }
  },
  mounted() {
    document.addEventListener('mousewheel', this.onmousewheel);
  }
}
</script>

<style>

</style>