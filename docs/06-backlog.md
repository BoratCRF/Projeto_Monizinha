# Projeto Monizinha — Backlog do Projeto

**Documento:** 06 — Backlog
**Versão:** 1.0
**Data:** 10/08/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha
**Milestone principal:** Versão 1.0

---

## Status por área

* **[HUB — VERSÃO 1.0]** Faz parte do produto inicial.
* **[CROCHÊ — VERSÃO 1.0]** Faz parte do produto inicial.
* **[BOLOS FAKE — VERSÃO FUTURA]** Permanecerá no backlog, mas não deverá interferir na implementação da versão 1.0.

O backlog deverá respeitar essa separação durante todo o desenvolvimento.

---

# 1. Objetivo

Este documento organiza todas as funcionalidades, tarefas técnicas, melhorias e trabalhos futuros conhecidos do Projeto Monizinha.

O backlog deverá permitir:

* identificar tudo que precisa ser desenvolvido;
* separar funcionalidades obrigatórias e opcionais;
* organizar tarefas por prioridade;
* diferenciar o que pertence à versão 1.0;
* preservar ideias para versões futuras;
* transformar funcionalidades em GitHub Issues;
* reduzir a possibilidade de tarefas serem esquecidas;
* evitar que novas ideias interrompam o desenvolvimento atual;
* facilitar o acompanhamento pelo GitHub Projects.

O backlog não determina necessariamente a ordem exata de implementação.

A ordem de execução será definida pelo roadmap, dependências técnicas e estado do projeto.

---

# 2. Relação com GitHub Issues

Cada item relevante deste backlog poderá gerar uma ou mais GitHub Issues.

Exemplo:

```text
Backlog:
Implementar catálogo da Loja de Crochê
```

Poderá gerar:

```text
Issue:
[CROCHÊ] Implementar página de catálogo
```

ou ser dividido em:

```text
[CROCHÊ] Criar view do catálogo
[CROCHÊ] Criar template do catálogo
[CROCHÊ] Implementar filtro por categoria
[CROCHÊ] Implementar paginação
```

O backlog registra **o que precisa existir**.

As Issues registram **o trabalho executável**.

---

# 3. Estados de trabalho

O GitHub Projects será a principal ferramenta para acompanhar o estado das tarefas.

Os estados definidos são:

```text
Backlog
   ↓
Próxima Sprint
   ↓
Em Desenvolvimento
   ↓
Revisão
   ↓
Testes
   ↓
Concluído
```

### Backlog

Tarefa conhecida, mas ainda não selecionada para implementação imediata.

### Próxima Sprint

Tarefa escolhida como próxima prioridade.

### Em Desenvolvimento

Tarefa atualmente sendo implementada.

### Revisão

Implementação concluída e aguardando revisão técnica ou funcional.

### Testes

Funcionalidade sendo validada.

### Concluído

Tarefa implementada, validada e registrada.

---

# 4. Prioridades

Serão utilizadas três prioridades principais.

## Alta

Funcionalidades:

* essenciais para o funcionamento;
* que bloqueiam outras tarefas;
* obrigatórias para publicação;
* relacionadas a segurança;
* relacionadas ao fluxo comercial principal.

Representação:

```text
Alta
```

---

## Média

Funcionalidades importantes, mas que não impedem diretamente o funcionamento principal.

Representação:

```text
Média
```

---

## Baixa

Melhorias que podem ser adiadas sem impedir a operação do site.

Representação:

```text
Baixa
```

---

# 5. Labels oficiais

As Issues deverão utilizar as labels existentes no repositório conforme a responsabilidade.

### Técnicas

```text
Backend
Frontend
Banco
Bug
Documentação
Deploy
Dashboard
SEO
Chatbot
```

### Área comercial

```text
Crochê
Bolos Fake
```

### Prioridade

```text
Alta
Média
Baixa
```

Uma Issue poderá possuir mais de uma label.

Exemplo:

```text
[CROCHÊ] Implementar carrinho

Labels:
Backend
Frontend
Crochê
Alta
```

---

# 6. Regras do backlog

1. Toda funcionalidade relevante deverá ser registrada.
2. Nem toda ideia registrada será implementada imediatamente.
3. Itens de Bolos Fake não poderão bloquear a versão 1.0.
4. Novas funcionalidades deverão ser classificadas antes de entrar em desenvolvimento.
5. Bugs críticos terão prioridade sobre novas funcionalidades.
6. Funcionalidades concluídas deverão ser refletidas no GitHub Projects.
7. Tarefas grandes deverão ser divididas em Issues menores.
8. Issues não deverão misturar funcionalidades sem relação direta.
9. Funcionalidades futuras poderão permanecer apenas neste documento até sua versão ser iniciada.
10. O backlog deverá ser atualizado conforme o projeto evoluir.

