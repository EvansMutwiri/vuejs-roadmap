<template>
  <h1>Counter</h1>

  <button @click="count++">{{ count }}</button>
</template>

<script>
export default {
    data () {
        return {
            count: 0
        }
    }
}
</script>

<style>
body {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}
    button {
        background: #b0e0e6;
        padding: 10px 30px;
        font: 600 18px;
        border: #b0e0e6;
        box-shadow: 0 2px 2px 0 black;
        margin: auto;
    }
</style>