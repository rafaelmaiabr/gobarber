<h1>Contrução do APP Gobarber <small>para fins de aprendizado</small></h1>

<strong>Criando a Estrutura</strong> Configuração via terminal
<ol>
  <li>Crie o projeto em um diretório. Ex.: Gobarber <pre>mkdir gobarber</pre></li>
  <li>Acesse o diretório <pre>cd gobarber</pre</li>
  <li>Inicialize o projeto <pre>yarn init -y</pre></li>
  <li>Abre o VSCode <pre>code .</pre></li>
</ol>

<strong>Dependencias utilizadas</strong>

<ol>
  <li><pre>yarn add express</pre></li>
  <li><pre>yarn add nodemon</pre></li>
  <li><pre>yarn add sucrase</pre>
  Para utilizar funções novas do js que o Node ainda não suporta como o Import e Export<br>
  Antes:
  <pre>const express = require('express');</pre>
  <pre>module.exports = new App().server;</pre>
  Depois:
  <pre>import express from 'express';</pre>
  <pre>export default new App().server;</pre>
  <i>Após alterar a chamada do import e export utilizar</i>
  <pre>yarn sucrase-node src/server.js</pre> ao invés de 
  <pre>node src/server.js</pre>
  </li>
</ol>
<hr>
<ol>
  <li>
  Verificar se código está seguindo padrões.
  <pre>
  yarn add eslint -D
  </pre>
  Configurando
  <pre>
  yarn eslint --init
  #Selecione as opções
  ? How would you like to use ESLint? == To check syntax, find problems, and enforce code style
  ? What type of modules does your project use? == JavaScript modules (import/export)
  ? Which framework does your project use? == None of these
  ? Does your project use TypeScript? == No
  ? Where does your code run? == Node
  ? How would you like to define a style for your project? == Use a popular style guide
  ? Which style guide do you want to follow? == Airbnb: https://github.com/airbnb/javascript
  ? What format do you want your config file to be in? == JavaScript
  </pre>
  </li>
</li>


<strong>Arquiterura</strong>

<ol>
  <li>SRC: Código manipulado no dia dia</li>
  <li>
    Roda o servidor
    <pre>yarn dev</pre>
    
  Roda o debug
    <pre>yarn dev:debug</pre>
  </li>
</ol>

------

<h2>Instalando o Docker <small>para a criação de ambientes isolados</small></h2>
<ol>
  <li>Download do Docker - SO <a href="https://docs.docker.com/install/linux/docker-ce/ubuntu/">Linux</a> | MAC</li>

  <li>Desinstale versões antigas do docker:
    <pre>sudo apt-get remove docker docker-engine docker.io containerd runc</pre>
  </li>
  <li>Atualize os pacotes do seu SO
    <pre>sudo apt-get update</pre>
  </li>
  <li>Instale as dependências
    <pre>sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common</pre>
  </li>
  <li>Adicione a chave CPG oficial do docker
    <pre>curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -</pre>
  </li>
  <li>Adicione o repositório
    <pre>
    sudo add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) \
    stable"
    </pre>
    <strong>Nota:</strong> Caso apresente o erro:
    <pre>Entrada mal formada, repositório não adicionado.</pre>
    Execute os comandos:
    <pre>
    sudo add-apt-repository "deb https://download.docker.com/linux/ubuntu bionic stable"
    sudo apt-get update
    sudo apt-get -y  install
    </pre>
    <br>
    Verifique se o Docker foi instalado: <pre>docker --version</pre>
  </li>
  <li> Permitindo o uso do docker sem a necessidade de SUDO
    <pre>
    sudo docker run hello-world
    sudo usermod -aG docker $USER
    newgrp docker

    # Teste se foi instalado corretamente
    docker run hello-world
   </pre>
  </li>  
</ol>
<i>Agradecimentos ao: <a href="Thiagohttps://github.com/thlindustries/desafios-gostack10-rocketseat/"> Thiago</a>, Renata e Mailson Garcia pelo apoio e ajuda através do Discord.</i>
<h2>Etapas Docker pós instalação no <a href="https://docs.docker.com/install/linux/linux-postinstall/">LINUX</a> para não usar a opção SUDO</h2>
<ol>
  <li>Gerenciar o Docker como um usuário não raiz
  <pre>
  sudo groupadd docker
  sudo usermod -aG docker $USER
  newgrp docker
  docker run hello-world
  </pre></li>
  <li>Configure o Docker para iniciar na inicialização.<br>
  Ativar: <pre>sudo systemctl enable docker</pre><br>
  Desativar: <pre>sudo systemctl disable docker</pre>
  </li>
</ol>

<hr>
<h1>Criando conteiners - Docker</h1>

<ol>
  <li>Criação do Postgress
  <pre>docker run --name database -e POSTGRES_PASSWORD=docker -p 5432:5432 -d postgres</pre>
  <i>Cria conteiner: Senha docker, alterna porta 5432 p/ 5432</i>
  </li>
  <li>Principais comandos:
  <pre>
  #Visualizar conteiners em execução
  docker ps
  
  #Lisar todos os conteiners
  docker ps -a
  
  #forçar parada de um conteiner
  docker stop database
  
  #iniciar conteiner utilizando nome ou ID. Ex. utilziando nome
  docker start database

  #Visualizar erros utilizar ( nome ou ID) do conteiner
  docker logs database

  </pre></li>
</ol>

<h1>Interface para visualizar bases Postgres - <a href="">POSTBIRD</a></h1>
Instalação via terminal: <pre>sudo snap install postbird</pre>

<h1>Conceito MVC</h1>
Model, View e Controller
<pre>
//ESTRUTURA DE UM CONTROLLER
class UserController {
  index() { }//Lista de usuários
  show() { }//Exibir um único usuário
  store() { }//Cadastrar usuário
  update() { }//Alterar usuário
  delete() { }//Remover usuário
}
</pre>

<h1>Definindo um padrão de código</h1>

