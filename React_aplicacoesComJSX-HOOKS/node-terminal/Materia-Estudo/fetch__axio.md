# Diferança entre fetch() e axio

## Fetch API:

- **O que é**:
  - O `fetch()` é uma API nativa do JavaScript para fazer requisições HTTP (como GET, POST, PUT, DELETE) para servidores.
  - Ele retorna uma `Promise` que resolve para um objeto `Response`, que contém informações sobre a resposta do servidor.
- **Vantagens**:
  - É nativo do navegador, então não precisa de bibliotecas externas.
  - É baseado em `Promises`, o que facilita o trabalho com código assíncrono.
- **Desvantagens**:
  - A sintaxe pode ser um pouco verbosa, especialmente para requisições mais complexas.
  - Não lida automaticamente com erros HTTP (como 404 ou 500). Você precisa verificar o status da resposta manualmente.
  - Para obter os dados em formato json, você precisa usar o método `response.json()`
- **Exemplo**:

```
fetch('https://api.exemplo.com/dados')
  .then(response => {
    if (!response.ok) {
      throw new Error(`Erro HTTP! status: ${response.status}`);
    }
    return response.json();
  })
  .then(data => {
    console.log(data);
  })
  .catch(error => {
    console.error('Ocorreu um erro:', error);
  });
```

## Axios:

- **O que é**:
  - Axios é uma biblioteca JavaScript popular para fazer requisições HTTP.
  - Ele funciona tanto no navegador quanto no Node.js.
  - Também retorna `Promises`.
- **Vantagens**:
  - Sintaxe mais concisa e fácil de usar.
  - Lida automaticamente com erros HTTP.
  - Transforma automaticamente os dados em JSON.
  - Possui recursos avançados, como interceptores (para interceptar e modificar requisições e respostas), cancelamento de requisições e proteção contra XSRF.
- **Desvantagens**:
  - Requer a inclusão de uma biblioteca externa.
- **Exemplo**:

```
axios.get('https://api.exemplo.com/dados')
  .then(response => {
    console.log(response.data);
  })
  .catch(error => {
    console.error('Ocorreu um erro:', error);
  });
```

## Principais Diferenças:

- **Sintaxe**: Axios geralmente tem uma sintaxe mais limpa e direta.
- **Tratamento de erros**: Axios lida com erros HTTP automaticamente, enquanto fetch() requer verificação manual.
- **Transformação de dados**: Axios transforma automaticamente os dados para JSON, enquanto fetch() requer que você use response.json().
- **Recursos adicionais**: Axios oferece recursos avançados, como interceptores e cancelamento de requisições.
- **Nativo vs. Biblioteca**: Fetch é nativo do navegador, Axios é uma biblioteca externa.

### Qual escolher?

- Se você precisa de uma solução simples e não quer adicionar bibliotecas externas, fetch() é uma boa opção.
- Se você precisa de recursos avançados, tratamento de erros automático e uma sintaxe mais concisa, Axios é a escolha ideal.

Para conhecer mais sobre o Axios e mais casos de uso, confira o artigo [Requisições HTTP utilizando o AXIOS!](https://www.alura.com.br/artigos/requisicoes-http-utilizando-axios)

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)
