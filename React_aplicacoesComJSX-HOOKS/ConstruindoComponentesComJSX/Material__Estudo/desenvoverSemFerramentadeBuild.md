# Para desenvolver sem Ferramentas de Build

Para desenvolver sem a necessidades de ferramentas build como o **Vite** por exemplos, podemos incluir, envoltas na TAG `script`:

- `https://cdnjs.cloudflare.com/ajax/libs/react/18.2.0/umd/react.production.min.js`: Para importar, via **CDN** o React no projeto [CDNsJs](https://cdnjs.com/libraries/react).

```
 <!-- ===== Importação do React ===== -->
    <script
      src="https://unpkg.com/react@18/umd/react.production.min.js"
      crossorigin="anonymous"
    ></script>
```

- `https://cdnjs.cloudflare.com/ajax/libs/react-dom/18.2.0/umd/react-dom.production.min.js`: Para importar o React **DOM**.

  - O React DOM é uma tecnologia do React e serve para permitir a **conexão do nosso código JavaScript com o DOM** (Document Object Model, ou "Modelo de Objeto de Documentos" em português), a árvore de elementos do HTML, que se refere a tudo que vai mostrar na nossa tela. [CDNsJs](https://cdnjs.com/libraries/react-dom)

```
 <!-- ===== Importação do React-DOM ===== -->
    <script
      src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"
      crossorigin="anonymous"
    ></script>
```

- `http://cdnjs.com/libraries/babel-standalone`: E por últo o **Babel**. O Babel é uma ferramenta de **compilação de códigos JavaScript** que podem estar em uma versão mais moderna, mas que o navegador não a suporte. Ele faz essa compilação, como se fosse uma tradução, para conseguirmos acessar aplicações mais novas em qualquer navegador.
  - Especificamente para o React, o Babel auxilia na **criação de componentes**, fazendo essa conversão do que é utilizado para construir componentes para o que o navegador entenda. [CDNs Js](https://cdnjs.com/libraries/babel-standalone)

```
    <!-- ====== Importação do Babel ===== -->
    <script
      src="https://unpkg.com/@babel/standalone/babel.min.js"
      crossorigin="anonymous"
    ></script>
```

## Renderizando Componentes

O próximo passo é a criação de uma página Js com `type="text/babel"`:

```
<script type="text/babel" src="./script.js"></script>
```

Após a criação da página Js, para vincular o que está sendo codado em JSX no HTML, na página HTML inserimos uma tag para fazer a vinculaçã:

```
<div id="root"></div>
```

Na página Js criada, inserimos:

```
ReactDom.createRoot(document.getElementById("root")).render()
```

- `ReactDom`: Chamamos a biblioteca `ReactDOM`, que faz a associação do react com a árvore do DOM do HTML e JavaScript, possibilitando a inserção se elementos.

- `createRoot(document.getElementById("root"))`: Definimos qual será a raiz da árvore de elementos.

- `render()`: Para renderizar o que está sendo construído na tela, utilizamos o método `render()`

### [Voltar ao MENU - React: construíndo componentes com JSX](../menu.md)
