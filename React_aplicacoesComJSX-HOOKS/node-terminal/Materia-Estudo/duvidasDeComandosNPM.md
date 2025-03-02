# Tirando Dúvidas de um Comando

Em pouco tempo, já utilizamos vários comando do NPM e é comum esquecermos o que um certo comando faz, ou confundir um com o outro.

Quando isso acontecer, você sempre pode procurar pelo comando na [documentação do NPM](https://docs.npmjs.com/cli/v11/commands), ou mesmo pesquisar no Google pelo nome do comando, e a página correspondente da documentação do NPM deve aparecer como um dos primeiros resultados.

No entanto, existe uma forma mais prática de tirar suas dúvidas em relação a um comando, usando o próprio terminal: basta digitar `<comando> --help` ou `<comando> -h`.

### Exemplos:

- `npm install --help`
- `npx --help`
- `npm init --help`

Por exemplo, ao executar `npm install --help`, o terminal responde assim:

```
Install a package

Usage:
npm install [<package-spec> ...]

Options:
[-S|--save|--no-save|--save-prod|--save-dev|--save-optional|--save-peer|--save-bundle]
[-E|--save-exact] [-g|--global]
[--install-strategy <hoisted|nested|shallow|linked>] [--legacy-bundling]
[--global-style] [--omit <dev|optional|peer> [--omit <dev|optional|peer> ...]]
[--strict-peer-deps] [--prefer-dedupe] [--no-package-lock] [--package-lock-only]
[--foreground-scripts] [--ignore-scripts] [--no-audit] [--no-bin-links]
[--no-fund] [--dry-run] [--cpu <cpu>] [--os <os>]
[-w|--workspace <workspace-name> [-w|--workspace <workspace-name> ...]]
[-ws|--workspaces] [--include-workspace-root] [--install-links]

aliases: add, i, in, ins, inst, insta, instal, isnt, isnta, isntal, isntall

Run "npm help install" for more info
```

Primeiro, ele dá uma descrição rápida do que o comando faz: “Instala um pacote”. Ele também dá a sintaxe de uso e as opções que você pode adicionar ao comando.

Note que ele também informa os “**aliases**” do comando, que são os atalhos ou apelidos. No caso desse comando, em vez de usar `npm install`, você também pode escrever `npm i`, `npm add`, etc.

Por fim, o terminal também diz que você pode executar npm help install, para encontrar mais informações do comando.

O comando `npm help <comando>` irá abrir uma página no navegador com a documentação completa do comando, o que também pode ser mais prático do que buscar pela página manualmente, além de ser disponível offline.

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)