---

# 7. [GERAL — VERSÃO 1.0] Fundação do projeto

## BKL-001 — Estruturar repositório

**Prioridade:** Alta
**Status:** Concluído
**Labels:** Documentação

### Objetivo

Criar a estrutura inicial do Projeto Monizinha.

### Inclui

* `docs/`;
* `src/`;
* `assets/`;
* `scripts/`;
* `.github/`;
* estrutura de Issues;
* arquivos principais do projeto.

---

## BKL-002 — Configurar GitHub

**Prioridade:** Alta
**Status:** Concluído
**Labels:** Documentação

### Inclui

* repositório;
* Issues;
* Projects;
* Milestone;
* Labels;
* Discussions;
* Wiki.

---

## BKL-003 — Criar documentação inicial

**Prioridade:** Alta
**Status:** Em andamento
**Labels:** Documentação

### Inclui

* `PRODUCT.md`;
* `01-vision.md`;
* `02-architecture.md`;
* `03-database.md`;
* `04-navigation.md`;
* `05-design-system.md`;
* `06-backlog.md`;
* `07-roadmap.md`;
* `08-development-standards.md`;
* `09-deploy.md`;
* `10-developer-guide.md`.

---

# 8. [GERAL — VERSÃO 1.0] Ambiente de desenvolvimento

## BKL-010 — Preparar ambiente Python

**Prioridade:** Alta
**Labels:** Backend

### Inclui

* verificar versão do Python;
* criar ambiente virtual;
* atualizar `pip`;
* instalar dependências;
* validar execução local.

---

## BKL-011 — Criar projeto Django

**Prioridade:** Alta
**Labels:** Backend

### Inclui

* criação dentro de `src/`;
* configuração inicial;
* estrutura `config`;
* separação adequada das configurações;
* execução local.

---

## BKL-012 — Criar aplicações Django

**Prioridade:** Alta
**Labels:** Backend

### Aplicações previstas

* `core`;
* `catalog`;
* `crochet`;
* `customer_service`.

Aplicações somente deverão ser criadas quando necessárias.

Aplicações exclusivas de Bolos Fake não fazem parte da versão 1.0.

---

## BKL-013 — Configurar variáveis de ambiente

**Prioridade:** Alta
**Labels:** Backend, Deploy

### Inclui

* `.env`;
* `.env.example`;
* `SECRET_KEY`;
* `DEBUG`;
* `DATABASE_URL`;
* `ALLOWED_HOSTS`;
* número do WhatsApp;
* demais configurações sensíveis.

O `.env` real não deverá ser versionado.

---

# 9. [GERAL — VERSÃO 1.0] PostgreSQL

## BKL-020 — Instalar e configurar PostgreSQL

**Prioridade:** Alta
**Labels:** Banco

### Inclui

* instalação local;
* criação do banco;
* criação de usuário;
* permissões;
* teste de conexão.

---

## BKL-021 — Integrar PostgreSQL ao Django

**Prioridade:** Alta
**Labels:** Banco, Backend

### Critério

O Django deverá executar corretamente utilizando PostgreSQL.

SQLite não será utilizado como banco principal do projeto.

---

## BKL-022 — Implementar modelos principais

**Prioridade:** Alta
**Labels:** Banco, Backend

### Modelos

* `Store`;
* `Category`;
* `Product`;
* `ProductImage`;
* `ProductOptionGroup`;
* `ProductOption`;
* `FAQ`;
* `SiteSettings`.

A implementação deverá seguir `docs/03-database.md`.

---

## BKL-023 — Criar migrações

**Prioridade:** Alta
**Labels:** Banco, Backend

### Inclui

* gerar migrations;
* revisar migrations;
* aplicar no banco;
* validar estrutura.

---

# 10. [GERAL — VERSÃO 1.0] Administração

## BKL-030 — Configurar Django Admin

**Prioridade:** Alta
**Labels:** Backend, Dashboard

### Objetivo

Permitir administração do conteúdo sem alteração direta de código.

---

## BKL-031 — Configurar administração de produtos

**Prioridade:** Alta
**Labels:** Backend, Dashboard, Crochê

### Deve permitir

* criar;
* editar;
* ativar;
* desativar;
* destacar;
* ordenar;
* adicionar imagens;
* configurar opções.

---

## BKL-032 — Configurar administração de categorias

**Prioridade:** Alta
**Labels:** Backend, Dashboard, Crochê

