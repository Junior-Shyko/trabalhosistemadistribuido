<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <template slot="header">
              <h4 class="card-title">Lista de usuários</h4>
              <p class="card-category">Lista com o nome de todos usuários cadastrados</p>
            </template>
            <table class="table">
              <thead class="thead-dark">
                <tr>
                  <th scope="col">ID</th>
                  <th scope="col">Nome</th>
                  <th scope="col">E-mail</th>
                  <th scope="col">Cidade</th>
                  <th scope="col">Ação</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for='user in users' :key="user.userWebservice_id">
                  <th scope="row">{{user.userWebservice_id}}</th>
                  <td>{{user.userWebservice_name}}</td>
                  <td>{{user.userWebservice_email}}</td>
                  <td>{{user.userWebservice_city}}</td>
                  <td>Editar</td>
                </tr>
                
              </tbody>
            </table>

          </card>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import LTable from 'src/components/Table.vue'
  import Card from 'src/components/Cards/Card.vue'
  import axios from 'axios';
  export default {
    components: {
      LTable,
      Card
    },
    data () {
      return {
        users: []
      }
    },
    methods: {
      allUsers: function() {
        axios.get('http://192.168.10.22:4000/api/webservice/users')
        .then(response => {
          // handle success
          console.log(response.data)
          this.users = response.data
        })
        .catch(function (error) {
          // handle error
          console.log(error)
        });
      }
    },
    created() {
      this.allUsers()
    }
  }
</script>
<style>
</style>
