# Projeto Monizinha — Modelagem do Banco de Dados

**Documento:** 03 — Banco de Dados
**Versão:** 1.0
**Data:** 01/08/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha
**Banco de dados:** PostgreSQL
**Data-alvo da versão 1.0:** 08/08/2026

## Status por área

* **[HUB — VERSÃO 1.0]** Será implementado e publicado na versão 1.0.
* **[CROCHÊ — VERSÃO 1.0]** Será implementado e publicado na versão 1.0.
* **[BOLOS FAKE — VERSÃO FUTURA]** Permanecerá documentado como preparação arquitetural, mas não será implementado nem publicado na versão 1.0.

Sempre que uma seção se referir exclusivamente a uma dessas áreas, ela deverá utilizar a identificação correspondente.

---

## 1. Objetivo

Este documento define a modelagem inicial do banco de dados do Projeto Monizinha.

A modelagem deverá permitir:

* administrar o Hub e a Loja de Crochê na versão 1.0, mantendo a estrutura preparada para a futura Loja de Bolos Fake;
* cadastrar categorias;
* cadastrar produtos de Crochê na versão 1.0 e permitir futuramente o cadastro de modelos de Bolos Fake;
* manter a separação estrutural entre o catálogo de Crochê e o futuro catálogo de Bolos Fake;
* cadastrar imagens;
* definir variações;
* marcar produtos como recentes ou destacados;
* publicar ou ocultar produtos;
* administrar perguntas frequentes;
* armazenar configurações básicas da marca;
* registrar estatísticas simples, caso sejam implementadas;
* permitir evolução futura para pedidos e pagamentos.

A versão 1.0 não armazenará pagamentos nem exigirá cadastro de clientes.

---

## 2. Princípios da modelagem

### Compartilhamento controlado

Produtos de Crochê e modelos de Bolos Fake compartilharão informações comuns, mas poderão possuir configurações e variações específicas.

### Separação comercial

Todo produto, categoria e conteúdo comercial deverá estar associado a uma loja.

### Flexibilidade

As variações não deverão depender de uma lista rígida de campos que só funcione para os produtos atuais.

### Simplicidade

Não serão criadas tabelas sem uso real na versão inicial.

### Evolução

A modelagem deverá permitir a criação futura de pedidos, clientes, pagamentos, estoque e entregas.

### Integridade

Relacionamentos e restrições deverão impedir registros inconsistentes sempre que possível.

---

## 3. Representação geral

```text
Store
  │
  ├── Category
  │      │
  │      └── Product
  │             │
  │             ├── ProductImage
  │             ├── ProductOptionGroup
  │             │       └── ProductOption
  │             └── ProductView
  │
  ├── FAQ
  └── StoreSettings

SiteSettings
```

Na versão inicial, carrinhos e orçamentos serão temporários e permanecerão na sessão do usuário.

---

## 4. Modelo `Store`

Representa uma loja pertencente à marca Artes de Monizinha.

A estrutura aceitará dois tipos de loja, porém, na versão 1.0, somente a Loja de Crochê deverá possuir registro ativo e catálogo publicado:

CROCHÊ — VERSÃO 1.0
* Crochê
BOLOS FAKE — VERSÃO FUTURA
* Bolos Fake

### Campos

| Campo               | Tipo                  | Obrigatório | Descrição                       |
| ------------------- | --------------------- | ----------: | ------------------------------- |
| `name`              | CharField             |         Sim | Nome público da loja            |
| `slug`              | SlugField             |         Sim | Identificador usado nas URLs    |
| `store_type`        | CharField com choices |         Sim | Tipo interno da loja            |
| `short_description` | CharField             |         Não | Descrição curta                 |
| `description`       | TextField             |         Não | Apresentação completa           |
| `whatsapp_number`   | CharField             |         Não | Número de atendimento da loja   |
| `instagram_url`     | URLField              |         Não | Perfil no Instagram             |
| `facebook_url`      | URLField              |         Não | Página no Facebook              |
| `is_active`         | BooleanField          |         Sim | Define se a loja está publicada |
| `created_at`        | DateTimeField         |         Sim | Data de criação                 |
| `updated_at`        | DateTimeField         |         Sim | Data da última alteração        |

### Valores de `store_type`

```text
CROCHET
FAKE_CAKES
```

### Regras

