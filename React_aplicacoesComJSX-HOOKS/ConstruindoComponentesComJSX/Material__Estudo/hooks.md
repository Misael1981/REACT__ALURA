# Hooks?

Em uma aplicação web é comum que existam dados que se alteram durante a navegação do usuário e a forma como você controla esses dados se chama **gerenciamento de estado**.

Por exemplo, se você tem um componente que mostra uma lista de tarefas, o gerenciamento de estado é o que permite que você adicione, remova ou marque as tarefas como feitas. O estado é a variável que guarda esses dados, e que pode mudar ao longo do tempo. Você já se perguntou como fazer com que os componentes do React possam lidar com essas situações?

Para isso, temos os **hooks**. Hooks são funções especiais que permitem que você “conecte” os seus componentes funcionais a recursos do React.

Um dos hooks mais importantes é o `useState`. Ele permite que você crie e atualize o estado dos seus componentes funcionais. O estado é uma variável que guarda algum valor que pode mudar ao longo do tempo, e que afeta a renderização do componente.

Você pode usar o `useState` dentro do seu componente funcional, passando como argumento o valor inicial do estado, como `useState(“”)` quando queremos inicializar um estado vazio.

O `useState` retorna um array com **dois elementos**: **o primeiro é o valor atual do estado**, e **o segundo é uma função que permite atualizar o estado**. Você pode usar a sintaxe de desestruturação para atribuir esses elementos a variáveis com nomes significativos. Por exemplo, se você quiser criar um estado que guarda o número de cliques em um botão, você pode fazer assim:

```
function Contador() {
  // Cria o estado "contagem" com valor inicial 0
  const [contagem, setContagem] = useState(0);

  // Cria uma função que incrementa o estado "contagem" em 1
  function incrementar() {
    setContagem(contagem + 1);
  }

  // Retorna o JSX do componente, que mostra o estado "contagem" e um botão que chama a função "incrementar"
  return (
    <div>
      <p>Você clicou {contagem} vezes</p>
      <button onClick={incrementar}>Clique aqui</button>
    </div>
  );
}
```

Note que, sempre que o estado é atualizado pela função setContagem, o componente é renderizado novamente, mostrando o novo valor na tela. Isso é uma das vantagens dos hooks: eles permitem que você crie componentes reativos e dinâmicos.

Caso queira saber mais sobre o useState, assista o Alura+ [Hooks do React: useState](https://cursos.alura.com.br/extra/alura-mais/hooks-do-react-usestate-c1530) e o artigo [React Hooks: o que é e como funcionam?](https://www.alura.com.br/artigos/react-hooks).

### [Voltar ao MENU - React: construíndo componentes com JSX](../menu.md)