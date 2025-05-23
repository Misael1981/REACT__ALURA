# SPA e recursos nativos do JS

Uma SPA (Single Page Application) é uma aplicação que acontece sempre na mesma página HTML, normalmente chamada de `index.html`. A “troca entre páginas” é feita puramente com o JS, ou por alguma ferramenta que abstrai o JS. No caso desse curso é a biblioteca `react-router-dom`, que no final das contas utiliza os próprios recursos do JS para realizar a navegação.

Dessa forma, a navegação entre as rotas é muito mais rápida do que em sites tradicionais, que, onde a cada link que clicamos, devemos esperar uma nova requisição ao servidor, e a página do navegador é recarregada quando a nova página HTML está pronta para ser exibida. Já em uma SPA, a ideia é passar a sensação de que a pessoa usuária está em uma aplicação desktop.

Alguns dos recursos nativos do JS que o `react-router-dom` utiliza por debaixo dos panos são o **window.history** e o **window.location**. O objetivo da biblioteca é melhorar a experiência de criação de uma SPA, abstraindo esses recursos nativos para métodos e componentes mais intuitivos e manuteníveis do que seria com JS puro.

O React em conjunto com o `react-router-dom` não é a única forma de construir SPAs. Outros frameworks front-end, como Angular e Vue.js também utilizam os mesmos recursos nativos do JS para criar seus próprios ecossistemas de navegação.

Você também pode conferir esse Hipsters Ponto Tube que fala mais sobre SPAs:

- ### [O que é uma Single-Page Application? (SPA) ](https://www.youtube.com/watch?v=opxYpCKzlLk&t=4s)

### [Voltar ao Menu - React: desenvolvendo em React Router com JavaScript](../menu.md)