* `slug` deverá ser único;
* `store_type` deverá ser único;
* lojas inativas não deverão aparecer para o público;
* o número do WhatsApp poderá utilizar uma configuração geral caso não seja definido por loja.

---

## 5. Modelo `Category`

Representa uma categoria dentro de uma loja.

CROCHÊ — VERSÃO 1.0

* bodies;
* biquínis;
* acessórios;
* decoração.

BOLOS FAKE — VERSÃO FUTURA:

* infantil;
* casamento;
* aniversário;
* mesversário;
* floral.

### Campos

| Campo           | Tipo                          | Obrigatório | Descrição                            |
| --------------- | ----------------------------- | ----------: | ------------------------------------ |
| `store`         | ForeignKey para Store         |         Sim | Loja proprietária da categoria       |
| `name`          | CharField                     |         Sim | Nome da categoria                    |
| `slug`          | SlugField                     |         Sim | Identificador para URL               |
| `description`   | TextField                     |         Não | Descrição da categoria               |
| `image`         | ImageField ou serviço externo |         Não | Imagem representativa                |
| `display_order` | PositiveIntegerField          |         Sim | Ordem de exibição                    |
| `is_active`     | BooleanField                  |         Sim | Define se a categoria está publicada |
| `created_at`    | DateTimeField                 |         Sim | Data de criação                      |
| `updated_at`    | DateTimeField                 |         Sim | Data da última alteração             |

### Regras

* o mesmo slug não poderá se repetir dentro da mesma loja;
* uma categoria de Crochê não poderá ser usada por um produto de Bolos Fake;
* categorias inativas não deverão aparecer no catálogo público;
* a exclusão de uma loja não deverá remover categorias acidentalmente.

### Restrição composta

```text
store + slug = único
```

---

## 6. Modelo `Product`

O modelo `Product` será utilizado na versão 1.0 para os produtos da Loja de Crochê.

Sua estrutura permanecerá genérica o suficiente para representar futuramente os modelos-base da Loja de Bolos Fake, sem exigir a criação de uma tabela de produtos completamente separada.

**[CROCHÊ — VERSÃO 1.0]** Produtos artesanais, variações, quantidade, carrinho e envio para o WhatsApp.

**[BOLOS FAKE — VERSÃO FUTURA]** Modelos de referência, características gerais, orçamento e envio para o WhatsApp.

O tipo de apresentação e o fluxo comercial serão determinados pela loja associada.

### Campos gerais

| Campo               | Tipo                             | Obrigatório | Descrição                         |
| ------------------- | -------------------------------- | ----------: | --------------------------------- |
| `store`             | ForeignKey para Store            |         Sim | Loja do produto                   |
| `category`          | ForeignKey para Category         |         Sim | Categoria principal               |
| `name`              | CharField                        |         Sim | Nome público                      |
| `slug`              | SlugField                        |         Sim | Identificador para URL            |
| `short_description` | CharField                        |         Não | Resumo exibido nos cards          |
| `description`       | TextField                        |         Sim | Descrição completa                |
| `base_price`        | DecimalField                     |         Não | Preço inicial ou de referência    |
| `price_on_request`  | BooleanField                     |         Sim | Indica preço somente sob consulta |
| `main_image`        | ImageField ou referência externa |         Não | Imagem principal                  |
| `is_featured`       | BooleanField                     |         Sim | Produto em destaque               |
| `is_active`         | BooleanField                     |         Sim | Produto visível ao público        |
| `display_order`     | PositiveIntegerField             |         Sim | Ordem manual                      |
| `created_at`        | DateTimeField                    |         Sim | Data de criação                   |
| `updated_at`        | DateTimeField                    |         Sim | Data da última alteração          |
| `published_at`      | DateTimeField                    |         Não | Data de publicação                |

### Campos comerciais

| Campo                   | Tipo         | Obrigatório | Descrição                        |
| ----------------------- | ------------ | ----------: | -------------------------------- |
| `production_time_text`  | CharField    |         Não | Prazo estimado em texto          |
| `customizable`          | BooleanField |         Sim | Indica se aceita personalização  |
| `requires_quote`        | BooleanField |         Sim | Indica necessidade de orçamento  |
| `whatsapp_message_note` | TextField    |         Não | Observação adicionada à mensagem |

### Regras

