<template>
  <div>
    <div id="divButton">
      <button @click="afficherClients()">
        Afficher les clients
      </button>
    </div>
    <div id="tableau">
      <table v-for="client in clients" :key="client.liste" :class="tableau">
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
import formulaire from '~/components/formulaire.vue'

export default {
    name: 'tableau',
    data() {
      return{
        tableau: 'tableau',
        clients: []
      }
    },
    props: {
      genre: {
        type : String,
        required: true
      },
      nombreClients: {
        type : Number,
        required: true
      }
    },
    methods: {
      afficherClients () {
        return Axios.get('https://randomuser.me/api/?results=' + this.nombreClients + '&gender=' + this.genre)
          .then(reponse => (this.clients = reponse.data.results))
      }
  }
}
</script>