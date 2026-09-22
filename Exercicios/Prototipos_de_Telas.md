# Prática Flexbox

> **Objetivo geral:** Construir as interfaces de sistema usando **exclusivamente CSS Flexbox**.

---

## Regras gerais

- Usar apenas `display: flex` para os layouts.

- O HTML deve ser semântico: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`.
- Os arquivos devem seguir as imagens da página 

---

## Exemplo 1 — Tela de Login

### Contexto

O sistema de almoxarifado possui três perfis de acesso: Discente, Gestor e Administrador. A tela de login é o ponto de entrada único para todos eles. Ela deve transmitir credibilidade e simplicidade — quem acessa pela primeira vez precisa entender imediatamente o que fazer.

### O que construir

Uma tela de login centralizada vertical e horizontalmente na viewport, contendo:

- **Cabeçalho da tela** com logotipo (pode ser texto estilizado) e nome do sistema
- **Card central** com os seguintes elementos dispostos em coluna com espaçamento consistente:
  - Título "Acesse sua conta"
  - Subtítulo com o nome da instituição
  - Campo de e-mail com rótulo acima
  - Campo de senha com rótulo acima
  - Botão "Entrar" com largura total
  - Texto de rodapé "Esqueceu sua senha? Fale com o administrador"

### Critério de conclusão

A tela fica perfeitamente centralizada em qualquer altura de viewport. Redimensionar a janela não quebra o layout.

---

## Protótipo 2 — Barra de Navegação e Dashboard

### Contexto

Após o login, o usuário acessa o painel principal. Antes de mostrar qualquer conteúdo, é necessário criar a estrutura que vai conter todas as telas internas: uma navbar fixa no topo e uma sidebar lateral com o menu de navegação.

### O que construir

**Navbar (topo):** barra horizontal de 60px de altura com três zonas lado a lado:

- Zona esquerda: logotipo + nome do sistema
- Zona central: campo de busca (input text com placeholder "Buscar equipamento...")
- Zona direita: ícone de notificações + avatar circular com inicial do usuário + nome e papel (ex: "João Silva — Gestor")

**Área principal:** área abaixo da navbar dividida em duas colunas:

- **Sidebar** (esquerda): largura fixa de `240px`, com links de menu em coluna. Inclua ao menos 5 itens: Início, Catálogo, Empréstimos, Devoluções, Configurações. O item ativo pode ter estilo diferenciado.
- **Área de conteúdo** (direita): ocupando todo o espaço restante.


### Restrições

- A sidebar não deve encolher quando o conteúdo principal for grande.
- O campo de busca deve crescer automaticamente para preencher o espaço entre logo e avatar.
- A altura da área principal deve preencher o restante da tela: `calc(100vh - 60px)`.

### Critério de conclusão

A navbar mantém as três zonas proporcionais ao redimensionar. A sidebar permanece com 240px fixos e o conteúdo ocupa o resto.

---

## Protótipo 3 — Cards de Estatística e Catálogo de Equipamentos


### Contexto

A área de conteúdo do dashboard, criada vazia no protótipo anterior, agora será preenchida com dois blocos essenciais para o Gestor: um resumo visual rápido do estado do almoxarifado (cards de estatística) e o catálogo completo de equipamentos disponíveis para empréstimo.

### O que construir
### 3.1 - Cards de estatística
**Bloco de estatísticas:** faixa horizontal com 4 cards lado a lado que quebram para a próxima linha em telas menores. Cada card exibe:

- Um número grande em destaque (ex: `42`)
- Um rótulo descritivo abaixo (ex: "Equipamentos cadastrados")
- Uma cor de acento lateral ou superior diferente para cada card (use `border-left` ou `border-top` com cores dos tokens)

Os quatro cards devem representar: **Total de Equipamentos**, **Empréstimos Ativos**, **Devoluções Pendentes**, **Itens em Manutenção**.
### 3.2 - Catálogo de equipamentos
Listagem de cards que quebra automaticamente. Cada card de equipamento exibe, em coluna interna:

- Área de imagem (pode ser um `div` colorido com altura fixa de `160px` representando a foto)
- Área de informações, com por exemplo: nome do equipamento, categoria (ex: "Audiovisual"), patrimônio (ex: "PAT-0042")
- Área de rodapé do card com: badge de status (Disponível / Emprestado / Manutenção) e botão de ação ("Solicitar" ou "Ver detalhes")

### Restrições

- Em telas largas (acima de 900px), o catálogo deve exibir 3 cards por linha.
- Em telas médias (600px–900px), 2 cards por linha.
- Em telas estreitas (abaixo de 600px), 1 card por linha.

### Critério de conclusão

Ao redimensionar o navegador, os cards de estatística e os cards de equipamento se reorganizam sozinhos em 1, 2 ou 3 colunas sem quebrar o layout.

---

## Protótipo 4 — Painel do Gestor: Tabela de Solicitações

### Contexto

O Gestor é a peça central do sistema — é ele quem aprova ou nega os pedidos de empréstimo e registra as devoluções. Sua tela de trabalho principal é uma lista de solicitações pendentes, com ações rápidas para cada uma.

### O que construir

### 4.1 - **Cabeçalho da seção:**
**Linha de informações**: Linha na horizontal com:

- Título "Solicitações Pendentes" (cresce para ocupar o espaço)
- Contador de itens (ex: "8 solicitações")
- Botão "Exportar" à direita

**Barra de filtros:** linha horizontal com:

- Grupo de botões de filtro por status: "Todas", "Aguardando", "Aprovadas", "Negadas" (botões lado a lado)
- Campo de busca à direita que ocupa o espaço restante

**Lista de solicitações:** Dado tabulado onde cada item da lista é uma "linha de tabela" construída com Flexbox, contendo as seguintes colunas distribuídas horizontalmente:

- **Solicitante** (nome + papel, em coluna): largura fixa de `180px`
- **Equipamento** (nome + patrimônio, em coluna): `flex: 1` (ocupa o máximo de espaço)
- **Data de solicitação**: largura fixa de `120px`, texto centralizado
- **Status**: largura fixa de `110px`, badge centralizado
- **Ações**: botões "Aprovar" e "Negar" lado a lado, largura fixa de `160px`

Inclua ao menos 5 linhas de dados fictícios. O cabeçalho da tabela deve usar as mesmas proporções das linhas.


### Restrições

- As proporções das colunas devem ser idênticas no cabeçalho e em cada linha — isso é garantido pelo Flexbox com os mesmos `flex` values.
- Os botões "Aprovar" e "Negar" devem ter estilos opostos: um preenchido (primary) e um com borda apenas (outline).
- Em telas estreitas (< 768px), as colunas de data e status podem ser escondidas com `display: none` — mas o resto deve continuar funcional com Flexbox.

### Critério de conclusão

Cabeçalho e linhas da tabela ficam perfeitamente alinhados em todas as colunas sem usar `<table>`. Redimensionar não desalinha os dados das colunas.

---
