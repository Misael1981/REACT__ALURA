# export e export default

## O Conceito de Módulos em JavaScript

Antes de falarmos sobre `export` e `export default`, é crucial entender o sistema de módulos do JavaScript (principalmente no contexto de ES Modules, que é o padrão atual). Antigamente, o JavaScript não tinha um sistema de módulos nativos, o que levava a problemas como poluição do escopo global e dificuldades na organização de código em grandes projetos.

Com a introdução dos módulos (através das palavras-chave `import` e `export`), cada arquivo JavaScript se torna um módulo isolado. Isso significa que variáveis, funções e classes declaradas em um módulo estão disponíveis dentro desse módulo por padrão. Para disponibilizar essas coisas para outros módulos, precisamos explicitamente exportá-las. E é aí que ambos o e `export` o `export default`.

## `export`(Exportações Nomeadas)

O `export`(sem a palavra `default`) é usado para exportar vários valores (variáveis, funções, classes, etc.) de um módulo. Cada item exportado dessa forma tem um nome específico.

Como usar `export`:

Você pode exportar declarações individuais diretamente:

```
// arquivo: moduloA.js
export const PI = 3.14159;

export function somar(a, b) {
  return a + b;
}

export class Pessoa {
  constructor(nome) {
    this.nome = nome;
  }
}
```

Ou você pode exportar uma lista de declarações no final do arquivo:

```
// arquivo: moduloB.js
const GRAVIDADE = 9.8;

function subtrair(a, b) {
  return a - b;
}

class Carro {
  constructor(modelo) {
    this.modelo = modelo;
  }
}

export { GRAVIDADE, subtrair, Carro };
```

### Como importar Exportações Nomeadas:

Para importar valores que foram exportados usando `export`, você precisa usar a mesma sintaxe com chaves `{}` e especificar os nomes exatos dos itens que você quer importar:

```
// arquivo: principal.js
import { PI, somar, Pessoa } from './moduloA.js';
import { GRAVIDADE, subtrair, Carro } from './moduloB.js';

console.log(PI); // Saída: 3.14159
console.log(somar(5, 3)); // Saída: 8
const pessoa = new Pessoa('João');
console.log(pessoa.nome); // Saída: João

console.log(GRAVIDADE); // Saída: 9.8
console.log(subtrair(10, 4)); // Saída: 6
const carro = new Carro('Fusca');
console.log(carro.modelo); // Saída: Fusca
```

Você também pode renomear as importações usando a palavra-chave `as`:

```
import { Carro as Veiculo } from './moduloB.js';

const meuVeiculo = new Veiculo('Uno');
console.log(meuVeiculo.modelo); // Saída: Uno
```

É possível importar todas as exportações designadas de um módulo como um objeto usando o `* as`:

```
import * as moduloA from './moduloA.js';

console.log(moduloA.PI); // Saída: 3.14159
console.log(moduloA.somar(2, 7)); // Saída: 9
const outraPessoa = new moduloA.Pessoa('Maria');
console.log(outraPessoa.nome); // Saída: Maria
```

## `export default`(Exportação Padrão - Exportação Padrão)

O `export default` é usado para exportar um único valor padrão de um módulo. Cada módulo só pode ter uma exportação única padrão. Essa geralmente é a principal funcionalidade ou o valor mais importante que o módulo oferece.

### Como usar `export default`:

Você pode exportar um valor padrão diretamente na sua declaração:

```
export // arquivo: componenteC.js
const MeuComponente = () => {
  return <div>Sou um componente padrão!</div>;
};
```

Ou você pode declarar o valor primeiro e depois exportá-lo como padrão:

```
// arquivo: funcaoD.js
function funcaoPrincipal(x) {
  return x * x;
}

export default funcaoPrincipal;
```

Você também pode exportar classes, objetos literários ou qualquer outra expressão como padrão:

```
// arquivo: objetoE.js
const configuracao = {
  tema: 'escuro',
  idioma: 'pt-BR'
};

export default configuracao;
```

### Como importar Exportações padrão:

Para importar um valor que foi exportado usando `export default`, você não precisa usar chaves `{}`. Você pode dar qualquer nome para importação:

```
// arquivo: app.js
import ComponenteQualquer from './componenteC.js';
import minhaFuncao from './funcaoD.js';
import config from './objetoE.js';

function App() {
  return (
    <div>
      <ComponenteQualquer />
      <p>O resultado é: {minhaFuncao(5)}</p>
      <p>Tema: {config.tema}, Idioma: {config.idioma}</p>
    </div>
  );
}

export default App;
```

Perceba que `MeuComponente` foi importado como `ComponenteQualquer`, `funcaoPrincipal` como `minhaFuncao` , e `configuracao` como `config`. **O nome da importação para um `default export` é você quem escolhe**.

### Principais Diferenças em Resumo:

| **Característica**           | `export`(**Exportação Nomeada**)                                     | `export default`(**Exportação padrão**)                                              |
| ---------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Quantidade por módulo**    | Podem ter múltiplas exportações nomeadas                             | Pode ter apenas um padrão de exportação                                              |
| **Sintaxe de exportação**    | `export const nome = valor;` ou `export { nome1, nome2 };`           | `export default valor;`                                                              |
| **Sintaxe de importação**    | `import { nome1, nome2 } from '...';`                                | `import nomeQualquer from '...';`                                                    |
| **Foco**                     | Exportar vários valores diferentes                                   | Exportar um valor principal do módulo                                                |
| **Renomeação na importação** | Use `as` dentro das chaves:`import { nome as novoNome } from '...';` | A renomeação é feita diretamente no nome da importação:`import novoNome from '...';` |

## Quando usar qual?

- **Use `export`(Exportações Nomeadas)** quando seu módulo precisa exportar vários valores que têm nomes específicos e são referenciados por esses nomes em outros módulos. Isso é útil para bibliotecas ou módulos que fornecem várias funções ou constantes relacionadas.

- **Use `export default`(Default Export)** quando seu módulo tem uma única funcionalidade principal ou um valor padrão a ser usado pela maioria dos outros módulos que o importam. Isso é comum para componentes React, funções utilitárias principais ou instâncias de classes singleton.

### Posso personalizar `export` e `export default` no mesmo módulo?

Sim, você pode ter tantas exportações designadas quanto uma exportação padrão em um mesmo módulo, embora não seja tão comum.

```
// arquivo: moduloMisto.js
export const VERSAO = '1.0.0';

export function utilidade() {
  console.log('Função utilitária');
}

const valorPadrao = 'Este é o valor padrão';
export default valorPadrao;
```

Na hora de importar:

```
import valorPrincipal, { VERSAO, utilidade } from './moduloMisto.js';

console.log(valorPrincipal); // Saída: Este é o valor padrão
console.log(VERSAO); // Saída: 1.0.0
utilidade(); // Saída: Função utilitária
```

Entender a diferença entre `export` e `export default` é fundamental para escrever código JavaScript modular e bem organizado, especialmente em projetos React onde a reutilização de componentes e itens importados é essencial.

### [Voltar ao Menu - React: como os componentes funcionam](../menu.md)
