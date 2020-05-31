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
    <div id="divButton">
      <button @click="afficherClients(nombreClients, genre)">
        Afficher les clients
      </button>
    </div>
    <div id="tableau">
      <table v-for="client in clients" :key="client" :class="tableau">
        <thead>
          <th colspan="2">
            Informations Client
          </th>
        </thead>
        <thead>
          <th colspan="2">
            <img :src="client.picture.large">
          </th>
        </thead>
        <tbody>
          <tr>
            <td>Gender</td>
            <td>{{ client.gender }}</td>
          </tr>
          <tr>
            <td>Name</td>
            <td>{{ client.name.title }} {{ client.name.first }} {{ client.name.last }}</td>
          </tr>
          <tr>
            <td>location</td>
            <td>{{ client.location.street.number }} {{ client.location.street.name }}</td>
          </tr>
          <tr>
            <td>email</td>
            <td> {{ client.email }} </td>
          </tr>
          <tr>
            <td>phone</td>
            <td>{{ client.phone }}</td>
          </tr>
        </tbody>
      </table>
    </div>
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

#tableau{
    margin-top: 20px;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

.tableau{
    margin: 10px;
    width: 400px;
    margin-right: 10px;
    text-align: center;
    border: 1px solid black;
}
.tableau thead th{
    background-color: #a29bfe;
}
</style>

<script>
import Axios from 'axios'

export default {
  data(){
    return{
      genre: 'male',
      nombreClients: 0,
      tableau: 'tableau',
      clients: []
    } 
  },
  methods: {
    afficherClients (nombreClients, genre) {
      return Axios.get('https://randomuser.me/api/?results=' + this.nombreClients + '&gender=' + this.genre)
        .then(reponse => (this.clients = reponse.data.results))
    }
  }
}
</script>