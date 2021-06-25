<template>
  <div class="card-root">
    <div class="card-title">
      <h1>An Event Title</h1>
      <span><i class="material-icons">schedule</i> 20:30</span>
    </div>
    <div class="evt-image">Image goes here</div>
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
  height: 250px;
  background: white;
  color: black;
  border-radius: 10px;

  box-shadow: 0px 2px 10px rgba(0,0,0,.25);
  display: grid;
  grid-template-areas:
  "title"
  "image";
  grid-template-rows: 20% 1fr;

  overflow: hidden;

  margin: 0px 20px;

  .card-title {
    grid-area: title;
    justify-self: start;
    align-self: flex-end;
    padding: 0px 25px;

    display: flex;
    justify-content: space-between;

    width: 100%;

    h1 {
      font-size: 28px;
      font-family: 'Inter', sans-serif;
      font-weight: bold;
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
    height: calc(100% - 50px);

    border-radius: 8px;
    margin: 25px;

    align-self: center;
    justify-self: center;
  }
}
</style>
