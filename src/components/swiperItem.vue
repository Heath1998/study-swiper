<template>
  <section class="section" :class="{'section-show': index === curIndex}">
    <div class="container"  >
      <img ref="leftImg" class="left" :class="{'left-show': index === activeIndex}" style="width:256px;" src="https://cdn.cnbj1.fds.api.mi-img.com/privacy-station/pc/static/media/0-4.f95aeceb.png" >
      <div class="right" :class="{ 'right-above': index < nextPosition||  index < curIndex, 'right-follow': index > curIndex || index >nextPosition,  }">
        <div><p class="title" >{{index}}</p>
        <p class="bigTitle">想要更多便利，必须提供充分理由</p>
        <p class="text">当应用获取定位选项。</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    index: {
      type: Number,
      default: -1000
    },
    activeIndex: {
      type: Number,
      default: -1000 
    },
    curIndex: {
      type: Number,
      default: -1000 
    },
    nextPosition: {
      type: Number,
      default: -1000 
    }
  },
  data() {
    return {
      isShow: false
    }
  },
  mounted() {
    this.$refs.leftImg.addEventListener('transitionstart', this.$parent.removeOnMouseWheel);
    this.$refs.leftImg.addEventListener('transitionend', this.$parent.addOnMouseWheel);
  }
}
</script>

<style>
.container {
  position: absolute;
  width: 90%;
  height: 100%;
  margin: 0 auto;
  display: flex;
  /* justify-content: space-between; */
  align-items: center;
}
.section {
  width: 100%;
  position: absolute;
  height: 100vh;
  opacity: 0;
  visibility: hidden;
}
.section-show {
  opacity: 1;
  visibility: inherit;
}
.left {
  opacity: 0;
  transform: scale(0.8, 0.8);
  transition: all 1s;
}
.left-show {
  transform: translate(0px, 0px);
  opacity: 1;
  visibility: inherit;
  transform: scale(1, 1);
}
.right {
  color: #ffffff;
  font-size: 40px;
  margin-left:70px;
  transition: all 1s;
  transform: translate(0px, 0px);
}
.right-show {
    transform: translate(0px, 0px);
}
.right-above {
    transform: translate(0px, -84px);
}
.right-follow {
    transform: translate(0px, 84px);
}
</style>