* a categoria deverá pertencer à mesma loja do produto;
* o slug deverá ser único dentro da loja;
* produtos inativos não deverão aparecer em buscas públicas;
* `base_price` poderá ficar vazio quando o valor depender integralmente de orçamento;
* produtos de Bolos Fake normalmente utilizarão `requires_quote=True`;
* produtos de Crochê poderão ter preço-base ou preço sob consulta;
* `published_at` permitirá identificar produtos recentes.

### Restrição composta

```text
store + slug = único
```

---

## 7. Modelo `ProductImage`

Representa imagens adicionais de um produto.

### Campos

| Campo           | Tipo                             | Obrigatório | Descrição                       |
| --------------- | -------------------------------- | ----------: | ------------------------------- |
| `product`       | ForeignKey para Product          |         Sim | Produto relacionado             |
| `image`         | ImageField ou referência externa |         Sim | Arquivo da imagem               |
| `alt_text`      | CharField                        |         Sim | Descrição acessível da imagem   |
| `caption`       | CharField                        |         Não | Legenda opcional                |
| `display_order` | PositiveIntegerField             |         Sim | Ordem na galeria                |
| `is_active`     | BooleanField                     |         Sim | Define se a imagem será exibida |
| `created_at`    | DateTimeField                    |         Sim | Data de criação                 |

### Regras

* um produto poderá ter várias imagens;
* somente imagens ativas serão exibidas;
* `alt_text` será obrigatório para acessibilidade e SEO;
* a imagem principal continuará no modelo `Product` para simplificar listagens;
* imagens adicionais serão exibidas na página individual.

---

## 8. Modelo `ProductOptionGroup`

Representa um grupo de escolhas disponíveis para um produto.

Exemplos:

* tamanho;
* cor;
* formato;
* modelo;
* acabamento;
* detalhes;
* quantidade de andares.

### Campos

| Campo                | Tipo                    | Obrigatório | Descrição                         |
| -------------------- | ----------------------- | ----------: | --------------------------------- |
| `product`            | ForeignKey para Product |         Sim | Produto relacionado               |
| `name`               | CharField               |         Sim | Nome apresentado ao cliente       |
| `code`               | SlugField               |         Sim | Identificador interno             |
| `input_type`         | CharField com choices   |         Sim | Tipo de entrada                   |
| `is_required`        | BooleanField            |         Sim | Indica seleção obrigatória        |
| `allow_custom_value` | BooleanField            |         Sim | Permite digitação livre           |
| `help_text`          | CharField               |         Não | Instrução para o cliente          |
| `display_order`      | PositiveIntegerField    |         Sim | Ordem de apresentação             |
| `is_active`          | BooleanField            |         Sim | Define se o grupo está disponível |

### Tipos de entrada

```text
SELECT
RADIO
CHECKBOX
TEXT
TEXTAREA
COLOR_TEXT
NUMBER
```

### Exemplos

```text
Produto: Body de Crochê
Grupo: Tamanho
Tipo: SELECT
Obrigatório: Sim
```

```text
Produto: Bolo Fake Floral
Grupo: Cores desejadas
Tipo: TEXT
Obrigatório: Sim
```

### Regras

* os grupos poderão variar de produto para produto;
* campos de texto não precisarão possuir opções cadastradas;
* a ordem deverá ser configurável pelo Admin;
* grupos inativos não aparecerão para o cliente.

---

## 9. Modelo `ProductOption`

Representa uma opção pertencente a um grupo.

Exemplos:

* P;
* M;
* G;
* azul;
* rosa;
* redondo;
* quadrado;
* 20 cm;
* 30 cm.

### Campos

| Campo              | Tipo                               | Obrigatório | Descrição                          |
| ------------------ | ---------------------------------- | ----------: | ---------------------------------- |
| `group`            | ForeignKey para ProductOptionGroup |         Sim | Grupo da opção                     |
| `label`            | CharField                          |         Sim | Texto apresentado ao cliente       |
| `value`            | SlugField ou CharField             |         Sim | Valor interno                      |
| `price_adjustment` | DecimalField                       |         Sim | Acréscimo ou redução no preço-base |
| `display_order`    | PositiveIntegerField               |         Sim | Ordem de apresentação              |
| `is_active`        | BooleanField                       |         Sim | Define disponibilidade             |

### Regras

* `price_adjustment` terá valor padrão zero;
* a opção poderá alterar o preço-base no futuro;
* a versão 1.0 poderá utilizar o campo apenas para preparar a estrutura;
* opções inativas não deverão ser selecionáveis;
* o mesmo valor não deverá se repetir dentro do mesmo grupo.

