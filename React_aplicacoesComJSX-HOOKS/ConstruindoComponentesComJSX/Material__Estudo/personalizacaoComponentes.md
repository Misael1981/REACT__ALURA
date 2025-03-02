# Personalização de Componentes

É comum querer reutilizar alguns componentes que você já criou, como botões, cards, menus, etc. Também permite personalizar esses componentes de acordo com o contexto em que eles são usados, como mudar a cor, o texto, o estilo, etc. Mas como você pode fazer isso?

Uma forma de personalizar componentes em React é passar dados para eles através de **props**. **Props** são propriedades que você define no componente pai e que são acessíveis no componente filho. Por exemplo, se você tem um componente `Botao`, você pode passar uma prop chamada tipo para definir o tipo do botão:

```
<Botao tipo=”submit” />
```

No componente `Botao`, você precisa usar a desestruturação de objetos no parâmetro da função que define o componente. A desestruturação de objetos é uma forma de extrair propriedades de um objeto e atribuí-las a variáveis com o mesmo nome.

Para isso, você irá usar as chaves `{}`. Assim, você pode acessar a prop tipo dentro do componente. Por exemplo:

```
function Botao({ tipo }) {
  return (
    <button type={tipo} className="form__botao">
      Login
    </button>
  );
}
```

Dessa forma, você pode passar a prop tipo para o componente Botao quando o usar, e o componente vai renderizar um botão com o tipo que você definiu.

Mas e se você quiser personalizar não só o tipo, mas também o conteúdo do componente? Por exemplo, se você quiser definir o texto do botão de forma dinâmica. Como você pode fazer isso?

Uma forma de personalizar o conteúdo do componente é usar a **props children**. 

```
Ela é uma prop especial que contém tudo o que você coloca entre as tags de abertura e fechamento do componente. Por exemplo, se você inserir um texto entre a abertura e fechamento do componente Button:
```

```
<Botao tipo="submit">Enviar</Botao> // Renderiza um botão do tipo submit com o texto Enviar
<Botao tipo="reset">Limpar</Botao> // Renderiza um botão do tipo reset com o texto Limpar
```

No componente `Card`, você pode acessar o conteúdo que você colocou dentro dele através de `this.props.children` ou `props.children`. Você pode usar essa prop para renderizar o conteúdo dentro do card, por exemplo, dentro de uma div:

```
function Botao({ tipo, children }) {
  return (
    <button type={tipo} className="form__botao">
      {children}
    </button>
  );
}
```

Props e props children são formas de passar dados entre componentes em React. A diferença entre elas é que props são propriedades nomeadas que você define no componente pai e que são acessíveis no componente filho, enquanto props children é uma propriedade especial que contém tudo o que você coloca entre as tags do componente. Você pode usar props para personalizar o estilo e o comportamento dos componentes, e props children para personalizar o conteúdo dos componentes.

### [Voltar ao MENU - React: construíndo componentes com JSX](../menu.md)