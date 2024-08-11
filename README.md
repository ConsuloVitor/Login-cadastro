<h1 align="center">Cadastro & Login <img alt="Principal linguagem do Github" src="https://img.shields.io/github/languages/top/ESChrystian/login-cad?color=56BEB8"/>
  <img alt="Contagem de linguagens no Github" src="https://img.shields.io/github/languages/count/ESChrystian/login-cad?color=56BEB8"/>
  <img alt="Tamanho do repositório" src="https://img.shields.io/github/repo-size/ESChrystian/login-cad?color=56BEB8"/>
 <img alt="Estrelas no Github" src="https://img.shields.io/github/stars/ESChrystian/login-cad?color=56BEB8" /></h1>
<p align=center>Validações e Array </p>

<h4 align="center"> 
	🚧  Login Cad 🚀 Em construção...  🚧
</h4> 
<hr>
<p>
  
  [Sobre](#sobre)  &#xa0; | &#xa0; [Funcionalidades](#sparkles-funcionalidades-do-código) &#xa0; | &#xa0; [Funcões](#-funcionalidades-das-funções) &#xa0; |  &#xa0; [Tecnologias](#rocket-tecnologias) &#xa0;  | &#xa0; [Requisitos](#white_check_mark-requisitos-para-instalação) &#xa0; 
  | &#xa0; [Clonar Repositório](#rocket-tecnologias) &#xa0; | [Início](#checkered_flag-início) |
  &#xa0; [Autor](#autor)
  
 
</p>

<br>

## Sobre
 
Após explicações sobre os conceitos de Array, funções e exemplos de fácil compreendimento pelo Professor de Desenvolvimento Web [Leonardo Rocha](https://github.com/leonardossrocha), O "Projeto de cadastro de usuários" foi lançado no Tems, plataforma de reuniões e entregas de arquivos com foco no mercado de trabalho, o trabalho consiste nas validações de formulário, criação de banco de dados no formato de Array e a documentação de todo processo criativo, utlizando as linguagens JavaScript, Html e Css. 

## :sparkles: Funcionalidades do Código

 ✔️ **Verificação de Campos Obrigatórios;**
 
 ✔️ **Mensagens de Erro Personalizadas;**
 
 ✔️ **Armazenamento Temporário de Dados;**
 
 ✔️ **Listagem Dinâmica de Dados;**

 ✔️ **Reuso de Código;**

 ✔️ **Animações Simples e Transições.**

## 🧾: Funcionalidades das Funções

**1. Função acessar()**
> Objetivo: Valida os campos de e-mail e senha na tela de login.

> Descrição:
> Verifica se os campos de login foram preenchidos.
> Se algum campo estiver vazio, exibe um alerta pedindo para que todos os campos sejam preenchidos.
> Caso todos os campos estejam preenchidos, a tela de login é deslocada para cima, e a tela de cadastro é centralizada na tela.

```
 // VALIDAR ACESSO EM TELA DE LOGIN

  function acessar() { // CRIA UMA FUNÇÃO  QUE VALIDA O QUE FOI ESCRITO NOS CAMPOS DE LOGIN
    let loginEmail = document.getElementById("loginEmail").value;
    let loginSenha = document.getElementById("loginSenha").value;

    if (!loginEmail || !loginSenha) {
        alert("Favor preencher todos os campos"); // Mostra Pop-up caso usuário não preencha corretamente os campos de Login.
    } else {
        // Após a validação do login, os formulários se movem...
        // Formulário de Login
        let login = document.getElementById("formLogin"); 
        // Formulário de cadastro
        let cadastro = document.getElementById("formCad"); 
        login.style.top = "-500px"; //1° etapa: formulário de Login sai da tela
        cadastro.style.left = "0" //2° etapa: formulário de cadastro se move ao centro da tela

    }
} 
```
#

**2. Função salvarUser()**
> Objetivo: Armazenar o nome do usuário em um array quando o cadastro é realizado.

> Descrição:
> Captura o valor do campo "nome do usuário" na tela de cadastro.
> Se o campo estiver preenchido, o nome é adicionado a um array (dadosLista).
> Após o envio, a função criaLista() é chamada para atualizar a lista de usuários exibida na tela.
> Se o campo não estiver preenchido, uma mensagem de alerta é exibida.
```
var dadosLista = []; //Array
var alert = document.getElementById("alert"); // Mensagem de Span, variavel utilizada nas funcões salvarUser e editar
var h6 = document.getElementById("text");
// FUNÇÃO QUE ARMAZENA EM ARRAY NOME NA TELA DE CADASTRO
function salvarUser() {
    let nomeUser = document.getElementById("nomeUser").value; // Pega valor do input digitado pelo usuário

    if (nomeUser) { //Se existe valor digitado pelo user

        dadosLista.push(nomeUser); // Adiciona valor ao array
        criaLista(); // Inicia a funcão cria lista
        document.getElementById("nomeUser").value = ""; // Após envio do campo de Login, o input fica vazio
        alert.innerHTML = ""; //Div onde fica mensagem de aviso fica vazia
        h6.style.display = "none";
    } else {
        // alert("Favor informar o nome para cadastro"); // Caso o usuário não preencha o campo ele aparecera um Pop-up para preenchimento completo do cadastro.
        alert.style.color = "red";
        alert.innerHTML = "Preencha o formulário de cadastro";
    }

}

```
#

**3. Função criaLista()**
> Objetivo: Gerar uma tabela dinâmica de usuários cadastrados.

> Descrição:
> Cria uma tabela que exibe os nomes dos usuários cadastrados no array.
> Para cada nome no array, uma nova linha é adicionada à tabela, contendo o nome do usuário e botões para "Editar" e "Excluir".

```
/ FUNÇÃO QUE CRIA LISTA DE USUÁRIOS

// <td> = criar a coluna | <tr> = criar a linha |<th> = cabeçalho da tabela| += = oque estiver dentro da tabela fica, mais adiciona mais algum item há tabela.

function criaLista() {
    let tabelaDesign = document.getElementById("tabela"); //Variável para personalização da tabela
    // Estrutura da tabela que receberá dados dos usuários
    let tabela = document.getElementById("tabela").innerHTML = "<tr><th>Nome Usuário</th><th>Ações</th></tr>"; 
    for (let i = 0; i <= (dadosLista.length - 1); i++) {
        tabelaDesign.style.backgroundColor = "#ffff";
        tabela += "<tr><td>" + dadosLista[i] + "</td><td><button type='button' onclick='editar(parentNode.parentNode.rowIndex)'>Editar</button><button type='button' onclick='excluir(parentNode.parentNode.rowIndex)'>Excluir</button></td></tr>";
        document.getElementById("tabela").innerHTML = tabela;

    }

}
```
#

**4. Função editar(i)**
> Objetivo: Permitir a edição do nome de um usuário na lista.

> Descrição:
> Preenche o campo de nome do usuário com o valor atual do nome selecionado na tabela.
> Remove o nome do array, permitindo que seja substituído por um novo valor.
```
// FUNÇÃO PARA EDITAR NOMES DE LISTA
function editar(i) {
    document.getElementById("nomeUser").value = dadosLista[(i - 1)]; dadosLista.splice(dadosLista[(i - 1)], 1);
    alert.innerHTML = "";

}
```
#
**5. Função excluir(i)**
> Objetivo: Excluir um nome da lista de usuários.

> Descrição:
> Remove o nome do usuário correspondente no array e também a linha correspondente na tabela.
``` 
// FUNÇÃO QUE EXCLUI NOME DA LISTA
function excluir(i) { 
    dadosLista.splice((i - 1), 1);
    document.getElementById('tabela').deleteRow(i);
}
```
<hr>

## :rocket: Tecnologias ##


<p align="center">
<img align="" src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white">
<img align="" src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white">
<img align="" src="https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white">
<img align="" src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white">
<img align="" src="https://img.shields.io/badge/GIT-E44C30?style=for-the-badge&logo=git&logoColor=white ">
</p><p align="center">
<img src="https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E">
<img src="https://img.shields.io/badge/markdown-%23000000.svg?style=for-the-badge&logo=markdown&logoColor=white">
<img src="https://img.shields.io/badge/OneDrive-0078D4.svg?style=for-the-badge&logo=microsoftonedrive&logoColor=white">
<img src="https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white">
</p>  



## :white_check_mark: Requisitos para Instalação ##

Antes de começar :checkered_flag:, você precisa ter [Git](https://git-scm.com) instalados.

## :checkered_flag: Início ##
>  Clone este projeto
```
$ https://github.com/ESChrystian/Login-cad.git

```
## Autor ##
[Chrystian de Almeida Silva](https://github.com/ESChrystian)
