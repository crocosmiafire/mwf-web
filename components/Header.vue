<template>
  <div class="header-root">
    <section class="left">
      <h3>Melbourne Winter Fest</h3>
    </section>
    <section>
      <div class="links">
        <a href="#About">About</a>
        <a href="#Book">Book</a>
        <a href="#Schedule">Schedule</a>
        <a href="#Maps">Maps</a>
        <a href="#FAQ">FAQ</a>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
.header-root {
  width: 100%;
  height: 65px;
  background: transparent;
  padding: 20px 30px;

  position: fixed;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
}

.links {
  a {
    margin: 0px 10px;
    text-decoration: none;
    color: white;
  }
}
</style>
