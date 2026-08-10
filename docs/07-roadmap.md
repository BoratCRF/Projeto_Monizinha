# Projeto Monizinha — Roadmap

**Documento:** 07 — Roadmap
**Versão:** 1.0
**Data:** 10/08/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha
**Data-alvo original da versão 1.0:** 08/08/2026
**Status atual:** Versão 1.0 em desenvolvimento

---

## Status por área

* **[HUB — VERSÃO 1.0]** Faz parte da entrega inicial.
* **[CROCHÊ — VERSÃO 1.0]** Faz parte da entrega inicial.
* **[BOLOS FAKE — VERSÃO FUTURA]** Permanecerá planejado para uma versão posterior.

Este roadmap deverá preservar essa separação durante toda a evolução do projeto.

---

# 1. Objetivo

Este documento define a evolução planejada do Projeto Monizinha ao longo de suas versões.

O roadmap deverá:

* organizar as grandes entregas;
* separar funcionalidades atuais e futuras;
* evitar expansão descontrolada do escopo;
* estabelecer prioridades;
* orientar o GitHub Projects;
* facilitar a criação de Milestones;
* preservar ideias futuras sem interromper o desenvolvimento atual;
* permitir evolução progressiva do sistema;
* reduzir retrabalho;
* manter clareza sobre o que cada versão representa.

O roadmap não substitui o backlog.

A relação entre os documentos será:

```text
PRODUCT.md
    ↓
Visão
    ↓
Arquitetura
    ↓
Backlog
    ↓
Roadmap
    ↓
Issues
    ↓
GitHub Projects
```

---

# 2. Filosofia de evolução

O Projeto Monizinha será desenvolvido de forma incremental.

Isso significa que cada versão deverá:

* possuir objetivo claro;
* entregar valor real;
* manter compatibilidade com as decisões anteriores sempre que possível;
* evitar reescrita desnecessária;
* corrigir problemas antes de adicionar complexidade;
* priorizar necessidades reais da loja.

O sistema não deverá crescer apenas porque determinada tecnologia ou funcionalidade existe.

Toda expansão deverá responder a uma necessidade comercial, técnica ou operacional.

---

# 3. Estratégia de versões

A evolução será organizada inicialmente em:

```text
0.x  → Desenvolvimento inicial
1.0  → Primeira versão funcional
1.1  → Estabilização e melhorias
1.2  → Gestão e conteúdo
1.5  → Operação comercial ampliada
2.0  → E-commerce
3.0+ → Expansões futuras
```

Essas versões representam direção geral.

O número exato poderá variar conforme a evolução real do projeto.

---

# 4. Versão 0.x — Desenvolvimento

A série `0.x` representa o período anterior ao primeiro lançamento funcional.

### Exemplos

```text
0.0.1
Estrutura inicial do repositório

0.0.2
Documentação do produto

0.1.0
Projeto Django configurado

0.2.0
Banco e models

0.3.0
Admin

0.4.0
Hub

0.5.0
Catálogo do Crochê

0.6.0
Carrinho

0.7.0
WhatsApp

0.8.0
Responsividade

0.9.0
Release Candidate
```

Esses números não precisam obrigatoriamente corresponder a Releases formais no GitHub.

Servem como referência de evolução.

---

# 5. Versão 1.0 — Primeira versão funcional

## Objetivo

Disponibilizar uma plataforma comercial utilizável publicamente para a marca Artes de Monizinha.

A versão 1.0 deverá permitir que um cliente:

1. acesse o site;
2. conheça a marca;
3. entre na Loja de Crochê;
4. navegue pelos produtos;
5. visualize categorias;
6. pesquise;
7. configure um produto;
8. adicione ao carrinho;
9. revise o pedido;
10. envie a solicitação pelo WhatsApp.

A administração deverá conseguir gerenciar o catálogo sem editar código.

---

# 6. [HUB — VERSÃO 1.0] Entregas

## Obrigatórias

