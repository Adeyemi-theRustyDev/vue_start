<script setup>
    import { ref } from 'vue';
    const newName = ref("");
    const names = ref([
        "Adeyemi",
        "Oyin",
        "Toni",
        "Gift",
        "Daniel",
        "Tomi"
    ]);
    const nameExists = ref({
        flag: false,
        message: "Name is already in the list"
    });

    const addName = () => {
        nameExists.value.flag = false;
        if (!names.value.includes(newName.value.trim())) {
            names.value.push(newName.value.trim()); 
        }
        else {
            nameExists.value.flag = true;
        }
        newName.value = ""

    }
</script>

<template>
    <div class="style-comp">
        <div v-if="nameExists.flag">
            <p>{{ nameExists.message }}</p>
        </div>
        <form @submit.prevent="addName">
            <input type="text" v-model="newName">
            <button>Add names</button>
        </form>
        <ul>

            <li v-for="name in names"> {{ name }}</li>
        </ul>
    </div>
</template>

<style scoped>
.style-comp {
    margin: auto;
    display: flex;
    flex-direction: column;
    width: 70%;
    background-color: #333;
    color: white;
    font-size: 2rem;
    justify-content: space-between;
    padding: 3em;
}

.style-comp form {
    display: flex;
    gap: 3em;
}

.style-comp input[type="text"] {
    width: 60%;
    border: 0;
    padding: 1.5em .5em;
}

.style-comp button {
    width: 20%;
}

.style-comp button:hover {
    cursor: pointer;
}</style>