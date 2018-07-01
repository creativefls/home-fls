<template>
  <v-layout>Redirecting...</v-layout>
</template>

<script>
export default {
  mounted () {
    this.$nextTick(() => {
      window.location.href = 'http://daftar.futureleadersummit.org'
    })
  }
}
</script>
