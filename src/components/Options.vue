<template>
    <div class="container">
        <div class="header">
            <h1>Eazy Bio</h1>

        </div>

        <button class="cancel" v-if="editing" @click="edit(false)">Cancel</button> <button class="save" v-else @click="edit(true)"> Edit </button>
        
        <div :class="['details']">
            <h2>First Name: {{ firstName }}</h2>
            <h2>Last Name: {{ lastName }}</h2>

            <h3>Fullname: {{ fullName }}</h3>
        </div>

        <form :class="['form']" v-if="editing">
            <input type="text" placeholder="First Name" v-model="first">
            <input type="text" placeholder="Last Name" v-model="last">
        </form>
        <hr>

        <div class="languages">
            <h1>My stack</h1>
            <ul>
                <li v-for="{id, label} in languages" :key="id"> {{ label }}</li>
            </ul>
            <p v-if="!languages.length">No languages added</p>
        </div>

        <form
            v-if="editing"
            @submit.prevent="addLang"
        >
            <input 
                type="text" 
                v-model="newItem"
                placeholder="Add new language"
            >

        <button v-bind:disabled="newItem.length === 0">Save</button>

        </form>

        <div class="languages">

            <h1>My Education</h1>

            <p v-if="qualifications.length < 2 && editing">press enter to add value</p>
            
            <ul>
                <li v-for="{id, label, completedStatus} in qualifications" :key="id" :class="[completedStatus ? 'completed': '']"> {{ label }}</li>
            </ul>
            <p v-if="!qualifications.length">No qualification added</p>
        </div>

        <form
            v-if="editing"
            @submit.prevent="addEdu"
        >
            <input 
                type="text" 
                v-model="newEdu"
                placeholder="Add qualification"
            >

            <label>
                <input type="checkbox" v-model="completedStatus">Completed
            </label>

        <button v-bind:disabled="newEdu.length === 0">Save</button>

        </form>
    </div>
</template>

<script>
import { ref, reactive} from '@vue/reactivity';

// import computed
import { computed } from '@vue/runtime-core';
export default {
    setup() {

        let first = ref('');
        let last = ref('');
        // let details = reactive({
        //     contact: '0722000000',
        //     address: 'Nairobi'
        // });

        const fullName = computed(() => {
            return first.value + ' ' + last.value;
        })

        let languages = ref([]);

        let qualifications = ref([
            
        ]);


        let newItem = ref("");

        let newEdu = ref("");
        let completedStatus = ref(false)

        let addLang = () => {
            languages.value.push({id: languages.value.length + 1, label: newItem.value });
            newItem.value = "";
        }

        let addEdu = () => {
            qualifications.value.push({id: qualifications.value.length + 1, label: newEdu.value, completedStatus: completedStatus.value });
            newEdu.value = "";
            completedStatus.value = "";
        }

        let editing = ref(false);

        let edit = (e)=> {
            editing.value = e;
            newItem.value = "";
            newEdu.value = "";
            completedStatus.value="";
        }

        return {
            firstName: first,
            lastName: last,
            first,
            last,
            fullName,
            languages,
            newItem,
            addLang,
            editing,
            edit,
            qualifications,
            newEdu,
            addEdu,
            completedStatus
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

.header {
    display: inline-flex;
}

.container {
    border: 1px none;
    padding: 6em;
    border-radius: 10px;
    background: linear-gradient(#d2cdc3, #e3d4b4);
    box-shadow: 2px 2px 0 0 #938f88;
    margin-top: 10%;
}

.details {
    background: #f1ece1;
    padding: 1%;
    margin: 1%;
    border-radius: 4px;
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
    width: 10em;
    border-radius: 4px;
    padding: 10px;
}

.cancel {
    color: #fbfbfb;
    background: #df435a;
    border: none;
    border-radius: 4px;
    padding: 10px;
    width: 100%;
}

.save {
    width: 100%;
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

.completed {
    color: green;
}
</style>