* página inicial;
* identidade da Artes de Monizinha;
* acesso à Loja de Crochê;
* identificação de Bolos Fake como “Em breve”;
* página Sobre;
* FAQ;
* Contato;
* Política de Privacidade;
* links para redes sociais;
* acesso ao WhatsApp;
* navegação responsiva;
* rodapé;
* estrutura SEO básica.

---

# 7. [CROCHÊ — VERSÃO 1.0] Entregas

## Catálogo

* página inicial própria;
* categorias;
* catálogo;
* busca;
* produtos destacados;
* produtos recentes;
* páginas individuais;
* imagens;
* descrições;
* preço-base ou consulta;
* variações.

## Carrinho

* adição;
* remoção;
* alteração de quantidade;
* opções selecionadas;
* persistência na sessão;
* validação dos itens;
* resumo.

## Finalização

* revisão;
* dados básicos;
* geração da mensagem;
* integração com WhatsApp;
* indicação de que o pedido ainda será confirmado.

## Administração

* produtos;
* categorias;
* imagens;
* variações;
* FAQ;
* configurações;
* usuários;
* permissões.

---

# 8. [BOLOS FAKE — VERSÃO FUTURA] Situação na 1.0

Na versão 1.0, Bolos Fake não terá:

* catálogo;
* busca;
* categorias públicas;
* páginas de modelos;
* formulário de orçamento;
* assistente próprio;
* fluxo comercial;
* carrinho;
* finalização.

Poderá existir apenas:

```text
Artes de Monizinha Bolos Fake
Em breve
```

A estrutura técnica deverá permanecer preparada para sua inclusão futura.

---

# 9. Critérios para considerar a versão 1.0 lançada

A versão 1.0 poderá ser considerada publicada quando:

### Infraestrutura

* aplicação estiver online;
* PostgreSQL estiver conectado;
* mídia funcionar;
* arquivos estáticos funcionarem;
* HTTPS estiver ativo;
* `DEBUG=False`;
* variáveis de ambiente configuradas.

### Hub

* Home funcionar;
* páginas institucionais funcionarem;
* Crochê estiver acessível;
* links sociais funcionarem;
* WhatsApp funcionar.

### Crochê

* produtos puderem ser cadastrados;
* categorias funcionarem;
* busca funcionar;
* página de produto funcionar;
* opções funcionarem;
* carrinho funcionar;
* finalização funcionar;
* WhatsApp receber mensagem adequada.

### Administração

* superusuário funcionar;
* proprietária possuir acesso adequado;
* colaboradora possuir permissões adequadas;
* produtos puderem ser alterados sem código.

### Qualidade

* celular testado;
* desktop testado;
* principais navegadores testados;
* erros críticos corrigidos;
* fluxo comercial completo validado.

---

# 10. Funcionalidades não bloqueadoras da versão 1.0

Os seguintes recursos poderão ficar incompletos sem impedir o lançamento:

* analytics próprio;
* produtos mais visualizados;
* contador de cliques;
* sitemap avançado;
* Search Console;
* assistente guiado;
* formulário próprio de contato;
* animações;
* galeria avançada;
* filtros complexos;
* dashboard personalizada;
* relatórios;
* Bolos Fake.

Esses itens somente deverão atrasar a publicação se houver justificativa clara.

---

# 11. Versão 1.1 — Estabilização

## Objetivo

Melhorar a primeira versão com base no uso real.

### Prioridades

* correção de bugs;
* ajustes de responsividade;
* ajustes de navegação;
* melhoria dos textos;
* otimização das imagens;
* melhorias de desempenho;
* ajustes no Django Admin;
* revisão de permissões;
* melhorias no carrinho;
* melhorias na mensagem do WhatsApp.

### SEO

* sitemap;
* robots.txt;
* Google Search Console;
* meta descriptions;
* Open Graph;
* revisão dos slugs;
* melhorias de conteúdo.

---

# 12. Versão 1.2 — Gestão e conteúdo

## Objetivo

Facilitar a operação do site pela proprietária e colaboradora.

### Possíveis funcionalidades

* melhorias importantes no Django Admin;
* formulários administrativos mais simples;
* organização de produtos;
* filtros administrativos;
* ordenação visual;
* melhor gerenciamento de imagens;
* gerenciamento de banners;
* gerenciamento de conteúdo da Home;
* gerenciamento de redes sociais;
* gerenciamento mais simples de FAQ.

