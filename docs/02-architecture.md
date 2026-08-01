# Projeto Monizinha — Arquitetura do Sistema

**Documento:** 02 — Arquitetura
**Versão:** 1.0
**Data:** 20/07/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha
**Data-alvo da versão 1.0:** 08/08/2026

---

## 1. Objetivo deste documento

Este documento define a arquitetura técnica inicial do Projeto Monizinha.

Seu objetivo é estabelecer:

* como o sistema será organizado;
* quais tecnologias serão utilizadas;
* quais aplicações Django existirão;
* quais responsabilidades pertencerão a cada aplicação;
* como as duas lojas compartilharão a infraestrutura;
* como os catálogos permanecerão visual e funcionalmente separados;
* como o sistema será preparado para evolução futura;
* quais decisões técnicas deverão orientar o desenvolvimento.

A definição detalhada das tabelas, campos e relacionamentos será registrada em `docs/03-database.md`.

---

## 2. Visão arquitetural

O Projeto Monizinha será desenvolvido como uma aplicação web monolítica modular utilizando Django.

Isso significa que o sistema terá:

* um único projeto Django;
* uma única implantação principal;
* um único banco de dados PostgreSQL;
* diferentes aplicações internas;
* templates separados por área;
* recursos compartilhados quando houver responsabilidade comum.

A arquitetura será representada da seguinte maneira:

```text
Usuário
   │
   ▼
Aplicação web Django
   │
   ├── Hub Artes de Monizinha
   ├── Loja de Crochê
   ├── Loja de Bolos Fake
   ├── Conteúdo institucional
   ├── Assistente de atendimento
   └── Administração
   │
   ▼
PostgreSQL
```

As lojas serão separadas para o visitante, mas permanecerão dentro da mesma plataforma técnica.

---

## 3. Estilo arquitetural

O projeto adotará inicialmente uma arquitetura de **monólito modular**.

### Características

* todas as funcionalidades serão executadas pelo mesmo projeto Django;
* cada área possuirá uma aplicação com responsabilidade definida;
* o banco de dados será compartilhado;
* não haverá microsserviços;
* não haverá frontend separado do backend;
* não haverá API obrigatória na versão 1.0;
* as páginas serão renderizadas pelo Django;
* JavaScript será utilizado apenas para interações necessárias.

### Motivos da escolha

Essa arquitetura foi escolhida porque:

* reduz a complexidade inicial;
* permite entrega dentro do prazo;
* facilita o desenvolvimento por uma única pessoa;
* funciona bem com o Django Admin;
* simplifica autenticação, templates e banco de dados;
* permite crescimento gradual;
* reduz custos de hospedagem;
* evita duplicação entre as lojas;
* não impede a criação futura de uma API.

---

## 4. Tecnologias principais

### Backend

* Python;
* Django;
* Django ORM.

### Banco de dados

* PostgreSQL.

### Frontend

* HTML5;
* CSS3;
* Bootstrap;
* JavaScript sem framework obrigatório.

### Administração

* Django Admin.

### Versionamento

* Git;
* GitHub.

### Gerenciamento do projeto

* GitHub Issues;
* GitHub Projects;
* GitHub Milestones;
* GitHub Discussions;
* documentação em Markdown.

### Hospedagem planejada

* aplicação Django hospedada em serviço compatível com Python;
* banco PostgreSQL hospedado como serviço;
* Render como opção inicial planejada;
* domínio gratuito da plataforma durante a versão inicial.

### Imagens

O armazenamento definitivo de imagens será definido na etapa de infraestrutura.

A solução escolhida deverá permitir:

* upload pelo painel administrativo;
* persistência dos arquivos após novos deploys;
* URLs públicas seguras;
* integração com o Django;
* custo inicial zero;
* migração futura.

---

## 5. Organização geral do repositório

A estrutura principal planejada será:

```text
Projeto-Monizinha/
│
├── .github/
│   └── ISSUE_TEMPLATE/
│
├── assets/
│
├── docs/
│   ├── 01-vision.md
│   ├── 02-architecture.md
│   ├── 03-database.md
│   ├── 04-navigation.md
│   ├── 05-design-system.md
│   ├── 06-backlog.md
│   ├── 07-roadmap.md
│   ├── 08-development-standards.md
│   ├── 09-deploy.md
│   └── 10-developer-guide.md
│
├── scripts/
│
├── src/
│   ├── config/
│   ├── apps/
│   ├── templates/
│   ├── static/
│   └── manage.py
│
├── .env.example
├── .gitignore
├── CHANGELOG.md
├── LICENSE
├── PRODUCT.md
├── README.md
└── requirements.txt
```

---

## 6. Organização do código Django

O código Django ficará dentro da pasta `src/`.

Estrutura planejada:

```text
src/
│
├── config/
│   ├── settings/
│   │   ├── base.py
│   │   ├── development.py
│   │   └── production.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
│
├── apps/
│   ├── core/
│   ├── catalog/
│   ├── crochet/
│   ├── fake_cakes/
│   ├── customer_service/
│   └── analytics/
│
├── templates/
│   ├── base/
│   ├── core/
│   ├── crochet/
│   ├── fake_cakes/
│   └── customer_service/
│
├── static/
│   ├── css/
│   ├── js/
│   ├── images/
│   └── icons/
│
└── manage.py
```

A estrutura poderá receber pequenas adaptações durante a criação do projeto Django, desde que as responsabilidades definidas neste documento sejam mantidas.

---

## 7. Aplicações Django

A versão inicial utilizará somente as aplicações necessárias para organizar as responsabilidades principais.

Não serão criadas aplicações sem uma necessidade concreta.

### 7.1 `core`

Responsável pelos recursos gerais e institucionais da plataforma.

Principais responsabilidades:

* página inicial do hub;
* página Sobre;
* página de contato;
* Política de Privacidade;
* informações de LGPD;
* perguntas frequentes;
* configurações gerais da marca;
* links de redes sociais;
* informações de contato;
* elementos compartilhados entre as lojas.

O `core` não deverá conter regras específicas de carrinho, Crochê ou Bolos Fake.

---

### 7.2 `catalog`

Responsável pela infraestrutura compartilhada dos catálogos.

Principais responsabilidades:

* produtos e modelos;
* categorias;
* imagens;
* slugs;
* produtos em destaque;
* produtos recentes;
* status de publicação;
* ordenação;
* mecanismos compartilhados de busca;
* informações comuns entre os catálogos.

O catálogo compartilhado não significa que as duas lojas terão a mesma interface.

A função dessa aplicação será centralizar apenas os dados e comportamentos realmente comuns.

---

### 7.3 `crochet`

Responsável pelas particularidades da Loja de Crochê.

Principais responsabilidades:

* página inicial da Loja de Crochê;
* catálogo visual de Crochê;
* filtros e navegação próprios;
* página individual de produto;
* variações aplicáveis aos produtos;
* seleção de quantidade;
* carrinho;
* resumo do pedido;
* geração da mensagem para o WhatsApp;
* componentes visuais específicos da loja.

O carrinho inicial poderá ser mantido na sessão do navegador, sem exigir login do cliente.

---

### 7.4 `fake_cakes`

Responsável pelas particularidades da Loja de Bolos Fake.

Principais responsabilidades:

* página inicial da Loja de Bolos Fake;
* catálogo visual de modelos;
* filtros e navegação próprios;
* página individual do modelo;
* formulário de orçamento-base;
* seleção de tamanho;
* seleção de formato;
* escolha de cores;
* detalhes gerais;
* resumo do orçamento;
* geração da mensagem para o WhatsApp;
* componentes visuais específicos da loja.

Essa aplicação não utilizará um carrinho tradicional na versão 1.0.

---

### 7.5 `customer_service`

