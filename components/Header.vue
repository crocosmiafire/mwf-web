<template>
  <div class="header-root" :class="scrollBG">
    <section class="left">
      <h3>Melbourne Winter Fest</h3>
    </section>
    <section>
      <div class="links">
        <a href="#About">About</a>
        <a href="#Book">Book</a>
        <a href="#Schedule">Schedule</a>
        <a href="#Maps">Maps</a>
        <a href="#FAQ">FAQ</a>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isScroll: false
    }
  },
  computed: {
    scrollBG () {
      if (this.isScroll) {
        return 'scroll'
      } else {
        return ''
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', () => {
      if (window.scrollY > 100) {
        this.isScroll = true
      } else {
        this.isScroll = false
      }
    })
  }
}
</script>

<style lang="scss" scoped>
.header-root {
  width: 100%;
  height: 65px;
  background: transparent;
  padding: 20px 30px;

  position: fixed;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
  z-index: 2;

  transition: 0.25s;
  transition-property: color, background;
}

.header-root.scroll {
  background: white;
  color: black;

  box-shadow: 0px 1px 5px rgba(0,0,0,.2);

  a {
    color: black;
  }
}

.links {
  a {
    margin: 0px 10px;
    text-decoration: none;
    color: white;
  }
}
</style>
