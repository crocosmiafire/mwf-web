<template>
  <div class="container">
    <section class="header">
      <div class="bg">
        <Background v-for="(item, index) in imgs" :key="index" :cur-img="curImg" :pimg="item" />
      </div>
      <div class="header-wrapper">
        <img class="main-logo" src="@/assets/Logo-var2op3.svg">
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
    <section id="Schedule" class="schedule">
      <div class="schedule-inner">
        <h1>Upcoming Events</h1>
        <div class="events-wrapper">
          <div class="fade left">
            <i class="material-icons">arrow_back_ios</i>
          </div>
          <div
            ref="cards"
            class="cards-container"
            :style="cursorChange"
            @mousedown="startDrag"
            @mousemove="dragging"
            @pointerup="stopDrag"
            @mouseleave="stopDrag"
          >
            <ScheduleCards v-for="item in events" :key="item.id" :info="item" />
          </div>
          <div class="fade right">
            <i class="material-icons">arrow_forward_ios</i>
          </div>
        </div>
      </div>
    </section>
    <section id="About" class="about">
      <div class="lmao">
        <div class="about-wrap">
          <div class="about-inner">
            <h1>The largest festival ever held in Melbourne</h1>
            <p>
              [PLACEHOLDER TEXT]
              Experience Melbourne like you've never experienced it before.
              From cafes and restaurants, to the Sidney Myer Music Bowl, everyone is celebrating this
              uniquely wonderful city.
            </p>
          </div>
        </div>
        <div class="bg-thing-wrap">
          <div class="bg-thing" />
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
        '/imgs/hosier-lane-front.jpg',
        '/imgs/flinders-front.jpg'
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
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
        },
        {
          title: 'An event title',
          time: '09:00',
          location: 'Somewhere',
          id: 'evt-5'
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
    stopDrag (evt) {
      let toStopAt = 0
      // 465px width
      for (let i = 0; i < this.events.length; i++) {
        const cardEl = document.querySelector('.cards-container').children[i].getBoundingClientRect()
        if (cardEl.x < -440) {
          continue
        } else if (cardEl.x >= -192) {
          toStopAt = i + 1
          break
        } else if (cardEl.x < -193) {
          toStopAt = i + 2
          break
        }
      }
      this.isMouseDown = false
      this.$refs.cards.scrollTo({
        left: 465 * toStopAt - 465,
        behavior: 'smooth'
      })
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

  transform: skewY(0deg);
  overflow: hidden;

  .lmao {
    width: 100%;
    height: 900px;
    position: relative;

    display: flex;
    justify-content: space-between;
    align-items: center;
    //transform: skewY(-3deg);

    overflow: hidden;

    .about-wrap {
      align-self: center;
      justify-self: center;
      transform: skewX(-15deg);
    }
    .about-inner {
      grid-area: about;
      margin-bottom: 50px;
      transform: skewX(15deg);
      padding: 0px 10px 0px 70px;
    }
    .bg-thing-wrap {
      grid-area: bgthing;
      height: 100%;
      width: 100%;
      position: relative;
      z-index: -1;
      align-self: flex-end;
      justify-self: end;
      transform: skewX(-15deg) translateX(100px);
      overflow: hidden;
    }
    .bg-thing {
      height: 120%;
      width: 120%;
      transform: skewX(15deg) translateX(-100px);
      background-image: url('https://www.webjet.com.au/travel/wp-content/uploads/2014/07/Melbourne_at_night.jpg');
      background-size: cover;
      background-position: right;
    }
    h1 {
      font-family: var(--header);
      font-size: 3.6em;
      letter-spacing: -0.03em;
      font-weight: normal;
      margin-top: 0px;
    }
    p {
      margin-top: 25px;
      font-size: 1.4em;
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

  transform: skewY(0deg);
  background: linear-gradient(#262262, #00A79D);
  color: white;

  .schedule-inner {
    width: 100%;
    height: 410px;

    //transform: skewY(-3deg);

    clip-path: url(#poly2clip);

    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    h1 {
      font-size: 3.5em;
      font-family: var(--header);
      letter-spacing: -0.03em;
      font-weight: normal;
    }

    .events-wrapper {
      display: flex;
      width: 100%;
      height: 100%;
      align-items: center;
      justify-content: center;

      .fade {
        width: 100px;
        height: 680px;

        position: absolute;
        pointer-events: none;

        display: flex;
        align-items: center;

        i {
          font-size: 3.5em;
          text-shadow: 0px 2px 8px rgb(0,0,0);
          pointer-events: all;
          cursor: pointer;

          /* padding: 30px 20px;
          background: rgba(0,0,0,.25);
          border-radius: 20px; */
        }

        i:hover {
          opacity: 0.75;
        }
      }

      .fade.left {
        left: 0;
        justify-content: flex-end;
      }

      .fade.right {
        right: 0;
        justify-content: flex-start;
      }

      .cards-container {
        padding: 0px 20px;
        margin-top: 60px;
        padding-bottom: 40px;

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
        display: none;
      }

      .cards-container::-webkit-scrollbar-thumb {
        background: #ffffff8e;
        border-radius: 20px;
      }

      .cards-container:hover::-webkit-scrollbar {
        display: block;
      }

      .cards-container:hover {
        padding-bottom: 30px;
      }
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
      font-size: 52px;

      margin: 0;
    }
  }
}

.header {
  width: 100%;
  height: 550px;
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
        color: #70c6ff;
        text-decoration: none;
        font-size: 1.6em;
      }

      a:hover {
        text-decoration: underline;
      }

      a:after {
        content: ' >';
      }
    }
  }
}
</style>
