<template>
  <card>
    <h4 slot="header" class="card-title">Cadastrar Usuário</h4>
    <form>
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
                    v-model="user.username">
          </base-input>
        </div>
        <div class="col-md-9">
          <base-input type="email"
                    label="E-mail"
                    placeholder="E-mail"
                    v-model="user.email">
          </base-input>
        </div>
      </div>

      <div class="row">
        <div class="col-md-6">
          <base-input type="text"
                    label="Nome"
                    placeholder="Nome"
                    v-model="user.firstName">
          </base-input>
        </div>
        <div class="col-md-6">
          <base-input type="text"
                    label="Sobre nome"
                    placeholder="Sobre Nome"
                    v-model="user.lastName">
          </base-input>
        </div>
        <div class="col-md-4">
          <base-input type="text"
                    label="C.E.P"
                    placeholder="cep local"
                    v-model="user.postalCode">
          </base-input>
        </div>
        <div class="col-md-8">
          <base-input type="text"
                    label="Endereço"
                    placeholder="Endereço"
                    v-model="user.address">
          </base-input>
        </div>
        <div class="col-md-3">
          <base-input type="text"
                    label="Número"
                    placeholder="número"
                    v-model="user.number">
          </base-input>
        </div>
        <div class="col-md-3">
          <base-input type="text"
                    label="Complemento"
                    placeholder="complemento"
                    v-model="user.complement">
          </base-input>
        </div>
        <div class="col-md-6">
          <base-input type="text"
                    label="Bairro"
                    placeholder="Bairro"
                    v-model="user.district">
          </base-input>
        </div>
        <div class="col-md-8">
          <base-input type="text"
                    label="Cidade"
                    placeholder="Cidade"
                    v-model="user.city">
          </base-input>
        </div>
        <div class="col-md-4">
          <base-input type="text"
                    label="Estado"
                    placeholder="Estado"
                    v-model="user.state">
          </base-input>
        </div>
        <div class="col-md-12">
          <base-input type="text"
                    label="Avatar"
                    placeholder="Url do avatar"
                    v-model="user.avatar">
          </base-input>
        </div>
      </div>
      <div class="text-center">
        <button type="submit" class="btn btn-info btn-fill float-right" @click.prevent="updateProfile">
          Cadastrar
          <i class="nc-icon nc-simple-add"></i>
          
        </button>
      </div>
      <div class="clearfix"></div>
    </form>
  </card>
</template>
<script>
  import Card from 'src/components/Cards/Card.vue'

  export default {
    components: {
      Card
    },
    data () {
      return {
        user: {
          company: 'Light dashboard',
          username: '',
          email: '',
          firstName: '',
          lastName: '',
          address: '',
          city: '',
          state: '',
          postalCode: '',
          avatar: ''
        }
      }
    },
    methods: {
      updateProfile () {
        alert('Cadastrar: ' + JSON.stringify(this.user))
      }
    }
  }

</script>
<style>

</style>
