<template>
    <div class="container">
        <h1>Resume Maker</h1>
        <h2>First Name: {{ firstName }}</h2>
        <h2>Last Name: {{ lastName }}</h2>

        <h3>Fullname: {{ fullName }}</h3>

        <div class="form">
            <input type="text" placeholder="First Name" v-model="first">
            <input type="text" placeholder="Last Name" v-model="last">
        </div>
        <hr>
        <div>
            <p>Contacts: {{ details.contact }}</p>
            <p>Location: {{ details.address }}</p>
        </div>

        <button @click="changeDetails">Change Details</button>

        <div class="languages">
            <h1>My stack</h1>
            <ul>
                <li v-for="{id, label} in languages" :key="id"> {{ label }}</li>
            </ul>
        </div>

        <form
            @submit.prevent="languages.push({id: languages.length + 1, label: newItem })"
        >
            <input 
                type="text" 
                v-model="newItem"
                placeholder="Add new language"
            >

        <button>Save</button>

        </form>
    </div>
</template>

<script>
import { ref, reactive} from '@vue/reactivity';

// import computed
import { computed } from '@vue/runtime-core';
export default {
    setup() {

        let first = ref(' ');
        let last = ref(' ');
        let details = reactive({
            contact: '0722000000',
            address: 'Nairobi'
        });

        let changeDetails = () => {
            details.contact = '+256565625',
            details.address = 'Uganda'
        }

        // 2 way binding
        // let changeFirstName = (event) => {
        //     first.value = event.target.value;
        // }

        // let changeLastName = (event) => {
        //     last.value = event.target.value;
        // }

        const fullName = computed(() => {
            return first.value + ' ' + last.value;
        })

        let languages = ref([
           {id: 1, label: "Javascript"},
           {id: 2, label: "CSS"},
           {id: 3, label: "html5"},
        ]);

        let newItem = ref(" ");

        return {
            firstName: first,
            lastName: last,
            details: details,
            changeDetails,
            first,
            last,
            fullName,
            languages
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
    background: #4384df;
    border: none;
    border-radius: 4px;
    padding: 10px;
}
input {
    margin: 5px;
    border: #4384df 1px solid;
    padding: 10px;
    border-radius: 4px;
}

ul {
    list-style: none;
}

.languages {
    color: #ffffff;
    font-weight: 800;
    font-family: 'Courier New', Courier, monospace;
    
    h1 {
        color: black;
    }
}
</style>