# Sobre a Instalação do Vite

Executamos o seguinte comando para criar o projeto Vite:

```
npm create vite@4.4.1
```

No entanto, depois de gerar o projeto, encontramos o seguinte no `package.json`:

```
"devDependencies": {
  "vite": "^4.4.5"
}
```

Note a diferença entre os números `4.4.1` e `4.4.5`. Será que houve algum erro na instalação para acontecer essa divergência de versões?

O que acontece é que, na verdade, esses números se referem a pacotes diferentes. Vamos entender melhor?

### Entendendo a diferença

Vamos retornar ao primeiro comando:

```
npm create vite@4.4.1
```

Esse comando tornou o terminal interativo, fazendo perguntas sobre a configuração do projeto a ser criado. Isso é bastante semelhante a quando configuramos o ESLint no nosso projeto.

Na verdade, o `npm create` é um **alias** (apelido) do `npm init`, então o comando acima é o mesmo que executar `npm init vite@4.4.1`.

Esse comando, por sua vez, é o equivalente a executar o seguinte:

```
npx create-vite@4.4.1
```

Ou seja, pedimos para o NPM **executar** o pacote `create-vite` na versão `4.4.1`. Você pode conferir esse pacote no [site do NPM](https://www.npmjs.com/package/create-vite).

Então percebemos que o `create-vite`, de forma semelhante ao `@eslint/create-config`, também é um pacote que torna o terminal interativo e gera a estrutura do projeto de acordo com as respostas que fornecemos.

Ao terminar de interagir com o terminal, temos uma estrutura de projeto gerada para nós. No `package.json` gerado, podemos conferir o `vite` dependência de desenvolvimento:

```
"vite": "^4.4.5",
```

Note que o `create-vite` e o `vite` são pacotes diferentes. Enquanto o `create-vite` é apenas o pacote que gera a estrutura inicial do projeto, o `vite` é o Vite em si, que disponibiliza o servidor Node.js.

Sabendo dessas diferenças, entendemos melhor as ferramentas com as quais estamos trabalhando, assim evitando confusões e resultados inesperados.

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)
