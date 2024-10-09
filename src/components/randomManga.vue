<script setup>
import axios from 'axios'
import {ref} from "vue";

const responses = ref([])
const show = ref(false)
function fetch(){
  axios.get('https://api.jikan.moe/v4/random/manga').then(response =>{
    responses.value = response.data
  })
  show.value = !show.value
}
</script>

<template>
  <button @click="fetch">random manga</button>
  <p v-show="show">{{responses}}</p>
</template>

<style scoped>

</style>