---

## BKL-033 — Configurar administração de FAQ

**Prioridade:** Média
**Labels:** Backend, Dashboard

---

## BKL-034 — Configurar permissões administrativas

**Prioridade:** Alta
**Labels:** Backend, Dashboard

### Perfis

* desenvolvedor;
* proprietária;
* colaboradora.

### Objetivo

Evitar acesso desnecessário às configurações técnicas.

---

# 11. [HUB — VERSÃO 1.0] Estrutura principal

## BKL-040 — Implementar página inicial

**Prioridade:** Alta
**Labels:** Frontend

### Deve incluir

* identidade Artes de Monizinha;
* apresentação;
* acesso ao Crochê;
* identificação de Bolos Fake como futuro;
* redes sociais;
* WhatsApp;
* chamadas comerciais.

---

## BKL-041 — Implementar cabeçalho

**Prioridade:** Alta
**Labels:** Frontend

### Inclui

* marca;
* navegação;
* Crochê;
* Sobre;
* FAQ;
* Contato;
* WhatsApp;
* menu responsivo.

---

## BKL-042 — Implementar rodapé

**Prioridade:** Média
**Labels:** Frontend

### Inclui

* links;
* contato;
* redes sociais;
* privacidade;
* identificação da marca.

---

## BKL-043 — Implementar página Sobre

**Prioridade:** Média
**Labels:** Frontend

---

## BKL-044 — Implementar FAQ

**Prioridade:** Média
**Labels:** Frontend, Backend

---

## BKL-045 — Implementar página Contato

**Prioridade:** Média
**Labels:** Frontend

### Mínimo necessário

* WhatsApp;
* Instagram;
* Facebook.

O formulário próprio poderá ser adiado caso comprometa outras tarefas prioritárias.

---

## BKL-046 — Implementar Política de Privacidade

**Prioridade:** Alta
**Labels:** Frontend, Documentação

### Deve considerar

* sessões;
* WhatsApp;
* formulários;
* dados pessoais;
* serviços externos.

---

# 12. [HUB — VERSÃO 1.0] Integrações sociais

## BKL-050 — Integrar Instagram

**Prioridade:** Média
**Labels:** Frontend

### Escopo inicial

Links para o perfil oficial.

Não será obrigatória incorporação automática de publicações.

---

## BKL-051 — Integrar Facebook

**Prioridade:** Média
**Labels:** Frontend

### Escopo inicial

Link para a página oficial.

---

## BKL-052 — Criar botão geral do WhatsApp

**Prioridade:** Alta
**Labels:** Frontend

### Deve

* utilizar número configurável;
* abrir em nova interação;
* funcionar em celular e desktop;
* possuir mensagem inicial quando apropriado.

---

# 13. [CROCHÊ — VERSÃO 1.0] Página inicial

## BKL-060 — Implementar Home do Crochê

**Prioridade:** Alta
**Labels:** Frontend, Crochê

### Deve apresentar

* identidade própria;
* banner;
* categorias;
* produtos destacados;
* produtos recentes;
* explicação do processo;
* catálogo;
* WhatsApp.

---

## BKL-061 — Implementar cabeçalho próprio

**Prioridade:** Alta
**Labels:** Frontend, Crochê

### Inclui

* acesso ao Hub;
* início do Crochê;
* catálogo;
* categorias;
* busca;
* carrinho;
* WhatsApp.

---

# 14. [CROCHÊ — VERSÃO 1.0] Catálogo

## BKL-070 — Implementar catálogo

**Prioridade:** Alta
**Labels:** Frontend, Backend, Crochê

### Deve

* listar somente produtos ativos;
* limitar à Loja de Crochê;
* exibir cards;
* permitir acesso aos detalhes.

---

## BKL-071 — Implementar categorias

**Prioridade:** Alta
**Labels:** Frontend, Backend, Crochê

### Deve

* listar categorias ativas;
* mostrar produtos relacionados;
* preservar navegação para o catálogo.

---

## BKL-072 — Criar card de produto

**Prioridade:** Alta
**Labels:** Frontend, Crochê

### Deve apresentar

* imagem;
* nome;
* descrição curta;
* preço-base ou consulta;
* categoria;
* ação para detalhes.

---

## BKL-073 — Implementar produtos em destaque

**Prioridade:** Média
**Labels:** Frontend, Backend, Crochê

---

## BKL-074 — Implementar produtos recentes

**Prioridade:** Média
**Labels:** Frontend, Backend, Crochê

A identificação deverá utilizar `published_at`.

---

# 15. [CROCHÊ — VERSÃO 1.0] Busca

