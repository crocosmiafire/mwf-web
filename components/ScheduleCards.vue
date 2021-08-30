<template>
  <div class="card-root">
    <div class="card-title">
      <div>
        <h1>{{ info.title }}</h1>
        <span><i class="material-icons">place</i> {{ info.location }}</span>
      </div>
      <span><i class="material-icons">schedule</i> {{ info.time }}</span>
    </div>
    <div class="evt-image" />
  </div>
</template>

<script>
export default {
  props: ['info']
}
</script>

<style lang="scss" scoped>
.card-root {
  min-width: 425px;
  height: 250px;
  background: black;
  color: white;
  border: solid 1px white;
  border-radius: 10px;

  box-shadow: 0px 2px 10px rgba(0,0,0,.25);
  display: grid;
  grid-template-areas:
  "title"
  "image";
  grid-template-rows: 2.1fr 4fr;

  overflow: hidden;

  margin: 0px 20px;
  user-select: none;

  .card-title {
    grid-area: title;
    justify-self: start;
    align-self: center;
    padding: 0px 25px;

    display: flex;
    justify-content: space-between;

    width: 100%;

    h1 {
      font-size: 22px;
      font-family: 'Manrope', 'Barlow', 'Inter', sans-serif;
      font-weight: 600;
      margin-bottom: 6px;
    }

    span {
      display: flex;
      align-items: center;
    }

    i {
      margin-right: 7px;
      font-size: 22px;
    }
  }

  .evt-image {
    background-image: url('http://theluxtraveller.com/wp-content/uploads/2015/06/Melbourne-at-night.jpg');
    background-size: cover;

    background-size: cover;
    width: 100%;
    height: 100%;
    align-self: center;
    justify-self: center;
    border: solid black 7px;
    box-sizing: border-box;
    border-radius: 0px 0px 12px 12px;
  }
}
</style>