---

# 13. Versão 1.3 — Atendimento guiado

## Objetivo

Reduzir ainda mais o trabalho manual antes do WhatsApp.

### Funcionalidades

* assistente de atendimento;
* perguntas guiadas;
* ajuda para escolha de produto;
* seleção de categoria;
* coleta de preferências;
* montagem automática de mensagem;
* integração com o catálogo;
* direcionamento para WhatsApp.

### Importante

O assistente continuará inicialmente baseado em regras e fluxos.

Não haverá necessidade automática de IA.

---

# 14. Versão 1.4 — Analytics

## Objetivo

Entender como o site está sendo utilizado.

### Métricas possíveis

* visualizações;
* produtos mais acessados;
* categorias mais acessadas;
* cliques para WhatsApp;
* origem dos acessos;
* páginas mais acessadas;
* termos de busca;
* produtos adicionados ao carrinho;
* abandono de carrinho.

### Implementação

Poderá utilizar:

* solução externa gratuita;
* analytics próprio;
* combinação das duas opções.

A solução será escolhida conforme necessidade real.

---

# 15. Versão 1.5 — Dashboard personalizada

## Objetivo

Criar uma experiência administrativa própria.

### Usuários principais

* proprietária;
* colaboradora;
* administrador.

### Possíveis áreas

```text
Dashboard
│
├── Resumo
├── Produtos
├── Categorias
├── Imagens
├── Destaques
├── FAQ
├── Mensagens
├── Estatísticas
└── Configurações comerciais
```

O Django Admin poderá continuar existindo para tarefas técnicas.

---

# 16. [BOLOS FAKE — VERSÃO FUTURA] Fase de implementação

A Loja de Bolos Fake será iniciada somente após estabilização suficiente da versão de Crochê.

## Objetivo

Adicionar uma segunda experiência comercial independente visualmente.

### Funcionalidades

* Home própria;
* identidade própria;
* catálogo;
* categorias;
* busca;
* página de modelo;
* galeria;
* características;
* tamanho;
* formato;
* cores;
* detalhes gerais;
* formulário de orçamento;
* resumo;
* WhatsApp.

### Regra comercial

Temas específicos protegidos por direitos autorais não deverão necessariamente ser utilizados como catálogo público.

A seleção final desses temas poderá continuar ocorrendo no WhatsApp.

---

# 17. Reaproveitamento para Bolos Fake

A implementação futura deverá reaproveitar:

* `Store`;
* `Category`;
* `Product`;
* `ProductImage`;
* `ProductOptionGroup`;
* `ProductOption`;
* FAQ;
* infraestrutura Django;
* autenticação;
* PostgreSQL;
* armazenamento de mídia;
* componentes compartilhados;
* SEO;
* deploy.

Deverá possuir separadamente:

* templates;
* estilos;
* fluxo de orçamento;
* textos;
* categorias;
* experiência comercial.

---

# 18. Versão 2.0 — E-commerce

## Objetivo

Transformar a plataforma em um sistema capaz de registrar e finalizar vendas internamente.

Essa versão somente deverá ser iniciada quando houver necessidade comercial real.

---

# 19. Contas de clientes

Possíveis funcionalidades:

* cadastro;
* login;
* recuperação de senha;
* perfil;
* endereços;
* histórico;
* dados de contato;
* preferências.

O modelo de autenticação deverá ser definido antes de iniciar essa fase.

---

# 20. Pedidos internos

Novos modelos poderão incluir:

```text
Order
OrderItem
OrderStatusHistory
```

### Fluxo possível

```text
Carrinho
   ↓
Checkout
   ↓
Pedido
   ↓
Pagamento
   ↓
Produção
   ↓
Entrega
```

O WhatsApp poderá continuar sendo utilizado como canal adicional.

---

# 21. Pagamentos

Poderão ser estudadas integrações com:

* Pix;
* cartão;
* gateway brasileiro;
* outros meios necessários.

A escolha deverá considerar:

