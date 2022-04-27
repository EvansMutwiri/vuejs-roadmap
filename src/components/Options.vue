<template>
    <div class="container">
        <h1>PortFolio</h1>
    <h2>First Name: {{ firstName }}</h2>
    <h2>Last Name: {{ lastName }}</h2>
    <hr>
    <div>
        <p> Contacts: {{ details.contact }}</p>
        <p> Location: {{ details.address }}</p>
    </div>
    </div>
</template>

<script>
import { ref } from '@vue/reactivity';
export default {
    setup() {
        let first = ref('Evans');
        let last = ref('Mutwiri');

        let details = ref({
            contact: '0722000000',
            address: 'Nairobi'
        });

        setTimeout(() => {
            details.value.address = 'Meru',
            details.value.contact = '0721212121'
        }, 4000)

        return {
            firstName: first,
            lastName: last,
            details: details
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

.container {
    border: 1px none;
    padding: 6em;
    border-radius: 10px;
    background: #d2cdc3;
    box-shadow: 2px 2px 0 0 #938f88;
    margin-top: 10%;
}

h1 {
    /* font: 800 'Verdana'; */
    font: 50px Georgia, serif 800;
}

h2 {
    font: 20px Arial, sans-serif;
}
</style>