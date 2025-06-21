# EasyStoreHub

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
- **Vite.js**
### Backend as a Service (BaaS)
- **Supabase**

**Vantagens do BaaS**
- Rede de Infraestrutura: Você não precisa se preocupar com a configuração de servidores e escalabilidade.

- Economia de Tempo: As funcionalidades são prontamente disponíveis, permitindo que você se concentre mais na lógica do seu aplicativo.
  
- Escalabilidade: A maioria das plataformas BaaS lida automaticamente com a escalabilidade, permitindo que o seu aplicativo cresça sem reconfigurações complexas.
- Segurança: Recursos integrados para autenticação, proteção de dados e gerenciamento de usuários.
---
## Estrutura do projeto

```Plaintext
/loja-institucional
├── /public
│   ├── favicon.ico            # Ícone do site
│   └── index.html             # Arquivo HTML principal
├── /src
│   ├── /assets                 # Imagens, ícones e outros recursos estáticos
│   │   ├── /images             # Imagens do site
│   │   └── /icons              # Ícones (por exemplo, do FontAwesome)
│   ├── /components             # Componentes reutilizáveis
│   │   ├── Button.vue          # Botão personalizado
│   │   ├── ProductCard.vue     # Cartão de produto
│   │   ├── CartModal.vue       # Modal do carrinho de compras
│   │   └── Header.vue          # Cabeçalho do site
│   ├── /views                  # Páginas do site
│   │   ├── Home.vue            # Página inicial
│   │   ├── Products.vue        # Página de listagem de produtos
│   │   ├── ProductDetail.vue    # Página de detalhes do produto
│   │   └── Checkout.vue        # Página de checkout
│   ├── /services                # Serviços para interação com o Supabase
│   │   └── supabaseService.js   # Funções para chamar a API do Supabase
│   ├── /store                  # Gerenciamento de estado (se necessário)
│   │   └── index.js            # Configuração do estado global
│   ├── /router                 # Configuração das rotas
│   │   └── index.js            # Definições das rotas
│   ├── /styles                 # Estilos globais e variáveis
│   │   ├── main.css            # Estilo principal
│   │   └── variables.css       # Variáveis de estilo
│   ├── App.vue                 # Componente principal do aplicativo
│   ├── main.js                 # Ponto de entrada do JavaScript
│   └── utils.js                # Funções utilitárias
│   └── supabaseClient.js       # Configuração do cliente Supabase
├── /tests                      # Testes do projeto (se necessário)
│   └── example.test.js         # Exemplo de arquivo de teste
├── package.json                # Dependências e scripts do projeto
├── vite.config.js              # Configurações do Vite
└── README.md                   # Documentação do projeto
```
