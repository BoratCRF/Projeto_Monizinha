# Projeto Monizinha — Navegação e Fluxos do Usuário

**Documento:** 04 — Navegação
**Versão:** 1.0
**Data:** 06/08/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha
**Data-alvo da versão 1.0:** 08/08/2026

---

## Status por área

* **[HUB — VERSÃO 1.0]** Será implementado e publicado na versão 1.0.
* **[CROCHÊ — VERSÃO 1.0]** Será implementado e publicado na versão 1.0.
* **[BOLOS FAKE — VERSÃO FUTURA]** Permanecerá documentado como preparação, mas não será implementado nem publicado como loja funcional na versão 1.0.

Sempre que uma seção se referir exclusivamente a uma dessas áreas, ela deverá utilizar a identificação correspondente.

---

## 1. Objetivo

Este documento define a estrutura de navegação, as páginas públicas e os principais fluxos de usuário do Projeto Monizinha.

A navegação deverá permitir que o visitante:

* identifique rapidamente a marca Artes de Monizinha;
* acesse a Loja de Crochê;
* encontre produtos e categorias;
* visualize detalhes dos produtos;
* escolha variações;
* adicione produtos ao carrinho;
* revise o pedido;
* envie o pedido para o WhatsApp;
* encontre informações institucionais;
* acesse os canais de contato;
* compreenda que a Loja de Bolos Fake será disponibilizada futuramente.

A navegação da versão 1.0 deverá priorizar dispositivos móveis, simplicidade e redução de etapas desnecessárias.

---

## 2. Estrutura geral de navegação

```text
Artes de Monizinha
│
├── [HUB — VERSÃO 1.0]
│   ├── Página inicial
│   ├── Sobre
│   ├── FAQ
│   ├── Contato
│   ├── Política de Privacidade
│   ├── Loja de Crochê
│   └── Bolos Fake — Em breve
│
├── [CROCHÊ — VERSÃO 1.0]
│   ├── Página inicial da loja
│   ├── Catálogo
│   ├── Categorias
│   ├── Busca
│   ├── Produto
│   ├── Carrinho
│   ├── Resumo do pedido
│   └── WhatsApp
│
└── [BOLOS FAKE — VERSÃO FUTURA]
    ├── Página inicial da loja
    ├── Catálogo de modelos
    ├── Categorias
    ├── Busca
    ├── Página do modelo
    ├── Formulário de orçamento
    ├── Resumo do orçamento
    └── WhatsApp
```

Na versão 1.0, somente o Hub e a Loja de Crochê terão navegação comercial completa.

---

## 3. Princípios de navegação

### Simplicidade

O visitante não deverá precisar compreender a estrutura técnica do projeto.

A navegação deverá apresentar somente as opções necessárias para chegar aos produtos, ao carrinho ou ao atendimento.

### Prioridade para dispositivos móveis

Menus, botões, formulários, cartões de produtos e carrinho deverão funcionar adequadamente em telas pequenas.

### Identificação de contexto

O usuário deverá perceber claramente se está:

* no Hub Artes de Monizinha;
* na Loja de Crochê;
* em uma página institucional;
* no carrinho;
* sendo encaminhado ao WhatsApp.

### Poucas etapas

O fluxo entre a descoberta de um produto e o envio do pedido deverá possuir o menor número possível de etapas.

### Continuidade

As informações selecionadas pelo usuário deverão ser preservadas durante a navegação, especialmente no carrinho.

### Retorno fácil

O usuário deverá conseguir retornar ao catálogo, à página anterior ou ao Hub sem depender do botão de retorno do navegador.

---

## 4. URLs principais

### [HUB — VERSÃO 1.0]

```text
/
```

Página inicial da marca Artes de Monizinha.

```text
/sobre/
```

Página institucional sobre a marca.

```text
/faq/
```

Perguntas frequentes gerais.

```text
/contato/
```

Informações e formulário de contato.

