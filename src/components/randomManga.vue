<script setup>
import axios from 'axios'
import {ref} from "vue";

const display = ref('')
const img = ref('')
const responses = ref([])
const show = ref(false)

function fetch(){
  axios.get('https://api.jikan.moe/v4/random/manga').then(response =>{
    console.log(response.data)
    responses.value[0] = 'title: '+response.data.data.title
    responses.value[1] ='url:'+response.data.data.url
    responses.value[2] = 'content: '+ response.data.data.synopsis
  })
  show.value = !show.value

}



</script>

<template>
  <button @click="fetch">random manga</button>
  <p v-show="show" v-for="item in responses">{{item}}</p>
  <img :src="display"></img>
</template>

<style scoped>

</style>