<template>
  <div class="root">
    <section class="footer">
      <div class="inner">
        <div />
        <p class="disc">
          This website is a concept and is not indicative of any real-life events.<br>The City of Melbourne and Victorian Government do not endorse this website.
        </p>
        <div>
          <img class="com-logo" src="@/assets/com.svg">
          <img class="com-logo" src="@/assets/vicgov.png">
        </div>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
div.root {
  width: 100%;
  height: 150px;
  background: linear-gradient(to left, #262262, #00A79D);
}

.footer {
  width: 100%;
  height: 130px;
  padding: 20px 75px;

  background: linear-gradient(to left, #262262, #00A79D);
  color: white;

  transform: skewY(-4deg) translateY(-65px);
}

.inner {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  transform: skewY(4deg) translateY(40px);

  width: 100%;
}

.disc {
  position: absolute;
  margin: 0;
  font-size: 12px;
}

.com-logo {
  height: 50px;
  width: auto;
  margin-left: 50px;
}
</style>
