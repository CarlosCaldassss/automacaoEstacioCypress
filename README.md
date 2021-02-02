<<<<<<< HEAD
=======
# automacao_cypress_estacio

Automação do fluxo de inscrição de um candidato pela forma Vestibular no site da Universidade Estácio de Sá.

>>>>>>> 71fb6bfdb4cebce237645c3d71ddcb25a5aee1d3
**# Automação-projeto-cypress**

Documentação do projeto.

Projeto de automação de testes utilizando o Cypress, Cucumber e a ligunguagem JavaScript.

**### Pré-Requisito:**

* Ter o Node js instalado com suas dependencias:
    * 1. Escolher uma IDE de JavaScript para programar: usaremos o VS Code neste tutorial.
        Execute os comandos no terminal do VS Code:

        “Comandos inciais:
            - Abra o VS code e entre dentro da pasta do projeto que você criou
            - Abra o terminal do VS code e execute os seguintes comandos:
                - npm init --yes (iniciando um repositorio npm)
                - npm install -D cypress (instalando a ultima versão do cypress
                - npx cypress open
        O npm vai baixar a pasta node_modulos”


        Configurações inciais:
            - Navegue ao arquivo de config “package.json”
            - Na linha 7 Onde tem “test: “echo\Error: test specified\”&& exit 1” troque para o comando 	abaixo:

                "cypress:open": "./node_modules/.bin/cypress open",
                "cypress:run": "./node_modules/.bin/cypress run"

    * 2. Instalar o Cypress com Cucumber:
            - No terminal do VS code execute o comando:
                npm install -D cypress-cucumber-preprocessor


    * Configurar o Cucumber no Cypress:

        Adicione ao arquivo cypress/plugins/index.js o seguinte script:

        "const cucumber = require('cypress-cucumber-preprocessor').default
        module.exports = (on, config) => {
        on('file:preprocessor', cucumber())
        }"
   
**### Entendendo os principais comandos do Cypress:**

Entendendo os principais comandos do Cypress
O funcionamento do Cypress é baseado em localizar elementos do site (botões, inputs, textos, imagens, etc.) e interagir com os mesmos. Podemos automatizar todas as ações que executamos manualmente ao utilizar a página web (e mais algumas).

O Cypress possui uma boa documentação com todos os seus comandos. Abaixo vamos ver os principais para iniciar.

**##GET:
###Sintaxe: cy.get(‘seletor’)**


Este comando é responsável por selecionar o elemento da tela no qual executamos uma ação. Funcionamento semelhante ao de levar o cursor do mouse em cima do que queremos.

cy.get('#idDoElemento') // seleciona elemento por seu id
cy.get('.class') // seleciona elemento por sua classe 
cy.get('[atributo="doElemento"]') // seleciona elemento por seu atributo
Para entender melhor como capturar seletores de elementos, você pode acessar um bom tutorial neste link.

**##CLICK:
###Sintaxe: .click()**


O comando click é utilizado para realizar a ação de clicar em um elemento da página e, para isso, deve ser utilizado em conjunto com o comando GET ou outro comando de mesma função. Funcionamento semelhante ao de clicar com o botão esquerdo do mouse no elemento que queremos.

cy.get('#idDoElemento').click() //clique simples
cy.get('.class').click({ force: true }) //força o clique mesmo em elementos que estejam invisíveis
cy.get('button').click({ multiple: true }) //clica em todos os elementos que forem selecionados

**##TYPE:
###Sintaxe: .type(‘texto’)**


Type é utilizado para setar informações em campos. Funcionamento semelhante ao de digitarmos com nosso teclado.

cy.get('#input-email').type('gabriel.fer@gmail.com') // insere 'gabriel.fer@gmail.com' no campo do elemento selecionado
cy.get('.senha-class').type('123456') // insere '123456' no campo do elemento selecionado

**##VISIT:
###Sintaxe: cy.visit(‘http://dev-testqa.com’)**


O comando visit é utilizado para acessar endereços virtuais. Com ele acessamos o site em que iremos realizar os testes.

cy.visit('http://localhost:8000') // acessa local informado
cy.visit('https://dev-qa.com') // acessa site informado
cy.visit('url, { timeout: 30000 }') // acessa site configurado no arquivo cypress.json e configura timeout de 30 segundos

**##SHOULD:
###Sintaxe: .should(‘configurações’)**


Should é um comando utilizado para fazer asserções na página. Este é normalmente o último comando a ser utilizado no cenário e serve para validar se o teste passou ou reprovou.

cy.get('.class').should('contain', 'Texto esperado') // Verifica se o elemento selecionado contém o texto que é esperado.
cy.get('#id-name').should('be.visible') // Verifica se o elemento está visível na página.
cy.get('div').should('not.be.empty') // Verifica se o elemento não está vazio.


**#### Estruturando o projeto:**

```O Cypress pode ser utilizado sem Cucumber:```
* Com uma estrutura simples explicada na documentação do mesmo. Neste tutorial veremos como estruturar utilizando a ferramenta de escrita de testes em BDD. Para isso, temos que conhecer as principais pastas e arquivos iniciais do projeto:
***

*A pasta ‘fixtures’ e os arquivos ‘commands.js’, ‘index,js’ e package-lock.json’ oferecem configurações avançadas que não serão abordadas neste tutorial.

Integration: nesta pasta colocamos os nossos arquivos com os cenários de teste escritos no formato BDD.

plugin/index.js: este arquivo é destinado para configuração de plugins. Utilizamos ele ao configurar o Cucumber.

support: dentro desta pasta colocamos os steps, os scripts e o mapeamento de elementos de nossos testes.

node_modules: aqui ficam os arquivos de funcionamento do Cypress e do Cucumber. Normalmente não precisamos mexer nesta pasta.

cypress.json: neste arquivo podemos realizar configurações globais do nosso projeto. Ex.: criar variáveis globais, definir resolução do navegador, setar uma URL padrão, entre outros.***

**#### Organização do projeto:**

```Pasta feature:```
* Steps: nesta pasta colocamos os passos que farão a conexão entre o que escrevemos em BDD e os scripts que fazemos em Cypress.

* Pageobjects: aqui deixamos os scripts feitos em Cypress.
A ideia do page objects é a de criarmos um arquivo.js para cada página ou fluxo do site. Dessa forma, mantemos a organização e facilitamos a manutenção do código, pois colocamos no arquivo os comandos que são executados na página/fluxo correspondentes ao nome do arquivo.
Ex.: HomePage.js, PdpPage.js, Checkout.js.

*Elements: possui o mesmo conceito do page objects, mas aqui colocamos os elementos da página. Tal organização permite que elementos sejam reutilizados e tenham fácil manutenção.
Ex.: HomeElements.js, PdpElements.js, CheckoutElements.js.

```
Adicione o seguinte código no arquivo package.json:

{
    "scripts": {
        "test:chrome": "cypress run --browser chrome --no-exit"
    },
    "cypress-cucumber-preprocessor": {
        "step_definitions": "cypress/support/steps"
    }
}

```

###### Autor: 
```Carlos Caldas```


