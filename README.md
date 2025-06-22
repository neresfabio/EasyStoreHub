# 🚧 EasyStoreHub

## Levantamento de Requisitos para Desenvolvimento de Site de Loja Virtual

### **Objetivo Geral**  
Criar um site institucional para exibir produtos de uma loja, organizados por categorias, permitindo que clientes visualizem itens, calculem o valor total do pedido e finalizem a compra via WhatsApp. O sistema deve ser gerenciável de forma intuitiva, mesmo por usuários sem experiência técnica.  

---

### **Requisitos Funcionais**  
1. **Catálogo de Produtos**  
   - Organização por categorias pré-definidas (ex.: eletrônicos, roupas, acessórios).  
   - Exibição de imagens, descrições, preços e disponibilidade dos produtos.  

2. **Gestão de Conteúdo Simplificada**  
   - Cadastro/edição de produtos com formulários simplificados (campos essenciais: nome, preço, categoria, imagem, descrição).  
   - Interface amigável para adicionar/remover categorias.  

3. **Carrinho de Compras**  
   - Seleção de múltiplos itens e cálculo automático do valor total.  
   - Visualização resumida do pedido (itens selecionados, quantidades, preço total).  

4. **Finalização de Pedido via WhatsApp**  
   - Redirecionamento automático para o WhatsApp da loja ao confirmar a compra.  
   - Envio automático de mensagem pré-formatada com detalhes do pedido (itens, total, dados do cliente).  

5. **Navegação Intuitiva**  
   - Busca por produtos (por nome ou categoria).  
   - Filtros para ordenação (preço, popularidade).  

---

### **Requisitos Não Funcionais**  
1. **Usabilidade**  
   - Interface responsiva (adaptação a celulares, tablets e desktops).  
   - Tempo de carregamento rápido para imagens e páginas.  

2. **Segurança**  
   - Proteção básica contra acesso não autorizado ao painel de gestão.  

3. **Integração com WhatsApp**  
   - Compatibilidade com envio de mensagens pré-formatadas (sem necessidade de login do cliente).  

---

### **Gestão do Site**  
- **Painel de Controle:**  
  - Acesso restrito ao dono da loja.  
  - Cadastro de produtos em até 3 passos (preenchimento de campos, upload de imagem, publicação).  
  - Visualização de pedidos recebidos via WhatsApp em uma lista simplificada.  

- **Atualizações Sem Complexidade:**  
  - Edição de preços e estoque diretamente no painel.  
  - Adição/remoção de categorias sem necessidade de codificação.  

---

### **Fluxo do Cliente**  
1. Acessa o site e navega pelas categorias.  
2. Seleciona produtos e visualiza o total no carrinho.  
3. Clica em "Finalizar Compra" e é redirecionado ao WhatsApp com o resumo do pedido.  
4. Conclui o pagamento e combina a entrega diretamente pelo WhatsApp.  

--- 

### **Observações Adicionais**  
- Não é necessário sistema de login para clientes.  
- Foco em simplicidade: evitar funcionalidades complexas (ex.: cupons de desconto, avaliações de produtos).  
- Priorizar clareza visual: layout limpo, com destaque para imagens e preços.  

--- 

**Resultado Esperado:** Site funcional, de fácil manutenção, que permita ao cliente explorar produtos e fechar pedidos de forma ágil via WhatsApp.

---
## Tecnologias
### Client
- **Vite.js + React**
### Service
- **Postgres**
---
## Sugestões de rotas para o servidor:

### 🛒 Produtos (Catálogo)

* `GET /produtos` – Listar todos os produtos
* `GET /produtos/:id` – Obter detalhes de um produto específico
* `POST /produtos` – Cadastrar um novo produto
* `PUT /produtos/:id` – Editar um produto existente
* `DELETE /produtos/:id` – Remover um produto

### 📂 Categorias

* `GET /categorias` – Listar todas as categorias
* `GET /categorias/:id` – Obter detalhes de uma categoria específica
* `POST /categorias` – Adicionar nova categoria
* `PUT /categorias/:id` – Editar uma categoria existente
* `DELETE /categorias/:id` – Remover uma categoria

### 📈 Filtros e Disponibilidade (opcional)

* `GET /produtos/categoria/:nome` – Listar produtos por categoria
* `GET /produtos/disponiveis` – Listar apenas produtos disponíveis

---

### 🧩 Modelo de Dados (Simplificado)

#### **Produto**

```plaintext
Produto {
  id: UUID
  nome: string
  preco: number
  categoriaId: UUID
  imagemUrl: string
  descricao: string
  disponibilidade: boolean
  criadoEm: Date
  atualizadoEm: Date
}
```

#### **Categoria**

```plaintext
Categoria {
  id: UUID
  nome: string
  criadoEm: Date
  atualizadoEm: Date
}
```

> Relacionamento:
> Cada **Produto** pertence a **uma Categoria** (`categoriaId`), e uma **Categoria** pode ter **vários Produtos** (relacionamento 1\:N).

---

### 🔄 Fluxos de Interação (Resumido)

#### 1. **Cadastro de Produto**

1. Usuário acessa um formulário de criação.
2. Backend oferece a lista de categorias disponíveis (`GET /categorias`).
3. Usuário preenche os dados e envia (`POST /produtos`).
4. Produto é salvo com vínculo à categoria selecionada.

#### 2. **Edição de Produto**

1. Usuário escolhe um produto para editar (`GET /produtos/:id`).
2. Sistema pré-carrega os dados do produto + categorias.
3. Após alteração, os dados são enviados (`PUT /produtos/:id`).

#### 3. **Remoção de Produto**

