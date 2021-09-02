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
    <section id="Maps" class="map">
      <div class="map-inner">
        <h1>Event Map</h1>
        <LeafletMap />
      </div>
    </section>
    <section id="About" class="about">
      <div class="lmao">
        <div class="about-wrap">
          <div class="about-inner">
            <h1>The largest festival ever held in Melbourne</h1>
            <p>
              Experience Melbourne like you've never experienced it before.
              From Melbourne Zoo, to the Sidney Myer Music Bowl, everyone is celebrating this
              uniquely wonderful city.
            </p>
          </div>
        </div>
        <div class="bg-thing-wrap">
          <div class="bg-thing" style="background-image: url('/imgs/flinders-front.jpg')" />
        </div>
      </div>
    </section>
    <section class="about a2">
      <div class="lmao">
        <div class="about-wrap">
          <div class="about-inner">
            <h1>Experience a unique Melbourne</h1>
            <p>
              Enjoy a wide range of activities and events, like the Royal Botanic Garden's photography workshop,
              to the Melbourne Winter Festival live performance in the Sidney Myer Music Bowl!
            </p>
          </div>
        </div>
        <div class="bg-thing-wrap">
          <div class="bg-thing" style="background-image: url('/imgs/laneway.jpg')" />
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
        'imgs/hosier-lane-front.jpg',
        'imgs/colour.jpg',
        'imgs/arcade.jpg',
        'imgs/musicbowl.jpg'
      ],
      curImg: 0,
      events: [
        {
          title: 'Photography Workshop',
          time: '09:00',
          location: 'Royal Botanic Gardens',
          id: 'evt-1'
        },
        {
          title: 'Australian Animals',
          time: '12:00',
          location: 'Melbourne Zoo',
          id: 'evt-2'
        },
        {
          title: 'History of Melbourne',
          time: '13:30',
          location: 'National Gallery of Victoria',
          id: 'evt-3'
        },
        {
          title: 'Free MCG Tour',
          time: '14:45',
          location: 'Melbourne Cricket Ground',
          id: 'evt-4'
        },
        {
          title: 'Twilight Market',
          time: '16:30',
          location: 'Queen Victoria Market',
          id: 'evt-5'
        },
        {
          title: 'MWF Live Performance',
          time: '20:00',
          location: 'Sidney Myer Music Bowl',
          id: 'evt-6'
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
  background-color: black;
  color: white;

  transform: skewY(0deg);
  overflow: hidden;

  .lmao {
    width: 100%;
    height: 900px;
    position: relative;

    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-areas: 'about bgthing';
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
      width: 100%;
      height: 100%;
      transform: skew(-15deg) translate(87px);
      overflow: hidden;
    }
    .bg-thing {
      height: 120%;
      width: 120%;
      transform: skewX(15deg) translate(-87px);
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

.about::after {
  content: '';
  position: absolute;
  height: 6px;
  background: linear-gradient(to left, #E000FF 25%, #FFFF00 25% 50%, #00D4FF 50% 75%, white 75%);
  right: 0;
  left: 0;
  top: 0;
}

.map::after {
  content: '';
  position: absolute;
  height: 6px;
  background: linear-gradient(to right, #E000FF 25%, #FFFF00 25% 50%, #00D4FF 50% 75%, white 75%);
  right: 0;
  left: 0;
  top: 0;
}

.about.a2::after {
  background: linear-gradient(to right, #E000FF 25%, #FFFF00 25% 50%, #00D4FF 50% 75%, white 75%);
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
  background-color: black;
  background-image: url(@/assets/background.svg);
  background-size: cover;
  background-position: center;
  color: white;

  .schedule-inner {
    width: 100%;
    height: 350px;

    //transform: skewY(-3deg);

    clip-path: url(#poly2clip);

    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    h1 {
      font-size: 3.5em;
      font-family: var(--header);
      letter-spacing: -0.04em;
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
  filter: brightness(0.5);
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
  //text-shadow: 0px 1px 10px rgba(0,0,0,0.9);

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

.map {
  height: 800px;
  width: 100%;
  transform: skewY(0deg);

  .map-inner {
    display: grid;
    grid-template-rows: 200px 1fr;
    color: white;
    height: 100%;
    width: 100%;

    h1 {
      font-size: 3.5em;
      font-family: var(--header);
      letter-spacing: -0.04em;
      font-weight: normal;
      align-self: center;
      justify-self: center;
    }
  }
}

/*
* wahoo mobile stuff
*/

@media (min-width: 1051px) {
  .about.a2 {
    .lmao {
      grid-template-areas: 'bgthing about';

      p {
        padding-right: 0px;
        padding-left: 20px;
      }

      .bg-thing-wrap {
        transform: skew(-15deg) translate(-87px);
      }

      .bg-thing {
        transform: skew(15deg) translate(87px);
      }

      .about-inner {
        text-align: right;
        padding: 0px 70px 0px 10px;
      }
    }
  }
}

@media (max-width: 1250px) {
  .header-wrapper {
    padding: 0 5%;
  }
}

@media (max-width: 1050px) {
  .header-wrapper {
    flex-direction: column;

    .main-logo {
      width: 300px;
    }

    .info-header {
      margin-left: 0px;
      margin-top: 40px;
      text-align: center;

      h2 {
        font-size: 2.35em;
      }
    }
  }

  .schedule {
    .schedule-inner {
      h1 {
        font-size: 2.6em;
        text-align: center;
      }
    }
  }

  .about {
    max-height: 800px;

    .lmao {
      grid-template-columns: none;
      grid-template-rows: 2fr 1fr;
      grid-template-areas:
      'about'
      'bgthing';

      .about-wrap {
        transform: skewX(0deg) skewY(-3deg);

        .about-inner {
          transform: skewX(0deg) skewY(3deg);
          margin-bottom: 30px;
          text-align: center;
          padding: 0px 30px;

          h1 {
            font-size: 2.5em;
          }

          p {
            padding-right: 0px;
            font-size: 1.1em;
          }
        }
      }

      .bg-thing-wrap {
        transform: skew(0deg) skewY(-3deg) translate(0px) translateY(-20px);
        height: 135%;

        .bg-thing {
          transform: skewX(0deg) skewY(3deg) translateY(-20px);
        }
      }
    }
  }
}
</style>
