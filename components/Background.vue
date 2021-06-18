<template>
  <div :style="`background-image: url('${pimg}')`" :class="show" />
</template>

<script>
export default {
  props: ['pimg', 'cur-img'],
  computed: {
    show () {
      if (this.curImg === this.$vnode.key) {
        return 'show'
      } else {
        return 'hide'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.show {
  opacity: 1;
}
.hide {
  opacity: 0;
}
</style>
