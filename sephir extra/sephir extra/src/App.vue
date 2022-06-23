<template>
  <html>
    <header>
      <div id="logoTitle">
        Sephir extra
      </div>
    </header>

    <main>
      <router-view />
      <!---<TheWelcome />-->
    </main>
  </html>
</template>

<style>
@import './assets/base.css';
</style>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
