<template>
  <div>
      <v-col
          cols="12"
        >
          <v-text-field
            v-model="campoInput"
            label="Digite uma tarefa para lista"
            outlined
            clearable
            @keyup.enter="handleAddTarefa"
          ></v-text-field>
        </v-col>

    <v-list
      flat
      subheader
    >

      <v-list-item-group
        multiple
        active-class=""
      >

      <div v-for="tarefa, index in tarefas"
      :key="index">

      <Tarefa 
      :tarefa="tarefa"
      />
      </div>

      </v-list-item-group>
    </v-list>
  </div>  
</template>

<script>
import Tarefa from '../components/tarefas/Tarefa.vue'
  export default {
    name: 'Home',

    components: {
      Tarefa
    },
    data(){
      return {
        campoInput:null,
        tarefas:[
          {titulo:"Teste", concluido:false },
          {titulo:"Teste2", concluido:false },
          {titulo:"Teste3", concluido:false },
      ]
    }
  },
    methods: {
      handleAddTarefa() {
        if(this.campoInput){
          this.tarefas.push({
            titulo:this.campoInput,
            concluido:false
            })
          this.campoInput = null;
      }
    }
  }
}
</script>