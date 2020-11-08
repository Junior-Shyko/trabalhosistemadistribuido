<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-12">
          <card class="strpied-tabled-with-hover"
                body-classes="table-full-width table-responsive"
          >
            <template slot="header">
              <h4 class="card-title">
                Lista de usuários
              </h4>
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
                <tr v-for='user in profiles' :key="user.userWebservice_id">
                  <th scope="row">{{user.userWebservice_id}}</th>
                  <td>{{user.userWebservice_name}}</td>
                  <td>{{user.userWebservice_email}}</td>
                  <td>{{user.userWebservice_city}}</td>
                  <td>
                     <b-button @click="showModal(user.userWebservice_id)">
                       <i class="fa fa-edit"></i>
                     </b-button>
                      
                    <button type="button" @click="showMsgBoxOne(user.userWebservice_id)" title="Excluir Usuário" class="btn btn-danger btn-fill">
                      <i class="fa fa-trash"></i>
                    </button>
                  </td>
                </tr>
                
              </tbody>
            </table>
          <b-modal ref="modal-edit">
            <template #modal-title>
            Alterando usuário
            </template>
            <div class="d-block">
              <form-user v-bind:user="user" type-data="atualizar"></form-user>
            </div>
          </b-modal>
          </card>
        </div>
      </div>
    </div>
  </div>
  
</template>
<script>
  import LTable from 'src/components/Table.vue'
  import Card from 'src/components/Cards/Card.vue'
  import FormUser from 'src/pages/UserProfile/Form.vue'
  import axios from 'axios';
  import Vue from 'vue';
  import VueSweetalert2 from 'vue-sweetalert2';
  Vue.use(VueSweetalert2);

  export default {
    components: {
      LTable,
      Card,
      FormUser
    },
    data () {
      return {
        profiles: [],
        user: []
      }
    },
    methods: {
      showModal(id) {
        console.log(id)
        this.$refs['modal-edit'].show()
        axios.get('http://192.168.10.22:4000/api/webservice/users/'+id)
        .then( response => {
          console.log(response)
          //this.user = response.data
        })
        .catch( error => {
          console.log(error)
        })
      },
      allUsers: function() {
        axios.get('http://192.168.10.22:4000/api/webservice/users')
        .then(response => {
          // handle success
          console.log(response.data)
          this.profiles = response.data
        })
        .catch(function (error) {
          // handle error
          console.log(error)
        });
      },
      showMsgBoxOne(id) {
        let axiosConfig = {
          headers: {
              'Content-Type': 'application/json',
              'Access-Control-Allow-Origin': '*',
              'X-Requested-With': 'XMLHttpRequest',
              'Access-Control-Allow-Origin': '*',
              'Access-Control-Allow-Methods': 'GET, POST, PATCH, PUT, DELETE, OPTIONS',
              'Access-Control-Allow-Headers': '*',
          }
        };
        console.log('clicou em excluir')
        //this.$refs['modal-1'].show()
        this.$bvModal.msgBoxConfirm('Deseja realmente excluir esse usuário?', {
          title: 'Excluir',
          size: 'sm',
          buttonSize: 'sm',
          okVariant: 'danger btn-fill',
          cancelVariant: 'primary btn-fill',
          okTitle: 'Sim, exluir',
          cancelTitle: 'Não, desistir',
          centered: false
        })
        .then( function (response) {
          // console.log(response)
          // console.log({id})
          
          axios.delete('http://192.168.10.22:4000/api/webservice/users/' + id,{
            headers: axiosConfig
          }).then(res => {
            console.log(res)
            //this.allUsers()
            Vue.swal({
              type: 'success',
              title: 'Sucesso',
              text: 'Usuário excluido.'
            });
            
          }).catch(erro => {
            console.log(erro)
          })
        })
        .catch(err => {
          // An error occurred
          console.log(err)
        })
      }
    },
    created() {
      this.allUsers()
    }
  }
</script>
<style>
</style>
