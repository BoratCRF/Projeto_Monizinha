# Projeto Monizinha — Visão do Produto

**Documento:** 01 — Visão
**Versão:** 1.0
**Data:** 20/07/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha
**Data-alvo da versão 1.0:** 08/08/2026

---

## 1. Declaração de visão

O Projeto Monizinha tem como visão transformar a presença digital da marca **Artes de Monizinha** em uma plataforma organizada, profissional e preparada para crescimento.

A plataforma deverá centralizar as lojas **Artes de Monizinha Crochê** e **Artes de Monizinha Bolos Fake**, oferecendo experiências próprias para cada uma, mas utilizando uma infraestrutura técnica compartilhada.

A versão inicial deverá facilitar a apresentação dos produtos e reduzir o trabalho manual necessário para iniciar pedidos e orçamentos pelo WhatsApp.

No longo prazo, o sistema poderá evoluir para um e-commerce completo, sem exigir a reconstrução de sua base principal.

---

## 2. Visão resumida

Para clientes interessados em produtos artesanais e personalizados, a Artes de Monizinha será uma plataforma que permite conhecer modelos, escolher características e preparar uma solicitação antes de falar com a atendente.

Diferentemente de um catálogo simples em redes sociais, o Projeto Monizinha organizará os produtos por loja, categoria e finalidade, orientando o cliente durante a seleção e gerando uma mensagem estruturada para o WhatsApp.

---

## 3. Cenário atual

A apresentação de produtos e o atendimento inicial acontecem principalmente por redes sociais e pelo WhatsApp.

Nesse modelo, a atendente precisa realizar manualmente atividades como:

* apresentar os modelos disponíveis;
* enviar fotos individualmente;
* explicar as opções de tamanho e cor;
* perguntar as mesmas informações para diferentes clientes;
* organizar solicitações incompletas;
* identificar qual produto ou modelo o cliente deseja;
* confirmar detalhes básicos antes de discutir preço, prazo e pagamento.

Além disso, as publicações em redes sociais não funcionam como um catálogo estruturado. Produtos antigos podem ficar difíceis de encontrar, e o cliente pode não conhecer todas as opções disponíveis.

---

## 4. Cenário desejado

Com o Projeto Monizinha em funcionamento:

1. O cliente acessará a página principal da Artes de Monizinha.
2. Escolherá entre a Loja de Crochê e a Loja de Bolos Fake.
3. Encontrará uma experiência visual e comercial adequada à loja escolhida.
4. Navegará por produtos, modelos e categorias.
5. Informará características básicas da solicitação.
6. Receberá um resumo do pedido ou orçamento.
7. Será encaminhado ao WhatsApp com uma mensagem organizada.
8. A atendente continuará a conversa somente para definir detalhes finais, preço, prazo, entrega e pagamento.

A administração poderá atualizar o catálogo sem editar diretamente o código do site.

---

## 5. Proposta de valor

O Projeto Monizinha deverá entregar valor para três grupos principais.

### 5.1 Para o cliente

* acesso fácil aos produtos disponíveis;
* visualização organizada das opções;
* redução de dúvidas iniciais;
* processo de escolha mais simples;
* solicitação enviada de maneira clara;
* atendimento final mais rápido;
* experiência adequada para celulares.

### 5.2 Para a proprietária e as atendentes

* redução de perguntas repetitivas;
* pedidos iniciais mais completos;
* menor necessidade de procurar e enviar fotos manualmente;
* catálogo centralizado;
* possibilidade de cadastrar e editar produtos;
* separação clara entre as duas lojas;
* atendimento mais organizado;
* maior facilidade para divulgar os produtos.

### 5.3 Para o desenvolvimento do projeto

* base real para aprendizagem e portfólio;
* arquitetura preparada para crescimento;
* documentação das decisões;
* possibilidade de adicionar recursos gradualmente;
* menor risco de reconstrução completa;
* estrutura que poderá ser adaptada para outros negócios artesanais no futuro.

---

## 6. Objetivos estratégicos

### 6.1 Curto prazo — Versão 1.0

Disponibilizar até 08/08/2026 uma plataforma funcional que permita:

