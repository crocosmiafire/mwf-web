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
  min-width: 500px;
  height: 350px;
  background: white;
  color: black;
  border-radius: 10px;

  box-shadow: 0px 2px 10px rgba(0,0,0,.25);
  display: grid;
  grid-template-areas:
  "title"
  "image";
  grid-template-rows: 1.5fr 4fr;

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
      font-size: 28px;
      font-family: 'Barlow', 'Inter', sans-serif;
      font-weight: bold;
      margin-bottom: 5px;
    }

    span {
      display: flex;
      align-items: center;
    }

    i {
      margin-right: 7px;
    }
  }

  .evt-image {
    background-image: url('http://theluxtraveller.com/wp-content/uploads/2015/06/Melbourne-at-night.jpg');
    background-size: cover;

    width: calc(100% - 50px);
    height: calc(100% - 25px);

    border-radius: 8px;
    margin: 0px 25px 25px;

    align-self: center;
    justify-self: center;
  }
}
</style>
