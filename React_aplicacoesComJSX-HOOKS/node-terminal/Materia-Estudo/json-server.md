# JSON Server

O JSON Server é uma ferramenta extremamente útil para desenvolvedores, especialmente aqueles que trabalham no front-end de aplicações web. Ele permite criar rapidamente uma API REST falsa (mock) a partir de um arquivo JSON. Aqui está um resumo dos pontos principais:

## O que é JSON Server?

- É um pacote Node.js que permite criar uma API REST completa com rotas, métodos HTTP (GET, POST, PUT, DELETE), filtragem, ordenação e mais, tudo a partir de um simples arquivo JSON.
- Ele serve como um "backend falso" que pode ser usado para testes e desenvolvimento quando um backend real ainda não está disponível.

## Por que usar o JSON Server?

- **Desenvolvimento Front-end**: Permite que desenvolvedores front-end trabalhem e testem suas aplicações sem depender de um backend real.
- **Prototipagem Rápida**: Ideal para criar protótipos rápidos de APIs e testar funcionalidades.
- **Testes**: Facilita a criação de cenários de teste com dados controlados.

## Como funciona?

- Você cria um arquivo JSON que representa seu "banco de dados".
- O JSON Server lê esse arquivo e cria automaticamente uma API RESTful com os dados.
- Você pode fazer requisições HTTP (GET, POST, etc.) para a API como se fosse um backend real.

## Principais características:

- Criação rápida de APIs REST falsas.
- Suporte para métodos HTTP padrão.
- Filtragem, ordenação e paginação de dados.
- Fácil de configurar e usar.

Em resumo, o JSON Server é uma ferramenta poderosa para acelerar o desenvolvimento e teste de aplicações web, especialmente quando o backend ainda não está pronto.

## Reiniciando o Projeto

O comando básico para iniciar o JSON Server e observar as alterações no seu arquivo JSON é

```
json-server --watch <endereço_do_arquivo.json>
```

### Exemplo:

Se o seu arquivo JSON se chama `db.json` e está na raiz do seu projeto, o comando seria:

```
json-server --watch db.json
```

### O que o comando faz:

- `json-server`: Chama o seguinte nível do JSON Server.
- `--watch`: Indica que o JSON Server deve observar o arquivo especificado e reiniciar automaticamente sempre que houver alterações.
- `<endereço_do_arquivo.json>`: É o caminho para seu arquivo JSON.

### Informações importantes:

- Certifique-se de que o JSON Server esteja instalado globalmente ( `npm install -g json-server`) ou localmente no seu projeto ( `npm install json-server`).
- O JSON Server geralmente inicia um servidor na porta 3000. Se essa porta já estiver em uso, você pode especificar uma porta diferente usando a opção `--port`:

```
json-server --watch db.json --port 3001
```

- Quando você altera o arquivo json, e salva, o json-server será reiniciado automaticamente.
- Para parar o json-server, no terminal, use o comando CTRL+C.

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)