### Restrição composta

```text
group + value = único
```

---

## 10. Modelo `FAQ`

Representa perguntas frequentes da plataforma ou de uma loja específica.

### Campos

| Campo           | Tipo                  | Obrigatório | Descrição                |
| --------------- | --------------------- | ----------: | ------------------------ |
| `store`         | ForeignKey para Store |         Não | Loja relacionada         |
| `question`      | CharField             |         Sim | Pergunta                 |
| `answer`        | TextField             |         Sim | Resposta                 |
| `display_order` | PositiveIntegerField  |         Sim | Ordem de exibição        |
| `is_active`     | BooleanField          |         Sim | Define se será publicada |
| `created_at`    | DateTimeField         |         Sim | Data de criação          |
| `updated_at`    | DateTimeField         |         Sim | Data da última alteração |

### Regras

* quando `store` estiver vazio, a pergunta será geral;
* quando `store` estiver preenchido, aparecerá somente na área correspondente;
* perguntas inativas não deverão aparecer publicamente.

---

## 11. Modelo `SiteSettings`

Representa configurações gerais da marca.

Deverá existir somente um registro ativo.

### Campos

| Campo                  | Tipo          | Obrigatório | Descrição                  |
| ---------------------- | ------------- | ----------: | -------------------------- |
| `brand_name`           | CharField     |         Sim | Nome da marca              |
| `short_description`    | CharField     |         Não | Descrição resumida         |
| `about_text`           | TextField     |         Não | Conteúdo da página Sobre   |
| `whatsapp_number`      | CharField     |         Sim | Número principal           |
| `contact_email`        | EmailField    |         Não | E-mail público             |
| `instagram_url`        | URLField      |         Não | Perfil principal           |
| `facebook_url`         | URLField      |         Não | Página principal           |
| `privacy_text`         | TextField     |         Não | Conteúdo de privacidade    |
| `contact_address_text` | CharField     |         Não | Região ou endereço público |
| `updated_at`           | DateTimeField |         Sim | Data da última alteração   |

### Regras

* não deverá armazenar senhas ou credenciais;
* o número do WhatsApp deverá utilizar o formato internacional;
* a aplicação deverá impedir ou desencorajar múltiplos registros;
* textos muito extensos poderão ser transferidos para modelos próprios no futuro.

---

## 12. Modelo `ContactMessage`

Representa mensagens enviadas pelo formulário de contato do site.

### Campos

| Campo        | Tipo                  | Obrigatório | Descrição               |
| ------------ | --------------------- | ----------: | ----------------------- |
| `name`       | CharField             |         Sim | Nome informado          |
| `email`      | EmailField            |         Não | E-mail para retorno     |
| `phone`      | CharField             |         Não | Telefone ou WhatsApp    |
| `subject`    | CharField             |         Não | Assunto                 |
| `message`    | TextField             |         Sim | Conteúdo da mensagem    |
| `store`      | ForeignKey para Store |         Não | Loja relacionada        |
| `is_read`    | BooleanField          |         Sim | Controle administrativo |
| `created_at` | DateTimeField         |         Sim | Data de envio           |

### Regras

* o formulário deverá exigir pelo menos uma forma de contato;
* o campo `message` será obrigatório;
* os dados deverão ser utilizados somente para atendimento;
* deverá existir aviso de privacidade no formulário;
* não serão armazenadas informações de pagamento.

---

## 13. Modelo opcional `ProductView`

Este modelo somente será implementado na versão 1.0 caso não comprometa o prazo.

Representa uma visualização simples de produto.

### Campos

| Campo         | Tipo                    | Obrigatório | Descrição               |
| ------------- | ----------------------- | ----------: | ----------------------- |
| `product`     | ForeignKey para Product |         Sim | Produto visualizado     |
| `session_key` | CharField               |         Não | Sessão anônima          |
| `viewed_at`   | DateTimeField           |         Sim | Momento da visualização |

### Limitações

* não deverá armazenar endereço IP completo sem necessidade;
* não deverá identificar clientes individualmente;
* poderá ser substituído futuramente por uma ferramenta de Analytics;
* registros antigos poderão ser agregados ou removidos.

---

## 14. Modelo opcional `WhatsAppClick`

Este modelo somente será implementado caso haja tempo disponível.

