# REACT NINDJAA

## Módulo 01: 

### AULA 02: Sobre o React

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

- Onde **NÃO** devemos utilizar o React?
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

### AULA 03: Começando a trabalhar com o React

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
    - Como fazemos para renderizar isso na tela?
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
    - Imagina como ficaria tenso criar uma porrada de ```React.createElement(elemento, propriedades, conteudo)``` para cada elemento que quisermos renderizar, aninhando função dentro de função e etc

    ``` javascript 
    React.render(<h1> Ola mundo </h1>, ondeVouRenderizar)
    ``` 
    - Entretanto, isso não funciona porque irá dar um erro. O Javascript não suporta a utilização do JSX logo de cara, então temos que pedir ajudar para um amiguinho (transpilador) para nos ajudar

    ``` html
      <script crossorigin src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.34/browser.js"></script>

      <script type="text/babel">
        const ondeVouRenderizar = document.getElementById('lugarzinBunitu')
        const name = 'jãozin'
        const element = <h1>Olá, {name}</h1>

        ReactDOM.render(
          element,
          ondeVouRenderizar
        )
      </script>

    ```

    ``` html 
      <div id="lugarzinBunitu">
        <h1>Olá, jãozin</h1>
      </div>
    ```

    - Assim conseguimos renderizar o que queríamos! o/ 
    > obs: Com a versão mais recente do babel (6.1.19) não funcionou
    - Atente-se à propriedade **type** na tag script
    - Através do JSX conseguimos colocar variáveis e código js dentro de __{chaves}__ e a utilizar
    - O babel compila a forma "amigável/legível" para as funções do React
      - Ele deu exemplo de que uma tag h1 renderizada dessa forma demorou 500ms para ser renderizada e a tag h1 diretamente no html demora apenas 3ms
  
  
  - Temos uma outra forma de criar elementos também, que é uma forma um pouco mais restrita porém mais legível

  ``` javascript
    React.DOM.span(propriedades, conteudo)
    React.DOM.i(props, conteudo)
  ```
  > **ESTA FORMA APARENTEMENTE NÃO FUNCIONA MAIS**

### AULA 06: Aninhando com JSX e criando componentes
  Ok sabemos utilizar o  ```render``` para o ```ReactDOM``` mas eae, quero criar os meus, como fazemos?
  
  ``` javascript
    class Titulozin extends React.Component {
      render () { return <h1><span> BUA HAHA </span></h1>}
    }
    ReactDOM.render(
      <Titulozin />,
      ondeVouRenderizar
    )
  ```

  O método ```render``` deve retornar sempre um elemento do tipo React.
  ```__ POR CONVENÇÃO COMPOENTES DEEM SEMPRE COMEÇAR COM LETRA MAIÚSCULA__```
  > obs.: Durante a aula ele usa React.createClass que já está desatualizado e não fununcia mais
  As vezes vamos colocar um parentes logo após o ```return``` apenas para poder ficar mais claro e poder fazer a quebra de linha logo após 

  ```javascript
    class Titulozin extends React.Component {
      render () { return (
        <h1>
          <span> BUA HAHA </span>
        </h1>
      )}
    }
  ```

  Não conseguimos retornar mais de uma tag. Precisamos ter uma tag que envolve todas as tagas que vamos retornar

  ```javascript
  class Titulozin extends React.Component {
    render () { return (
        <h1><span> ISSO AQUI </span></h1>
        <h1><span> NÃO VAI FUNCIONAR </span></h1>
    )}
  }
  class Titulozin extends React.Component {
    render () { return (
      <div>
        <h1><span> ISSO AQUI </span></h1>
        <h1><span> VAI FUNCIONAR </span></h1>
      </div>
    )}
  }
  ```


## Módulo 02: React + Webpack
### AULA 07:
### AULA 08:
### AULA 09:
### AULA 10:
### AULA 11:
### AULA 12:
### AULA 13:
### AULA 14:
### AULA 15:
### AULA 16:
### AULA 17:
### AULA 18:
### AULA 19:
### AULA 20:
### AULA 21:
### AULA 22:
### AULA 23:
### AULA 24:
### AULA 25:
### AULA 26:
### AULA 27:
### AULA 28:
### AULA 29:
### AULA 30:
### AULA 31:
### AULA 32:
### AULA 33:
### AULA 34:
### AULA 35:
### AULA 36:
### AULA 37:
### AULA 38:
### AULA 39:
### AULA 40:
### AULA 41:
### AULA 42:
### AULA 43:
### AULA 44:
### AULA 45:
### AULA 46:
### AULA 47:
### AULA 48:
### AULA 49:
### AULA 50:
### AULA 51:
### AULA 52:
### AULA 53:
### AULA 54:
### AULA 55:
### AULA 56:
### AULA 57:
### AULA 58:
### AULA 59:
### AULA 60:
### AULA 61:
### AULA 62:
### AULA 63:
### AULA 64:
### AULA 65:
