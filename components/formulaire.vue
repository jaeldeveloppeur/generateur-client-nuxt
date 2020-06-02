<template>
  <div class="container">
    <form>
      <label for="nombre">Nombre de clients à générer :  </label>
      <input id="nombre" v-model="nombreClients" type="number">
      <label for="genre">Genre :  </label>
      <select id="genre" v-model="genre">
        <option>male</option>
        <option>female</option>
      </select>
    </form>
    <tableau v-bind:nombreClients="parseInt(nombreClients)" v-bind:genre="genre"/>
  </div>
</template>

<style>
  form{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    margin: 20px;
}

form input{
    margin: 0 20px;
    height: 50px;
    border-radius: 20px;
    border: 1px solid grey;
    padding: 10px;
    text-align: center;
}

form select{
    height: 50px;
    width: 100px;
    text-align: center;
    margin: 0 20px;
}

#divButton{
    margin-top: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
}

button{
    color: #fff !important;
    text-transform: uppercase;
    text-decoration: none;
    background: #60a3bc;
    padding: 20px;
    border-radius: 50px;
    display: inline-block;
    border: none;
}

button:hover{
    text-shadow: 0px 0px 6px rgba(255, 255, 255, 1);
    -webkit-box-shadow: 0px 5px 40px -10px rgba(0,0,0,0.57);
    -moz-box-shadow: 0px 5px 40px -10px rgba(0,0,0,0.57);
    transition: all 0.4s ease 0s;
}
</style>

<script>
import tableau from '~/components/tableau.vue'

export default {
  name: 'formulaire',
  components: { 'tableau' : tableau },
  data() {
    return {
      genre: 'male',
      nombreClients: 1,
    }
  },
}
</script>