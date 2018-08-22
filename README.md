# REACT NINDJAA

## Módulo 01: 

### A02: Sobre o React



### A02: Sobre o React

facebook.github.io/react

- React é uma biblioteca javascript para criar interfaces
  - Não é um framework, é uma biblioteca
  - Pode utilizar com oturos frameworks, para fazer trechos de interface de usuários e para fazer sua aplicação ionteira
  - Ele é basicamente o V do MVC: a parte visual

- Onde vamos utilizar o React? 
  - Aplicações dinâmicas / interatias com muita manipulação do DOM
    - Webapps
    - Mobile apps
    - Sistema de administração de CMS
      - Ex.: Wordpress está usando para um sistema de administração (pois é uma interface dinâminca e interativa que precisa sim de muita manipulação do DOM )

- Onde <b>NÃO</b> devemos utilizar o React?
  - Sistemas que só exibem conteúdo
    - Websites institucionais
    - blogs
  - A ideia naõ é criar itnerface e sim uma forma fácil de manipular e perfomática de iteração entre as interfaces.

- Quais problemas o React resolve?
  - Modularização
    - É muito facil modularizar o código e separar as responsabilidades com React
  - Componentização
    - Como tudo o que fazemos é um componente o utilizamos para cirar componentes de UI. Isso é o que facilita a modularização do código
  - Performance
    - Como ele trabalha com um DOM virtual ao invés de manipular o DOM de verdade (fazendo diffs do que foi alterado na aplicação com o dom real, tudo por debaixo dos panos, atualizando no DOM real apenas o que foi mudado de fato)

### A03: Começando a trabalhar com o React

  (foto do site do react) https://reactjs.org/
  - getting started (https://reactjs.org/docs/getting-started.html)
  - Starter Kit, tem o react.js e o react-dom-server.js que precisamos
    - (links para o cdn)

  - Vamos no terminal
    - instalar o http-server
      - nom i http-server 
      - usado para podermos executar o nosso servidor
    - chamar o ```http-server``` na pasta para poder servir o rolezin
  (print do http-server executando)
  ``` HTML
  <script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
  <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
  ```
  - Quando fazemos um import temos o React Global
    - Se formos para o console e fizermos um React vai aparecer todas as propriedades e etc
    - Vamos usar a create element para criar um elemento usando o react
    ``` javascript
      let elemento = 'h1'
      let propriedades = undefined
      let conteudo = 'Hello World Reacat'
      let h1 = React.createElement(elemento, propriedades, conteudo)
    ```
    - COmo fazemos para renderizar isso na tela?
      - Usamos o ReactDOM: 

      ```javascript 
        const elemento = React.createElement(elemento, propriedades, conteudo)
        const ondeVouRenderizar = document.getElementById('lugarzinBunitu')
        ReactDOM.render(elemento, ondeVouRenderizar)
      ```
    - React CreateElement x document.createElement
      - Ao criar com o javascript ele cria um elemento do DOM. Ao usar o do react ele cria apenas um objeto comum que é utilizado com o React para fazer a comparação ao alterar algo; se este elemento for alterado aí o React vai alterar no dom.
    - Conseguimos renderizar elementos SVG também com o ```javascritp React.createElement```
 
### AULA 04: Criando elementos aninhados

  ```javascript
    const span = React.createElement('span', null, 'Texto do span')
    const h1 = React.createElement('h1', null, span)
    const ondeVouRenderizar = document.getElementById('lugarzinBunitu')
    ReactDOM.render(h1, ondeVouRenderizar)
  ```
  - Ao fazer isso geramos:
  ``` html
    <div id="lugarzinBunitu">
      <h1>
        <span>Texto do span</span>
      </h1>
    </div>
  ```

  - Podemos também passar um array e elementos para criar mais de um:
  ``` javascript
    const lista = React.createElement('ul', null, [
        React.createElement('li', null, 'item: 1 uhuuu'),
        React.createElement('li', null, 'item: 2 ahaaa')
      ])
    ReactDOM.render(lista, ondeVouRenderizar)
  ```

  ``` html
  <div id="lugarzinBunitu">
    <ul>
      <li>item: 1 uhuuu</li>
      <li>item: 2 ahaaa</li>
    </ul>
  </div>
  ```
  - Ao fazer isso apagamos o que tinha antes na div ```lugarzinBunitu```
  > DÚBIDA: Como eu faço um texto + o span ?


### AULA 05: Conhecendo o JSX
  - JSX: JAVASCRIPT + XML
    - Serve para que poçamos representar nossos componentes de forma mais visual e que tenha mais a cara dos elmeentos que são renderizados no DOM
    - Imagina como ficaria tenso criar uma porradad de ```React.createElement(elemento, propriedades, conteudo)``` para cada elemento que quisermos renderizar
  - Temos uma outra forma de criar elementos também, que é uma forma um pouco mais restrita porém mais legível

  ``` javascript
    React.DOM.span(propriedades, conteudo)
    React.DOM.i(props, conteudo)
  ```
  ** ESTA FORMA APARENTEMENTE NÃO FUNCIONA MAIS **