1. Usuário seleciona um produto e solicita exclusão (`DELETE /produtos/:id`).
2. Sistema remove o produto (ou apenas marca como inativo, se desejar manter o histórico).

#### 4. **Gestão de Categorias**

* Adicionar: `POST /categorias`
* Editar: `PUT /categorias/:id`
* Remover: `DELETE /categorias/:id`

> Dica: Antes de remover uma categoria, verificar se há produtos vinculados.

#### 5. **Listagem de Produtos**

* Página inicial: `GET /produtos` (com paginação ou filtro por categoria)
* Detalhe de um produto: `GET /produtos/:id`
* Filtro por categoria: `GET /produtos/categoria/:nome`

---

## 🚦 Início

### 🧭 **Roteiro para Desenvolvimento das Telas - Catálogo de Produtos**

#### 🧱 Etapa 1: Estrutura Base

1. **Criar layout geral da aplicação**

   * Header com nome/logo do site
   * Barra de navegação com categorias (eletrônicos, roupas, acessórios etc.)
   * Espaço central para exibição dos produtos
   * Footer com informações gerais

---

#### 📂 Etapa 2: Tela - Página Inicial / Catálogo Geral

* Mostrar todos os produtos disponíveis
* Elementos:

  * Filtro por categoria (pode ser um menu lateral ou um dropdown)
  * Campo de busca
  * Grade de produtos com:

    * Imagem
    * Nome do produto
    * Preço
    * Indicação de disponibilidade (Ex.: "Em estoque" ou "Indisponível")
* Responsividade (celular, tablet, desktop)

---

#### 📄 Etapa 3: Tela - Página de Categoria Específica

* Mostra apenas os produtos da categoria selecionada
* Destaque o nome da categoria (ex.: "Roupas")
* Pode reaproveitar o mesmo layout do catálogo geral, com filtro ativo

---

#### 🧾 Etapa 4: Tela - Detalhe do Produto (opcional, mas recomendado)

* Mostra detalhes de um produto ao clicar nele
* Elementos:

  * Imagem grande
  * Nome
  * Descrição completa
  * Preço
  * Disponibilidade
  * Botão “Voltar” ou “Adicionar ao carrinho” (se for o caso)

---

#### 📱 Etapa 5: Ajustes Visuais e Responsividade

* Garantir que o site funcione bem em:

  * Desktop
  * Tablets
  * Celulares
* Ajustar fontes, espaçamentos, tamanhos de imagem etc.

---

#### 🧪 Etapa 6: Testes manuais

* Testar cliques, filtros, categorias e busca
* Verificar se todas as informações estão sendo exibidas corretamente

---

## 🛠️ Roteiro Técnico: Organização dos Componentes React para o Catálogo de Produtos

### 📁 Estrutura de Pastas Sugerida

```
src/
│
├── assets/               # Imagens e arquivos estáticos
├── components/           # Componentes reutilizáveis
│   ├── Header.jsx
│   ├── Footer.jsx
│   ├── ProductCard.jsx
│   ├── ProductList.jsx
│   ├── CategoryFilter.jsx
│   └── SearchBar.jsx
│
├── pages/                # Páginas do site
│   ├── Home.jsx
│   ├── CategoryPage.jsx
│   └── ProductDetail.jsx
│
├── data/                 # Arquivos mock de dados (json)
│   └── products.js
│
├── App.jsx
└── main.jsx
```

---

## 🧩 Componentes Detalhados

### 🔹 `Header.jsx`

* Contém logo + menu de navegação com categorias

### 🔹 `Footer.jsx`

* Informações como redes sociais, direitos autorais, etc.

### 🔹 `SearchBar.jsx`

* Campo de input com ícone de lupa
* Prop: `onSearch(term)`

### 🔹 `CategoryFilter.jsx`

* Lista com os botões ou dropdown das categorias
* Prop: `onSelectCategory(category)`

### 🔹 `ProductCard.jsx`

* Recebe os dados de um produto via props
* Mostra:

  * Imagem
  * Nome
  * Preço
  * Disponibilidade

### 🔹 `ProductList.jsx`

* Renderiza um grid de vários `ProductCard`
* Prop: `products=[]`

---

## 📄 Páginas

### 🏠 `Home.jsx`

* Mostra todos os produtos
* Inclui:

  * `SearchBar`
  * `CategoryFilter`
  * `ProductList`

### 🗂️ `CategoryPage.jsx`

* Filtra os produtos por categoria selecionada
* Pode reutilizar `ProductList` e `CategoryFilter`

### 🔍 `ProductDetail.jsx`

* Exibe um único produto com detalhes completos

---

## 🧪 Exemplo de Arquivo de Dados (Mock)

**`src/data/products.js`**

```js
export const products = [
  {
    id: 1,
    name: "Smartphone XYZ",
    description: "Um smartphone com ótimo desempenho.",
    category: "Eletrônicos",
    price: 1499.99,
    available: true,
    image: "/assets/smartphone.jpg"
  },
  {
    id: 2,
    name: "Camiseta Branca",
    description: "Tecido 100% algodão.",
    category: "Roupas",
    price: 49.90,
    available: false,
    image: "/assets/camiseta.jpg"
  },
  // ...
];
```

---

## 🧭 Navegação com React Router (se for usar)

**Exemplo de configuração simples em `App.jsx`**

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import CategoryPage from "./pages/CategoryPage";
import ProductDetail from "./pages/ProductDetail";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/categoria/:categoria" element={<CategoryPage />} />
        <Route path="/produto/:id" element={<ProductDetail />} />
      </Routes>
    </BrowserRouter>
  );
}

export default App;
```

---


