# Componentes Funcionais

Componentes funcionais são uma forma mais simples de criar um componente React.

Mas ela não é a única forma possível. Podemos criar componentes utilizando Classes do ES6.

Vamos entender um pouco mais as diferenças?

Aqui vai um componente funcional:

```
function BoasVindas(props) {
  return <h1>Olá, {props.nome}</h1>;
}
```

O mesmo componente, baseado em classes, seria:

```
class BoasVindas extends React.Component {
  render() {
    return <h1>Olá, {this.props.nome}</h1>;
  }
}
```

Além da sintaxe, existem diversas diferenças. Se você quiser ir mais fundo no conceito de componentes baseado em classes, a [documentação](https://pt-br.react.dev/reference/react/Component#defining-a-class-component) é a nossa melhor fonte.

### [Voltar ao Menu - React: desenvolvendo com JavaScript](../menu.md)
