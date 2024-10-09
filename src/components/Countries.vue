<script setup>
import axios from 'axios'
import {ref} from "vue";

const responses = ref([])
const show = ref(false)
function fetch(){
  axios.get('https://countriesnow.space/api/v0.1/countries/population').then(response =>{
    responses.value = response.data
  })
  show.value = !show.value
}
</script>

<template>
  <button @click="fetch">countries</button>
  <p v-show="show">{{responses}}</p>
</template>

<style scoped>

</style>