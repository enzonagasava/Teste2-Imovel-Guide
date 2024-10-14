<script setup>
        import { ref, watch } from 'vue';

    const emit = defineEmits(['updateUser', 'changeColor', 'changeBorder']);

    const user = ref({
    name: '',
    sobrename: '',
    photo: ''
    });

    const handleFileChange = (e) => {
    const file = e.target.files[0];
    user.value.photo = URL.createObjectURL(file);
    };

    watch(user, (newUser) => {
    emit('updateUser', newUser);
    }, { deep: true });

    const changeColor = (color) => {
    emit('changeColor', color);
    };

    const changeBorder = (color) => {
    emit('changeBorder', color)
    };
</script>


<template>
<div class="row ">
    <div class="container col mt-5">
        <div id="containerForm"  class="d-flex p-3">
            <div class="d-block">
                <div class="preview">
                    <img style="width: 100%; height: 100%;" :src="user.photo" v-if="user.photo">
                </div>
                <label class="label-selecao" for="selecao-arquivo"> ADICIONAR FOTO</label>
        <input class="btn" id="selecao-arquivo" type="file" @change="handleFileChange">
            </div>
        <div class="m-3">
            <label for="">Nome</label>
            <input class="mb-4" type="text" v-model="user.name" placeholder="Nome">
            <label for="">Sobrenome</label>
            <input type="text" v-model="user.sobrename" placeholder="Sobrenome">
        </div>
        </div>        
    </div>
</div>
<div class="row mt-5" style="display: flex; justify-content: center;">
    <div class="col justify-content-center" style="max-width: 550px; justify-content: flex-start">
        <div class="d-flex">
    <button type="button" @click="changeColor('#ecb117'); changeBorder('#000');"  style="background-color: #ecb117; width: 2.5em; height: 1.5em;"></button>
    <button type="button" @click="changeColor('#9b0021'); changeBorder('#cccccc');" style="background-color: #9b0021; width: 2.5em; height: 1.5em; margin-left: 1em"></button>
    </div>

    </div>

</div>
    </template>

<style>

@media (max-width:768px){

        #containerForm {
            display: block!important;
            width: 300px!important;
            height: 500px !important;
        }

        .preview {
            width: 100%!important;
        }
    }

.container {
    display: flex;
    justify-content:center;
}

#containerForm{
    width: 550px;
    height: 350px;
    border: solid 1px #cccccc;
}

.preview{
    width: 250px;
    height: 250px;
    border: solid 1px #000;
}


input{
    height: 2.5em;
    width: 220px;
    text-transform: uppercase
}

input[type='file']{
    display: none;
}

.label-selecao{
    background-color: #ff9900;
    color: #fff;
    cursor: pointer;
    margin-top: .5em;
    padding: 6px;
    align-items: center;
    text-align: center;
    width: 100%;
    height: 40px;
    font-size: 20px;
}

img {
    width: 180px;
    height: 180px;
    margin-bottom: 20px;
    object-fit: cover;
}
</style>