* taxas;
* segurança;
* documentação;
* manutenção;
* experiência do cliente;
* volume de vendas.

Nenhuma solução será escolhida antecipadamente.

---

# 22. Entrega e frete

Possíveis funcionalidades:

* retirada;
* entrega local;
* endereço;
* cálculo de frete;
* transportadora;
* acompanhamento.

A complexidade dependerá principalmente do tipo de produto vendido.

---

# 23. Produção

Como os produtos são artesanais, uma expansão futura poderá incluir:

* fila de produção;
* prazo;
* status;
* data esperada;
* responsável;
* observações;
* prioridade;
* materiais.

Essa área somente será desenvolvida caso o volume de pedidos justifique.

---

# 24. Estoque

Nem todo produto do Projeto Monizinha possuirá estoque tradicional.

Será necessário diferenciar:

```text
Produto pronto
Produto sob encomenda
Material disponível
Capacidade de produção
```

Por isso, um módulo de estoque somente será projetado após análise operacional.

---

# 25. Versão 2.x — Comercial avançado

Possíveis funcionalidades:

* cupons;
* promoções;
* favoritos;
* avaliações;
* recomendações;
* produtos relacionados;
* recuperação de carrinho;
* notificações;
* e-mails;
* campanhas;
* relatórios financeiros.

---

# 26. Versão 3.0 — Plataforma ampliada

A versão 3.0 não possui escopo fixo.

Possíveis caminhos:

* aplicativo;
* PWA;
* API;
* integração com marketplaces;
* integração com redes sociais;
* automação de atendimento;
* sistema de produção;
* múltiplos pontos de venda;
* novas linhas de produtos;
* novas lojas dentro do Hub.

Essa fase deverá ser decidida com base na evolução real do negócio.

---

# 27. Roadmap visual

```text
PROJETO MONIZINHA

0.x
│
├── Documentação
├── Django
├── PostgreSQL
├── Models
├── Admin
├── Hub
├── Crochê
├── Carrinho
├── WhatsApp
├── Testes
└── Deploy
     │
     ▼
1.0
PRIMEIRA VERSÃO FUNCIONAL
     │
     ▼
1.1
ESTABILIZAÇÃO + SEO
     │
     ▼
1.2
GESTÃO DE CONTEÚDO
     │
     ▼
1.3
ASSISTENTE
     │
     ▼
1.4
ANALYTICS
     │
     ▼
1.5
DASHBOARD
     │
     ▼
BOLOS FAKE
     │
     ▼
2.0
E-COMMERCE
     │
     ▼
3.0+
EXPANSÃO
```

---

# 28. Prioridade de desenvolvimento atual

O foco deverá permanecer:

```text
1. Documentação
2. Ambiente
3. Django
4. PostgreSQL
5. Models
6. Admin
7. Hub
8. Crochê
9. Carrinho
10. WhatsApp
11. Testes
12. Deploy
```

Tudo que estiver fora dessa sequência deverá ser avaliado antes de interromper o trabalho atual.

---

# 29. Política de novas ideias

Novas ideias deverão seguir este fluxo:

```text
Ideia
  ↓
Backlog
  ↓
Avaliação
  ↓
Versão
  ↓
Issue
  ↓
Desenvolvimento
```

Uma ideia nova não deverá alterar automaticamente a tarefa atual.

Essa regra existe para preservar estabilidade e reduzir mudanças frequentes de direção.

---

# 30. Política de mudanças arquiteturais

Mudanças relevantes deverão ocorrer apenas quando:

* existir erro na arquitetura atual;
* requisito real não puder ser atendido;
* risco importante for identificado;
* limitação técnica for comprovada;
* necessidade futura já tiver se tornado atual.

Não deverão ocorrer somente porque surgiu uma alternativa diferente.

Antes de uma alteração significativa deverão ser avaliados:

* motivo;
* benefício;
* impacto;
* risco;
* retrabalho;
* prazo.

---

# 31. Política de adiamento

Uma funcionalidade deverá ser candidata a adiamento quando:

* não impedir vendas;
* não impedir administração;
* não afetar segurança;
* não bloquear deploy;
* não for dependência técnica;
* puder ser implementada posteriormente;
* exigir esforço desproporcional.