```text
/politica-de-privacidade/
```

Política de Privacidade e informações relacionadas à LGPD.

### [CROCHÊ — VERSÃO 1.0]

```text
/croche/
```

Página inicial da Loja de Crochê.

```text
/croche/produtos/
```

Catálogo completo.

```text
/croche/categorias/<slug>/
```

Produtos de uma categoria.

```text
/croche/produtos/<slug>/
```

Página individual de produto.

```text
/croche/busca/
```

Resultados da busca.

```text
/croche/carrinho/
```

Carrinho do usuário.

```text
/croche/finalizar/
```

Revisão e preparação do pedido para o WhatsApp.

### [BOLOS FAKE — VERSÃO FUTURA]

As URLs abaixo ficam reservadas como planejamento futuro:

```text
/bolos-fake/
/bolos-fake/modelos/
/bolos-fake/categorias/<slug>/
/bolos-fake/modelos/<slug>/
/bolos-fake/orcamento/<slug>/
/bolos-fake/finalizar/
```

Essas páginas não deverão ser implementadas como fluxo comercial funcional na versão 1.0.

---

## 5. [HUB — VERSÃO 1.0] Página inicial

A página inicial será a entrada principal da plataforma.

### Objetivos

* apresentar a marca Artes de Monizinha;
* permitir acesso rápido à Loja de Crochê;
* informar que a Loja de Bolos Fake será disponibilizada futuramente;
* apresentar informações resumidas sobre o trabalho artesanal;
* direcionar para WhatsApp e redes sociais;
* oferecer acesso às páginas institucionais.

### Estrutura planejada

```text
Cabeçalho
│
├── Logo Artes de Monizinha
├── Início
├── Crochê
├── Sobre
├── FAQ
├── Contato
└── WhatsApp

Banner principal
│
├── Nome da marca
├── Apresentação curta
└── Botão para conhecer a Loja de Crochê

Escolha das áreas
│
├── Loja de Crochê — Acessar
└── Bolos Fake — Em breve

Apresentação da marca

Produtos ou trabalhos em destaque

Chamada para o WhatsApp

Redes sociais

Rodapé
```

### Card da Loja de Crochê

Deverá possuir:

* nome da loja;
* imagem representativa;
* descrição curta;
* botão de acesso;
* indicação clara de que está disponível.

### Card de Bolos Fake

Na versão 1.0 poderá possuir:

* nome da futura loja;
* imagem ou elemento visual;
* descrição curta;
* identificação “Em breve”;
* botão desativado ou ausência de botão comercial.

O card não deverá levar a um catálogo incompleto.

---

## 6. [HUB — VERSÃO 1.0] Cabeçalho

O cabeçalho principal deverá conter:

* logotipo ou nome da marca;
* link para a página inicial;
* link para a Loja de Crochê;
* link para Sobre;
* link para FAQ;
* link para Contato;
* acesso ao WhatsApp.

Em telas pequenas, os links deverão ficar em um menu recolhível.

### Comportamento

* o logotipo deverá levar ao Hub;
* o item da página atual poderá ser destacado;
* o botão do WhatsApp deverá ser facilmente identificável;
* o cabeçalho não deverá ocupar espaço excessivo em dispositivos móveis.

---

## 7. [HUB — VERSÃO 1.0] Rodapé

O rodapé deverá ser compartilhado pelas páginas institucionais e poderá ser adaptado na Loja de Crochê.

Deverá conter:

* nome da marca;
* acesso à Loja de Crochê;
* página Sobre;
* FAQ;
* Contato;
* Política de Privacidade;
* Instagram;
* Facebook;
* WhatsApp;
* informação de direitos autorais;
* identificação de que os produtos são artesanais.

---

## 8. [HUB — VERSÃO 1.0] Página Sobre

A página Sobre deverá apresentar:

