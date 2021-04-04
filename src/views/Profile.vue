/* eslint-disable prettier/prettier */
/* eslint-disable prettier/prettier */
<template>
  <div class="wrapper">
    <parallax
      class="section page-header header-filter"
      :style="headerStyle"
    ></parallax>
    <div class="main main-raised">
      <div class="section profile-content">
        <div class="container">
          <div class="md-layout">
            <div class="md-layout-item md-size-50 mx-auto">
              <div class="profile">
                <div class="avatar">
                  <img
                    :src="img"
                    alt="Circle Image"
                    class="img-raised rounded-circle img-fluid"
                  />
                </div>
                <div class="name">
                  <h3 class="title">Ana Ciconelle</h3>
                  <h6>Pesquisadora</h6>
                </div>
              </div>
            </div>
          </div>
          
          <div class="profile-tabs">
            <tabs
              :tab-name="['Incluir Diagnóstico', 'Exames DICOM', 'Resumo exames','Resumo pacientes']"
              :tab-icon="['upload', 'folder', 'dashboard','favorite']"
              plain
              nav-pills-icons
              color-button="success"
            >
              <!-- here you can add your content for tab-content -->
              <template slot="tab-pane-1">
                <form class="md-layout md-alignment-center">
                <md-card class="md-layout-item md-size-50 md-small-size-50">
                  <md-card-header>
                    <div class="md-title" style="margin-left: 2rem">Informações adicionais ao exame (Tarefa 2) </div>
                  </md-card-header>
                  <md-card-content>
                        <select v-model="paciente.paciente_id"  class="md-layout-item">
                          <option value="" disabled selected>Escolha um paciente</option>
                          <option v-for="pacientes in paciente" :key="pacientes.paciente_id" :value="pacientes.paciente_id">{{ pacientes.paciente_id }}</option>
                        </select> <br>
                        <label for="diagnostico">Diagnóstico</label> <br>
                        <md-radio v-model="paciente.diagnostico" value="pneumonia">Pneumonia</md-radio>
                        <md-radio v-model="paciente.diagnostico" value="tuberculose">Tuberculose</md-radio>
                        <md-radio v-model="paciente.diagnostico" value="normal">Normal</md-radio> <br>
                        <label for="grau_de_severidade">Grau de Severidade</label> <br>
                        <md-radio v-model="paciente.grau_de_severidade" value="grave">Grave</md-radio>
                        <md-radio v-model="paciente.grau_de_severidade" value="moderado">Moderado</md-radio>
                        <md-radio v-model="paciente.grau_de_severidade" value="leve">Leve</md-radio>
                        <md-radio v-model="paciente.grau_de_severidade" value="ausente">Ausente</md-radio><br>
                        <label for="nivel_de_normalidade">Nível de normalidade</label> <br>
                        <md-radio v-model="paciente.nivel_de_normalidade" value="tipico">Típico</md-radio>
                        <md-radio v-model="paciente.nivel_de_normalidade" value="atipico">Atípico</md-radio>
                        <md-card-actions>
                          <md-button @click="enviaDiagnostico()" class="md-primary md-round"><md-icon >archive</md-icon> Incluir Diagnóstico</md-button>
                        </md-card-actions>

                  </md-card-content>
                </md-card>
                </form>

              </template>
              <template slot="tab-pane-2">
                <div class="md-layout">
                  <md-table  v-model="paciente" md-card>
                    <md-table-toolbar>
                      <h1 class="md-title" style="color:gray !important">Lista de pacientes (Tarefa 1)</h1>
                    </md-table-toolbar>
                    <md-table-row slot="md-table-row" slot-scope="{ item }">
                      <md-table-cell md-label="ID" md-sort-by="paciente_id" >{{ item.paciente_id }}</md-table-cell>
                      <md-table-cell md-label="Genero" md-sort-by="paciente_sexo">{{ item.paciente_sexo }}</md-table-cell>
                      <md-table-cell md-label="Número Acesso" md-sort-by="numero_acesso">{{ item.numero_acesso }}</md-table-cell>
                      <md-table-cell md-label="Data" md-sort-by="data_estudo">{{ item.data_estudo }}</md-table-cell>
                      <md-table-cell md-label="Espaçamento dos Slices" md-sort-by="espacamento_slice">{{ item.espacamento_slice }}</md-table-cell>
                    </md-table-row>
                  </md-table>

                </div>
              </template>
              <template slot="tab-pane-3">
              <h4 class="info-title">Tarefa 3</h4>
              <div class="md-layout">
              <div v-for="pacientes in paciente" :key="pacientes" >
                <div class="md-layout-item">
                  <div class="card-expansion">
                  <md-card class = "md-card-exam" >
                    <md-card-media>
                      <img :src="pacientes.imagem" alt="People">
                    </md-card-media>

                    <md-card-header>
                      <div class="md-title">{{pacientes.paciente_id}}</div>
                      <div class="md-subhead">{{pacientes.numero_acesso}}</div>
                    </md-card-header>
                    <md-card-expand>
                        <md-card-expand-trigger>
                          <md-button class="md-icon-button">
                            <md-icon>keyboard_arrow_down</md-icon>
                          </md-button>
                        </md-card-expand-trigger>
                      <md-card-expand-content>
                        <md-card-content>
                        Gênero: {{pacientes.paciente_sexo}} <br>
                        Data do estudo: {{pacientes.data_estudo}} <br>
                        Espaçamento do slice: {{pacientes.espacamento_slice}} mm <br>
                        <p v-if="! pacientes.diagnostico">
                          Exame adicional não cadastrado
                        </p>
                        <p v-else-if="pacientes.diagnostico == 'normal'">
                          Paciente com diagnóstico Normal
                        </p>
                        <p v-else>
                        Paciente com diagnóstico {{pacientes.diagnostico}} em grau {{pacientes.grau_de_severidade}} e nível de normalidade considerado {{pacientes.nivel_de_normalidade}} <br>
                        </p>    
                        </md-card-content>
                      </md-card-expand-content>
                    </md-card-expand>
                  </md-card>
                  </div>
                </div>
              </div>
            </div>    
              </template>
        
              <template slot="tab-pane-4">
              <h4 class="info-title">Tarefa 3</h4>
             <div class="card">
             <i class="fa fa-clipboard">
               {{paciente.length}}
             </i>

               <h1>
               exames DICOM
               </h1>
             </div>
              <div class="card">
             <i class="fa fa-stethoscope">
               {{tuberculose}}
             </i>

               <h1>
              com tuberculose
               </h1>

             </div>
              <div class="card">
              <i class="fa fa-stethoscope">            
                {{pneumonia}}
             </i>

               <h1>
               com pneumonia
               </h1>

             </div>

                <div  v-for="pacientes in paciente" :key="pacientes" >
              <div v-if="pacientes.grau_de_severidade == 'grave' "> 
              <div class="alert alert-danger">
                <div class="container">
                  <div class="alert-icon">
                    <md-icon>info_outline</md-icon>
                  </div>
                  <b> Paciente {{pacientes.paciente_id}} </b> :com diagnostico de {{pacientes.diagnostico}} em estado grave!
              </div>
              </div>
              </div>
              <div v-else-if="!pacientes.diagnostico">
                <div class="alert alert-sucess">
                 <div class="container">
                  <div class="alert-icon">
                    <md-icon>info_outline</md-icon>
                  </div>
                  <b> Paciente {{pacientes.paciente_id}} </b> : sem diagnóstico
              </div>
              </div>
              </div>
              <div v-else-if="pacientes.diagnostico == 'normal'">
                <div class="alert alert-info">
                 <div class="container">
                  <div class="alert-icon">
                    <md-icon>info_outline</md-icon>
                  </div>
                  <b> Paciente {{pacientes.paciente_id}} </b> : com diagnóstico normal
              </div>
              </div>
              </div>
              <div v-else>
                <div class="alert alert-warning">
                 <div class="container">
                  <div class="alert-icon">
                    <md-icon>info_outline</md-icon>
                  </div>
                  <b> Paciente {{pacientes.paciente_id}} </b> :com diagnostico de {{pacientes.diagnostico}} em estado {{pacientes.grau_de_severidade}}
              </div>
              </div>
              </div>


              </div>  
              </template>

            </tabs>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Tabs } from "@/components";
