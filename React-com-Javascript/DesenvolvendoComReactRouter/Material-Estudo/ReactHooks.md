# React Hooks: o que é e como funcionam?

<img src="../img/ReactHooks-01.jpg">

## Introdução

Neste artigo, vamos aprender o que é **React Hooks** e como eles funcionam.

Seja você uma pessoa com pouca ou muita experiência desenvolvendo aplicações web com React, muito provavelmente você já utilizou componentes de função (function components) e também precisou alterar os estados de alguma aplicação.

Neste artigo, abordaremos uma forma de controlar os estados de uma aplicação através dos componentes de função.

## O que é React Hooks? Como funciona?

Até a versão 16.7 do React, algumas **funcionalidades** só eram possíveis de ser acessadas através de classes (como, por exemplo, o lifecycle). Apesar da possibilidade de criar componentes a partir de função, até essa versão, eles só recebiam propriedades, não podendo acessar todas as funcionalidades do React, como as classes.

Na versão 16.8 do React, foram lançado os **hooks**, que permitem o uso de vários recursos de forma simples através de funções. Eles também ajudam a **organizar a lógica** utilizada dentro dos **componentes**.

Dentro da nossa rotina de desenvolvimento, uma tarefa comum é a criação de um portfólio para mostrarmos as nossas habilidades para possíveis recrutamentos, um amigo ou até mesmo para que a gente possa ter um histórico da nossa evolução enquanto devs.

Normalmente, colocamos os nossos projetos dentro do Github, porém, se a gente quiser criar o nosso site para mostrar estes projetos, como faríamos?

Em nosso **projeto com React**, teremos um componente que será responsável por listar os nossos repositórios do GitHub. Gostaríamos de ter uma estrutura como esta abaixo:

```
import React from 'react';

function ListaDeRepositorios() {
  return (
   <ul>
    <li>Curso da Alura - HTML e CSS</li>
    <li>Curso da Alura - React</li>
    <li>Curso da Alura - Manipulando DOM com JS</li>
   </ul>
  );
}
export default ListaDeRepositorios;
```

Já temos a nossa lista de repositórios, correto? Porém, se a gente quiser adicionar mais repositórios, teríamos que criar mais `<li>` para isso, pois o nosso código ainda está estático. Como faremos para gerar essa lista de maneira dinâmica?

## Hook useEffect

Com o nosso componente criado, podemos começar a adicionar as funcionalidades. Iremos construir uma aplicação que lista os repositórios da nossa conta do GitHub, então precisarei acessar a API deles.

Faremos uma requisição HTTP utilizando o `fetch` do JavaScript para buscar a lista de repositórios desta API. Vale ressaltar que o `fetch` gera efeitos colaterais (desejados ou não) em nosso código, pois ele é uma operação de I/O (input/output).

A documentação oficial do React nos orienta como lidar com efeitos colaterais em nossos componentes, então vamos utilizar o hook `useEffect` para lidar com estes efeitos gerados pelo `fetch()` com o código abaixo:

```
import React, { useEffect } from 'react';
function ListaDeRepositorios() {
  useEffect(() => {
    async function carregaRepositorios () {
      const resposta = await fetch('https://api.github.com/users/julio-cesar96/repos');
      const repositorios = await resposta.json();
 return repositorios;
    }
    carregaRepositorios();
  }, []);

  return (
    <>
      ...
    </>
  );
}
export default ListaDeRepositorios;
```

O hook `useEffect` nos auxilia a lidar com os side-effects (efeitos colaterais) e podemos usá-los também como ciclo de vida do componente.

No exemplo acima, o side-effect é a chamada **API**. Este hook recebe dois parâmetros: o primeiro é uma função que será executada quando o componente for inicializado e atualizado (pode ser assíncrona ou não). Em nosso exemplo, este primeiro parâmetro é uma `arrow function` assíncrona, que faz uma requisição à API e guarda na `const resposta`, em formato de json, e, depois, na `const repositorios`. Já o segundo parâmetro indica em qual situação o side-effect irá modificar.

No nosso caso, como queremos carregar a lista somente uma vez, passamos um array vazio `[]`, pois ele garante a execução **única** (parecido com o funcionamento do `componentDidMount()`).

Agora que já estamos trazendo os dados da API, como fazemos para gerar uma **lista dinâmica** a partir desses **dados**?

## Hook useState

Com os dados da API em mãos, precisamos conseguir armazená-los em uma lista e depois exibi-los em tela, mas como podemos fazer isto?

Vamos pensar…

Usamos o hook `useEffect` para controlar os side-effects da requisição HTTP `fetch()` que fizemos, após a chamada, há uma mudança de estado dentro da nossa aplicação, pois ela passa a ter os dados vindos da API que antes não tinha. Para que possamos lidar com as mudanças de estado da nossa aplicação, iremos usar o hook `useState`. Para isso, usamos o hook desta forma:

```
import React, { useState } from 'react';
function ListaDeRepositorios() {
  const [repositorio, setRepositorio] = useState([]);
  …
 return (
    <>
      ...
    </>
  );
}
export default ListaDeRepositorios;
```

O `useState`, que permite a criação de estado no componente através de função e faz o gerenciamento do estado local do componente retorna um array como resultado. Por isso, é possível fazermos uma **desestruturação** para receber partes desse retorno. O array de retorno possui dois índices.

O primeiro valor deste array é uma variável que guarda o estado em si, que chamamos de `repositorio`. Já o segundo valor é uma variável que é uma função, e é através dela que faremos as atualizações do valor do nosso estado, usamos `setRepositorio` para nomear a nossa função, o set vem antes do nome por ser **uma convenção da comunidade**.

Como a nossa função `setRepositorio` é a responsável por alterar o estado de `repositorio`, precisamos colocá-la dentro do escopo da função `useEffect`, porque ela é a responsável por pegar os dados que vão modificar o estado da nossa aplicação. Desta forma, nossa função `useEffect` fica assim:

```
 useEffect(() => {
    async function carregaRepositorios () {
      const resposta = await fetch('https://api.github.com/users/julio-cesar96/repos');
      const repositorios = await response.json();

      setRepositorio(repositorios);
    }
    carregaRepositorios();
  }, []);
```

A diferença dentro dessa função é que retiramos o `return repositorios` e adicionamos a função `setRepositorios()`, passando como parâmetro a constante `repositorios`, pois, como foi explicado, é essa função responsável por atualizar os estado da nossa aplicação.

Agora que já temos os dados dos repositórios vindo da API do GitHub e estamos atualizando o estado da nossa aplicação com eles, o último passo é exibir ele de forma dinâmica dentro da tag `ul` desta forma:

```
import React, { useEffect, useState } from 'react';

function ListaDeRepositorios() {
    ...
    return (
        <>
          <ul>
            {repositorio.map(repositorio => (
              <li key={repositorio.id}>
                {repositorio.name}
              </li>
            ))}
          </ul>
        </>
    );
}
```

Para que fosse possível gerar dinamicamente, utilizamos o método `map()` para poder percorrer o nosso array `repositorio`, que possui a lista de repositórios, e imprimir um a um na tela.

- ### [Artigo de Júlio César Brito da Silva para a Alura](https://www.alura.com.br/artigos/react-hooks)

### [Voltar ao Menu - React: desenvolvendo em React Router com JavaScript](../menu.md)