* origem da Artes de Monizinha;
* tipo de trabalho realizado;
* natureza artesanal e sob demanda dos produtos;
* apresentação da Loja de Crochê;
* menção à futura expansão para Bolos Fake, quando apropriado;
* formas de contato.

### Fluxo esperado

```text
Página Sobre
    │
    ├── Conhecer a Loja de Crochê
    ├── Entrar em contato
    └── Voltar ao Hub
```

---

## 9. [HUB — VERSÃO 1.0] FAQ

A página de perguntas frequentes poderá apresentar:

* perguntas gerais;
* perguntas específicas da Loja de Crochê;
* informações sobre personalização;
* informações sobre prazo;
* informações sobre pagamento;
* informações sobre entrega ou retirada;
* esclarecimento de que a solicitação enviada não confirma automaticamente o pedido.

### Comportamento

As perguntas poderão ser agrupadas por área:

```text
Perguntas gerais

Perguntas sobre Crochê
```

Perguntas referentes exclusivamente a Bolos Fake não serão obrigatórias na versão 1.0.

---

## 10. [HUB — VERSÃO 1.0] Página de contato

A página deverá apresentar:

* WhatsApp;
* Instagram;
* Facebook;
* e-mail, caso utilizado;
* formulário de contato, caso implementado;
* horário ou orientação de atendimento, caso definido.

### Fluxos possíveis

```text
Contato
│
├── Abrir WhatsApp
├── Acessar Instagram
├── Acessar Facebook
└── Enviar formulário
```

Caso o formulário não seja implementado antes do lançamento, a página continuará funcional com os canais externos.

---

## 11. [HUB — VERSÃO 1.0] Política de Privacidade e LGPD

A página deverá informar, de forma simples:

* quais dados podem ser coletados;
* finalidade do formulário de contato;
* utilização de sessões para o carrinho;
* redirecionamento para o WhatsApp;
* utilização de serviços externos;
* forma de solicitar correção ou remoção de dados;
* identificação de que o site não armazena dados de pagamento na versão 1.0.

A página deverá estar acessível pelo rodapé e pelos formulários que coletarem dados pessoais.

---

## 12. [CROCHÊ — VERSÃO 1.0] Página inicial da loja

A página inicial da Loja de Crochê será diferente da página inicial do Hub.

### Objetivos

* apresentar a identidade da Loja de Crochê;
* destacar produtos;
* apresentar categorias;
* permitir acesso rápido ao catálogo;
* permitir acesso ao carrinho;
* explicar resumidamente o processo de compra;
* direcionar para o WhatsApp.

### Estrutura planejada

```text
Cabeçalho da Loja de Crochê

Banner da loja

Categorias em destaque

Produtos em destaque

Produtos recentes

Como funciona
│
├── Escolha o produto
├── Selecione as opções
├── Adicione ao carrinho
└── Finalize pelo WhatsApp

Chamada para atendimento

Rodapé
```

---

## 13. [CROCHÊ — VERSÃO 1.0] Cabeçalho da loja

O cabeçalho da Loja de Crochê deverá conter:

* identidade ou nome da loja;
* link para o Hub;
* link para a página inicial do Crochê;
* link para o catálogo;
* acesso às categorias;
* busca;
* carrinho;
* WhatsApp.

### Indicador do carrinho

O ícone ou link do carrinho poderá exibir:

* quantidade total de itens;
* indicação visual quando houver itens adicionados.

O cabeçalho deverá permanecer simples em dispositivos móveis.

---

## 14. [CROCHÊ — VERSÃO 1.0] Catálogo

O catálogo exibirá os produtos ativos da Loja de Crochê.

### Elementos da página

* título;
* descrição curta;
* campo de busca;
* categorias;
* ordenação, caso implementada;
* cartões dos produtos;
* paginação, caso necessária;
* mensagem quando não houver resultados.

### Cartão de produto

Cada cartão deverá apresentar:

* imagem principal;
* nome;
* descrição curta;
* preço-base ou indicação “Sob consulta”;
* identificação de personalização, quando aplicável;
* botão ou link para ver detalhes.

O botão principal deverá levar à página individual do produto.

---

## 15. [CROCHÊ — VERSÃO 1.0] Navegação por categorias

O usuário poderá acessar uma categoria pela página inicial da loja ou pelo catálogo.

### Fluxo

```text
Loja de Crochê
      │
      ▼
Categoria
      │
      ▼
Produtos da categoria
      │
      ▼
Página do produto
```

A página deverá mostrar:

* nome da categoria;
* descrição;
* produtos ativos relacionados;
* opção de retornar ao catálogo completo.

Categorias inativas não deverão aparecer.

---

## 16. [CROCHÊ — VERSÃO 1.0] Busca

A busca deverá procurar produtos ativos da Loja de Crochê.

### Campos pesquisáveis

* nome;
* descrição curta;
* descrição completa;
* categoria.

### Fluxo

```text
Usuário informa o termo
        │
        ▼
Validação do termo
        │
        ▼
Busca limitada ao Crochê
        │
        ▼
Resultados
```

### Regras

* a busca não deverá retornar produtos de Bolos Fake;
* termos vazios poderão redirecionar para o catálogo;
* produtos inativos não deverão aparecer;
* a página deverá informar o termo pesquisado;
* nenhum resultado deverá apresentar uma mensagem amigável.

---

## 17. [CROCHÊ — VERSÃO 1.0] Página individual do produto

A página individual será o principal ponto de decisão do cliente.

### Informações exibidas

* nome;
* imagem principal;
* galeria;
* descrição;
* preço-base ou indicação de consulta;
* prazo estimado;
* opções de personalização;
* quantidade;
* observações;
* botão para adicionar ao carrinho;
* acesso ao WhatsApp;
* produtos relacionados, caso implementado.

### Fluxo principal

```text
Produto
   │
   ├── Visualizar imagens
   ├── Ler descrição
   ├── Selecionar opções
   ├── Escolher quantidade
   └── Adicionar ao carrinho
```

### Validação

Antes de adicionar ao carrinho, o sistema deverá verificar:

* produto ativo;
* opções obrigatórias;
* valores válidos;
* quantidade válida;
* opções pertencentes ao produto.

---

## 18. [CROCHÊ — VERSÃO 1.0] Adição ao carrinho

### Fluxo

```text
Selecionar produto
       │
       ▼
Escolher variações
       │
       ▼
Definir quantidade
       │
       ▼
Adicionar ao carrinho
       │
       ▼
Confirmação
```

Após adicionar, o usuário poderá:

* continuar comprando;
* abrir o carrinho;
* alterar o item;
* remover o item;
* iniciar a finalização.

### Comportamento esperado

Caso o mesmo produto seja adicionado com as mesmas opções, o sistema poderá:

* aumentar a quantidade; ou
* criar uma nova linha.

A escolha definitiva será feita durante a implementação, priorizando clareza para o cliente.

Produtos iguais com opções diferentes deverão permanecer separados.

---

## 19. [CROCHÊ — VERSÃO 1.0] Carrinho

A página do carrinho deverá apresentar:

* produtos adicionados;
* imagem resumida;
* nome;
* opções selecionadas;
* quantidade;
* preço-base ou indicação de consulta;
* ação para remover;
* ação para alterar quantidade;
* ação para continuar comprando;
* ação para finalizar.

### Carrinho vazio

Quando não houver itens, a página deverá apresentar:

* mensagem clara;
* botão para acessar o catálogo;
* possível acesso aos produtos em destaque.

### Revalidação

Ao abrir o carrinho, o sistema deverá conferir:

* existência do produto;
* status ativo;
* opções válidas;
* preço atual;
* disponibilidade das opções.

---

## 20. [CROCHÊ — VERSÃO 1.0] Finalização

A finalização não representará pagamento nem confirmação automática.