Adiar não significa abandonar.

O item permanecerá registrado no backlog.

---

# 32. Milestones

## Milestone — Versão 1.0

### Objetivo

Primeira versão funcional do Hub + Crochê.

### Status

Em desenvolvimento.

---

## Milestone — Versão 1.1

### Objetivo

Estabilização e melhorias após lançamento.

---

## Milestone — Bolos Fake

Poderá ser criado quando o desenvolvimento dessa loja for iniciado.

---

## Milestone — Versão 2.0

Poderá ser criado quando houver decisão de iniciar o e-commerce completo.

---

# 33. Releases

Releases oficiais poderão ser criadas para:

```text
v1.0.0
v1.1.0
v1.2.0
v2.0.0
```

Correções poderão utilizar:

```text
v1.0.1
v1.0.2
v1.1.1
```

O padrão de versionamento será detalhado nos padrões de desenvolvimento.

---

# 34. Critérios para avançar de versão

Uma nova versão somente deverá ser priorizada quando:

1. a versão atual estiver suficientemente estável;
2. bugs críticos estiverem corrigidos;
3. existir necessidade real;
4. escopo estiver definido;
5. dependências forem conhecidas;
6. impacto estiver compreendido.

O roadmap representa direção, não obrigação de implementar tudo.

---

# 35. Riscos do roadmap

## Excesso de funcionalidades

Risco:

```text
Tentar implementar várias versões simultaneamente.
```

Mitigação:

* trabalhar apenas no milestone atual.

---

## Mudanças frequentes

Risco:

```text
Alterar arquitetura ou metodologia a cada nova ideia.
```

Mitigação:

* registrar ideias no backlog;
* manter decisões estáveis;
* mudar somente com justificativa.

---

## Crescimento prematuro

Risco:

```text
Construir sistemas para problemas que ainda não existem.
```

Mitigação:

* validar necessidade antes de desenvolver.

---

## Dívida técnica

Risco:

```text
Priorizar apenas velocidade e prejudicar manutenção futura.
```

Mitigação:

* documentação;
* revisão;
* testes;
* arquitetura modular;
* refatoração controlada.

---

# 36. Princípio de longo prazo

O objetivo não é prever exatamente como o Projeto Monizinha será daqui a vários anos.

O objetivo é garantir que:

```text
a versão atual resolva o problema atual
```

e:

```text
a arquitetura atual não impeça a próxima evolução
```

Essa será a principal filosofia do roadmap.

---

# 37. Decisões fixadas

1. A versão 1.0 será Hub + Crochê.
2. Bolos Fake ficará para uma versão futura.
3. O roadmap será incremental.
4. Novas ideias irão primeiro para o backlog.
5. A versão atual terá prioridade sobre versões futuras.
6. Bugs críticos terão prioridade.
7. Estabilização ocorrerá antes de grandes expansões.
8. SEO avançado ficará após o fluxo principal.
9. Dashboard personalizada ficará após o Django Admin.
10. Assistente guiado não bloqueará o lançamento.
11. Analytics não bloqueará o lançamento.
12. E-commerce somente será iniciado quando houver necessidade comercial.
13. Pagamento não será implementado antecipadamente.
14. A arquitetura deverá permitir crescimento sem superdimensionamento.
15. Mudanças relevantes deverão possuir justificativa.
16. O roadmap poderá evoluir sem mudar a metodologia geral do projeto.

---

# 38. Relação com outros documentos

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

A modelagem está registrada em:

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

O backlog está registrado em:

```text
/docs/06-backlog.md
```

Os padrões de desenvolvimento serão registrados em:

```text
/docs/08-development-standards.md
```

Em caso de conflito:

1. `PRODUCT.md` define o escopo;
2. `01-vision.md` define a direção;
3. `02-architecture.md` define a estrutura;
4. `03-database.md` define os dados;
5. `04-navigation.md` define os fluxos;
6. `05-design-system.md` define a interface;
7. `06-backlog.md` define o trabalho conhecido;
8. este documento define a evolução por versões.
