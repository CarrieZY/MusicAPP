<template>
  <div id="app">
    <m-header></m-header>
    <tab></tab>
    <keep-alive>
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
import MHeader from 'components/header/header'
import tab from 'components/tab/tab'
export default {
  name: 'App',
  components:{
    MHeader,
    tab
  }
}
</script>

<style>

</style>