Responsável pelo assistente guiado de atendimento e pelos recursos comuns de comunicação.

Principais responsabilidades:

* fluxo inicial do assistente;
* perguntas predefinidas;
* coleta de respostas;
* montagem do resumo;
* geração de links para o WhatsApp;
* padronização das mensagens;
* direcionamento para a loja adequada;
* tratamento dos dados temporários do atendimento.

O assistente não utilizará inteligência artificial paga na versão 1.0.

Parte dos fluxos específicos poderá utilizar serviços das aplicações `crochet` e `fake_cakes`.

---

### 7.6 `analytics`

Responsável por estatísticas internas simples.

Na versão 1.0, sua implementação será limitada e não deverá atrasar o lançamento.

Possíveis responsabilidades:

* registro de visualizações de produtos;
* registro de cliques para o WhatsApp;
* identificação de produtos mais acessados;
* dados básicos para administração.

Caso essa funcionalidade ameace o prazo da versão 1.0, a aplicação poderá ser criada sem todos os relatórios planejados ou transferida para uma versão posterior.

---

## 8. Aplicações que não serão criadas inicialmente

### `users`

Não será criado um modelo personalizado de cliente na versão inicial.

O sistema utilizará a autenticação administrativa oferecida pelo Django.

Caso seja necessário personalizar usuários administrativos, a decisão deverá ser tomada antes da primeira migração definitiva.

Contas de clientes serão consideradas em versões futuras.

### `orders`

A versão inicial não terá confirmação interna de pedidos nem pagamento.

O carrinho e o orçamento serão encaminhados para o WhatsApp.

Um módulo de pedidos poderá ser adicionado futuramente quando o sistema passar a registrar vendas internamente.

### `payments`

Não fará parte da versão 1.0.

### `api`

Não será criada apenas como preparação abstrata para o futuro.

Uma API será adicionada quando houver consumidor real, como:

* aplicativo;
* frontend separado;
* integração externa;
* serviço de automação.

### `dashboard`

Na versão 1.0, o painel principal será o Django Admin.

Uma aplicação de dashboard personalizada só será criada quando houver requisitos definidos que não sejam atendidos pelo Admin.

---

## 9. Separação entre os catálogos

A Loja de Crochê e a Loja de Bolos Fake possuirão templates, URLs e fluxos próprios.

### Crochê

```text
/croche/
/croche/produtos/
/croche/categorias/<slug>/
/croche/produtos/<slug>/
/croche/carrinho/
/croche/finalizar/
```

### Bolos Fake

```text
/bolos-fake/
/bolos-fake/modelos/
/bolos-fake/categorias/<slug>/
/bolos-fake/modelos/<slug>/
/bolos-fake/orcamento/<slug>/
/bolos-fake/finalizar/
```

Cada área poderá possuir:

* cabeçalho próprio;
* rodapé adaptado;
* cores próprias;
* banners próprios;
* cards próprios;
* linguagem comercial própria;
* formulário próprio.

A separação visual não exigirá projetos ou bancos de dados distintos.

---

## 10. Templates

Os templates serão organizados por área.

Estrutura inicial:

```text
templates/
│
├── base/
│   ├── base.html
│   ├── partials/
│   └── components/
│
├── core/
│   ├── home.html
│   ├── about.html
│   ├── contact.html
│   ├── faq.html
│   └── privacy.html
│
├── crochet/
│   ├── base_crochet.html
│   ├── home.html
│   ├── catalog.html
│   ├── product_detail.html
│   ├── cart.html
│   └── checkout_summary.html
│
├── fake_cakes/
│   ├── base_fake_cakes.html
│   ├── home.html
│   ├── catalog.html
│   ├── model_detail.html
│   ├── quote_form.html
│   └── quote_summary.html
│
└── customer_service/
    └── assistant.html
```

### Herança de templates

Existirá uma base geral para elementos compartilhados.

As lojas poderão possuir bases específicas:

```text
base.html
   ├── base_crochet.html
   └── base_fake_cakes.html
```

Assim, a estrutura comum poderá ser reutilizada sem obrigar as duas lojas a terem a mesma aparência.

---

## 11. Arquivos estáticos

Os arquivos estáticos serão separados por responsabilidade.

```text
static/
│
├── css/
│   ├── base.css
│   ├── components.css
│   ├── crochet.css
│   ├── fake-cakes.css
│   └── admin-custom.css
│
├── js/
│   ├── main.js
│   ├── crochet-cart.js
│   ├── fake-cake-quote.js
│   └── customer-assistant.js
│
├── images/
└── icons/
```

### Diretrizes

* estilos compartilhados deverão permanecer nos arquivos gerais;
* estilos específicos deverão permanecer nos arquivos de cada loja;
* JavaScript será dividido por funcionalidade;
* arquivos muito grandes deverão ser separados;
* imagens de produtos enviadas pelo Admin não serão tratadas como arquivos estáticos;
* Bootstrap poderá ser carregado inicialmente por CDN ou instalado localmente, conforme decisão de implementação.

---

## 12. Camadas da aplicação

O sistema será organizado em camadas simples.

### Apresentação

Responsável por:

* templates;
* formulários;
* componentes visuais;
* mensagens para o usuário;
* JavaScript de interface.

### Aplicação

Responsável por:

* views;
* fluxos de navegação;
* processamento de formulários;
* montagem de carrinho e orçamento;
* geração de mensagens para o WhatsApp.

### Domínio

Responsável por:

* models;
* regras relacionadas aos produtos;
* categorias;
* variações;
* disponibilidade;
* validações comerciais.

### Infraestrutura

Responsável por:

* PostgreSQL;
* armazenamento de imagens;
* variáveis de ambiente;
* hospedagem;
* logs;
* coleta de arquivos estáticos.

Para a versão inicial, essas camadas não exigirão diretórios excessivamente complexos. A separação será aplicada quando realmente melhorar a leitura e a manutenção.

---

## 13. Banco de dados

O banco oficial será PostgreSQL desde o início.

O banco armazenará, entre outros dados:

* produtos;
* modelos;
* categorias;
* imagens;
* variações;
* configurações;
* perguntas frequentes;
* conteúdo institucional;
* usuários administrativos;
* possíveis registros de visualizações e cliques.

O carrinho do Crochê não precisará ser salvo no banco na versão 1.0.

Ele poderá utilizar a sessão do Django.

O formulário de orçamento de Bolo Fake também poderá manter dados temporários na sessão até o envio ao WhatsApp.

A modelagem detalhada será definida em `docs/03-database.md`.

---

## 14. Sessões

As sessões poderão ser utilizadas para:

* carrinho temporário do Crochê;
* etapas do assistente;
* informações temporárias do orçamento;
* preservação dos dados durante a navegação.

Não deverão ser armazenadas nas sessões:

* senhas;
* credenciais;
* dados de pagamento;
* informações sensíveis desnecessárias;
* conteúdo permanente do catálogo.

---

## 15. Integração com WhatsApp

A integração inicial será realizada por meio de links com mensagens pré-preenchidas.

Fluxo:

```text
Dados selecionados
      │
      ▼
Validação e organização
      │
      ▼
Geração da mensagem
      │
      ▼
Codificação da URL
      │
      ▼
Abertura do WhatsApp
```

A lógica de geração das mensagens deverá permanecer centralizada em funções ou serviços reutilizáveis.

Não deverão existir diferentes trechos duplicados montando mensagens de WhatsApp em várias views.

As mensagens deverão identificar:

* origem do pedido;
* loja escolhida;
* produto ou modelo;
* variações selecionadas;
* quantidade, quando aplicável;
* detalhes gerais;
* dados básicos fornecidos pelo cliente;
* observações importantes.

---

## 16. Administração

