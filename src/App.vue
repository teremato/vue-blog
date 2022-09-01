<template>
  <app-header/>
  <div class="container">
    <post-list/>
  </div>
</template>

<script>
import appHeader from './components/header.vue'
import postList from './components/post-list.vue'

export default {
  components: {
    ['app-header']: appHeader,
    ['post-list']: postList
  }
}
</script>

<style lang="css">
  * {
    margin: 0;
    padding: 0;
    
    font-family: Arial, Helvetica, sans-serif;
    font-size: 15px;
  }
  .container {
    display: flex;
    justify-content: center;
  }
</style>