### Dados básicos possíveis

* nome do cliente;
* telefone, quando necessário;
* observações gerais;
* preferência de contato;
* informações complementares.

Não deverão ser solicitados dados que não sejam necessários para o atendimento inicial.

### Fluxo

```text
Carrinho
   │
   ▼
Revisar produtos
   │
   ▼
Informar dados básicos
   │
   ▼
Gerar resumo
   │
   ▼
Abrir WhatsApp
```

### Mensagem de confirmação

A página deverá deixar claro:

* o pedido ainda será confirmado pela atendente;
* preço final poderá depender de personalizações;
* prazo será confirmado;
* entrega ou retirada será combinada;
* pagamento será definido no WhatsApp.

---

## 21. [CROCHÊ — VERSÃO 1.0] Geração da mensagem para o WhatsApp

A mensagem deverá ser organizada e legível.

### Estrutura conceitual

```text
Olá! Gostaria de solicitar um pedido pela Loja de Crochê da Artes de Monizinha.

Cliente: [nome]

Itens:

1. [nome do produto]
Quantidade: [quantidade]
Opções:
- Tamanho: [valor]
- Cor: [valor]
- Detalhes: [valor]

Observações:
[texto informado]

Entendo que o pedido, o valor final, o prazo, a entrega e o pagamento serão confirmados durante o atendimento.
```

### Regras

* os dados deverão ser codificados corretamente na URL;
* o número deverá usar o formato internacional;
* produtos e opções deverão ser revalidados;
* campos vazios opcionais não deverão gerar linhas desnecessárias;
* a mensagem deverá identificar que foi gerada pelo site;
* nenhuma mensagem deverá confirmar automaticamente uma venda.

---

## 22. [CROCHÊ — VERSÃO 1.0] Fluxo comercial completo

```text
Hub
 │
 ▼
Loja de Crochê
 │
 ├── Categoria
 │      │
 │      ▼
 │    Produto
 │
 ├── Busca
 │      │
 │      ▼
 │    Produto
 │
 └── Catálogo
        │
        ▼
      Produto
        │
        ▼
Selecionar opções
        │
        ▼
Adicionar ao carrinho
        │
        ▼
Revisar carrinho
        │
        ▼
Finalizar
        │
        ▼
WhatsApp
```

---

## 23. [BOLOS FAKE — VERSÃO FUTURA] Navegação planejada

A Loja de Bolos Fake terá navegação própria quando for implementada.

### Fluxo futuro previsto

```text
Hub
 │
 ▼
Loja de Bolos Fake
 │
 ├── Categorias
 ├── Busca
 └── Catálogo de modelos
        │
        ▼
Página do modelo
        │
        ▼
Selecionar características gerais
        │
        ▼
Preencher orçamento-base
        │
        ▼
Revisar solicitação
        │
        ▼
WhatsApp
```

Essa navegação não faz parte da implementação da versão 1.0.

---

## 24. [BOLOS FAKE — VERSÃO FUTURA] Tratamento no Hub

Na versão 1.0, a futura Loja de Bolos Fake poderá ser apresentada como “Em breve”.

### Opções permitidas

* card informativo sem link;
* botão desativado;
* selo “Em breve”;
* texto curto informando que a área está em preparação.

### Não deverá ocorrer

* acesso a catálogo incompleto;
* acesso a formulário de orçamento não funcional;
* redirecionamento para páginas vazias;
* mistura de produtos de Crochê com Bolos Fake;
* apresentação da loja como disponível quando ainda não estiver pronta.

---

## 25. Navegação administrativa

A administração será realizada inicialmente pelo Django Admin.

### Acesso

```text
/admin/
```

### Usuários

* desenvolvedor;
* proprietária;
* colaboradora autorizada.

### Principais áreas administrativas

```text
Administração
│
├── Lojas
├── Categorias
├── Produtos
├── Imagens
├── Grupos de opções
├── Opções
├── FAQ
├── Configurações do site
├── Mensagens de contato
├── Usuários
└── Grupos e permissões
```