* acessar o hub principal;
* escolher uma das lojas;
* navegar pelos catálogos;
* pesquisar produtos e modelos;
* visualizar categorias;
* acessar páginas individuais;
* montar um carrinho de produtos de Crochê;
* preparar um orçamento-base de Bolo Fake;
* gerar mensagens estruturadas;
* encaminhar solicitações ao WhatsApp;
* gerenciar o conteúdo pelo Django Admin;
* utilizar o site em celulares e computadores.

### 6.2 Médio prazo

Após o lançamento inicial:

* melhorar o SEO;
* adicionar métricas de utilização;
* aprimorar o assistente de atendimento;
* aperfeiçoar o painel administrativo;
* facilitar a gestão das imagens;
* adicionar avaliações e mídias;
* melhorar desempenho e acessibilidade;
* acompanhar os produtos mais acessados;
* registrar solicitações enviadas pelo site, respeitando a privacidade dos usuários.

### 6.3 Longo prazo

Conforme a necessidade do negócio:

* criar contas de clientes;
* registrar pedidos internamente;
* integrar pagamentos;
* calcular frete;
* controlar produção e estoque;
* permitir acompanhamento de pedidos;
* criar cupons e promoções;
* produzir relatórios comerciais;
* integrar outros canais de atendimento;
* expandir o catálogo para novas linhas de produtos.

---

## 7. Experiências separadas, plataforma compartilhada

A plataforma deverá combinar dois princípios.

### Separação visual e comercial

Cada loja terá liberdade para utilizar:

* identidade visual própria;
* página inicial própria;
* navegação própria;
* categorias próprias;
* apresentação própria dos produtos;
* fluxo próprio de preparação da solicitação;
* componentes específicos.

A Loja de Crochê terá foco em produtos, variações, quantidades e carrinho.

A Loja de Bolos Fake terá foco em modelos de referência, características gerais e preparação de orçamento.

### Compartilhamento técnico

Sempre que adequado, as lojas compartilharão:

* projeto Django;
* banco de dados;
* autenticação administrativa;
* configurações;
* componentes institucionais;
* infraestrutura de hospedagem;
* padrões de segurança;
* recursos de SEO;
* gerenciamento de imagens;
* funcionalidades comuns do catálogo.

O compartilhamento técnico não deverá eliminar as particularidades de cada loja.

---

## 8. Princípios de experiência do usuário

### Simplicidade

O cliente deverá compreender rapidamente:

* onde está;
* quais produtos estão disponíveis;
* como visualizar os detalhes;
* como preparar uma solicitação;
* como entrar em contato.

### Prioridade para celulares

Como grande parte dos acessos deverá ocorrer por links enviados em redes sociais e WhatsApp, todas as páginas deverão ser planejadas primeiro para dispositivos móveis.

### Orientação

O site deverá orientar o cliente durante o pedido, evitando formulários longos e informações técnicas desnecessárias.

### Transparência

O sistema deverá deixar claro que:

* os produtos são artesanais;
* determinados produtos são feitos sob demanda;
* os valores finais podem depender de personalizações;
* a solicitação enviada não representa pagamento ou confirmação automática;
* os detalhes finais serão confirmados pelo WhatsApp.

### Separação clara

O cliente deverá perceber facilmente quando está na Loja de Crochê ou na Loja de Bolos Fake.

### Continuidade

O envio para o WhatsApp deverá preservar as informações selecionadas no site, evitando que o cliente precise repetir todo o pedido.

---

## 9. Princípios técnicos

### Evolução progressiva

A arquitetura deverá permitir a adição de novas funcionalidades sem exigir a reconstrução completa do sistema.

### Simplicidade adequada

O projeto não deverá receber tecnologias ou estruturas complexas sem uma necessidade real.

### Segurança desde o início

Senhas, credenciais, dados administrativos e configurações sensíveis não deverão ser armazenados diretamente no código-fonte.

### Responsabilidades separadas

Cada módulo deverá possuir uma função clara, evitando concentração excessiva de código em um único arquivo ou aplicação.

### Documentação viva

A documentação deverá acompanhar as decisões e mudanças relevantes do projeto.

### Custo inicial zero

A versão 1.0 deverá funcionar utilizando ferramentas e planos gratuitos.

### Independência responsável

Serviços externos deverão ser utilizados apenas quando trouxerem benefícios claros e suas limitações deverão ser conhecidas.

---

## 10. Diretrizes visuais

A identidade principal deverá representar a marca Artes de Monizinha e funcionar como ligação entre as duas lojas.

