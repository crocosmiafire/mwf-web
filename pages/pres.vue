<template>
  <div class="pres-root">
    <img src="imgs/pres.png">
    <a href="/mwf-web">
      <div class="button">
        <span>Enter Website</span>
      </div>
    </a>
  </div>
</template>

<script>
export default {
  layout: 'pres'
}
</script>

<style lang="scss" scoped>
.pres-root {
  display: grid;
  grid-template-rows: 4fr 1fr;
  justify-items: center;
  align-items: center;
  color: white;

  img {
    width: 1280px;
    height: auto;
  }

  a {
    text-decoration: none;
  }

  .button {
    padding: 15px 20px;
    border: solid 6px;
    width: 250px;
    border-top-color: #E000FF;
    border-right-color: #FFFF00;
    border-bottom-color: #00D4FF;
    border-left-color: white;
    border-radius: 15px;
    font-size: 1.4em;
    cursor: pointer;
    user-select: none;

    display: flex;
    align-items: center;
    justify-content: center;
    color: white;

    i {
      margin-left: 10px;
    }
  }
  .button:hover {
    background: #ffffff21;
  }

  .button:active {
    background: #ffffff21;
    opacity: 0.5;
  }
}
</style>
