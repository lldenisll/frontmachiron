             <div class="md-layout md-alignment-center">
                <div class="card-expansion ">
                <md-card class="md-layout-item resumo " >

                  <md-card-media >
                    <img class="exame" :src="pacientes.imagem"  alt="People" >
                  </md-card-media>

                  <md-card-header>
                    <div class="md-title">{{pacientes.paciente_id}}</div>
                    <div class="md-subhead"> {{pacientes.numero_acesso}}</div>

                  </md-card-header>
                  <md-card-expand>
                    <md-card-actions md-alignment="space-between">
                      <md-card-expand-trigger>
                        <md-button class="md-icon-button">
                          <md-icon>keyboard_arrow_down</md-icon>
                        </md-button>
                      </md-card-expand-trigger>
                    </md-card-actions>

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