Cada loja poderá utilizar sua própria direção visual, mantendo algum elemento de reconhecimento da marca principal.

A definição detalhada de:

* paletas de cores;
* tipografia;
* logotipos;
* ícones;
* botões;
* cartões;
* banners;
* espaçamentos;
* comportamento responsivo;

será registrada posteriormente no documento de sistema visual.

A identidade visual não será definida dentro deste documento.

---

## 11. Diretrizes de conteúdo

O conteúdo apresentado ao público deverá:

* utilizar português brasileiro;
* ser simples e acolhedor;
* evitar termos técnicos;
* informar que os produtos são artesanais;
* apresentar fotos com boa qualidade;
* utilizar descrições objetivas;
* explicar as opções disponíveis;
* orientar o cliente até o WhatsApp;
* evitar promessas que dependam de confirmação da atendente.

O código-fonte poderá adotar nomes em inglês, seguindo os padrões de desenvolvimento que serão definidos posteriormente.

---

## 12. Limites da visão inicial

O Projeto Monizinha não deverá ser tratado, na versão 1.0, como:

* marketplace;
* sistema de entrega;
* sistema financeiro;
* sistema fiscal;
* rede social;
* aplicativo nativo;
* plataforma de produção industrial;
* substituto completo do atendimento humano;
* e-commerce com pagamento automático.

Esses limites protegem o prazo e mantêm o foco na entrega de valor comercial imediato.

---

## 13. Riscos principais

### Prazo reduzido

A versão funcional deverá ser entregue em 20 dias.

**Direção:** priorizar o fluxo comercial essencial e adiar recursos que não sejam necessários para apresentar produtos e encaminhar solicitações.

### Excesso de funcionalidades

A tentativa de construir um e-commerce completo impediria a entrega dentro do prazo.

**Direção:** manter o escopo fixado no `PRODUCT.md`.

### Dependência de serviços gratuitos

Planos gratuitos podem possuir limitações de uso, desempenho e armazenamento.

**Direção:** documentar essas limitações e manter possibilidade de migração futura.

### Falta de conteúdo

O site depende de fotos, descrições, categorias e informações reais dos produtos.

**Direção:** solicitar e organizar o conteúdo durante o desenvolvimento, sem esperar a conclusão de toda a programação.

### Uso por administradores não técnicos

A proprietária e uma colaboradora deverão conseguir atualizar o catálogo.

**Direção:** configurar o Django Admin de forma clara, com campos compreensíveis e permissões adequadas.

### Complexidade das variações

Os produtos de Crochê e os modelos de Bolo Fake podem possuir características diferentes.

**Direção:** modelar as variações com flexibilidade, sem transformar todas as particularidades em campos fixos desnecessários.

---

## 14. Critérios de alinhamento

Antes de adicionar uma funcionalidade, deverão ser respondidas as seguintes perguntas:

1. Ela ajuda o cliente a conhecer ou solicitar um produto?
2. Ela reduz trabalho manual da atendente?
3. Ela é necessária para a versão 1.0?
4. Ela pode comprometer a data de lançamento?
5. Ela respeita o custo inicial de R$ 0?
6. Ela funciona adequadamente em celular?
7. Ela mantém as particularidades das duas lojas?
8. Ela pode ser mantida com os recursos disponíveis?

Caso uma funcionalidade seja útil, mas não essencial para o lançamento, deverá ser registrada no backlog de versões futuras.

---

## 15. Resultado esperado

Ao final da versão 1.0, a Artes de Monizinha deverá possuir uma presença digital própria, centralizada e organizada.

O cliente deverá conseguir sair de uma situação de descoberta:

> “Quais produtos vocês fazem?”

para uma solicitação estruturada:

> “Escolhi este produto, com estas características e nesta quantidade.”

A plataforma não substituirá o atendimento humano. Ela tornará o atendimento mais rápido, organizado e preparado.

---

## 16. Relação com outros documentos

Este documento define a visão e a direção do produto.

O escopo detalhado está registrado em:

```text
/PRODUCT.md
```

As decisões sobre estrutura técnica serão registradas em:

```text
/docs/02-architecture.md
```

A modelagem do banco de dados será registrada em:

```text
/docs/03-database.md
```

Em caso de conflito, o `PRODUCT.md` será considerado a principal referência de escopo da versão 1.0.