Representa um clique de finalização para o WhatsApp.

### Campos

| Campo         | Tipo                    | Obrigatório | Descrição           |
| ------------- | ----------------------- | ----------: | ------------------- |
| `store`       | ForeignKey para Store   |         Sim | Loja de origem      |
| `product`     | ForeignKey para Product |         Não | Produto relacionado |
| `source`      | CharField               |         Sim | Origem do clique    |
| `session_key` | CharField               |         Não | Sessão anônima      |
| `clicked_at`  | DateTimeField           |         Sim | Momento do clique   |

### Possíveis valores de `source`

```text
PRODUCT
CART
QUOTE
ASSISTANT
CONTACT
```

---

## 15. Carrinho de Crochê

O carrinho da versão 1.0 não terá tabela própria.

Ele será armazenado na sessão do Django.

### Estrutura conceitual

```json
{
  "items": [
    {
      "product_id": 10,
      "quantity": 2,
      "selected_options": {
        "tamanho": "M",
        "cor": "Azul"
      }
    }
  ]
}
```

### Regras

* o preço e os dados oficiais deverão ser consultados novamente no banco;
* o navegador não deverá ser tratado como fonte confiável de preço;
* produtos inativos deverão ser removidos ou sinalizados;
* opções inválidas deverão ser rejeitadas;
* o carrinho poderá ser perdido quando a sessão expirar;
* login de cliente não será necessário.

---

## 16. [BOLOS FAKE — VERSÃO FUTURA] Orçamento

Esta funcionalidade não será implementada nem publicada na versão 1.0. A seção permanece no documento apenas para preservar a direção futura da modelagem.

Os dados poderão ser:

* enviados diretamente pelo formulário;
* preservados temporariamente na sessão;
* utilizados para gerar o resumo;
* convertidos em mensagem para o WhatsApp.

### Estrutura conceitual

```json
{
  "product_id": 20,
  "selected_options": {
    "tamanho": "30 cm",
    "formato": "Redondo",
    "cores": "Azul e branco"
  },
  "general_details": "Acabamento com flores",
  "customer_name": "Nome do cliente"
}
```

A versão 1.0 não tratará esse orçamento como pedido confirmado.

---

## 17. Usuários e permissões

Será utilizado inicialmente o modelo de usuário padrão do Django.

### Perfis planejados

#### Desenvolvedor

* acesso de superusuário;
* acesso a todas as configurações;
* gerenciamento de usuários;
* acesso técnico completo.

#### Proprietária

* cadastro e edição de produtos;
* cadastro e edição de categorias;
* gerenciamento de imagens;
* gerenciamento de FAQ;
* visualização de mensagens;
* sem acesso desnecessário às configurações técnicas.

#### Colaboradora

* permissões comerciais autorizadas;
* sem acesso a usuários, grupos ou configurações críticas;
* permissões ajustáveis pelo Django Admin.

Não será criado um modelo personalizado de usuário apenas para representar esses perfis.

Os grupos e permissões do Django serão utilizados.

---

## 18. Relacionamentos

### Store e Category

```text
Store 1 ───── N Category
```

Uma loja possui várias categorias.

Uma categoria pertence a uma loja.

### Store e Product

```text
Store 1 ───── N Product
```

Uma loja possui vários produtos.

Um produto pertence a uma loja.

### Category e Product

```text
Category 1 ───── N Product
```

Uma categoria possui vários produtos.

Um produto possui uma categoria principal na versão 1.0.

### Product e ProductImage

```text
Product 1 ───── N ProductImage
```

Um produto pode possuir várias imagens adicionais.

### Product e ProductOptionGroup

```text
Product 1 ───── N ProductOptionGroup
```

Um produto pode possuir vários grupos de opções.

### ProductOptionGroup e ProductOption

```text
ProductOptionGroup 1 ───── N ProductOption
```

Um grupo pode possuir várias opções.

### Store e FAQ

```text
Store 1 ───── N FAQ
```

A associação será opcional porque também existirão perguntas gerais.

---

## 19. Comportamento de exclusão

As exclusões deverão evitar perda acidental de conteúdo.

### Recomendações

