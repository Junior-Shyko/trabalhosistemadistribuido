<template>
    <form ref="form">
      <div class="row">
        <!-- <div class="col-md-5">
          <base-input type="text"
                    label="Company"
                    :disabled="true"
                    placeholder="Light dashboard"
                    v-model="user.company">
          </base-input>
        </div> -->
        <div class="col-md-3">
          <base-input type="text"
                    label="Username"
                    placeholder="Username"
                    v-model="user.userWebservice_username">
          </base-input>
        </div>
        <div class="col-md-9">
          <base-input type="email"
                    label="E-mail"
                    placeholder="E-mail"
                    v-model="user.userWebservice_email">
          </base-input>
        </div>
      </div>

      <div class="row">
        <div class="col-md-6">
          <base-input type="text"
                    label="Nome"
                    placeholder="Nome"
                    v-model="user.userWebservice_name">
          </base-input>
        </div>
        <div class="col-md-6">
          <base-input type="text"
                    label="Sobre nome"
                    placeholder="Sobre Nome"
                    v-model="user.userWebservice_lastname">
          </base-input>
        </div>
        <div class="col-md-4">
          <base-input type="text"
                    label="C.E.P"
                    placeholder="cep local"
                    v-model="user.userWebservice_cep">
          </base-input>
        </div>
        <div class="col-md-8">
          <base-input type="text"
                    label="Endereço"
                    placeholder="Endereço"
                    v-model="user.userWebservice_address">
          </base-input>
        </div>
        <div class="col-md-3">
          <base-input type="text"
                    label="Número"
                    placeholder="número"
                    v-model="user.userWebservice_number">
          </base-input>
        </div>
        <div class="col-md-3">
          <base-input type="text"
                    label="Complemento"
                    placeholder="complemento"
                    v-model="user.userWebservice_complement">
          </base-input>
        </div>
        <div class="col-md-6">
          <base-input type="text"
                    label="Bairro"
                    placeholder="Bairro"
                    v-model="user.userWebservice_district">
          </base-input>
        </div>
        <div class="col-md-8">
          <base-input type="text"
                    label="Cidade"
                    placeholder="Cidade"
                    v-model="user.userWebservice_city">
          </base-input>
        </div>
        <div class="col-md-4">
          <base-input type="text"
                    label="Estado"
                    placeholder="Estado"
                    v-model="user.userWebservice_state">
          </base-input>
        </div>
        <div class="col-md-12">
          <base-input type="text"
                    label="Avatar"
                    placeholder="Url do avatar"
                    name="userWebservice_avatar"
                    v-model="user.userWebservice_avatar">
          </base-input>
        </div>
        <div class="col-md-12">
          <base-input type="text"
                    label="Id"
                    name="userWebservice_id"
                    v-model="user.userWebservice_id">
          </base-input>
        </div>
      </div>
      <div class="text-center">
        <div v-if="typeData == 'cadastro'">
          <button type="submit" class="btn btn-primary btn-fill float-right" @click.prevent="createProfile">
            cadastrar
            <i class="fa fa-save"></i>
          </button>
        </div>
        <div v-else>
            <button type="submit" class="btn btn-primary btn-fill float-right" @click.prevent="updateProfile">
            Atualizar
            <i class="fa fa-edit"></i>
        </button>
        </div>
        
      </div>
      <div class="clearfix"></div>
    </form>
</template>

<script>
  import axios from 'axios';
  import Vue from 'vue';
  import VueSweetalert2 from 'vue-sweetalert2';
export default {
    props:['user', 'typeData'],
    methods: {
      createProfile () {
        // alert('Cadastrar: ' + JSON.stringify(this.user))
        axios.post('http://192.168.10.22:4000/api/webservice/users',{
            userWebservice_username: this.user.userWebservice_username,
            userWebservice_email: this.user.userWebservice_email,
            userWebservice_name: this.user.userWebservice_name,
            userWebservice_lastname: this.user.userWebservice_lastname,
            userWebservice_address: this.user.userWebservice_address,
            userWebservice_complement: this.user.userWebservice_complement,
            userWebservice_number: this.user.userWebservice_number,
            userWebservice_district: this.user.userWebservice_district,
            userWebservice_city: this.user.userWebservice_city,
            userWebservice_state: this.user.userWebservice_state,
            userWebservice_cep: this.user.userWebservice_cep,
            userWebservice_avatar: this.user.userWebservice_avatar
        })
        .then(response => {
            console.log(response)
            this.clearUser()
            Vue.swal({
              type: 'success',
              title: 'Sucesso',
              text: 'Usuário cadastrado.'
            });
        })
        .catch(error => {
            console.log(error)
        })
      },
      updateProfile () {
        console.log(this.user.userWebservice_id)
        axios({
          method: 'PUT',
          url: 'http://192.168.10.22:4000/api/webservice/users/'+this.user.userWebservice_id,
          data: {
            userWebservice_username: this.user.userWebservice_username,
            userWebservice_email: this.user.userWebservice_email,
            userWebservice_name: this.user.userWebservice_name,
            userWebservice_lastname: this.user.userWebservice_lastname,
            userWebservice_address: this.user.userWebservice_address,
            userWebservice_complement: this.user.userWebservice_complement,
            userWebservice_number: this.user.userWebservice_number,
            userWebservice_district: this.user.userWebservice_district,
            userWebservice_city: this.user.userWebservice_city,
            userWebservice_state: this.user.userWebservice_state,
            userWebservice_cep: this.user.userWebservice_cep,
            userWebservice_avatar: this.user.userWebservice_avatar
          }
        })
        .then( response => {
          Vue.swal({
            type: 'success',
            title: 'Sucesso',
            text: 'Dados do usuário alterado.'
          });
          this.$refs['modal-edit'].hide()
        })
        .catch( error => {
          Vue.swal({
            type: 'error',
            title: 'Erro',
            text: 'Ocorreu um erro inesperado'
          });
        });
      },
      clearUser() {
        this.user.userWebservice_username = '';
        this.user.userWebservice_email = '';
        this.user.userWebservice_name = '';
        this.user.userWebservice_lastname = '';
        this.user.userWebservice_address = '';
        this.user.userWebservice_number = '';
        this.user.userWebservice_complement = '';
        this.user.userWebservice_district = '';
        this.user.userWebservice_city = '';
        this.user.userWebservice_state = '';
        this.user.userWebservice_cep = '';
        this.user.userWebservice_avatar = '';
      }
    },
    created() {
        console.log(this.user);
        console.log(this.typeData);
    }
}
</script>

<style>

</style>