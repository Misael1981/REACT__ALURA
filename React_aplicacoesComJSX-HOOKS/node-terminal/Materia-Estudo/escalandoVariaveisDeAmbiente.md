# Escalando as Variáveis de Ambiente

Conseguimos dinamizar com sucesso a URL de requisição dos vídeos com o seguinte código:

```
const urlVideos = import.meta.env.PROD ?
  "https://gist.githubusercontent.com/antonio-evaldo/e8a63621b51c883931eb3fa3a3eca990/raw/12f5c46ee6dd00d03c051adadaf341e06452cea0/videos.txt" :
  "http://localhost:3000/videos";
```

Essa abordagem funcionou tranquilamente para nosso projeto, contudo, ela não é tão escalável. Isso quer dizer que essa abordagem é difícil de manter se o projeto começar a crescer muito.

Imagine que precisamos utilizar essa informação dinâmica em vários arquivos diferentes do projeto. Seria necessário sempre escrevermos essa condição ternária para obter a URL correta, o que geraria bastante repetição de código, não é mesmo?

## Resolvendo o problema

Com isso, podemos imaginar que seria bom centralizar essa informação em um arquivo separado. É possível fazer isso com nossos conhecimentos de JavaScript, mas o Vite fornece um recurso nativo muito bacana para esse tipo de situação: [os arquivos](https://vite.dev/guide/env-and-mode.html#env-files) `.env`, que são arquivos de variáveis de ambiente.

Vamos utilizar esse recurso?

1. Primeiro, crie um arquivo chamado `.env.development` (o nome deve ser exatamente assim) na raiz do projeto com o seguinte conteúdo:

```
    VITE_URL_VIDEOS=http://localhost:3000/videos
```

O `development` do nome do arquivo informa que queremos definir variáveis para o ambiente de desenvolvimento. Nesse caso, definimos uma variável chamada `VITE_URL_VIDEOS` com o valor `http://localhost:3000/videos`.

Para esses arquivos do Vite, devemos seguir a sintaxe `VITE_VARIAVEL=valor`. Os nomes das variáveis devem ser iniciados com `VITE_`.

2. Segundo, crie mais um arquivo chamado `.env.production` na raiz do projeto com o seguinte conteúdo:

```
    VITE_URL_VIDEOS=https://gist.githubusercontent.com/antonio-evaldo/e8a63621b51c883931eb3fa3a3eca990/raw/12f5c46ee6dd00d03c051adadaf341e06452cea0/videos.txt
```

O `production` no nome do arquivo informa que queremos definir variáveis para o **ambiente de produção**. Nesse caso, definimos mais uma vez uma variável `VITE_URL_VIDEOS`, mas agora o valor que será usado em produção é a URL do GitHub.

3. Por fim, vamos retornar ao arquivo `script.js` e modificar a atribuição da variável `urlVideos` para receber o valor da variável de ambiente `VITE_URL_VIDEOS` em vez de utilizar o operador ternário:

```
    const urlVideos = import.meta.env.VITE_URL_VIDEOS;
```

Com isso, o nosso código funcionará igual a antes! Você pode testar nos servidores de desenvolvimento e de prévia de produção.

A grande vantagem dessa abordagem é que agora só precisaremos escrever `import.meta.env.VITE_URL_VIDEOS` em vez de realizar uma condição ternária no código sempre que quisermos uma informação dinâmica, assim evitando repetição e reduzindo o código.

Mas além disso, outra vantagem que ganhamos é a centralização das informações das variáveis de ambiente. Conforme aumentamos a quantidade de informações dinâmicas no nosso código, basta irmos adicionando novas variáveis nos arquivos `.env.development` e `.env.production`:

```
VITE_URL_VIDEOS=url...
VITE_VARIAVEL_2=valor2
VITE_VARIAVEL_3=valor3
VITE_VARIAVEL_4=valor4
```

Dessa forma, se um dia precisarmos alterar qualquer informação de desenvolvimento ou de produção, já saberemos onde procurar.

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)