## BKL-080 — Implementar busca

**Prioridade:** Alta
**Labels:** Backend, Frontend, Crochê

### Pesquisar

* nome;
* descrição;
* descrição curta;
* categoria.

### Restrições

* somente Crochê;
* somente produtos ativos.

---

## BKL-081 — Criar página de resultados

**Prioridade:** Alta
**Labels:** Frontend, Crochê

### Deve tratar

* resultados encontrados;
* nenhum resultado;
* termo pesquisado;
* retorno ao catálogo.

---

# 16. [CROCHÊ — VERSÃO 1.0] Página do produto

## BKL-090 — Implementar detalhes do produto

**Prioridade:** Alta
**Labels:** Backend, Frontend, Crochê

### Deve apresentar

* nome;
* descrição;
* imagens;
* preço;
* prazo;
* personalização;
* opções;
* quantidade;
* ação para carrinho.

---

## BKL-091 — Implementar galeria

**Prioridade:** Média
**Labels:** Frontend, Crochê

### Deve permitir

* imagem principal;
* imagens adicionais;
* miniaturas ou navegação equivalente.

---

## BKL-092 — Implementar seleção de opções

**Prioridade:** Alta
**Labels:** Backend, Frontend, Crochê

### Suporte planejado

* SELECT;
* RADIO;
* CHECKBOX;
* TEXT;
* TEXTAREA;
* COLOR_TEXT;
* NUMBER.

---

## BKL-093 — Validar opções selecionadas

**Prioridade:** Alta
**Labels:** Backend, Crochê

### Validar

* grupo correto;
* opção pertencente ao produto;
* campos obrigatórios;
* opção ativa;
* valores válidos.

---

# 17. [CROCHÊ — VERSÃO 1.0] Carrinho

## BKL-100 — Criar estrutura do carrinho em sessão

**Prioridade:** Alta
**Labels:** Backend, Crochê

### Deve armazenar

* produto;
* quantidade;
* opções selecionadas.

Não deverá utilizar preço enviado pelo navegador como fonte oficial.

---

## BKL-101 — Adicionar produto ao carrinho

**Prioridade:** Alta
**Labels:** Backend, Frontend, Crochê

---

## BKL-102 — Remover produto do carrinho

**Prioridade:** Alta
**Labels:** Backend, Frontend, Crochê

---

## BKL-103 — Alterar quantidade

**Prioridade:** Alta
**Labels:** Backend, Frontend, Crochê

---

## BKL-104 — Exibir página do carrinho

**Prioridade:** Alta
**Labels:** Frontend, Backend, Crochê

### Deve apresentar

* itens;
* imagens;
* opções;
* quantidade;
* preços;
* ações;
* resumo.

---

## BKL-105 — Validar carrinho

**Prioridade:** Alta
**Labels:** Backend, Crochê

### Deve verificar

* produto existente;
* produto ativo;
* opções existentes;
* opções ativas;
* preço atual.

---

## BKL-106 — Carrinho vazio

**Prioridade:** Média
**Labels:** Frontend, Crochê

Deverá apresentar orientação para retornar ao catálogo.

---

# 18. [CROCHÊ — VERSÃO 1.0] Finalização pelo WhatsApp

## BKL-110 — Criar resumo do pedido

**Prioridade:** Alta
**Labels:** Backend, Frontend, Crochê

### Deve conter

* cliente;
* produtos;
* quantidades;
* opções;
* observações;
* informação de que o pedido ainda será confirmado.

---

## BKL-111 — Gerar mensagem do WhatsApp

**Prioridade:** Alta
**Labels:** Backend, Crochê

### Deve

* gerar texto legível;
* remover campos vazios;
* identificar origem;
* listar itens;
* listar opções;
* preservar caracteres especiais corretamente.

---

## BKL-112 — Gerar URL do WhatsApp

**Prioridade:** Alta
**Labels:** Backend, Crochê

### Deve

* utilizar número internacional;
* codificar mensagem;
* funcionar no WhatsApp Web;
* funcionar em dispositivos móveis.

---

## BKL-113 — Limpar carrinho após finalização

**Prioridade:** Média
**Labels:** Backend, Crochê

A limpeza deverá ocorrer somente em momento apropriado.

O clique no WhatsApp não deverá causar perda prematura dos itens caso o usuário precise retornar.

---

# 19. [GERAL — VERSÃO 1.0] Assistente de atendimento

## BKL-120 — Criar assistente inicial

**Prioridade:** Média
**Labels:** Chatbot, Frontend

### Objetivo

Orientar o cliente sem utilizar IA paga.

