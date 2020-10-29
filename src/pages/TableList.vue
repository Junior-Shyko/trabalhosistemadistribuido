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
            <!-- <l-table class="table-hover table-striped table-sm"
                     :columns="table1.columns"
                     :data="table1.data">
            </l-table> -->
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
        
      }
    },
    methods: {
      allUsers: function() {
        axios.get('http://134.122.90.6:4000/api/webservice/users')
        .then(function (response) {
          // handle success
          console.log(response.data)
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
