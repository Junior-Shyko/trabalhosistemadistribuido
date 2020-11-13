<template>
  <card>
    <h4 slot="header" class="card-title">Cadastrar Usuário</h4>
    <form-user v-bind:user="user" type-data="cadastro"></form-user>
  </card>
</template>
<script>
  import Card from 'src/components/Cards/Card.vue'
  import Vue from 'vue';
  import VueSweetalert2 from 'vue-sweetalert2';
  import FormUser from 'src/pages/UserProfile/Form.vue'

  Vue.use(VueSweetalert2);

  export default {
    components: {
      Card,
      FormUser
    },
    data () {
      return {
        user: {
          userWebservice_id: '',
          userWebservice_username: '',
          userWebservice_email: '',
          userWebservice_name: '',
          userWebservice_lastname: '',
          userWebservice_address: '',
          userWebservice_number: '',
          userWebservice_complement: '',
          userWebservice_district: '',
          userWebservice_city: '',
          userWebservice_state: '',
          userWebservice_cep: '',
          userWebservice_avatar: ''
        }
      }
    }
  }

</script>
<style>

</style>
