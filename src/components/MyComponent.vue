<template>
  <h1>Hey I am {{ name }}</h1>
</template>

<script>
export default {
    data () {
        return {
            name: 'Evans'
        }
    }
}
</script>

<style>
    h1 {
        color: red;
    }
</style>