A administração inicial será realizada pelo Django Admin.

O painel deverá permitir:

* cadastro de categorias;
* cadastro de produtos;
* cadastro de modelos;
* envio de imagens;
* definição de destaques;
* ativação e desativação de itens;
* edição de textos básicos;
* gerenciamento de FAQ;
* gerenciamento de usuários e permissões.

### Perfis administrativos iniciais

Poderão existir:

* desenvolvedor com acesso completo;
* proprietária com acesso ao conteúdo comercial;
* colaboradora com acesso autorizado ao conteúdo.

As permissões deverão evitar que usuários comerciais alterem configurações técnicas sem necessidade.

---

## 17. Configurações e variáveis de ambiente

Informações sensíveis serão armazenadas em variáveis de ambiente.

Exemplos:

```text
SECRET_KEY
DEBUG
DATABASE_URL
ALLOWED_HOSTS
CSRF_TRUSTED_ORIGINS
WHATSAPP_NUMBER
MEDIA_STORAGE_CONFIG
```

O arquivo `.env` local não deverá ser enviado ao GitHub.

O repositório terá apenas:

```text
.env.example
```

Esse arquivo mostrará os nomes das variáveis necessárias, sem conter valores reais ou segredos.

---

## 18. Configurações por ambiente

O projeto deverá separar configurações de desenvolvimento e produção.

### Desenvolvimento

* `DEBUG=True`;
* banco PostgreSQL local ou remoto de desenvolvimento;
* mensagens detalhadas de erro;
* execução local;
* ferramentas auxiliares de desenvolvimento.

### Produção

* `DEBUG=False`;
* hosts permitidos definidos;
* banco PostgreSQL de produção;
* arquivos estáticos configurados;
* cookies e segurança ajustados;
* logs adequados;
* segredos definidos pela plataforma de hospedagem.

A configuração comum será mantida em `base.py`.

---

## 19. Segurança

A versão inicial deverá seguir, no mínimo, as práticas oferecidas pelo Django.

### Requisitos

* proteção CSRF;
* uso do ORM;
* validação de formulários;
* senhas gerenciadas pelo Django;
* credenciais fora do código;
* `DEBUG=False` em produção;
* restrição de hosts;
* permissões administrativas;
* upload de imagens validado;
* prevenção de exposição de informações sensíveis;
* conexão HTTPS fornecida pela hospedagem;
* atualização das dependências antes do lançamento.

Não serão armazenados dados de pagamento na versão 1.0.

---

## 20. SEO técnico

A arquitetura deverá permitir:

* URLs com slugs;
* títulos e descrições por página;
* páginas individuais para produtos;
* textos alternativos para imagens;
* HTML semântico;
* canonical URLs, quando necessário;
* sitemap;
* robots.txt;
* Open Graph;
* compartilhamento adequado em redes sociais;
* redirecionamentos permanentes caso URLs futuras sejam alteradas.

A primeira versão deverá possuir a estrutura básica, mesmo que a estratégia avançada de SEO seja realizada posteriormente.

---

## 21. Desempenho

O sistema terá volume inicial pequeno, mas seguirá práticas básicas.

### Diretrizes

* otimização das imagens;
* paginação quando necessária;
* consultas eficientes;
* uso de `select_related` e `prefetch_related` quando aplicável;
* carregamento adiado de imagens;
* redução de JavaScript desnecessário;
* cache de navegador para arquivos estáticos;
* limitação de bibliotecas externas;
* páginas responsivas e leves.

Não será criada uma infraestrutura complexa de cache sem necessidade comprovada.

---

## 22. Testes

A versão inicial deverá possuir testes para os fluxos críticos.

Prioridades:

* acesso às páginas principais;
* listagem de produtos;
* filtragem por loja;
* categorias;
* busca;
* carrinho do Crochê;
* cálculo do resumo;
* formulário de orçamento;
* geração da mensagem para o WhatsApp;
* permissões administrativas;
* páginas inexistentes;
* produtos inativos.