import axios from "axios";

export default {
  name: 'LayoutHorizontalColumns',
  components: {
    Tabs
  },
  bodyClass: "profile-page",
  data() {
    return {
      urlPaciente: "https://glacial-ravine-66808.herokuapp.com/api/paciente/",
      tuberculose:0,
      pneumonia:0,
      paciente: [
        {
          paciente_id: '',
          paciente_sexo: '',
          numero_acesso: '',
          data_estudo: '',
          espacamento_slice: '',
          imagem:'',
          diagnostico:'',
          grau_de_severidade:'',
          nivel_de_normalidade:''
        },
      ],
  };
  },
  props: {
    header: {
      type: String,
      default: require("@/assets/img/header.jpeg")
    },
    img: {
      type: String,
      default: require("@/assets/img/the-researcher.png")
    }
  },
    created() {
    this.initialize();
  },
  methods:{
  initialize() {
    this.tuberculose = 0
    this.pneumonia = 0
      axios.get(this.urlPaciente).then((response) => {
        this.paciente = response.data;
        for(var i = 0; i<this.paciente.length; i++){
          if(this.paciente[i].diagnostico == 'tuberculose'){
            this.tuberculose+=1
            console.log(this.tuberculose)
          }
          else if(this.paciente[i].diagnostico == 'pneumonia'){
            this.pneumonia+=1
            console.log(this.pneumonia)
          }
        }
      }); 
    },
  enviaDiagnostico(){
    axios
    .put(this.urlPaciente+this.paciente.paciente_id+'/',{
      diagnostico: this.paciente.diagnostico,
      grau_de_severidade: this.paciente.grau_de_severidade,
      nivel_de_normalidade: this.paciente.nivel_de_normalidade,
    })
    .then((response) => {
      alert('cadastrado com sucesso')
      this.paciente.paciente_id = ''
      this.paciente.diagnostico = ''
      this.paciente.grau_de_severidade = ''
      this.paciente.nivel_de_normalidade = ''
      this.initialize()
    })
    .catch((e) => {
          console.log(e);
        });
  }
    },
    
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.header})`
      };
    },
  }
};

</script>

<style lang="scss" scoped>
  .card-expansion {
    height: 530px;
  }
.card {
  display: inline-block;
  height: 160px;
  margin: 1rem;
  position: relative;
  width: 300px;
  background: #9b27b0af;
  text-align: center;
  border-radius: 14px;
  margin-bottom: 4rem;

}

.card h1{
  color: whitesmoke;
  font-size: 2rem;
  
}
.card i{
  padding-top: 10px;
  color:whitesmoke;
  font-size: 5rem;

}
  .dash-header{
    height: 100px;
  }
  .dash {
    width: 320px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
  }
  .md-card-exam {
    width: 320px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
  }
.section {
  padding: 0;
}

.resumo{
  width: 400px;
}

.profile-tabs::v-deep {
  .md-card-tabs .md-list {
    justify-content: center;
  }

  [class*="tab-pane-"] {
    margin-top: 3.213rem;
    padding-bottom: 50px;

    img {
      margin-bottom: 2.142rem;
    }
  }
}
</style>
