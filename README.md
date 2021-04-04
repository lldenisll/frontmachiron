<h3 align="center">Machiron</h3>

  <p align="center">
    Aplicativo web para monitorar exames no formato DICOMN.
    <br />
     <a href="https://github.com/lldenisll/doctor_backend" target="blank"> To english, please check the back-end repository</a>
    <br />
    <a href="https://lldenisll.github.io/#/" target="blank">Abrir Front-end</a>
    ·
    <a href="https://github.com/lldenisll/doctor_backend" target="blank">Repositório Back-End</a>
   </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Sobre o projeto</h2></summary>
  <ol>
    <li>
      <a href="#sobre">Sobre</a>
      <ul>
        <li><a href="#tecnologias">Tecnologias</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
    </li>
    <li><a href="#tarefas">Tarefas</a></li>
    <li><a href="#próximos-passos">Próximos passos</a></li>
    <li><a href="#meu-contato">Contato</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## Sobre

Resumo das tarefas solicitadas. Stack utilizada: Python no backend com Django para criação de API. Banco de dados postgres. Matplotlib para criação de imagens dos exames. Pydicom para leitura dos arquivos DICOM e front-end utilizando vueJS e material UI kit.

### Tecnologias

* []() Python + Django + Django Rest Framework
* []() VueJS
* []() GitHub + Postgresql + Heroku



<!-- GETTING STARTED -->
## Getting Started

Para fazer uma cópia local

### Instalação back-end

1. Clone repository
   ```sh
   git clone https://github.com/lldenisll/doctor_backend
   ```
2. Create virtual env
   ```sh
   python3 -m venv /path/to/virtual/env
   ```
   3. Activate virtual env
   ```sh
   source/path/virtual/env/bin/activate
   ```
3. Instale os requerimentos 
   ```sh
   pip install requirements.txt
   ```
3. Make migrations
   ```sh
   python manage.py makemigrations
   python manage.py migrate
   ```
3. Run server!
   ```sh
   python manage.py runserver
   ```
### Instalação do Front-end 

1. Clone o repositório
   ```sh
   git clone https://github.com/lldenisll/frontmachiron
   ```
2. Instale npm 
   ```sh
   npm install
   ```
3. Run
   ```sh
   npm run serve
   ```
### Banco de dados
Caso queira uma cópia local com seu banco de dados, configura na pasta settings.py (para postgres) consulte se tiver dúvidas para utilizar o sqlite.
## Tarefas

Tarefa 01 - API feita com DJANGO REST FRAMEWORK para buscar nos exames DICOM o ID, idade e sexo do paciente e data do exame e espaçamento dos slices. Criação de script que percorrre todas as pastas de um diretório e cria um JSON file que pode ser carregado no banco de dados com as informações solicitadas para o exame DICOM. Script auxiliar que cria e salva as imagens com base no atributo pixel_array.

Tarefa 02 -Criação de model para cadastro de Paciente, que pode ser carregado com o script da tarefa 1 para carregar no banco de dados os dados que vem do arquivo DICOM, incluindo a imagem de um slice do exame. O model ainda inclui as informações de diagnóstico grau de severidade e normalidade. De forma que o pesquisador pode acessar o cadastro do paciente e incluir ou modificiar um diagnóstico.

Tarefa 03 - Elaboração de front-end com vueJS e utilizando um kit de UI para ajudar no processo. O front end consome as informações da API, e permite o cadastro e alteração de um diagnóstico para os exames já cadastrados. Traz um resumo de todos os exames com as principais informações. E uma tela que alerta para pacientes em estado grave ou sem diagnóstico preenchido.

## Próximos passos
Incluir opção do pesquisador fazer o upload de uma pasta contendo varios arquivos DICOM de um exame.
Nesse caso o backend usará o script para percorrer toda a pasta e coletar as informações mais relevantes.
Se relevante o script pode percorrer todos os arquivos da pasta e montar um gif com as imagens de cada slice

## Meu contato

Dênis Gonçalves dos Santos 
[![LinkedIn][linkedin-shield]][linkedin-url]



[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/denis142/

