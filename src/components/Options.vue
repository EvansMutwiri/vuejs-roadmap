<template>
    <div class="container">
        <h1>PortFolio</h1>
        <h2>First Name: {{ firstName }}</h2>
        <h2>Last Name: {{ lastName }}</h2>
        <hr>
        <div>
            <p>Contacts: {{ details.contact }}</p>
            <p>Location: {{ details.address }}</p>
        </div>

        <button @click="changeDetails">Change Details</button>
    </div>
</template>

<script>
import { ref, reactive } from '@vue/reactivity';
export default {
    setup() {

        // use case: ref for strings and numbers
        let first = ref('Evans');
        let last = ref('Mutwiri');

        // use case: reactive for objects
        let details = reactive({
            contact: '0722000000',
            address: 'Nairobi'
        });

        let changeDetails = () => {
            details.contact = '+256565625',
            details.address = 'Uganda'
        }

        return {
            firstName: first,
            lastName: last,
            details: details,
            changeDetails
        }
    }
}
</script>

<style lang="scss">
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
    background: linear-gradient(#d2cdc3, #e3d4b4);
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
button {
    color: #fbfbfb;
    background: rgb(67, 132, 223);
    border: none;
    border-radius: 4px;
    padding: 10px;
}
</style>