Cada usuário deverá visualizar apenas os recursos permitidos.

---

## 26. Fluxo administrativo de cadastro de produto

### [CROCHÊ — VERSÃO 1.0]

```text
Acessar Admin
     │
     ▼
Selecionar Produtos
     │
     ▼
Adicionar produto
     │
     ├── Definir Loja de Crochê
     ├── Escolher categoria
     ├── Informar nome
     ├── Informar descrição
     ├── Informar preço ou consulta
     ├── Enviar imagem principal
     ├── Definir destaque
     └── Publicar
     │
     ▼
Adicionar imagens adicionais
     │
     ▼
Adicionar grupos de opções
     │
     ▼
Adicionar opções
     │
     ▼
Testar página pública
```

A interface administrativa deverá utilizar nomes e descrições compreensíveis para usuários não técnicos.

---

## 27. Estados de navegação

As páginas deverão tratar diferentes estados.

### Carregamento normal

Conteúdo disponível e navegação funcional.

### Conteúdo vazio

Exemplos:

* categoria sem produtos;
* busca sem resultados;
* carrinho vazio;
* ausência de produtos em destaque.

### Conteúdo indisponível

Exemplos:

* produto desativado;
* categoria desativada;
* URL incorreta;
* loja inativa.

### Erro

Exemplos:

* erro de formulário;
* falha interna;
* sessão inválida;
* informação obrigatória ausente.

Cada estado deverá apresentar orientação clara para o próximo passo.

---

## 28. Páginas de erro

### Erro 404

Deverá informar que a página não foi encontrada e oferecer:

* retorno ao Hub;
* acesso à Loja de Crochê;
* acesso ao catálogo.

### Erro 403

Deverá informar que o acesso não é permitido.

### Erro 500

Deverá informar que ocorreu um problema inesperado e oferecer:

* retorno à página inicial;
* acesso ao WhatsApp, quando possível.

Mensagens técnicas não deverão ser exibidas ao público.

---

## 29. Breadcrumbs

Breadcrumbs poderão ser utilizados nas páginas internas.

### Exemplo

```text
Início > Crochê > Acessórios > Chaveiro artesanal
```

### Objetivos

* indicar a localização atual;
* facilitar retorno às categorias;
* melhorar organização;
* contribuir para SEO.

Na versão 1.0, serão prioritários nas páginas:

* categoria;
* produto;
* busca;
* carrinho;
* finalização.

---

## 30. Botões de ação

Os botões deverão utilizar textos claros.

### Exemplos recomendados

```text
Conhecer a Loja de Crochê
Ver produtos
Ver detalhes
Adicionar ao carrinho
Continuar comprando
Revisar pedido
Finalizar pelo WhatsApp
Entrar em contato
Voltar ao catálogo
```

### Exemplos a evitar

```text
Clique aqui
Enviar
Continuar
Confirmar
Próximo
```

Textos genéricos poderão ser usados apenas quando o contexto deixar a ação evidente.

---

## 31. Navegação em dispositivos móveis

### Requisitos

* menu recolhível;
* botões com área de toque adequada;
* carrinho acessível;
* busca utilizável;
* formulários sem rolagem horizontal;
* imagens responsivas;
* textos legíveis;
* ausência de elementos que dependam apenas de passar o mouse;
* botão do WhatsApp facilmente acessível.

### Barra fixa

Uma barra inferior ou botão flutuante poderá ser utilizado para:

* WhatsApp;
* carrinho;
* ação principal do produto.

Essa decisão será definida no documento visual e durante a implementação.

---

## 32. Preservação do carrinho

O carrinho permanecerá na sessão durante a navegação.

### Deve ser preservado ao:

* trocar de página;
* acessar outra categoria;
* pesquisar produtos;
* retornar ao Hub;
* fechar e reabrir páginas enquanto a sessão permanecer válida.

