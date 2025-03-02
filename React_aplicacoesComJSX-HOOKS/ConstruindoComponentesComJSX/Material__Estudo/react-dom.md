# React DOM

Estamos desenvolvendo componentes e precisamos renderizá-los na tela, mas somente utilizar a sintaxe semelhante ao do HTML como `<Titulo/>` não bastava. Como poderíamos imprimir os elementos visuais na tela?

Para isso utilizamos o React-DOM, uma biblioteca que fornece métodos para manipular o DOM (Document Object Model), que é a representação da estrutura e do conteúdo da página web. O React-DOM permite que você renderize os seus componentes React no DOM, usando dois métodos principais: `createRoot()` e `render()`.

O método `createRoot` cria uma raiz do React, que é um ponto de entrada para o seu aplicativo React no DOM. Já o método `render` renderiza um elemento React no DOM, usando a raiz do React criada pelo método `createRoot`.

### [Voltar ao MENU - React: construíndo componentes com JSX](../menu.md)