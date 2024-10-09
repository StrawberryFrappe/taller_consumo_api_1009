<script setup>
import axios from 'axios'
import {ref} from "vue";

const display = ref('')
const img = ref('')
const responses = ref([])
const show = ref(false)

function fetch(){
  axios.get('https://api.jikan.moe/v4/recommendations/anime').then(response =>{
    for (const el of response.data.data){
      responses.value.push(el)
    }
  })
  show.value = !show.value

}



</script>

<template>
  <button @click="fetch">anime recomend</button>
  <p v-show="show" v-for="item in responses">{{item}}</p>
  <img :src="display"></img>
</template>

<style scoped>

</style>