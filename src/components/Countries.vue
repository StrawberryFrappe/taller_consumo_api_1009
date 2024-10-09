<script setup>
import axios from 'axios'
import {ref} from "vue";

const responses = ref([])
const show = ref(false)
function fetch(){
  axios.get('https://countriesnow.space/api/v0.1/countries/population').then(response =>{
    for (const el of response.data.data){
      responses.value.push("country: "+el.country +"  ||  code:"+ el.code)
    }
  })
  show.value = !show.value
}
</script>

<template>
  <button @click="fetch">countries</button>
  <p v-show="show" v-for="item in responses">{{item}}</p>
</template>

<style scoped>

</style>