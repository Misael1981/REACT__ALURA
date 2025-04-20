# React Icons

## O que são os ícones do React?

O React Icons é uma biblioteca que permite importar ícones populares diretamente como componentes React. A grande vantagem é que você não precisa se preocupar em baixar arquivos de ícones individualmente, configurar fontes ou lidar com os complexos de SVG diretamente. Ele já traz vários conjuntos de ícones famosos, como Font Awesome, Material Design Icons, Bootstrap Icons, e muitos outros, tudo pronto para usar no seu código React.

## Por que usar o React Icons?

- **Facilidade de uso**: A importação e o uso dos ícones são super simples.
- **Grande Variedade**: A biblioteca oferece acesso a uma vasta coleção de ícones de diferentes estilos.
- **Personalização**: Você pode personalizar o tamanho, o cor e outros estilos dos ícones facilmente através de adereços.
- **Desempenho**: Como são componentes SVG, os ícones são escaláveis ​​e não perdem qualidade em diferentes tamanhos.
- **Organização**: Centraliza a gestão de ícones no seu projeto.

## Como usar o React Icons:

### Passo 1: Instalação

Primeiro, você precisa instalar o pacote [react-icons](https://react-icons.github.io/react-icons/) no seu projeto React. Abra seu terminal na pasta do projeto e execute um dos seguintes comandos, dependendo do seu gerenciador de pacotes (npm ou fio):

```
npm install react-icons --save
```

### Passo 2: Importando os Ícones

Após a instalação, você pode importar os ícones que deseja usar diretamente dos pacotes de ícones específicos dentro de `react-icons`. A estrutura de importação segue o padrão:

```
import { NomeDoIcone } from 'react-icons/NomeDoPacoteDeIcones';
```

### Vejamos alguns exemplos de pacotes e como importar ícones deles:

- **Fonte Awesome 5 (fa)**:

```
import { FaBeer } from 'react-icons/fa';
import { FaHome } from 'react-icons/fa';
```

- #### Ícones do Material Design (md):

```
import { MdAlarm } from 'react-icons/md';
import { MdSettings } from 'react-icons/md';
```

- #### Ícones do Bootstrap (bi):

```
import { BiAlarm } from 'react-icons/bi';
import { BiWifi } from 'react-icons/bi';
```

- #### Heroicons (oi):

```
import { HiOutlineBell } from 'react-icons/hi';
import { HiSolidUser } from 'react-icons/hi';
```

Você pode encontrar uma lista completa de pacotes de ícones disponíveis e os nomes dos ícones na [documentação oficial do React Icons](https://react-icons.github.io/react-icons/).

### Passo 3: Utilizando os Ícones em seus Componentes

Uma vez importado, o ícone se comporta como um componente React normal. Você pode renderizá-lo diretamente no seu JSX:

```
import React from 'react';
import { FaBeer, FaHome } from 'react-icons/fa';
import { MdAlarm } from 'react-icons/md';

function MeuComponente() {
  return (
    <div>
      <FaBeer /> {/* Renderiza o ícone de cerveja do Font Awesome */}
      <FaHome size="32" color="blue" /> {/* Ícone de casa com tamanho e cor personalizados */}
      <MdAlarm style={{ fontSize: '2em', color: 'green' }} /> {/* Ícone de alarme com estilos inline */}
    </div>
  );
}

export default MeuComponente;
```

Personalizando os ícones:

Você pode personalizar a aparência dos ícones passando pelos adereços do componente:

- `size`: Defina o tamanho do ícone (aceita números para pixels ou strings como '1.5em', '32px').
- `color`: Definir a cor do ícone (aceita nomes de núcleos, códigos hexadecimais, etc.).
- `style`: Permite aplicar estilos CSS inline diretamente ao ícone.
- `className`: Permite aplicar classes CSS para estilizar o ícone através de um arquivo CSS.

### [Voltar ao Menu - React: como os componentes funcionam](../menu.md)
