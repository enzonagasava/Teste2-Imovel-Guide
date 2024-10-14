<script setup>
import UserForm from './UserForm.vue';
import UserCard from './UserCard.vue';
import { ref } from 'vue';


    const user = ref({
    name: '',
    surname: '',
    photo: ''
    });

    const cardColor = ref('#ecb117');

    const colorBorder = ref('#000');

    const updateUser = (updatedUser) => {
    user.value = updatedUser;
    };

    const changeColor = (color) => {
    cardColor.value = color;
    };

    const changeBorder = (colorB) => {
    colorBorder.value = colorB
    };
</script>

<template>
        <div>
        <user-form @updateUser="updateUser" @changeColor="changeColor" @changeBorder="changeBorder" ></user-form>
        <user-card :user="user" :cardColor="cardColor" :colorBorder="colorBorder"></user-card>
    </div>

</template>

