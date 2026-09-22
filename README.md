# 🐾 Instituto Patas & Laços - Plataforma Web (SPA)

> **Resgatando vidas, reconstruindo lares.** Uma Single Page Application (SPA) desenvolvida para otimizar a gestão de projetos, atração de voluntários e captação de recursos para o ecossistema de proteção animal.

---

## 📖 Sobre o Projeto
Esta aplicação front-end foi construída para modernizar a presença digital do Instituto Patas & Laços. A plataforma permite navegação fluida sem recarregamento da página, apresentação dinâmica de campanhas, gerenciamento acessível de foco e retenção contínua do histórico de doações do usuário, garantindo uma experiência interativa, inclusiva e de alto desempenho.

---

## ✨ Funcionalidades Principais
* **Roteamento Dinâmico (SPA):** Navegação instantânea entre as seções (Início, Projetos, Voluntariado, Doações) gerenciada via JavaScript modular (`router.js`) e manipulação programática da árvore do DOM.
* **Acessibilidade Instrumental (WCAG 2.1 AA):** Gerenciamento dinâmico de foco (`tabindex="-1"` e `.focus()`) na troca de rotas, nomes acessíveis contextuais (`aria-label`) em botões de ação e anúncios em tempo real via ARIA Live Regions (`role="status"`, `aria-live="polite"`).
* **Persistência de Dados:** Armazenamento seguro de registros de voluntários e simulação de doações no `localStorage` com serialização e desserialização via `JSON.stringify` e `JSON.parse`.
* **Renderização de Componentes:** Geração automática e desacoplada de cartões de projetos e vagas através de *Template Literals* e métodos funcionais de iteração (`.map()`).
* **Feedback Visual e Interativo:** Integração com formulários reativos, notificações flutuantes (*Toasts*) e animações de celebração (*Canvas-Confetti*) após conversões de apoio.
* **Design Responsivo (Mobile-First):** Layout adaptável sustentado por CSS Grid, Flexbox, variáveis nativas (`:root`) e técnica de *Checkbox Hack* para o menu hambúrguer.

---

## 🛠️ Tecnologias Utilizadas
A arquitetura do projeto prioriza a performance nativa e padrões modernos da web:
* **HTML5:** Estrutura estritamente semântica e acessível com tags de contexto e elemento `<picture>`.
* **CSS3:** Arquitetura baseada em variáveis globais (`:root`), CSS Grid Layout, Flexbox e metodologia BEM.
* **JavaScript (ES6+ Modules):** Lógica desacoplada com responsabilidade única (SRP), utilizando `import`/`export` nativos.
* **Vite:** Ferramenta de *build* e *bundler* para resolução de dependências, empacotamento com Rollup e minificação automatizada de código.
* **Git e GitHub:** Versionamento semântico seguindo rigorosamente a estratégia **GitFlow** (branches `main`, `develop` e `feature/*`) associada a *Conventional Commits* e validação por *Pull Requests*.

---

## ⚡ Otimização de Ativos e Performance Web
* **Logotipo e Métricas de LCP:** O principal elemento gráfico da aplicação foi otimizado migrando do formato JPEG original (~605 kB) para o formato moderno **WebP** (`logotipoCSS3.webp`), estruturado no HTML via tag `<picture>` com dimensões explícitas (`width="100"` e `height="100"`). Essa alteração reduziu o peso de transferência em mais de 85%, antecipando o *Largest Contentful Paint* (LCP) e eliminando riscos de *Cumulative Layout Shift* (CLS).
* **Minificação de Código:** O pipeline de compilação gera artefatos otimizados na pasta `dist/`, totalizando apenas ~20.97 kB de código unificado (HTML, CSS e JS), resultando em uma carga inicial de apenas **~6.35 kB transferidos sob compressão Gzip**.

---

## 🚀 Deploy e Roteamento em Produção (Vercel)

A aplicação está publicada na plataforma **Vercel**, integrada à esteira de entrega contínua (CI/CD) a partir da branch `main`.

### Estratégia de Roteamento SPA e Fallback
Em servidores web estáticos convencionais, requisições diretas a caminhos internos (ou o recarregamento via `F5` em uma subrota) resultam em erro **HTTP 404 (Not Found)**, uma vez que o servidor busca arquivos físicos que não existem no disco.

Para garantir a sustentação da arquitetura Single Page Application sem interrupções:
1. A infraestrutura adota a estratégia de **Rewrite Fallback**, configurada via `vercel.json`:
   ```json
   {
     "rewrites": [
       {
         "source": "/(.*)",
         "destination": "/index.html"
       }
     ]
   }
   ```
2. Essa instrução faz com que qualquer requisição de rota seja reescrita no servidor para entregar sempre o ponto de entrada principal (`index.html`).
3. Uma vez carregado no navegador do usuário, o roteador em JavaScript (`router.js`) assume o controle da URL no cliente (*Client-Side Routing*), renderizando o componente correspondente sem disparar novas requisições de página inteira.

---

## ⚙️ Instalação Local e Execução

### Pré-requisitos
* [Node.js](https://nodejs.org/) (versão LTS recomendada)
* Gerenciador de pacotes `npm`

### Passo a passo
1. Clone o repositório:
   ```bash
   git clone git@github.com:WeltonSantosFr/CS-Front-End-Development.git
   ```
2. Acesse a pasta do projeto:
   ```bash
   cd CS-Front-End-Development
   ```
3. Instale as dependências de desenvolvimento:
   ```bash
   npm install
   ```
4. Inicie o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```
5. Para compilar e pré-visualizar a versão final minificada de produção:
   ```bash
   npm run build
   npm run preview
   ```

---

## 📂 Estrutura de Arquivos
O projeto adota o Princípio da Responsabilidade Única (SRP), separando marcação, estilo, componentes de infraestrutura e comportamento:
```text
/
├── index.html            # Ponto de entrada (Entry point) da SPA e casca semântica
├── package.json          # Manifesto do Node.js, dependências e scripts de build
├── vercel.json           # Configuração de rewrites para sustentação de rotas SPA
├── css/
│   └── index.css         # Design System (tokens, grid, responsividade e componentes)
├── js/
│   ├── main.js           # Orquestrador de inicialização e mapeamento de eventos globais
│   ├── router.js         # Motor de navegação SPA e gestão programática de foco
│   ├── ui.js             # Templates dinâmicos de interface (Template Literals)
│   └── storage.js        # Persistência e recuperação de dados no localStorage
└── assets/
    └── images/
        ├── logotipoCSS3.webp  # Ativo gráfico otimizado de alta performance
        └── logotipoCSS3.jpeg  # Ativo legado para fallback de renderização
```

---

*Desenvolvido por Welton Santos como requisito prático acadêmico para o curso de Ciência da Computação.*
