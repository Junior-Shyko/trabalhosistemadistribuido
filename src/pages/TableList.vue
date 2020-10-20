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
            <l-table class="table-hover table-striped table-sm"
                     :columns="table1.columns"
                     :data="table1.data">
            </l-table>
          </card>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import LTable from 'src/components/Table.vue'
  import Card from 'src/components/Cards/Card.vue'
  const tableColumns = ['Id', 'Name', 'Email', 'UserName', 'District', 'Acao']
  const tableData = [{
    id: 1,
    name: 'Dakota Rice',
    email: 'nataliaemily_@teo.com.br',
    username: 'Niger',
    district: 'Oud-Turnhout',
    acao: 'Editar | Excluir'
  },
  {
    id: 2,
    name: 'Minerva Hooper',
    email: 'nataliaemily_@teo.com.br',
    username: 'Curaçao',
    district: 'Sinaai-Waas',
    acao: 'Editar | Excluir'
  },
  {
    id: 3,
    name: 'Sage Rodriguez',
    email: 'nataliaemily_@teo.com.br',
    username: 'Netherlands',
    district: 'Baileux',
    acao: 'Editar | Excluir'
  },
  {
    id: 4,
    name: 'Philip Chaney',
    email: 'nataliaemily_@teo.com.br',
    username: 'Korea, South',
    district: 'Overland Park',
    acao: 'Editar | Excluir'
  },
  {
    id: 5,
    name: 'Doris Greene',
    email: 'nataliaemily_@teo.com.br',
    username: 'Malawi',
    district: 'Feldkirchen in Kärnten',
    acao: 'Editar | Excluir'
  }]
  export default {
    components: {
      LTable,
      Card
    },
    data () {
      return {
        table1: {
          columns: [...tableColumns],
          data: [...tableData]
        },
        table2: {
          columns: [...tableColumns],
          data: [...tableData]
        }
      }
    }
  }
</script>
<style>
</style>