Os testes poderão combinar:

* testes automatizados do Django;
* testes manuais;
* checklist responsivo;
* validação em navegadores diferentes.

---

## 23. Tratamento de erros

O sistema deverá possuir páginas adequadas para:

* erro 404;
* erro 403;
* erro 500.

Erros de formulários deverão ser apresentados de maneira clara.

O usuário não deverá visualizar:

* rastreamentos internos;
* configurações;
* credenciais;
* mensagens técnicas do servidor.

---

## 24. Logs e monitoramento

A versão inicial deverá registrar:

* erros da aplicação;
* falhas críticas;
* informações relevantes do deploy.

Dados pessoais não deverão ser registrados sem necessidade.

Ferramentas externas de monitoramento poderão ser avaliadas posteriormente.

---

## 25. Deploy

O fluxo de deploy planejado será:

```text
Desenvolvimento local
        │
        ▼
Commit no Git
        │
        ▼
Push para o GitHub
        │
        ▼
Deploy na hospedagem
        │
        ▼
Migrações e arquivos estáticos
        │
        ▼
Aplicação online
```

O processo detalhado será documentado em `docs/09-deploy.md`.

---

## 26. Evolução futura

A arquitetura deverá permitir futuramente:

* cadastro de clientes;
* sistema de pedidos;
* pagamentos;
* controle de estoque;
* painel administrativo personalizado;
* API;
* integração com aplicativos;
* integrações com serviços externos;
* notificações;
* relatórios;
* novos tipos de loja.

Essas possibilidades não justificam criar antecipadamente módulos vazios ou estruturas sem uso na versão atual.

---

## 27. Decisões arquiteturais fixadas

Para a versão 1.0, ficam definidas as seguintes decisões:

1. O backend será desenvolvido em Django.
2. O banco será PostgreSQL.
3. O frontend será renderizado pelo Django.
4. Bootstrap será utilizado como base visual.
5. Não será utilizado React na versão inicial.
6. O sistema será um monólito modular.
7. As duas lojas estarão no mesmo projeto.
8. Os catálogos terão experiências visuais separadas.
9. A infraestrutura compartilhada será reutilizada.
10. O Crochê terá carrinho temporário.
11. Bolos Fake terá fluxo de orçamento.
12. A finalização ocorrerá pelo WhatsApp.
13. O Django Admin será o painel inicial.
14. Não haverá pagamento online na versão 1.0.
15. Não haverá conta de cliente na versão 1.0.
16. Não será criada API sem necessidade real.
17. Credenciais serão armazenadas em variáveis de ambiente.
18. O custo obrigatório inicial deverá permanecer em R$ 0.

Mudanças nessas decisões deverão possuir justificativa técnica ou comercial documentada.

---

## 28. Critérios de aprovação da arquitetura

A arquitetura será considerada adequada quando:

* permitir a separação clara das duas lojas;
* evitar duplicação desnecessária;
* permitir gerenciamento pelo Django Admin;
* suportar o carrinho temporário;
* suportar o orçamento de Bolos Fake;
* integrar o envio para o WhatsApp;
* funcionar com PostgreSQL;
* permitir deploy gratuito;
* oferecer segurança básica;
* ser compreensível para manutenção futura;
* não criar complexidade que comprometa o prazo.

---

## 29. Relação com outros documentos

A definição do produto está registrada em:

```text
/PRODUCT.md
```

A visão está registrada em:

```text
/docs/01-vision.md
```

A modelagem detalhada será registrada em:

```text
/docs/03-database.md
```

Os fluxos de navegação serão registrados em:

```text
/docs/04-navigation.md
```

A identidade visual será registrada em:

```text
/docs/05-design-system.md
```

Em caso de conflito:

1. o `PRODUCT.md` define o escopo;
2. o `01-vision.md` define a direção;
3. este documento define a estrutura técnica.
