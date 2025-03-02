# Erros encontrados pelo ESLint

O ESLint é uma ferramenta muito útil para garantir a consistência e qualidade do código JavaScript, ajudando a prevenir diversos erros comuns. Aqui estão alguns exemplos de erros que o ESLint pode ajudar a identificar e corrigir:

### 1 - Variáveis não utilizadas:

- Evita declarar variáveis que não são utilizadas no código, o que pode indicar um problema de lógica ou código não otimizado.

```
// Variável não utilizada
`let` x =` 10`;
```

### 2 - Declaração de variáveis sem o uso de `const`, `let` ou `var`:

- Garante que todas as variáveis sejam devidamente declaradas com `const`, `let` ou `var` para evitar vazamentos de variáveis globais.

```
// Variável não declarada
x = 10;
console.log(x);
```

### 3 - Erro de escopo:

- Previne problemas relacionados a escopo de variáveis, identificando quando variáveis estão sendo acessadas fora do escopo em que foram declaradas.

```
function exemplo() {
  if (true) {
    let x = 10;
  }
  console.log(x); // Erro: x não está definido neste escopo
}
```

### 4 - Uso de `==` em vez de `===`:

- Ajuda a prevenir comparações com coerção de tipo, incentivando o uso de `===` para comparações estritas de igualdade.

```
// Uso de == em vez de ===
if (x == '10') {
  // Esta condição pode ser verdadeira mesmo que x não seja do tipo string
}
```

Esses são apenas alguns exemplos de erros que o ESLint pode ajudar a prevenir no código JavaScript. O ESLint pode capturar ou não algumas dessas regras, dependendo de como está definido o seu arquivo de configuração.

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)