| Relacionamento                     | Comportamento |
| ---------------------------------- | ------------- |
| Store → Category                   | PROTECT       |
| Store → Product                    | PROTECT       |
| Category → Product                 | PROTECT       |
| Product → ProductImage             | CASCADE       |
| Product → ProductOptionGroup       | CASCADE       |
| ProductOptionGroup → ProductOption | CASCADE       |
| Store → FAQ                        | SET_NULL      |
| Store → ContactMessage             | SET_NULL      |
| Product → ProductView              | CASCADE       |
| Product → WhatsAppClick            | SET_NULL      |

Produtos e categorias deverão preferencialmente ser desativados em vez de excluídos.

---

## 20. Índices

Deverão ser criados índices para campos utilizados frequentemente em filtros.

### Campos prioritários

* `Store.slug`;
* `Store.store_type`;
* `Category.slug`;
* `Category.store`;
* `Category.is_active`;
* `Product.slug`;
* `Product.store`;
* `Product.category`;
* `Product.is_active`;
* `Product.is_featured`;
* `Product.published_at`;
* `Product.created_at`.

Restrições únicas também poderão gerar índices automaticamente.

---

## 21. Busca

A busca inicial poderá utilizar filtros do Django ORM.

Campos pesquisáveis:

* nome;
* descrição curta;
* descrição completa;
* nome da categoria.

A consulta sempre deverá limitar os resultados à loja atual.

Exemplo conceitual:

```python
Product.objects.filter(
    store=store,
    is_active=True,
).filter(
    Q(name__icontains=query)
    | Q(short_description__icontains=query)
    | Q(description__icontains=query)
)
```

Uma solução avançada de busca do PostgreSQL poderá ser adicionada posteriormente.

---

## 22. Produtos recentes

Um produto poderá ser considerado recente utilizando `published_at`.

A aplicação poderá definir uma janela, como:

```text
Publicado nos últimos 30 dias
```

Não será necessário armazenar um campo manual `is_recent`.

---

## 23. Produtos em destaque

O campo `is_featured` permitirá que a administração selecione produtos em destaque.

A ordenação poderá considerar:

1. `display_order`;
2. data de publicação;
3. nome.

---

## 24. Slugs

Slugs serão utilizados nas URLs públicas.

### Exemplos

```text
body-flamengo
biquini-artesanal
bolo-floral-redondo
bolo-fake-casamento
```

### Regras

* usar letras minúsculas;
* substituir espaços por hífens;
* evitar caracteres especiais;
* manter unicidade dentro da loja;
* não alterar slugs publicados sem necessidade;
* criar redirecionamentos caso mudanças futuras afetem URLs indexadas.

---

## 25. Valores monetários

Valores deverão utilizar `DecimalField`, nunca `FloatField`.

Configuração inicial sugerida:

```text
max_digits = 10
decimal_places = 2
```

Isso permite valores de até:

```text
99.999.999,99
```

O preço-base poderá ser nulo quando depender de orçamento.

---

## 26. Datas

Os campos deverão utilizar timezone configurado no Django.

Configuração planejada:

```text
LANGUAGE_CODE = "pt-br"
TIME_ZONE = "America/Sao_Paulo"
USE_TZ = True
```

Campos de criação e alteração deverão ser preenchidos automaticamente.

---

## 27. Imagens

O banco não armazenará os bytes das imagens diretamente.

Ele armazenará referências aos arquivos gerenciados pelo mecanismo de mídia do Django ou por serviço externo.

A solução de armazenamento deverá garantir persistência após deploys.

### Dados obrigatórios

* arquivo ou URL gerenciada;
* texto alternativo;
* produto relacionado;
* ordem de exibição.

### Validações planejadas

* extensão permitida;
* tipo de conteúdo;
* limite de tamanho;
* dimensões adequadas;
* otimização antes ou durante o upload, quando viável.

---

## 28. Modelos futuros

Os seguintes modelos não serão implementados agora, mas poderão ser adicionados futuramente:

```text
Customer
CustomerAddress
Order
OrderItem
OrderStatusHistory
Payment
ShippingMethod
Coupon
Inventory
ProductionTask
ProductReview
Favorite
Notification
```

A ausência desses modelos não impede sua criação posterior.

---

## 29. Ordem de implementação

Os modelos deverão ser implementados nesta ordem:

Na versão 1.0, os modelos serão implementados e utilizados somente nos fluxos do Hub e da Loja de Crochê. Recursos exclusivos de Bolos Fake não fazem parte desta etapa.

