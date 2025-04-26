# O que é o React Router

**Em termos simples, o [React Router](https://reactrouter.com/home) DOM te permite criar "páginas" diferentes dentro da sua aplicação React sem que o navegador precise recarregar a página inteira**. Isso proporciona uma experiência de usuário muito mais fluida e rápida, simulando a navegação tradicional em um site com múltiplas páginas, mas tudo dentro de uma Single Page Application (SPA).

Pense assim: Normalmente, quando você clica em um link em um site tradicional, o navegador faz uma nova requisição para o servidor, que envia um novo arquivo HTML, CSS e JavaScript, e a página inteira é recarregada. Com o React Router DOM, a sua aplicação React "intercepta" esse clique e, em vez de fazer uma nova requisição completa, ela apenas atualiza os componentes que precisam ser alterados na tela, mantendo o restante da aplicação intacto.

## Principais Componentes e Conceitos do React Router DOM:

### 1. `BrowserRouter`:

- Este é um componente que você geralmente envolve toda a sua aplicação React no ponto mais alto (geralmente no seu arquivo `index.js` ou `App.js`).
- Ele usa a API de histórico do navegador (`pushState`, `replaceState` e o evento `popstate`) para manter a interface do usuário sincronizada com a URL no navegador. Isso permite que você use os botões "voltar" e "avançar" do navegador e também compartilhar links específicos da sua aplicação.

```
import { BrowserRouter } from 'react-router-dom';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

### 2. `Routes` e `Route`:

- O componente `<Routes>` atua como um container para agrupar múltiplas rotas `<Route>`. Ele renderiza o primeiro `<Route>` filho que corresponder à localização atual (a URL no navegador).
- O componente `<Route>` é usado para definir uma rota específica. Ele recebe duas props principais:
  - `path`: Uma string que define o padrão da URL que essa rota deve corresponder (ex: `/`, `/sobre`, `/usuarios/:id`). Você pode usar parâmetros dinâmicos com dois pontos (`:`).
  - `element`: O componente React que deve ser renderizado quando a URL corresponder ao `path`.

```
import { Routes, Route } from 'react-router-dom';
import Home from './pages/Home';
import Sobre from './pages/Sobre';
import Usuarios from './pages/Usuarios';
import UsuarioDetalhe from './pages/UsuarioDetalhe';

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/sobre" element={<Sobre />} />
      <Route path="/usuarios" element={<Usuarios />} />
      <Route path="/usuarios/:id" element={<UsuarioDetalhe />} />
    </Routes>
  );
}
```

Neste exemplo, se a URL for `/`, o componente `Home` será renderizado. Se for `/sobre`, o Sobre será renderizado, e assim por diante. Para `/usuarios/:id,` o `:id` é um parâmetro dinâmico que estará disponível no componente `UsuarioDetalhe`.

### 3. `Link` e `NavLink`:

- O componente `<Link>` é usado para criar links de navegação dentro da sua aplicação React. Ele funciona de forma semelhante a uma tag `<a>` do HTML, mas em vez de fazer uma recarga completa da página, ele apenas atualiza a URL (usando o `BrowserRouter`) e o React Router DOM renderiza o componente correspondente à nova rota.
- A prop `to` do `<Link>` especifica o caminho para o qual o link deve navegar.
- O componente `<NavLink>` é uma variação do `<Link>` que adiciona funcionalidades extras para estilizar o link que está atualmente ativo (a página que o usuário está visualizando). Ele geralmente recebe uma prop `className` ou `style` que é aplicada quando o link está ativo.

```
import { Link, NavLink } from 'react-router-dom';

function Menu() {
  return (
    <nav>
      <ul>
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <NavLink to="/sobre" className={({ isActive }) => (isActive ? 'active' : '')}>Sobre</NavLink>
        </li>
        <li>
          <Link to="/usuarios">Usuários</Link>
        </li>
      </ul>
    </nav>
  );
}
```

### 4. `useNavigate`:

Este é um Hook que te permite navegar programaticamente para diferentes rotas dentro dos seus componentes. Você obtém a função `navigate` ao chamar `useNavigate()`. Você pode então chamar essa função com o caminho desejado para fazer a navegação (útil em eventos de formulário, cliques de botões, etc.).

```
import { useNavigate } from 'react-router-dom';

function MeuComponente() {
  const navigate = useNavigate();

  const handleSubmit = () => {
    // Lógica do formulário aqui...
    navigate('/sucesso');
  };

  return (
    <form onSubmit={handleSubmit}>
      {/* ... campos do formulário ... */}
      <button type="submit">Enviar</button>
    </form>
  );
}
```

### 5. `useParams`:

Este é um Hook que te permite acessar os valores dos parâmetros dinâmicos definidos nas suas rotas (`<Route path="/usuarios/:id" ... />`). Ele retorna um objeto com os nomes dos parâmetros como chaves e seus valores como valores.

```
import { useParams } from 'react-router-dom';

function UsuarioDetalhe() {
  const { id } = useParams();
  // Agora você pode usar o valor de 'id' para buscar os detalhes do usuário
  return (
    <div>Detalhes do usuário com ID: {id}</div>
  );
}
```

### 6. `useLocation`

O `useLocation` é outro Hook fundamental que o React Router DOM oferece! Ele te dá acesso ao objeto de localização atual. Esse objeto contém informações úteis sobre a URL que o usuário está visualizando, como o pathname, search (query parameters), hash, e o state (um objeto que pode ser passado durante a navegação).

### Em termos práticos, `useLocation` te permite:

- **Acessar o caminho da URL**: Saber em qual "página" o usuário está (`location.pathname`).
- **Ler query parameters**: Extrair informações da string de consulta na URL (`location.search`). Por exemplo, se a URL for `/produtos?categoria=livros&ordenar=preco`, você pode acessar `categoria` e `ordenar`.
- **Trabalhar com hashes**: Obter a parte da URL que vem depois do `#` (`location.hash`), que é frequentemente usada para navegação dentro da mesma página.
- **Acessar o state**: Receber dados que foram passados programaticamente durante a navegação usando o componente `<Link>` ou a função `navigate` com a opção `state`. Isso é útil para passar informações entre páginas sem que elas apareçam na URL.

### Como usar o useLocation:

Você simplesmente o chama dentro de um componente funcional para obter o objeto de localização:

```
import { useLocation } from 'react-router-dom';

function MeuComponente() {
  const location = useLocation();

  console.log('Pathname:', location.pathname);
  console.log('Search:', location.search);
  console.log('Hash:', location.hash);
  console.log('State:', location.state);

  return (
    <div>
      <p>Você está em: {location.pathname}</p>
      {location.search && <p>Query: {location.search}</p>}
      {location.state?.mensagem && <p>Mensagem passada: {location.state.mensagem}</p>}
    </div>
  );
}
```

#### Em resumo, o React Router DOM é uma biblioteca poderosa que te dá as ferramentas necessárias para criar uma navegação rica e fluida em suas aplicações React para a web, permitindo que você construa SPAs com múltiplas "páginas" sem as recargas completas do navegador.

### [Voltar ao Menu - React: desenvolvendo em React Router com JavaScript](../menu.md)
