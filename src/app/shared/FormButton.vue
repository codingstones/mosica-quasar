<template>
  <q-btn color="primary"
         class="full-width"
         :disabled="disabled"
         @click="onClick()">
    <slot></slot>
  </q-btn>
</template>

<script>
  export default {
    props: ['onClick', 'disabled']
  }
</script>
