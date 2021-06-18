<template>
  <div class="container">
    <section class="header">
      <div class="bg">
        <Background v-for="(item, index) in imgs" :key="index" :cur-img="curImg" :pimg="item" />
      </div>
      <div class="header-wrapper">
        <h1>Melbourne<br>Winter Fest</h1>
        <h2>28 June - 4 July</h2>
        <div class="instant-nav-btns">
          <div class="nav-btn">
            <a href="#">Book Tickets</a>
          </div>
          <div class="nav-btn">
            <a href="#">See Schedule</a>
          </div>
        </div>
      </div>
    </section>
    <section>
      <h1>About</h1>
    </section>
  </div>
</template>

<script>
export default {
  data () {
    return {
      imgs: [
        'https://summersoundsfestival.com/content/uploads/sites/2/2021/01/138946391_3877321168999287_6162802858430709152_o-3000x0-c-default.jpg',
        'https://cdn.concreteplayground.com/content/uploads/2017/05/Queen-Victoria-Market-Winter-Night.jpeg',
        'http://theluxtraveller.com/wp-content/uploads/2015/06/Melbourne-at-night.jpg'
      ],
      curImg: 0
    }
  },
  mounted () {
    setInterval(() => {
      if (this.curImg === this.imgs.length - 1) {
        this.curImg = 0
      } else {
        this.curImg++
      }
    }, 5000)
  }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Domine&display=swap');
.container {
}

:root {
  --header: 'Domine', 'Inter', sans-serif;
}

.bg {
  position: absolute;
  width: 100%;
  height: 600px;
  z-index: -1;
  filter: brightness(0.3);
  top: 0;

  div {
    position: absolute;
    width: 100%;
    height: 100%;
    background-position: center;
    background-size: cover;
    transition: 1.5s;
    transition-property: opacity;
  }
}

.header-wrapper {
  padding: 0px 15%;
}

.header {
  width: 100%;
  height: 600px;
  background-position: center !important;
  background-size: cover !important;
  color: white;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding-top: 70px;

  transition: 0.5s;

  h1 {
    font-size: 4.5em;
    font-family: var(--header);
  }

  .instant-nav-btns {
    margin-top: 40px;

    display: flex;
    flex-direction: column;

    .nav-btn {
      margin-bottom: 10px;

      a {
        color: #9ac3ff;
        text-decoration: none;
        font-size: 1.6em;
      }

      a:after {
        content: ' >';
      }
    }
  }
}
</style>