1. `Store`;
2. `Category`;
3. `Product`;
4. `ProductImage`;
5. `ProductOptionGroup`;
6. `ProductOption`;
7. `FAQ`;
8. `SiteSettings`;
9. `ContactMessage`;
10. modelos opcionais de estatísticas.

Essa ordem respeita os relacionamentos entre as entidades.

---

## 30. Escopo mínimo para o lançamento

### [HUB — VERSÃO 1.0]

Para o Hub funcionar, serão necessários:

* `SiteSettings`;
* informações gerais da marca;
* links para redes sociais;
* acesso público à Loja de Crochê;
* apresentação da futura Loja de Bolos Fake apenas se for exibida como “em breve”.

### [CROCHÊ — VERSÃO 1.0]

Para a Loja de Crochê funcionar, serão obrigatórios:

* `Store`;
* `Category`;
* `Product`;
* `ProductImage`;
* `ProductOptionGroup`;
* `ProductOption`;
* `FAQ`;
* `carrinho armazenado em sessão`;
* `geração da mensagem para o WhatsApp`.

`ContactMessage` será implementado caso o formulário de contato armazene mensagens no banco.

`ProductView` e `WhatsAppClick` não são obrigatórios para o lançamento.

### [BOLOS FAKE — VERSÃO FUTURA]

Não serão obrigatórios na versão 1.0:

* `catálogo de Bolos Fake`;
* `modelos de Bolos Fake`;
* `formulário de orçamento`;
* `opções específicas de tamanho, formato e acabamento`;
* fluxo de finalização de orçamento.

A estrutura compartilhada deverá apenas evitar que essa futura implementação exija reconstrução da base.

---

## 31. Decisões fixadas

Para a versão 1.0:

1. O banco oficial será PostgreSQL.
2. Existirá um modelo `Store`.
3. O modelo `Product` será utilizado pelo Crochê na versão 1.0 e preparado para uso futuro por Bolos Fake.
4. Todo produto estará associado a uma loja.
5. Categorias também estarão associadas a uma loja.
6. O Crochê terá opções configuráveis por produto na versão 1.0, as opções específicas de Bolos Fake serão implementadas futuramente.
7. O carrinho será armazenado em sessão.
8. O orçamento de Bolos Fake não será implementado na versão 1.0.
9. Não haverá tabela de pedidos confirmados.
10. Não haverá cadastro de clientes.
11. O usuário padrão do Django será utilizado.
12. Permissões administrativas serão gerenciadas por grupos.
13. Produtos deverão ser desativados em vez de excluídos sempre que possível.
14. Valores monetários utilizarão Decimal.
15. URLs utilizarão slugs.
16. Imagens não serão armazenadas diretamente no PostgreSQL.
17. Estatísticas não poderão atrasar a versão funcional.
18. Somente o Hub e a Loja de Crochê serão publicados na versão 1.0.
19. A Loja de Bolos Fake será mantida como escopo futuro documentado.
20. Funcionalidades exclusivas de Bolos Fake não poderão atrasar a entrega da versão 1.0.

---

## 32. Critérios de aprovação

### [HUB — VERSÃO 1.0]

A modelagem será considerada adequada quando permitir:

* configurar a marca Artes de Monizinha;
* publicar o Hub;
* disponibilizar acesso à Loja de Crochê;
* manter a futura expansão para Bolos Fake identificada.

### [CROCHÊ — VERSÃO 1.0]

A modelagem será considerada adequada quando permitir:

* cadastrar a Loja de Crochê;
* cadastrar categorias;
* cadastrar produtos;
* cadastrar várias imagens;
* configurar opções diferentes por produto;
* ocultar produtos e categorias;
* destacar produtos;
* gerar o carrinho;
* gerar a mensagem para o WhatsApp;
* administrar o conteúdo pelo Django Admin;
* construir URLs amigáveis.

### [BOLOS FAKE — VERSÃO FUTURA]

A modelagem deverá permitir a futura inclusão de:

* modelos de Bolos Fake;
* categorias próprias;
* opções específicas;
* formulário de orçamento;
* geração de mensagem para o WhatsApp;

sem exigir reconstrução dos modelos compartilhados.

---

## 33. Relação com outros documentos

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

Os fluxos de navegação serão definidos em:

```text
/docs/04-navigation.md
```

Em caso de conflito:

1. `PRODUCT.md` define o escopo;
2. `01-vision.md` define a direção;
3. `02-architecture.md` define a estrutura;
4. este documento define os dados.
