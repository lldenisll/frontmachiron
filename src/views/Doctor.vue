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
                  <h3 class="title">Pessoa Legal</h3>
                  <h6>Radiologista</h6>
                </div>
              </div>
            </div>
          </div>
          
          <div class="profile-tabs">
            <tabs
              :tab-name="['Incluir Diagnóstico']"
              :tab-icon="['upload']"
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
      default: require("@/assets/img/radio.png")
    }
  },
    created() {
    this.initialize();
  },
  methods:{
  initialize() {
      axios.get(this.urlPaciente).then((response) => {
        this.paciente = response.data;
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
