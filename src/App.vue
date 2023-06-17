<script setup>
import { ref } from 'vue';

const itemm = ref([]);

async function datos() {
  const res = await fetch("https://jsonplaceholder.typicode.com/posts");
  const respuesta = await res.json();
  itemm.value = respuesta;
  console.log(respuesta)
}

datos()
</script>


<template>
  <header>
    <div class="container">
      <div class='card' v-for="item in itemm">
        <h2 class='item-title'>{{ item.title }}</h2>
        <p class='item'>{{ item.body }}</p>
        <h1 class='item'>{{ item.id }}</h1>
      </div>
    </div>
  </header>
</template>
<style>
.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 5px;
}

.card {
  border: 1px solid black;
  border-radius: 3px;
  margin: 5px;
  display: flex;
  flex-direction: column;
  
}
.item-title{
  background-color: rgb(152, 136, 166);
  width: 97%;
  padding: 5px;
  height: 150px;
  text-align: center;
  color: white;
}
.item{
  padding: 5px;
}

@media (max-width:1200px) {
  .container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 5px;
  }
}

@media (max-width:900px) {
  .container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 5px;
  }
}

@media (max-width:500px) {
  .container {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 5px;
  }
}

</style>

