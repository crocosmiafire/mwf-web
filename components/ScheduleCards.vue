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
  background: white;
  color: black;
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
      font-size: 26px;
      font-family: 'Barlow', 'Inter', sans-serif;
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

    width: 105%;
    height: 105%;

    align-self: center;
    justify-self: center;
  }
}
</style>
