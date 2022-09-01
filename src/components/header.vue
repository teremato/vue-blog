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
        background-color: rgba(255, 255, 255, 0.5);
        box-shadow: 4px 14px 27px 0px rgba(34, 60, 80, 0.2);
        color: gray;
    }
    .header span {
        color: crimson;
    }
</style>