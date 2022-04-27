<template>
<h1>PortFolio</h1>
  <h2>First Name: {{firstName}}</h2>
  <h2>Last Name: {{lastName}}</h2>
</template>

<script>
import { ref } from '@vue/reactivity';
export default {
    setup () {
        let first = ref('Evans');
        let last = ref('Mutwiri');

        setTimeout(() => {
            first.value = 'Mutwiri',
            last.value = 'Evans'
        }, 4000);
        return {
            firstName : first,
            lastName : last
        }
    }
}
</script>

<style>
body {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
}

h1 {
        /* font: 800 'Verdana'; */
        font: 40px Georgia, serif;
    }
h2 {
    font: 20px Arial, sans-serif;
}
</style>