<script setup>
import axios from 'axios'
import {ref} from "vue";
const dolar = ref('')
const UF = ref('')
const date = ref('')
const loading = ref(true)

const getData = async () => {
  loading.value = true
  try {
    const { data } = await axios.get('https://api-dolar-hp7p.onrender.com/');
    // console.log(data)
    dolar.value = data.dolar
    UF.value = data.UF
    date.value = data.date
  } catch (error) {
    console.log(error)
  }finally{
    loading.value = false
  }
}
getData();
</script>

<template>
  <h1 v-if="loading">Loading data....</h1>
  <h1 v-else>Api Dolar Dolar: {{ dolar }} UF: {{ UF }} Fecha: {{ date }}</h1>
</template>