---

## BKL-121 — Criar fluxo guiado para Crochê

**Prioridade:** Média
**Labels:** Chatbot, Crochê

### Poderá ajudar com

* escolha de categoria;
* tipo de produto;
* personalização;
* direcionamento ao catálogo;
* atendimento pelo WhatsApp.

---

## BKL-122 — Integrar assistente ao WhatsApp

**Prioridade:** Média
**Labels:** Chatbot, Backend

O assistente deverá gerar uma mensagem baseada nas respostas.

### Regra

O assistente não deverá impedir o lançamento caso ainda não esteja completo.

O carrinho + WhatsApp têm prioridade superior.

---

# 20. [GERAL — VERSÃO 1.0] Imagens

## BKL-130 — Definir armazenamento de mídia

**Prioridade:** Alta
**Labels:** Backend, Deploy

### Critérios

* custo R$ 0;
* persistência;
* Django Admin;
* facilidade;
* suporte a produção.

---

## BKL-131 — Configurar upload de imagens

**Prioridade:** Alta
**Labels:** Backend

---

## BKL-132 — Validar imagens

**Prioridade:** Média
**Labels:** Backend

### Considerar

* formato;
* tamanho;
* extensão;
* conteúdo.

---

## BKL-133 — Otimizar imagens

**Prioridade:** Média
**Labels:** Frontend, Deploy

### Objetivos

* reduzir carregamento;
* preservar qualidade;
* melhorar experiência mobile;
* melhorar SEO.

---

# 21. [GERAL — VERSÃO 1.0] Responsividade

## BKL-140 — Adaptar Hub para celulares

**Prioridade:** Alta
**Labels:** Frontend

---

## BKL-141 — Adaptar catálogo para celulares

**Prioridade:** Alta
**Labels:** Frontend, Crochê

---

## BKL-142 — Adaptar página do produto

**Prioridade:** Alta
**Labels:** Frontend, Crochê

---

## BKL-143 — Adaptar carrinho

**Prioridade:** Alta
**Labels:** Frontend, Crochê

---

## BKL-144 — Adaptar finalização

**Prioridade:** Alta
**Labels:** Frontend, Crochê

---

# 22. [GERAL — VERSÃO 1.0] Acessibilidade

## BKL-150 — Implementar textos alternativos

**Prioridade:** Média
**Labels:** Frontend, SEO

---

## BKL-151 — Validar contraste

**Prioridade:** Média
**Labels:** Frontend

---

## BKL-152 — Validar navegação por teclado

**Prioridade:** Média
**Labels:** Frontend

---

## BKL-153 — Validar formulários acessíveis

**Prioridade:** Média
**Labels:** Frontend

---

# 23. [GERAL — VERSÃO 1.0] SEO básico

## BKL-160 — Implementar títulos das páginas

**Prioridade:** Média
**Labels:** SEO

---

## BKL-161 — Implementar meta descriptions

**Prioridade:** Média
**Labels:** SEO

---

## BKL-162 — Implementar URLs amigáveis

**Prioridade:** Alta
**Labels:** SEO, Backend

---

## BKL-163 — Implementar breadcrumbs

**Prioridade:** Média
**Labels:** SEO, Frontend

---

## BKL-164 — Criar sitemap

**Prioridade:** Baixa
**Labels:** SEO

Poderá ser realizado após o fluxo comercial principal.

---

## BKL-165 — Criar robots.txt

**Prioridade:** Baixa
**Labels:** SEO

---

## BKL-166 — Preparar Google Search Console

**Prioridade:** Baixa
**Labels:** SEO

Poderá ser realizado após o site estar publicamente acessível.

---

# 24. [GERAL — VERSÃO 1.0] Segurança

## BKL-170 — Configurar segurança de produção

**Prioridade:** Alta
**Labels:** Backend, Deploy

### Inclui

* `DEBUG=False`;
* `ALLOWED_HOSTS`;
* CSRF;
* HTTPS;
* cookies;
* segredos;
* configurações apropriadas.

---

## BKL-171 — Revisar permissões administrativas

**Prioridade:** Alta
**Labels:** Backend, Dashboard

---

## BKL-172 — Validar formulários

**Prioridade:** Alta
**Labels:** Backend

---

## BKL-173 — Validar upload de arquivos

**Prioridade:** Alta
**Labels:** Backend

---

# 25. [GERAL — VERSÃO 1.0] Páginas de erro

## BKL-180 — Criar página 404

**Prioridade:** Média
**Labels:** Frontend

---

## BKL-181 — Criar página 403

**Prioridade:** Baixa
**Labels:** Frontend