### Poderá ser perdido quando:

* a sessão expirar;
* os cookies forem apagados;
* o navegador bloquear sessões;
* o usuário utilizar outro dispositivo;
* ocorrer limpeza manual do carrinho.

A versão 1.0 não sincronizará carrinhos entre dispositivos.

---

## 33. Acessibilidade da navegação

A navegação deverá considerar:

* ordem lógica dos elementos;
* uso por teclado;
* foco visível;
* textos alternativos;
* rótulos em formulários;
* contraste adequado;
* mensagens de erro associadas aos campos;
* títulos hierárquicos;
* links com significado;
* indicação textual além de cores e ícones.

---

## 34. SEO e navegação

A navegação deverá contribuir para a descoberta das páginas pelos mecanismos de busca.

### Requisitos

* links HTML reais;
* URLs descritivas;
* páginas de produto acessíveis diretamente;
* títulos próprios;
* breadcrumbs;
* links internos;
* ausência de páginas duplicadas desnecessárias;
* páginas inativas não publicadas;
* futura integração com sitemap.

O carrinho e a finalização não deverão ser tratados como páginas públicas de conteúdo para indexação.

---

## 35. Critérios de aprovação

### [HUB — VERSÃO 1.0]

A navegação será considerada adequada quando o usuário conseguir:

* acessar a página inicial;
* compreender a marca;
* identificar a Loja de Crochê;
* acessar a Loja de Crochê;
* encontrar Sobre, FAQ, Contato e Privacidade;
* acessar o WhatsApp;
* compreender que Bolos Fake será disponibilizado futuramente.

### [CROCHÊ — VERSÃO 1.0]

A navegação será considerada adequada quando o usuário conseguir:

* acessar a página inicial da loja;
* navegar por categorias;
* abrir o catálogo;
* pesquisar produtos;
* visualizar um produto;
* selecionar opções;
* escolher quantidade;
* adicionar ao carrinho;
* revisar o carrinho;
* iniciar a finalização;
* abrir o WhatsApp com a mensagem preenchida.

### [BOLOS FAKE — VERSÃO FUTURA]

A versão 1.0 não exige navegação comercial funcional para Bolos Fake.

A arquitetura deverá apenas preservar:

* identificação separada;
* URLs futuras planejadas;
* possibilidade de catálogo próprio;
* possibilidade de fluxo de orçamento próprio.

---

## 36. Decisões fixadas

Para a versão 1.0:

1. O Hub será a entrada principal.
2. A Loja de Crochê terá navegação própria.
3. Bolos Fake será tratado como versão futura.
4. O catálogo de Crochê será separado visualmente.
5. A busca será limitada à Loja de Crochê.
6. O carrinho será acessível pelo cabeçalho da loja.
7. A finalização ocorrerá pelo WhatsApp.
8. A solicitação não representará pedido confirmado.
9. Não haverá login de cliente.
10. Não haverá pagamento online.
11. O carrinho será armazenado na sessão.
12. Páginas institucionais serão acessíveis pelo Hub.
13. O site será planejado prioritariamente para celulares.
14. Produtos inativos não serão acessíveis publicamente.
15. O Django Admin será o painel inicial.
16. Não serão publicadas páginas incompletas de Bolos Fake.
17. A navegação deverá evitar duplicação desnecessária entre Hub e Crochê.
18. Alterações de navegação que comprometam o prazo deverão ser adiadas.

---

## 37. Relação com outros documentos

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

A modelagem do banco está registrada em:

```text
/docs/03-database.md
```

A identidade visual será definida em:

```text
/docs/05-design-system.md
```

Em caso de conflito:

1. `PRODUCT.md` define o escopo;
2. `01-vision.md` define a direção;
3. `02-architecture.md` define a estrutura;
4. `03-database.md` define os dados;
5. este documento define a navegação e os fluxos.
