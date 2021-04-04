<template>
  <div class="wrapper">
    <parallax class="section page-header header-filter" :style="headerStyle">
      <div class="container">
        <div class="md-layout">
          <div
            class="md-layout-item md-size-50 md-small-size-70 md-xsmall-size-100"
          >
            <h1 class="title">Acompanhe seus pacientes.</h1>
            <h4>
              Cadastre diagnóstico de seus pacientes de forma simples e 
              rápida. Sincronize com os exames radiológicos. Veja tudo no 
              mesmo lugar
            </h4>
            <br />
            <md-button
              href="http://127.0.0.1:8081/#/profile"
              class="md-success md-lg"
              ><i class="fas fa-stethoscope"></i> Entre agora</md-button
            >
          </div>
        </div>
      </div>
    </parallax>
    <div class="main main-raised">
      <div class="section">
        <div class="container">
          <div class="md-layout">
            <div
              class="md-layout-item md-size-66 md-xsmall-size-100 mx-auto text-center"
            >
              <h2 class="title text-center">O que esperar</h2>
              <h5 class="description">
                Resumo das tarefas solicitadas. Stack utilizada: Python no backend com Django para criação de API. 
                Banco de dados postgres. Matplotlib para criação de imagens dos exames.
                Pydicom para leitura dos arquivos DICOM e front-end utilizando vueJS e material UI kit. 
              </h5>
              
            </div>
          </div>
          <div class="features text-center">
            <div class="md-layout">
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="info">
                  <div class="icon icon-info">
                    <i class="fas fa-list"></i>
                  </div>
                  <h4 class="info-title">Tarefa 1</h4>
                  <p>
                    API feita com DJANGO REST FRAMEWORK para buscar nos exames DICOM o ID, 
                    idade e sexo do paciente e data do exame e espaçamento dos slices. Criação de script que percorrre
                    todas as pastas de um diretório e cria um JSON file que pode ser carregado no banco de dados com as informações solicitadas para o exame DICOM. 
                    Script auxiliar que cria e salva as imagens com base no atributo pixel_array.

                  </p>
                </div>
              </div>
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="info">
                  <div class="icon icon-success">
                    <i class="fa fa-database"></i>
                  </div>
                  <h4 class="info-title">Tarefa 2</h4>
                  <p>
                    Criação de model para cadastro de Paciente, que pode ser carregado com o script da tarefa 1 para carregar no banco de dados
                    os dados que vem do arquivo DICOM, incluindo a imagem de um slice do exame. O model ainda inclui as informações de diagnóstico
                    grau de severidade e normalidade. De forma que o pesquisador pode acessar o cadastro do paciente e incluir ou modificiar um diagnóstico.
                  </p>
                </div>
              </div>
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="info">
                  <div class="icon icon-danger">
                    <i class="fa fa-chart-pie"></i>
                  </div>
                  <h4 class="info-title">Tarefa 3</h4>
                  <p>
                    Elaboração de front-end com vueJS e utilizando um kit de UI para ajudar no processo. 
                    O front end consome as informações da API, e permite o cadastro e alteração de um diagnóstico 
                    para os exames já cadastrados. Traz um resumo de todos os exames com as principais informações. 
                    E uma tela que alerta para pacientes em estado grave ou sem diagnóstico preenchido.
                  </p>
                </div>
              </div>
            </div>
              <h2 class="title text-center">Próximos passos</h2>
              <h5 class="description">
                Incluir opção do pesquisador fazer o upload de uma pasta contendo varios arquivos DICOM de um exame. <br>
                Nesse caso o backend usará o script para percorrer toda a pasta e coletar as informações mais relevantes. <br>
                Se relevante o script pode percorrer todos os arquivos da pasta e montar um gif com as imagens de cada slice 
              </h5>
          </div>
          
        </div>
        
      </div>
      
      <div class="section text-center">
        <div class="container">
          <h2 class="title">Nossa equipe</h2>
          <div class="team">
            <div class="md-layout">
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="team-player">
                  <md-card class="md-card-plain">
                    <div class="md-layout-item md-size-50 mx-auto">
                      <img
                        :src="teamImg1"
                        alt="Thumbnail Image"
                        class="img-raised rounded-circle img-fluid"
                      />
                    </div>
                    <h4 class="card-title">
                      Dênis Gonçalves
                      <br />
                      <small class="card-description text-muted">Desenvolvedor</small>
                    </h4>

                    <md-card-content>
                      <p class="card-description">
                        Atuo como desenvolvedor no projeto, tanto do back-end como do front-end. Responsável pelo deploy e manutenção.
                        Aspirante a cientista de dados, estudante dedicado de estatística e algortimos de machine learning.
                      </p>
                    </md-card-content>

                    <md-card-actions class="text-center">
                      <md-button
                        href="https://www.linkedin.com/in/denis142/"
                        target="blank"
                        class="md-just-icon md-simple"
                      >
                        <i class="fab fa-linkedin"></i>
                      </md-button>
                      <md-button
                        href="https://github.com/lldenisll/doctor_backend"
                        class="md-just-icon md-simple"
                        target="blank"
                      >
                        <i class="fab fa-github"></i>
                      </md-button>
                    </md-card-actions>
                  </md-card>
                </div>
              </div>
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="team-player">
                  <md-card class="md-card-plain">
                    <div class="md-layout-item md-size-50 mx-auto">
                      <img
                        :src="teamImg2"
                        alt="Thumbnail Image"
                        class="img-raised rounded-circle img-fluid"
                      />
                    </div>
                    <h4 class="card-title">
                      Lais Leite
                      <br />
                      <small class="card-description text-muted"
                        >Companheira</small
                      >
                    </h4>

                    <md-card-content>
                      <p class="card-description">
                        Deu a maior força e cuidou da casa nos dias que fiz a atividade para que 
                        eu pudesse me concentrar somente nisso. E me ouviu falando sozinho por horas 
                      </p>
                    </md-card-content>


                  </md-card>
                </div>
              </div>
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="team-player">
                  <md-card class="md-card-plain">
                    <div class="md-layout-item md-size-50 mx-auto">
                      <img
                        :src="teamImg3"
                        alt="Thumbnail Image"
                        class="img-raised rounded-circle img-fluid"
                      />
                    </div>
                    <h4 class="card-title">
                      Amora 
                      <br />
                      <small class="card-description text-muted">Cachorra</small>
                    </h4>

                    <md-card-content>
                      <p class="card-description">
                        Me faz levantar para levar ela dar uma volta e ativar a circulação. Também me ouve falando sozinho por horas. 
                      </p>
                    </md-card-content>
                  </md-card>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
 
    </div>
  </div>
</template>

<script>
export default {
  bodyClass: "landing-page",
  props: {
    header: {
      type: String,
      default: require("@/assets/img/chiron.jpeg")
    },
    teamImg1: {
      type: String,
      default: require("@/assets/img/denis.jpg")
    },
    teamImg2: {
      type: String,
      default: require("@/assets/img/lais.jpeg")
    },
    teamImg3: {
      type: String,
      default: require("@/assets/img/amora.jpg")
    }
  },
  data() {
    return {
      name: null,
      email: null,
      message: null
    };
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.header})`
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.md-card-actions.text-center {
  display: flex;
  justify-content: center !important;
}
.contact-form {
  margin-top: 30px;
}

.md-has-textarea + .md-layout {
  margin-top: 15px;
}
</style>