---

## BKL-182 — Criar página 500

**Prioridade:** Média
**Labels:** Frontend

---

# 26. [GERAL — VERSÃO 1.0] Testes

## BKL-190 — Testar modelos

**Prioridade:** Alta
**Labels:** Backend, Banco

---

## BKL-191 — Testar catálogo

**Prioridade:** Alta
**Labels:** Backend, Crochê

---

## BKL-192 — Testar busca

**Prioridade:** Alta
**Labels:** Backend, Crochê

---

## BKL-193 — Testar carrinho

**Prioridade:** Alta
**Labels:** Backend, Crochê

---

## BKL-194 — Testar geração do WhatsApp

**Prioridade:** Alta
**Labels:** Backend, Crochê

---

## BKL-195 — Testar permissões

**Prioridade:** Alta
**Labels:** Backend, Dashboard

---

## BKL-196 — Testar responsividade

**Prioridade:** Alta
**Labels:** Frontend

### Dispositivos

* celular;
* tablet;
* desktop.

---

## BKL-197 — Testar navegadores

**Prioridade:** Média
**Labels:** Frontend

Prioridade:

* Chrome;
* Edge;
* Firefox;
* navegadores móveis baseados em Chromium/WebKit.

---

# 27. [GERAL — VERSÃO 1.0] Deploy

## BKL-200 — Preparar aplicação para produção

**Prioridade:** Alta
**Labels:** Deploy, Backend

---

## BKL-201 — Configurar Render

**Prioridade:** Alta
**Labels:** Deploy

---

## BKL-202 — Configurar PostgreSQL de produção

**Prioridade:** Alta
**Labels:** Deploy, Banco

---

## BKL-203 — Configurar variáveis no Render

**Prioridade:** Alta
**Labels:** Deploy

---

## BKL-204 — Configurar arquivos estáticos

**Prioridade:** Alta
**Labels:** Deploy, Frontend

---

## BKL-205 — Configurar mídia

**Prioridade:** Alta
**Labels:** Deploy

---

## BKL-206 — Executar migrations em produção

**Prioridade:** Alta
**Labels:** Deploy, Banco

---

## BKL-207 — Criar superusuário de produção

**Prioridade:** Alta
**Labels:** Deploy, Dashboard

---

## BKL-208 — Realizar teste pós-deploy

**Prioridade:** Alta
**Labels:** Deploy

### Validar

* Hub;
* Crochê;
* Admin;
* banco;
* imagens;
* carrinho;
* WhatsApp;
* páginas estáticas.

---

# 28. [GERAL — VERSÃO 1.0] Conteúdo real

## BKL-220 — Reunir informações da marca

**Prioridade:** Alta
**Labels:** Documentação

### Inclui

* apresentação;
* contato;
* WhatsApp;
* Instagram;
* Facebook;
* informações institucionais.

---

## BKL-221 — Reunir produtos de Crochê

**Prioridade:** Alta
**Labels:** Crochê

### Para cada produto

* nome;
* categoria;
* descrição;
* preço-base;
* prazo;
* opções;
* personalizações;
* fotos.

---

## BKL-222 — Organizar imagens

**Prioridade:** Alta
**Labels:** Crochê

---

## BKL-223 — Criar categorias reais

**Prioridade:** Alta
**Labels:** Crochê

---

## BKL-224 — Criar FAQ real

**Prioridade:** Média
**Labels:** Documentação, Crochê

---

# 29. [BOLOS FAKE — VERSÃO FUTURA] Backlog preservado

Os itens abaixo permanecerão registrados, mas **não deverão entrar em desenvolvimento durante a versão 1.0**.

---

## BKL-F001 — Ativar Loja de Bolos Fake

**Versão:** Futura
**Prioridade atual:** Baixa
**Labels:** Bolos Fake

---

## BKL-F002 — Criar identidade visual própria

**Versão:** Futura
**Labels:** Frontend, Bolos Fake

---

## BKL-F003 — Criar catálogo de modelos

**Versão:** Futura
**Labels:** Backend, Frontend, Bolos Fake

---

## BKL-F004 — Criar categorias de Bolos Fake

**Versão:** Futura
**Labels:** Bolos Fake, Banco

---

## BKL-F005 — Criar página de modelo

**Versão:** Futura
**Labels:** Frontend, Bolos Fake

---

## BKL-F006 — Criar opções de tamanho

**Versão:** Futura
**Labels:** Backend, Bolos Fake

---

## BKL-F007 — Criar opções de formato

**Versão:** Futura
**Labels:** Backend, Bolos Fake

---

