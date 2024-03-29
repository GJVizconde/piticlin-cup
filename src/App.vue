<script setup lang="ts">
import axios from 'axios';
import { ref } from 'vue';

let player1 = ref({id:'', name:'', flag:''})
let player2 = ref({id:'', name:'', flag:''})

const callPlayer1 = async () => {
  const countriesArray = (await axios.get('https://piticlin-api.onrender.com/api/countries')).data;
  const randomIndex = Math.floor(Math.random() * countriesArray.length); // Genera un índice aleatorio
   player1.value = countriesArray[randomIndex];

   console.log(player1.value)
}

const callPlayer2 = async () => {
  const countriesArray = (await axios.get('https://piticlin-api.onrender.com/api/countries')).data;
  const randomIndex = Math.floor(Math.random() * countriesArray.length); // Genera un índice aleatorio
   player2.value = countriesArray[randomIndex];

   console.log(player1.value)
}



</script>

<template>
  <div class="">
    <header class=" py-10">
    <h1 class=" text-6xl text-center text-white" >Piticlin Cup</h1>
    </header>
    <div class=" flex items-center justify-center   ">
      <div class=" flex gap-[50px] items-center">
        <article class=" flex flex-col border border-white w-[200px]
        ">
          <figure class=" w-full h-[180px] bg-white" >
            <img class=" w-full" :src=player1.flag alt="">
          </figure>
          <p class=" text-black bg-white text-3xl text-center">{{ player1.name }} </p>
        </article>
        <p class=" text-white text-8xl">VS</p>
        <article class=" flex flex-col border border-white w-[200px]
        ">
          <figure class=" w-full h-[180px] bg-white" >
            <img class=" w-full" :src=player2.flag alt="">
          </figure>
          <p class=" text-black bg-white text-3xl text-center">{{ player2.name }} </p>
        </article>
      </div>



    </div>
    <div class=" flex flex-col items-center justify-center">
      <section class=" flex items-center justify-center mt-[50px] gap-[30px]">
          <button class=" text-white bg-green-600  p-5 rounded " @click="callPlayer1">Player 1</button>
          <button class=" text-white bg-blue-600  p-5 rounded " @click="callPlayer2">Player 2</button>
      </section>
      <button class=" text-white bg-red-600  p-5 rounded mt-[50px]" @click="callPlayer1">Borrar</button>
    </div>

    
  </div>


</template>

