<template>
  <div class="container">
    <section class="header">
      <div class="bg">
        <Background v-for="(item, index) in imgs" :key="index" :cur-img="curImg" :pimg="item" />
      </div>
      <div class="header-wrapper">
        <img class="main-logo" src="@/assets/Logo-var2op2.svg">
        <div class="info-header">
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
      </div>
    </section>
    <section class="about">
      <div class="lmao">
        <div id="About" class="about-inner">
          <h1>The ultimate Melbourne festival</h1>
          <p>
            [PLACEHOLDER TEXT]
            Experience Melbourne like you've never experienced it before.
            From cafes and restaurants, to the Sidney Myer Music Bowl, everyone is celebrating this
            uniquely wonderful city.
          </p>
        </div>
        <div class="bg-thing" />
      </div>
    </section>
    <section class="schedule">
      <div class="schedule-inner">
        <h1>Upcoming Events</h1>
        <div
          ref="cards"
          class="cards-container"
          :style="cursorChange"
          @mousedown="startDrag"
          @mousemove="dragging"
          @mouseup="stopDrag"
          @mouseleave="stopDrag"
        >
          <ScheduleCards v-for="item in events" :key="item.id" :info="item" />
        </div>
      </div>
    </section>
    <Footer />
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
      curImg: 0,
      events: [
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-1'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-2'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-3'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-4'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        }
      ],
      isMouseDown: false
    }
  },
  computed: {
    cursorChange () {
      if (this.isMouseDown) {
        return 'cursor: grabbing'
      } else {
        return ''
      }
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
  },
  methods: {
    startDrag () {
      this.isMouseDown = true
    },
    dragging (evt) {
      if (this.isMouseDown) {
        this.$refs.cards.scrollLeft -= evt.movementX
      }
    },
    stopDrag () {
      this.isMouseDown = false
    }
  }
}
</script>

<style lang="scss">
.about {
  z-index: 1;

  display: flex;
  align-items: center;
  justify-content: flex-end;

  width: 100%;
  max-height: 650px;
  background-color: white;

  transform: skewY(3deg);
  overflow: hidden;

  .lmao {
    width: 100%;
    height: 900px;
    position: relative;

    display: flex;
    justify-content: space-between;
    align-items: center;
    transform: skewY(-3deg);

    overflow: hidden;

    .about-inner {
      padding-left: 125px;
      width: 50%;
      margin-bottom: 50px;
    }

    .bg-thing {
      position: relative;
      z-index: -1;

      height: 100%;
      width: 45%;

      background-image: url('https://www.webjet.com.au/travel/wp-content/uploads/2014/07/Melbourne_at_night.jpg');
      background-size: cover;
      background-position: right;
    }

    h1 {
      font-family: var(--header);
      font-size: 4em;
      letter-spacing: -0.03em;
      font-weight: normal;
      margin-top: 0px;
    }

    p {
      margin-top: 25px;
      font-size: 1.5em;
      padding-right: 20px;
      line-height: 1.45em;
    }
  }
}

#poly1 {
  width: 0;
  height: 0;
}

.schedule {
  z-index: 1;

  width: 100%;

  padding: 100px 0px;

  transform: skewY(3deg);
  background: linear-gradient(#262262, #00A79D);
  color: white;

  .schedule-inner {
    width: 100%;
    height: 600px;

    transform: skewY(-3deg);

    clip-path: url(#poly2clip);

    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    h1 {
      font-size: 4em;
      font-family: var(--header);
      letter-spacing: -0.03em;
      font-weight: normal;
    }

    .cards-container {
      margin-top: 60px;
      padding-bottom: 30px;

      display: flex;

      //align-items: center;
      justify-content: flex-start;

      overflow: hidden;
      overflow-x: auto;

      width: 100%;
      cursor: grab;
    }

    .cards-container::-webkit-scrollbar {
      background: transparent;
      height: 10px;
    }

    .cards-container::-webkit-scrollbar-thumb {
      background: #ffffff8e;
      border-radius: 20px;
    }
  }
}

.bg {
  position: absolute;
  width: 100%;
  height: 740px;
  z-index: -1;
  filter: brightness(0.3);
  top: 0;
  overflow: hidden;

  background-color: black;

  div {
    position: absolute;
    width: 100%;
    height: 100%;
    background-position: center;
    background-size: cover;
    transition: 1.5s;
    transition-property: opacity, transform;
    transform: scale(1.1);
  }
}

.header-wrapper {
  padding: 0px 15%;
  display: flex;
  align-items: center;

  .info-header {
    margin-left: 80px;
    margin-top: 25px;

    h2 {
      font-size: 44px;

      margin: 0;
    }
  }
}

.header {
  width: 100%;
  height: 650px;
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  //text-align: center;
  padding-top: 40px;

  transition: 0.5s;

  h1 {
    font-size: 4.5em;
    font-family: var(--header);
    font-weight: normal;
    letter-spacing: -0.03em;
  }

  .main-logo {
    filter: brightness(10);
    width: 500px;
    height: auto;
  }

  .instant-nav-btns {
    margin-top: 20px;

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
