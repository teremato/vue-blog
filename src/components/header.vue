<template>
  <header class="header">
    <div class="logo">Blog <span>Vue3</span></div>
  </header>
</template>

<script>
export default {
    name: 'app-header'
}
</script>

<style lang="css" scoped>
    .header {
        font-size: 25px;

        text-transform: uppercase;

        padding: 15px;
        box-shadow: 4px 14px 27px 0px rgba(34, 60, 80, 0.1);

        background-color: rgba(255, 255, 255, 0.5);
        color: gray;
    }
    .logo {
      font-size: inherit;

      margin-left: 9%;
    }
    .logo span {
      font-size: inherit;

      color: rgb(255, 15, 83);
    }
</style>