## BKL-F008 — Criar seleção de cores

**Versão:** Futura
**Labels:** Backend, Frontend, Bolos Fake

---

## BKL-F009 — Criar formulário de orçamento

**Versão:** Futura
**Labels:** Backend, Frontend, Bolos Fake

---

## BKL-F010 — Gerar resumo do orçamento

**Versão:** Futura
**Labels:** Backend, Bolos Fake

---

## BKL-F011 — Integrar orçamento ao WhatsApp

**Versão:** Futura
**Labels:** Backend, Bolos Fake

---

## BKL-F012 — Criar assistente específico de Bolos Fake

**Versão:** Futura
**Labels:** Chatbot, Bolos Fake

---

# 30. [FUTURO] E-commerce

Os itens desta seção somente deverão ser considerados após validação da necessidade comercial.

## BKL-F020 — Criar cadastro de clientes

---

## BKL-F021 — Criar login de clientes

---

## BKL-F022 — Criar sistema interno de pedidos

---

## BKL-F023 — Criar histórico de pedidos

---

## BKL-F024 — Implementar pagamento online

---

## BKL-F025 — Implementar Pix

---

## BKL-F026 — Implementar cartão

---

## BKL-F027 — Implementar cálculo de frete

---

## BKL-F028 — Criar controle de estoque

---

## BKL-F029 — Criar acompanhamento de produção

---

## BKL-F030 — Criar cupons

---

## BKL-F031 — Criar favoritos

---

## BKL-F032 — Criar avaliações de clientes

---

# 31. [FUTURO] Dashboard personalizada

## BKL-F040 — Projetar dashboard própria

**Labels:** Dashboard

---

## BKL-F041 — Criar página inicial administrativa

---

## BKL-F042 — Criar gestão visual de produtos

---

## BKL-F043 — Criar estatísticas

---

## BKL-F044 — Criar relatórios

---

## BKL-F045 — Criar controle de pedidos

---

## BKL-F046 — Criar gestão de usuários comerciais

---

# 32. [FUTURO] Analytics

## BKL-F050 — Registrar visualizações

---

## BKL-F051 — Registrar cliques no WhatsApp

---

## BKL-F052 — Produtos mais acessados

---

## BKL-F053 — Categorias mais acessadas

---

## BKL-F054 — Origem dos acessos

---

## BKL-F055 — Taxa de envio para WhatsApp

---

# 33. [FUTURO] SEO avançado

## BKL-F060 — Google Search Console

---

## BKL-F061 — Structured Data

---

## BKL-F062 — Open Graph completo

---

## BKL-F063 — Estratégia de palavras-chave

---

## BKL-F064 — Otimização de páginas de produto

---

## BKL-F065 — Conteúdo indexável adicional

---

# 34. Itens explicitamente fora da versão 1.0

Os seguintes recursos não poderão ser tratados como bloqueadores da primeira versão:

```text
Loja funcional de Bolos Fake
Pagamento online
Login de cliente
Área do cliente
Estoque
Frete automático
Cupons
Favoritos
Dashboard personalizada
IA generativa
API pública
Aplicativo móvel
Sistema completo de pedidos
Relatórios avançados
SEO avançado
```

---

# 35. Backlog mínimo crítico da versão 1.0

Se houver necessidade de priorização extrema, estes itens formam o núcleo obrigatório.

### Fundação

* Django configurado;
* PostgreSQL funcionando;
* variáveis de ambiente;
* modelos essenciais.

### Administração

* Django Admin;
* produtos;
* categorias;
* imagens;
* opções;
* permissões.

### Hub

* página inicial;
* acesso ao Crochê;
* contato;
* WhatsApp;
* privacidade.

### Crochê

* Home;
* catálogo;
* categorias;
* produto;
* opções;
* carrinho;
* finalização;
* WhatsApp.

### Produção

* responsividade;
* segurança;
* deploy;
* banco de produção;
* mídia;
* testes críticos.

---

# 36. Critérios para retirar tarefas da versão 1.0

Um item poderá ser adiado quando:

1. não impedir vendas;
2. não comprometer segurança;
3. não impedir administração;
4. não bloquear outra funcionalidade crítica;
5. possuir alternativa simples;
6. demandar tempo desproporcional ao benefício;
7. pertencer claramente a uma versão futura.

A retirada deverá ser registrada no GitHub e, quando relevante, neste documento.

---

# 37. Critérios para adicionar novas funcionalidades

Antes de adicionar algo novo à versão 1.0, deverão ser respondidas:

