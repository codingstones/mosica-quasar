<template>
  <q-toolbar>
    <q-btn flat @click="clickDrawer()">
      <q-icon name="menu" />
    </q-btn>
    <q-toolbar-title>
      Anarchy JS
    </q-toolbar-title>
    <q-btn color='secondary'>
      <q-icon name="search"/>
      SEARCH
    </q-btn>
  </q-toolbar>
</template>

<script>
  export default {
    methods: {
      clickDrawer() {
        this.$emit('drawerClick')
      }
    }
  }
</script>

<style scoped>
  img { max-width: 60px; }
</style>
