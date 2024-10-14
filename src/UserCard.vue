<script setup >

import { defineProps } from 'vue';

    const props = defineProps({
    user: Object,
    cardColor: String,
    colorBorder: String
    });


    
</script>

<template>
    <div class="row d-block">
        <div class="col d-flex justify-content-center">
            <div :style="{ backgroundColor: cardColor }" class="card" style="width: 300px; height: 300px; border-radius: 0;">
                <div :style="{borderColor: colorBorder}" class='innerCard' style="border: solid 3px; height: 90%; width: 90%;">
                    <img :src="user.photo" alt="Foto do Usuário" v-if="user.photo" style="width: 100%; height: 100%; margin-bottom: 0;">
                </div>
    </div>
        </div>
    </div>
    <div class="row">
        <div class="col d-flex justify-content-center mt-1 ">
            <p class="p-2 align-items-center d-flex justify-content-center" style="background-color: #000; width: 300px; height: 50px; color: #cccccc">ADMINISTRADOR &nbsp;
                <span style="text-transform: uppercase" :style="{color : cardColor}">{{ user.name }} {{ user.surname }}</span>
            </p>
        </div>
        </div>
</template>

<style>
.card {
    border: 1px solid #cccccc;
    padding: 16px;
    margin-top: 20px;
    width: 200px;
    height: 250px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

    .innerCard {
    width: 90%;
    height: 90%;
    border: solid 3px;
    }
</style>