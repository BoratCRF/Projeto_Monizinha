# Projeto Monizinha — Documento do Produto

**Nome interno:** Projeto Monizinha
**Nome público:** Artes de Monizinha
**Versão do documento:** 1.0
**Data de início do projeto:** 20/07/2026
**Data-alvo da versão funcional:** 08/08/2026
**Status:** Em planejamento e desenvolvimento

---

## 1. Visão geral

O Projeto Monizinha é uma plataforma web criada para centralizar e divulgar duas lojas artesanais pertencentes à marca **Artes de Monizinha**:

* Artes de Monizinha Crochê;
* Artes de Monizinha Bolos Fake.

O site principal funcionará como um hub, permitindo que o visitante escolha qual das duas lojas deseja acessar.

Embora as duas lojas façam parte da mesma marca e compartilhem a mesma infraestrutura técnica, cada uma terá catálogo, identidade visual, navegação e fluxo de compra próprios.

O projeto será desenvolvido inicialmente como um catálogo comercial com atendimento e finalização dos pedidos pelo WhatsApp.

---

## 2. Problema que o projeto resolve

Atualmente, o atendimento, a apresentação dos produtos e a montagem dos pedidos dependem principalmente de conversas manuais pelas redes sociais e pelo WhatsApp.

Esse processo pode causar:

* repetição constante das mesmas explicações;
* dificuldade para apresentar todos os modelos disponíveis;
* demora na coleta das informações necessárias;
* pedidos incompletos;
* dificuldade para organizar produtos, fotos, categorias e variações;
* dependência excessiva da atendente durante as etapas iniciais da venda.

O Projeto Monizinha deverá reduzir esses problemas oferecendo uma plataforma na qual o cliente possa conhecer os produtos, selecionar características e chegar ao WhatsApp com uma solicitação organizada.

---

## 3. Objetivo principal

Criar uma plataforma profissional, responsiva e gratuita que permita:

* apresentar os produtos das duas lojas;
* separar claramente as experiências de Crochê e Bolos Fake;
* facilitar a escolha de modelos, cores, tamanhos e detalhes;
* montar pedidos ou solicitações de orçamento;
* enviar os dados organizados diretamente para o WhatsApp;
* permitir o gerenciamento dos produtos por usuários autorizados;
* construir uma base preparada para evoluir para um e-commerce completo.

---

## 4. Público-alvo

O público-alvo inicial é composto por pessoas interessadas em produtos artesanais e personalizados.

### Loja de Crochê

Clientes interessados em produtos como:

* Body temático de Times Brasileiros;
* Biquínis;
*

### Loja de Bolos Fake

Clientes interessados em produtos como:

* bolos cenográficos;
* bolos para festas infantis;
* bolos para aniversários;
* bolos para casamentos;
* bolos para mesversários;
* bolos para eventos;
* modelos personalizados para decoração.

---

## 5. Estrutura comercial

O Projeto Monizinha não será inicialmente um e-commerce com pagamento online.

O site funcionará como uma plataforma de apresentação, seleção e preparação de pedidos.

A finalização comercial acontecerá pelo WhatsApp.

### Fluxo comercial do Crochê

1. O cliente acessa a Loja de Crochê.
2. Navega pelos produtos e categorias.
3. Escolhe um produto.
4. Seleciona suas variações disponíveis.
5. Adiciona o produto ao carrinho.
6. Pode adicionar outros produtos.
7. Informa dados básicos necessários para o atendimento.
8. O site gera um resumo do pedido.
9. O cliente é encaminhado ao WhatsApp.
10. Pagamento, prazo, entrega e detalhes finais são definidos com a atendente.

### Fluxo comercial dos Bolos Fake

1. O cliente acessa a Loja de Bolos Fake.
2. Navega pelos modelos e categorias.
3. Escolhe um modelo-base.
4. Informa tamanho, formato, cores e detalhes gerais.
5. O site gera uma solicitação de orçamento.
6. O cliente é encaminhado ao WhatsApp.
7. Temas protegidos por direitos autorais, personagens, times e outras personalizações específicas serão definidos somente durante o atendimento.
8. Preço, prazo, entrega e detalhes finais são definidos com a atendente.

---

## 6. Separação entre as lojas

As lojas de Crochê e Bolos Fake deverão ser percebidas pelo visitante como ambientes distintos.

Cada loja poderá possuir:

* cores próprias;
* banners próprios;
* menu próprio;
* categorias próprias;
* página inicial própria;
* página de produto própria;
* componentes específicos;
* fluxo comercial próprio.

A infraestrutura administrativa e técnica poderá ser compartilhada sempre que isso reduzir duplicação de código sem prejudicar a identidade de cada loja.

---

## 7. Funcionalidades da versão 1.0

A versão 1.0 deverá estar funcional e online até 08/08/2026.

### Hub principal

* página inicial da marca Artes de Monizinha;
* apresentação resumida da marca;
* escolha entre Crochê e Bolos Fake;
* links para Instagram, Facebook e WhatsApp;
* acesso às páginas institucionais.

### Loja de Crochê

* página inicial própria;
* catálogo de produtos;
* categorias;
* busca;
* produtos em destaque;
* produtos recentes;
* página individual do produto;
* exibição de imagens;
* seleção de variações;
* escolha de quantidade;
* carrinho;
* edição dos itens do carrinho;
* remoção de itens;
* resumo do pedido;
* envio do pedido para o WhatsApp.

### Loja de Bolos Fake

* página inicial própria;
* catálogo de modelos;
* categorias;
* busca;
* modelos em destaque;
* modelos recentes;
* página individual do modelo;
* galeria de imagens;
* formulário de orçamento-base;
* escolha de tamanho;
* escolha de formato;
* escolha de cores;
* campo para detalhes gerais;
* resumo da solicitação;
* envio da solicitação para o WhatsApp.

### Conteúdo institucional

* página Sobre;
* FAQ;
* formulário de contato;
* Política de Privacidade;
* informações relacionadas à LGPD;
* links para redes sociais;
* galeria;
* avaliações com suporte futuro para fotos e vídeos.

### Administração

* autenticação de administradores;
* uso inicial do Django Admin;
* cadastro de produtos;
* cadastro de categorias;
* cadastro de imagens;
* edição de produtos;
* ativação e desativação de produtos;
* definição de destaques;
* gerenciamento de perguntas frequentes;
* gerenciamento de conteúdo básico;
* usuários administrativos para o desenvolvedor, a proprietária e uma colaboradora autorizada.

---

## 8. Assistente de atendimento

A versão inicial não utilizará uma API paga de inteligência artificial nem uma integração oficial automatizada com o WhatsApp.

Será criado um assistente guiado dentro do site.

Esse assistente deverá:

* identificar qual loja o cliente deseja;
* apresentar opções relevantes;
* fazer perguntas previamente definidas;
* coletar informações básicas;
* montar um resumo;
* gerar uma mensagem organizada;
* abrir o WhatsApp com a mensagem preenchida.

O objetivo não é substituir completamente o atendimento humano.

O objetivo é reduzir o tempo gasto nas etapas repetitivas e entregar à atendente uma solicitação inicial mais completa.

---

## 9. Restrições da versão inicial

O projeto deverá começar com custo de R$ 0.

Por isso, a versão 1.0 não deverá depender de:

* domínio pago;
* hospedagem paga;
* API paga do WhatsApp;
* chatbot com inteligência artificial paga;
* gateway de pagamento;
* sistema de frete pago;
* serviços obrigatoriamente pagos.

O projeto poderá utilizar planos gratuitos de serviços externos, desde que suas limitações sejam documentadas.

---

## 10. Funcionalidades fora da versão 1.0

As seguintes funcionalidades não são obrigatórias para o lançamento inicial:

* pagamento online;
* Pix integrado;
* cartão de crédito;
* controle de estoque completo;
* cálculo automático de frete;
* conta de cliente;
* histórico de pedidos do cliente;
* cupons;
* favoritos;
* avaliações públicas enviadas diretamente pelo cliente;
* painel administrativo personalizado;
* chatbot com IA;
* automação oficial dentro do WhatsApp;
* aplicativo móvel;
* integração completa com Instagram ou Facebook;
* relatórios comerciais avançados;
* emissão fiscal.

Essas funcionalidades poderão ser desenvolvidas em versões futuras.

---

## 11. Objetivos de longo prazo

O sistema deverá ser preparado para evoluir sem exigir uma reconstrução completa.

Possíveis evoluções:

* painel administrativo personalizado;
* sistema interno de pedidos;
* cadastro de clientes;
* login e área do cliente;
* pagamento por Pix e cartão;
* cálculo de frete;
* acompanhamento do pedido;
* controle de produção;
* controle de estoque;
* cupons;
* avaliações;
* relatórios de vendas;
* métricas de produtos;
* integração com serviços externos;
* API própria;
* aplicativo móvel ou Progressive Web App;
* expansão para novos tipos de produtos artesanais.

---

## 12. Requisitos de qualidade

O Projeto Monizinha deverá ser:

* responsivo;
* fácil de utilizar em celulares;
* acessível;
* seguro;
* organizado;
* documentado;
* fácil de manter;
* preparado para crescimento;
* simples para os administradores;
* visualmente coerente;
* rápido o suficiente para conexões móveis;
* compatível com os navegadores modernos.

---

## 13. Tecnologias definidas

A stack inicial do projeto será:

### Backend

* Python;
* Django.

### Banco de dados

* PostgreSQL.

### Front-end

* HTML5;
* CSS3;
* Bootstrap;
* JavaScript.

### Administração

* Django Admin na versão inicial;
* painel personalizado em versão futura.

### Versionamento e gerenciamento

* Git;
* GitHub;
* GitHub Issues;
* GitHub Projects;
* GitHub Milestones;
* documentação em Markdown.

### Hospedagem planejada

* Render ou outra plataforma compatível com Django e PostgreSQL, conforme validação técnica durante a etapa de deploy.

### Armazenamento de imagens

A solução será definida durante a etapa de arquitetura e deploy, considerando:

* custo zero;
* persistência dos arquivos;
* facilidade de integração;
* facilidade de administração;
* limitações dos planos gratuitos.

---

## 14. SEO

O projeto deverá nascer com uma estrutura básica favorável ao SEO.

Isso inclui:

* URLs descritivas;
* slugs;
* títulos de páginas;
* descrições;
* HTML semântico;
* textos alternativos em imagens;
* páginas individuais para produtos;
* estrutura preparada para sitemap;
* estrutura preparada para robots.txt;
* estrutura preparada para Google Search Console.

Exemplos de URLs:

```text
/croche/
/croche/produtos/
/croche/produtos/urso-amigurumi/

/bolos-fake/
/bolos-fake/modelos/
/bolos-fake/modelos/bolo-floral-redondo/
```

O trabalho avançado de posicionamento no Google poderá ser realizado após o lançamento da versão 1.0.

---

## 15. Indicadores de sucesso da versão 1.0

A versão inicial será considerada funcional quando:

* o site estiver acessível publicamente;
* o visitante puder escolher uma das lojas;
* os catálogos forem carregados corretamente;
* produtos puderem ser cadastrados pelo Django Admin;
* a busca e as categorias funcionarem;
* o carrinho da Loja de Crochê funcionar;
* o formulário de orçamento dos Bolos Fake funcionar;
* as mensagens forem geradas corretamente;
* o redirecionamento para o WhatsApp funcionar;
* o site funcionar adequadamente em celular e computador;
* nenhum erro crítico bloquear a navegação ou o envio de pedidos.

---

## 16. Princípios do produto

As decisões do projeto deverão seguir os seguintes princípios:

### Entregar valor primeiro

A versão 1.0 deve permitir que a loja apresente produtos e receba solicitações reais.

### Não reconstruir sem necessidade

A base deverá permitir evolução progressiva.

### Evitar complexidade prematura

Funcionalidades que não ajudam no lançamento não devem atrasar a versão 1.0.

### Separar as experiências

Crochê e Bolos Fake devem possuir identidades e jornadas próprias.

### Compartilhar a infraestrutura

Código e recursos comuns deverão ser reutilizados quando isso não comprometer as particularidades das lojas.

### Manter custo inicial zero

Nenhuma funcionalidade obrigatória da versão 1.0 deverá depender de pagamento.

### Documentar decisões importantes

Alterações relevantes de arquitetura, escopo ou tecnologia deverão ser registradas.

---

## 17. Escopo fixado

Este documento define o escopo inicial oficial do Projeto Monizinha.

Mudanças poderão acontecer durante o desenvolvimento, mas deverão ser classificadas como:

* correção;
* melhoria;
* nova funcionalidade;
* alteração de escopo;
* decisão técnica.

Alterações que possam comprometer o prazo de 08/08/2026 deverão ser adiadas para uma versão posterior, salvo quando forem indispensáveis para o funcionamento ou para a segurança do sistema.
