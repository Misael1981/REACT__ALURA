# Criando Scripts para Automatizar o Processo

Criar um script para automatizar a execução `json-server` é uma ótima maneira de economizar tempo e evitar erros. Existem duas formas principais de fazer isso: usando o `package.json` seu projeto ou criando um script separado.

## 1. Usando o `package.json`

Esta é a maneira mais comum e recomendada. Este `package.json` é um arquivo que contém informações sobre seu projeto, incluindo scripts que podem ser executados com o `npm` ou `yarn`.

1. **Abra o arquivo `package.json`** na raiz do seu projeto.
2. **Localize uma seção"scripts"** . Se ela não existir, crie.
3. **Adicione um novo script** com um nome de sua preferência, como "`json-server`", e o comando `json-server --watch backend/videos.json` como valor.

O `package.json` deve ficar parecido com isto:

```
{
  "name": "seu-projeto",
  "version": "1.0.0",
  "scripts": {
    "json-server": "npx json-server --watch backend/videos.json"
  },
  "dependencies": {
    "json-server": "^0.17.0"
  }
}
```

1. **Salve o arquivo**.
2. **Execute o script usando o comando `npm run json-server` ou `yarn json-server` no seu terminal**.

### Vantagens:

- Centraliza todos os scripts do projeto em um único lugar.
- Facilita a execução dos scripts, pois basta usar `npm run` ou `yarn`.
- Torna o projeto mais organizado e documentado.

## 2. Criando um script separado

Também se pode criar um arquivo de script separado, como um arquivo `.sh`(para Linux/macOS) ou `.bat`(para Windows).

### Exemplo (Linux/macOS):

1. **Crie um arquivo chamadojson-server.sh na raiz do seu projeto**.
2. **Adicione o seguinte conteúdo ao arquivo**:

```
#!/bin/bash
npx json-server --watch backend/videos.json
```

1. **Salve o arquivo** .
2. **Dê permissão de execução ao arquivo usando o comando `chmod +x json-server.sh`**.
3. **Execute o script** usando o comando `./json-server.sh` no seu terminal.

### Exemplo (Windows):

1. **Crie um arquivo chamado `json-server.bat`** na raiz do seu projeto.
2. **Adicione o seguinte conteúdo ao arquivo**:

```
npx json-server --watch backend/videos.json
```

1. **Salve o arquivo** .
2. **Execute o script** clicando duas vezes no arquivo ou usando o comando `json-server.bat` no seu terminal.

### Vantagens:

- Permite criar scripts mais complexos, com várias etapas.
- Pode ser útil para projetos que não usam `npm`ou `yarn`.

### Desvantagens:

- Solicite mais configuração inicial.
- Pode ser mais difícil gerenciar vários scripts.

### Recomendação:

A forma mais recomendada é usar o `package.json`, pois centraliza todos os scripts do projeto e facilita a execução. No entanto, se você precisar de scripts mais complexos ou não estiver usando `npm` ou `yarn`, criar um script separado pode ser uma boa opção.

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)
