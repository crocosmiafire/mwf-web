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
    <section class="about">
      <svg
        id="poly1"
        width="0"
        height="0"
      >
        <g>
          <defs>
            <clipPath id="poly1clip">
              <polygon
                id="SVGID_1_"
                points="2243.18,1287.08 1977.84,1212.37 1746.08,1353.03 1501.67,1270.49 1269.91,1411.15
                1025.49,1328.62 793.73,1469.28 549.31,1386.74 317.55,1527.4 73.13,1444.86 -180.16,1582.87 -118.66,1399.96 -225.99,1288.57
                -132.68,1152.69 -240.01,1041.29 -146.7,905.41 -254.03,794.01 -160.72,658.13 -268.06,546.73 -174.75,410.84 -256.01,245.34
                9.33,320.05 241.09,179.39 485.51,261.93 717.27,121.27 961.69,203.8 1193.44,63.15 1437.86,145.68 1669.62,5.02 1914.05,87.56
                2167.33,-50.45 2105.83,132.46 2213.16,243.85 2119.85,379.73 2227.19,491.13 2133.88,627.01 2241.21,738.41 2147.9,874.29
                2255.23,985.69 2162.33,1125.97"
              />
            </clipPath>
          </defs>
          <use xlink:href="#SVGID_1_" style="overflow:visible;fill:#FFFFFF;" />
        </g>
      </svg>
      <div class="lmao">
        <div class="about-inner" id="About">
          <h1>The ultimate Melbourne festival</h1>
          <p>
            Experience Melbourne like you've never experienced it before.
            From cafes and restaurants, to the Sidney Myer Music Bowl, everyone is celebrating this
            uniquely wonderful city.
          </p>
        </div>
        <div class="bg-thing" />
      </div>
    </section>
    <!-- <section class="schedule">
      <svg
        id="poly1"
        width="0"
        height="0"
      >
        <g>
          <defs>
            <clipPath id="poly2clip">
              <polygon
                id="SVGID_1_"
                points="2160.8,1348.6 1906.5,1242.2 1659.4,1353.6 1426.8,1242 1179.7,1353.5 947.1,1241.9
                699.9,1353.4 467.4,1241.7 220.2,1353.2 -12.4,1241.6 -280.5,1347.8 -197.3,1173.7 -290.3,1050.1 -181.2,926.6 -274.2,803
                -165,679.4 -258,555.8 -148.9,432.3 -241.9,308.7 -132.8,185.1 -193.4,11 60.9,117.4 308.1,5.9 540.6,117.5 787.8,6 1020.4,117.6
                1267.5,6.2 1500.1,117.8 1747.2,6.3 1979.8,117.9 2248,11.7 2164.7,185.8 2257.7,309.4 2148.6,432.9 2241.6,556.6 2132.5,680.1
                2225.5,803.7 2116.4,927.2 2209.4,1050.9 2100.1,1178.8"
              />
            </clipPath>
          </defs>
          <use xlink:href="#SVGID_1_" style="overflow:visible;fill:#FFFFFF;" />
        </g>
      </svg>
      <div class="schedule-inner">
        <h1>yeah</h1>
      </div>
    </section> -->
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

:root {
  --header: 'Domine', 'Inter', sans-serif;
}

.about {
  position: relative;
  bottom: 225px;
  z-index: 1;

  .lmao {
    width: 100%;
    height: 1100px;
    z-index: -1;
    position: relative;

    background-color: white;

    clip-path: url(#poly1clip);

    display: flex;
    justify-content: space-between;

    .about-inner {
      padding: 360px 0px 0px 125px;
      width: 50%;

      transform: translateY(100px);
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
    }

    p {
      margin-top: 25px;
      font-size: 1.25em;
      padding-right: 20px;
      line-height: 1.5em;
    }
  }
}

.schedule {
  position: relative;
  z-index: 1;

  .schedule-inner {
    width: 100%;
    height: 500px;
    background: black;
    color: white;

    padding: 350px 0px;

    clip-path: url(#poly2clip);

    display: flex;
    justify-content: center;
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
}

.header {
  width: 100%;
  height: 600px;
  color: white;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding-top: 70px;

  transition: 0.5s;

  h1 {
    font-size: 4.5em;
    font-family: var(--header);
    font-weight: normal;
    letter-spacing: -0.03em;
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
