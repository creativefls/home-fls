<template>
  <v-container fluid>

    <test-component/>
    <test-component/>
    <test-component/>
    <test-component/>


  </v-container>
</template>

<script>
import TestComponent from '~/components/home-page/TestComponent'

export default {
  components: { TestComponent }
}
</script>
