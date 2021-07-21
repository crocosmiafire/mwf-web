<template>
  <section class="footer">
    <div class="inner">
      <div class="left">
        <img class="main-logo" src="@/assets/Logo-var2op2.svg">
      </div>
      <div class="right">
        <div class="link-grid">
          <div class="field-main">
            <h3>yo</h3>
            <a>Home</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.footer {
  width: 100%;
  height: 200px;
  padding: 20px 30px;

  transform: skewY(3deg);
}

.inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  transform: skewY(-3deg);

  width: 100%;
  height: 100%;
}

.left img {
  height: 50px;
  width: auto;
}
</style>
