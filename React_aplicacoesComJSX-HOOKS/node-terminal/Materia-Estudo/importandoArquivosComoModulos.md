# Importando Arquivos como Módulos

Ao trabalhar em um projeto Vite, é possível que você se depare com o seguinte erro no console do navegador:

```
Uncaught SyntaxError: Cannot use import statement outside a module
```

Esse erro não aconteceu com a gente porque, no `index.html`, a importação do `script.js` já estava sendo feita com o atributo `type="module"`:

```
<script src="script.js" type="module"></script>
```

Por padrão, o Vite trabalha com os [ECMAScript Modules (ESM)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules), tanto em arquivos JavaScript do front-end quanto do Node.

Dessa forma, caso você se depare com esse erro no futuro, basta adicionar esse atributo na importação do arquivo JavaScript e ele será utilizado como um módulo.

### [Voltar ao Menu - Node.js e terminal: dominando o ambiente de desenvolvimento front-end](../menu.md)
