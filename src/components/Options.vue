<template>
  <h2>{{name}}</h2>
</template>

<script>
export default {
    data () {
        return {
            name : "Evans"
        }
    }, 
    mounted () {
        setTimeout(() => {
            this.name = "Mutwiri";
        }, 4000);
    }
}
</script>

<style>

</style>