1. É necessário para o cliente comprar?
2. É necessário para administrar produtos?
3. Corrige um problema crítico?
4. É necessário para segurança?
5. É necessário para colocar o site online?
6. Já existe uma alternativa suficiente?
7. Pode ser desenvolvido depois?

Se a funcionalidade puder ser desenvolvida posteriormente sem prejudicar o produto, deverá permanecer no backlog.

---

# 38. Bugs

Bugs deverão ser registrados como GitHub Issues com a label:

```text
Bug
```

### Bug crítico

Impede:

* acesso;
* cadastro;
* catálogo;
* carrinho;
* WhatsApp;
* administração;
* segurança;
* deploy.

Deverá receber prioridade:

```text
Alta
```

### Bug moderado

Existe alternativa e não interrompe completamente o fluxo.

Prioridade:

```text
Média
```

### Bug visual ou pequeno

Não impede o funcionamento.

Prioridade:

```text
Baixa
```

---

# 39. Definition of Done

Uma Issue somente deverá ser movida para **Concluído** quando aplicável:

* código implementado;
* comportamento validado;
* nenhum erro conhecido bloqueando a funcionalidade;
* responsividade básica testada;
* código salvo no Git;
* commit realizado;
* documentação atualizada, quando necessário;
* Issue atualizada ou fechada;
* item movido no GitHub Projects.

Para tarefas de documentação:

* documento criado;
* conteúdo revisado;
* salvo no repositório;
* commit realizado;
* Issue fechada;
* item movido para Concluído.

---

# 40. Definition of Ready

Uma tarefa estará pronta para desenvolvimento quando:

* objetivo estiver claro;
* escopo estiver definido;
* dependências anteriores estiverem concluídas;
* documentos necessários estiverem disponíveis;
* não existir decisão arquitetural crítica pendente;
* os critérios mínimos de conclusão forem compreensíveis.

Isso evitará iniciar tarefas sem informações suficientes.

---

# 41. Ordem macro de execução

O backlog deverá ser trabalhado seguindo aproximadamente:

```text
Documentação
      ↓
Ambiente
      ↓
Django
      ↓
PostgreSQL
      ↓
Models
      ↓
Admin
      ↓
Hub
      ↓
Catálogo de Crochê
      ↓
Produto
      ↓
Carrinho
      ↓
WhatsApp
      ↓
Responsividade
      ↓
Testes
      ↓
Deploy
      ↓
Melhorias pós-lançamento
```

O roadmap detalhará essa progressão.

---

# 42. Fonte oficial de acompanhamento

Existirão três níveis de acompanhamento.

### `docs/06-backlog.md`

Registra o escopo conhecido.

### GitHub Issues

Registra tarefas executáveis.

### GitHub Projects

Registra o estado atual de cada tarefa.

Portanto:

```text
Backlog = O que precisamos
Issues = O que faremos
Project = Onde estamos
```

---

# 43. Decisões fixadas

1. O GitHub Projects será a principal ferramenta de acompanhamento.
2. O backlog permanecerá versionado no repositório.
3. Issues serão derivadas do backlog.
4. Tarefas grandes deverão ser divididas.
5. Hub e Crochê possuem prioridade na versão 1.0.
6. Bolos Fake permanecerá no backlog futuro.
7. Pagamentos não pertencem à versão 1.0.
8. Dashboard personalizada não pertence à versão 1.0.
9. O carrinho e WhatsApp são funcionalidades críticas.
10. Django Admin é suficiente inicialmente.
11. SEO avançado não poderá bloquear publicação.
12. O assistente guiado poderá ser adiado se necessário.
13. Bugs críticos terão prioridade sobre novas funcionalidades.
14. Novas ideias não entrarão automaticamente na versão atual.
15. O backlog deverá evoluir sem mudar constantemente a metodologia do projeto.

---

# 44. Relação com outros documentos

O escopo oficial está registrado em:

```text
/PRODUCT.md
```

A visão está registrada em:

```text
/docs/01-vision.md
```

A arquitetura está registrada em:

```text
/docs/02-architecture.md
```

A modelagem de dados está registrada em:

```text
/docs/03-database.md
```

A navegação está registrada em:

```text
/docs/04-navigation.md
```

O sistema visual está registrado em:

```text
/docs/05-design-system.md
```

O planejamento das versões será registrado em:

```text
/docs/07-roadmap.md
```

Em caso de conflito:

1. `PRODUCT.md` define o escopo;
2. `01-vision.md` define a direção;
3. `02-architecture.md` define a estrutura;
4. `03-database.md` define os dados;
5. `04-navigation.md` define os fluxos;
6. `05-design-system.md` define a interface;
7. este documento organiza o trabalho.
