# Projeto Monizinha — Padrões de Desenvolvimento

**Documento:** 08 — Padrões de Desenvolvimento
**Versão:** 1.0
**Data:** 10/08/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha

---

## 1. Objetivo

Este documento define os padrões técnicos e organizacionais utilizados no desenvolvimento do Projeto Monizinha.

Seu objetivo é garantir:

* consistência entre arquivos;
* facilidade de leitura;
* facilidade de manutenção;
* organização do repositório;
* redução de erros;
* previsibilidade;
* melhor colaboração com ferramentas de IA;
* commits compreensíveis;
* código preparado para evolução futura.

Esses padrões deverão ser seguidos sempre que possível.

Alterações deverão ocorrer apenas quando houver justificativa técnica concreta.

---

# 2. Princípios gerais

O desenvolvimento deverá priorizar:

* clareza;
* simplicidade;
* legibilidade;
* segurança;
* reutilização;
* manutenção;
* documentação;
* testes;
* baixo acoplamento;
* responsabilidade clara.

O projeto não deverá buscar complexidade apenas por parecer mais profissional.

A solução mais simples que atenda corretamente ao requisito deverá ser preferida.

---

# 3. Idioma do projeto

O código-fonte será escrito prioritariamente em inglês.

### Exemplos corretos

```python
Product
Category
ProductImage
Cart
Store
created_at
updated_at
is_active
```

### Evitar

```python
Produto
Categoria
ImagemProduto
Carrinho
Loja
data_criacao
```

---

## 3.1 Interface pública

Os textos exibidos ao usuário deverão utilizar português brasileiro.

Exemplo:

```python
class Product(models.Model):
    name = models.CharField(
        "Nome do produto",
        max_length=150,
    )
```

Código:

```text
Product
```

Interface:

```text
Produto
```

---

## 3.2 Documentação

A documentação principal poderá permanecer em português brasileiro.

Isso inclui:

* `/docs`;
* README;
* Wiki;
* Issues;
* roadmap;
* backlog.

Termos técnicos poderão permanecer em inglês quando forem padrões conhecidos.

---

# 4. Python

O código Python deverá seguir as recomendações do PEP 8.

### Principais regras

* indentação com 4 espaços;
* nunca utilizar tabs;
* nomes claros;
* evitar linhas excessivamente longas;
* separar responsabilidades;
* remover imports não utilizados;
* evitar código morto;
* evitar duplicação.

---

# 5. Nomeação em Python

## Classes

Utilizar `PascalCase`.

```python
Product
ProductImage
ProductOptionGroup
SiteSettings
```

---

## Funções

Utilizar `snake_case`.

```python
get_product()
generate_whatsapp_message()
validate_cart_item()
```

---

## Variáveis

Utilizar `snake_case`.

```python
product_name
cart_items
selected_options
```

---

## Constantes

Utilizar letras maiúsculas.

```python
DEFAULT_PAGE_SIZE = 12
MAX_IMAGE_SIZE = 5
```

---

## Variáveis booleanas

Deverão preferencialmente indicar claramente estado ou condição.

```python
is_active
is_featured
is_required
has_options
can_checkout
```

Evitar:

```python
active
featured
required
check
```

quando o significado não for óbvio.

---

# 6. Django Apps

Cada aplicação Django deverá representar uma responsabilidade clara.

Estrutura definida:

```text
apps/
├── core/
├── catalog/
├── crochet/
└── customer_service/
```

Aplicações futuras serão adicionadas somente quando houver necessidade real.

---

## 6.1 Regra de responsabilidade

### `core`

Conteúdo institucional e recursos gerais.

### `catalog`

Dados e comportamentos compartilhados de catálogo.

### `crochet`

Fluxos exclusivos da Loja de Crochê.

### `customer_service`

Recursos do atendimento guiado e geração de mensagens.

Nenhuma aplicação deverá se tornar um local genérico para código sem responsabilidade definida.

---

# 7. Models

Models deverão representar dados e regras diretamente relacionadas a esses dados.

### Exemplo

```python
class Product(models.Model):
    name = models.CharField(max_length=150)
    slug = models.SlugField()
    is_active = models.BooleanField(default=True)
```

---

## 7.1 Ordem dos campos

Preferencialmente:

1. relacionamentos;
2. identificação;
3. conteúdo;
4. dados comerciais;
5. flags;
6. ordenação;
7. datas.

Exemplo:

```python
class Product(models.Model):
    store = models.ForeignKey(...)
    category = models.ForeignKey(...)

    name = models.CharField(...)
    slug = models.SlugField(...)

    description = models.TextField(...)
    base_price = models.DecimalField(...)

    is_active = models.BooleanField(...)
    is_featured = models.BooleanField(...)

    display_order = models.PositiveIntegerField(...)

    created_at = models.DateTimeField(...)
    updated_at = models.DateTimeField(...)
```

---

## 7.2 `__str__`

Models administrativos deverão possuir representação clara.

```python
def __str__(self):
    return self.name
```

---

## 7.3 Meta

Configurações como ordenação e nomes deverão utilizar `Meta`.

```python
class Meta:
    ordering = ["display_order", "name"]
```

---

## 7.4 Validações

Regras críticas deverão ser validadas no backend.

Não confiar exclusivamente em JavaScript.

Exemplos:

* categoria pertencente à loja correta;
* opção pertencente ao produto;
* quantidade válida;
* produto ativo;
* slug único;
* arquivos permitidos.

---

# 8. Views

Views deverão permanecer simples.

Sua responsabilidade principal será:

* receber a requisição;
* validar dados;
* chamar regras ou serviços;
* preparar contexto;
* retornar resposta.

Evitar colocar grandes quantidades de lógica dentro de uma view.

---

## 8.1 Nomes

Exemplos:

```python
home
product_list
product_detail
cart_detail
cart_add
cart_remove
checkout
```

Nomes deverão refletir claramente a ação realizada.

---

## 8.2 Function-Based Views ou Class-Based Views

Não haverá obrigação de utilizar somente um formato.

A decisão será baseada em simplicidade.

### Function-Based Views

Preferidas quando o fluxo for simples e específico.

### Class-Based Views

Podem ser utilizadas para:

* listagens;
* detalhes;
* formulários;
* CRUDs;
* comportamentos que se beneficiem da estrutura genérica do Django.

Não converter uma view simples em classe apenas por convenção.

---

# 9. Services

Quando uma lógica:

* for reutilizada;
* não pertencer diretamente à view;
* envolver múltiplos passos;
* precisar ser testada isoladamente;

ela poderá ser movida para um módulo de serviço.

Exemplo:

```text
crochet/
└── services/
    ├── cart.py
    └── whatsapp.py
```

---

## 9.1 Exemplo de responsabilidade

```python
generate_whatsapp_message()
```

não deverá ser repetida dentro de diferentes views.

Deverá existir em um local central.

---

# 10. Forms

Formulários Django serão utilizados sempre que houver envio de dados relevante ao backend.

### Responsabilidades

* validação;
* normalização;
* mensagens de erro;
* campos obrigatórios;
* segurança.

JavaScript poderá melhorar a experiência, mas não substituirá validação de backend.

---

# 11. URLs

URLs deverão:

* utilizar minúsculas;
* utilizar hífens;
* ser descritivas;
* permanecer estáveis;
* evitar parâmetros desnecessários.

### Correto

```text
/croche/produtos/
/croche/produtos/urso-amigurumi/
/politica-de-privacidade/
```

### Evitar

```text
/Product?id=12
/croche/Produto/12
/page1/
```

---

# 12. Namespaces de URLs

Aplicações deverão utilizar namespaces.

Exemplo:

```python
app_name = "crochet"
```

Uso:

```django
{% url "crochet:product_detail" product.slug %}
```

Isso deverá ser preferido a URLs codificadas manualmente.

---

# 13. Templates

Templates deverão ser organizados por área.

```text
templates/
├── base/
├── core/
├── crochet/
└── customer_service/
```

---

## 13.1 Herança

Elementos comuns deverão utilizar herança de templates.

Exemplo:

```text
base.html
   ↓
base_crochet.html
   ↓
product_detail.html
```

---

## 13.2 Componentes reutilizáveis

Componentes repetidos poderão ser separados em:

```text
partials/
components/
```

Exemplos:

```text
_product_card.html
_breadcrumbs.html
_messages.html
_footer.html
```

Não duplicar grandes blocos de HTML entre páginas.

---

# 14. HTML

O HTML deverá utilizar elementos semânticos.

Preferir:

```html
<header>
<nav>
<main>
<section>
<article>
<footer>
```

Evitar construir todas as páginas apenas com:

```html
<div>
```

---

## 14.1 Hierarquia de títulos

Cada página deverá possuir uma estrutura coerente.

Exemplo:

```text
h1 — Produto
h2 — Descrição
h2 — Personalização
h2 — Produtos relacionados
```

Evitar saltos desnecessários:

```text
h1
h4
h2
```

---

# 15. CSS

A maior parte do layout utilizará Bootstrap.

CSS próprio será utilizado para:

* identidade visual;
* ajustes;
* componentes específicos;
* estados;
* personalizações.

---

## 15.1 Evitar estilos inline

Evitar:

```html
<div style="color: red;">
```

Preferir:

```html
<div class="product-warning">
```

---

## 15.2 Variáveis CSS

Cores e valores recorrentes deverão utilizar variáveis.

```css
:root {
    --color-brand-primary: #b8647a;
}
```

---

## 15.3 Seletores

Preferir classes.

```css
.product-card {}
.product-card__title {}
```

Evitar estilos excessivamente dependentes de estrutura.

```css
div > div > section > p {}
```

---

# 16. JavaScript

JavaScript será utilizado apenas quando necessário.

### Exemplos

* atualização visual do carrinho;
* menus;
* campos dinâmicos;
* galeria;
* interação com opções;
* melhorias de formulários.

---

## 16.1 JavaScript não deverá controlar regras críticas

O servidor deverá sempre validar novamente:

* valores;
* produtos;
* opções;
* quantidade;
* permissões.

---

## 16.2 Nomeação

Utilizar `camelCase`.

```javascript
const cartItems = [];
const selectedOptions = {};
```

Funções:

```javascript
updateCartCount();
showProductImage();
```

---

# 17. Comentários

Comentários deverão explicar **por quê**, não apenas repetir o código.

### Ruim

```python
# Incrementa quantidade
quantity += 1
```

### Melhor

```python
# Produtos com as mesmas opções são agrupados no mesmo item do carrinho.
quantity += 1
```

Comentários obsoletos deverão ser removidos.

---

# 18. Docstrings

Funções e classes complexas poderão utilizar docstrings.

Exemplo:

```python
def generate_whatsapp_message(cart, customer_data):
    """
    Generate the formatted WhatsApp message used by the
    Crochet checkout flow.
    """
```

Funções óbvias não precisam de documentação excessiva.

---

# 19. Imports

Imports deverão ser organizados em grupos.

```python
# Standard library
from decimal import Decimal

# Django
from django.shortcuts import get_object_or_404

# Local
from .models import Product
```

Evitar:

```python
from module import *
```

---

# 20. Dependências

Toda dependência externa deverá possuir motivo claro.

Antes de instalar um pacote, verificar:

1. Django ou Python já resolvem?
2. O pacote é mantido?
3. É realmente necessário?
4. Adiciona risco?
5. Pode dificultar deploy?
6. Existe alternativa mais simples?

Não instalar pacotes apenas para economizar poucas linhas.

---

# 21. `requirements.txt`

Dependências utilizadas deverão ser registradas.

Exemplo conceitual:

```text
Django
psycopg
gunicorn
python-dotenv
Pillow
whitenoise
```

Versões exatas serão definidas durante a configuração real do ambiente.

Não deverão ser inventadas antecipadamente neste documento.

---

# 22. Variáveis de ambiente

Credenciais não deverão ser enviadas ao GitHub.

### Nunca versionar

```text
.env
```

### Versionar

```text
.env.example
```

Exemplo:

```text
SECRET_KEY=
DEBUG=
DATABASE_URL=
WHATSAPP_NUMBER=
```

O `.env.example` não deverá possuir valores secretos reais.

---

# 23. Segredos

Nunca deverão aparecer em:

* código;
* commits;
* Issues públicas;
* README;
* screenshots;
* logs públicos;
* mensagens de erro.

Exemplos:

* senha do PostgreSQL;
* `SECRET_KEY`;
* tokens;
* chaves de APIs;
* credenciais de serviços.

---

# 24. Git

Git será utilizado desde o início para registrar a evolução.

Todo trabalho relevante deverá resultar em commits compreensíveis.

---

# 25. Branch principal

A branch principal será:

```text
main
```

Ela deverá representar o estado estável atual do projeto.

---

# 26. Branches de desenvolvimento

Quando necessário, poderão ser utilizadas branches específicas.

Formato:

```text
tipo/descricao-curta
```

Exemplos:

```text
feature/crochet-cart
feature/product-catalog
fix/cart-quantity
docs/database-model
refactor/whatsapp-service
```

---

## 26.1 Tipos recomendados

```text
feature/
fix/
docs/
refactor/
test/
chore/
```

---

# 27. Commits

Os commits deverão ser pequenos o suficiente para possuir objetivo compreensível.

Formato recomendado:

```text
tipo: descrição curta
```

### Exemplos

```text
feat: add crochet product catalog
fix: validate inactive cart products
docs: update database model
test: add cart validation tests
refactor: centralize whatsapp message generation
chore: configure development environment
```

---

# 28. Tipos de commit

### `feat`

Nova funcionalidade.

```text
feat: add cart page
```

### `fix`

Correção de bug.

```text
fix: prevent inactive product checkout
```

### `docs`

Documentação.

```text
docs: define development standards
```

### `refactor`

Mudança interna sem alterar comportamento esperado.

```text
refactor: extract cart validation service
```

### `test`

Testes.

```text
test: add product model tests
```

### `style`

Mudanças exclusivamente visuais ou de formatação.

```text
style: adjust product card spacing
```

### `chore`

Configuração ou manutenção.

```text
chore: update dependencies
```

---

# 29. Mensagens de commit

Mensagens deverão:

* ser curtas;
* indicar claramente a alteração;
* evitar textos genéricos.

### Evitar

```text
update
changes
fix
test
new stuff
final
agora vai
```

---

# 30. Pull Requests

Como o projeto possui inicialmente um desenvolvedor principal, Pull Requests não serão obrigatórios para toda alteração.

Poderão ser utilizados quando:

* Codex implementar uma funcionalidade;
* uma alteração for grande;
* for necessário revisar antes de juntar à `main`;
* houver colaboração futura.

---

# 31. GitHub Issues

Cada Issue deverá possuir um objetivo claro.

### Título

Formato recomendado:

```text
[ÁREA] Ação
```

Exemplos:

```text
[CROCHÊ] Implementar carrinho
[HUB] Criar página inicial
[BANCO] Criar model Product
[DEPLOY] Configurar Render
```

---

# 32. Conteúdo de uma Issue

Quando necessário:

```text
## Objetivo

## Escopo

## Critérios de conclusão

## Dependências

## Observações
```

Issues simples não precisam possuir documentação exagerada.

---

# 33. Labels

Utilizar as labels definidas no projeto.

Exemplo:

```text
[CROCHÊ] Implementar carrinho

Backend
Frontend
Crochê
Alta
```

Não criar novas labels sem necessidade clara.

---

# 34. Milestones

Issues pertencentes à versão atual deverão utilizar:

```text
Versão 1.0
```

Funcionalidades futuras não deverão ser colocadas artificialmente nesse milestone.

---

# 35. GitHub Projects

Cada Issue ativa deverá refletir corretamente seu estado.

```text
Backlog
Próxima Sprint
Em Desenvolvimento
Revisão
Testes
Concluído
```

A coluna **Concluído** deverá representar trabalho realmente finalizado.

---

# 36. Definition of Done

Uma funcionalidade será considerada concluída quando aplicável:

* código implementado;
* comportamento testado;
* erros conhecidos críticos corrigidos;
* código revisado;
* responsividade básica validada;
* commit realizado;
* Issue atualizada;
* documentação atualizada quando necessária;
* item movido para Concluído.

---

# 37. Testes

Testes automatizados deverão priorizar regras críticas.

### Prioridades

* models;
* validações;
* carrinho;
* busca;
* produtos ativos;
* opções;
* geração do WhatsApp;
* permissões.

---

# 38. Organização de testes

Os testes poderão ser organizados como:

```text
tests/
├── test_models.py
├── test_views.py
├── test_services.py
└── test_forms.py
```

ou em arquivos separados conforme crescimento.

Evitar arquivos de teste gigantes.

---

# 39. Nomes dos testes

Deverão indicar comportamento.

Exemplo:

```python
def test_inactive_product_is_not_listed():
    ...
```

Preferir a:

```python
def test_product_1():
    ...
```

---

# 40. Dados de teste

Testes deverão:

* criar seus próprios dados;
* não depender de banco manual;
* não depender da ordem de execução;
* evitar dados reais de clientes.

---

# 41. Tratamento de erros

Erros esperados deverão ser tratados.

Exemplos:

* produto inexistente;
* produto inativo;
* opção inválida;
* carrinho vazio;
* formulário inválido.

Não utilizar `try/except` genérico sem necessidade.

Evitar:

```python
try:
    ...
except:
    pass
```

---

# 42. Logs

Logs deverão registrar informações úteis sem expor dados sensíveis.

Exemplos válidos:

* erro de sistema;
* falha de integração;
* exceção inesperada.

Evitar registrar:

* senhas;
* tokens;
* conteúdo privado desnecessário;
* dados pessoais completos sem necessidade.

---

# 43. Segurança

Toda funcionalidade deverá considerar:

* autenticação;
* autorização;
* validação;
* CSRF;
* exposição de dados;
* upload;
* inputs;
* URLs.

Não assumir que um dado é confiável apenas porque veio do próprio frontend.

---

# 44. Performance

O projeto não deverá realizar otimizações prematuras.

Primeiro:

```text
funcionar corretamente
```

Depois:

```text
medir
```

Depois:

```text
otimizar
```

Boas práticas simples deverão existir desde o início.

Exemplos:

* evitar consultas repetidas;
* carregar relações adequadamente;
* otimizar imagens;
* paginar quando necessário.

---

# 45. Compatibilidade

A versão 1.0 deverá priorizar:

* Google Chrome;
* Microsoft Edge;
* Firefox;
* navegadores móveis modernos.

Recursos experimentais não deverão ser necessários para utilizar o site.

---

# 46. Responsividade

Toda página pública deverá ser testada em pelo menos:

```text
Mobile
Desktop
```

Quando possível:

```text
Tablet
```

Nenhuma Issue de frontend deverá ser considerada concluída se o layout estiver quebrado em celular.

---

# 47. Acessibilidade

Ao implementar componentes:

* utilizar labels;
* textos alternativos;
* foco visível;
* HTML semântico;
* contraste;
* botões descritivos;
* navegação por teclado quando aplicável.

---

# 48. Imagens

Imagens de produtos deverão:

* possuir `alt_text`;
* ser otimizadas;
* evitar nomes aleatórios quando possível;
* não ser armazenadas diretamente no banco.

Exemplo de nome:

```text
body-croche-rosa-frente.webp
```

Evitar:

```text
IMG_847291.jpg
```

quando houver oportunidade de organizar antes do upload.

---

# 49. Datas

Datas técnicas deverão utilizar timezone corretamente.

Configuração:

```python
LANGUAGE_CODE = "pt-br"
TIME_ZONE = "America/Sao_Paulo"
USE_TZ = True
```

Não utilizar datas hardcoded para regras permanentes sem necessidade.

---

# 50. Valores monetários

Sempre utilizar:

```python
Decimal
```

ou:

```python
DecimalField
```

Nunca utilizar `float` para valores monetários.

---

# 51. Slugs

Slugs deverão:

* ser minúsculos;
* utilizar hífens;
* evitar alterações após publicação;
* possuir restrições adequadas.

Exemplo:

```text
body-croche-vermelho
```

---

# 52. Migrações

Toda alteração de model deverá gerar migration correspondente.

Fluxo:

```text
Alterar model
   ↓
makemigrations
   ↓
Revisar migration
   ↓
migrate
   ↓
Testar
```

Migrações já utilizadas em produção não deverão ser apagadas sem justificativa técnica.

---

# 53. Banco de produção

Nunca editar diretamente tabelas em produção para substituir migrations.

Alterações estruturais deverão ser feitas pelo Django sempre que possível.

---

# 54. Admin

Configurações administrativas deverão priorizar facilidade de uso.

Utilizar quando apropriado:

* `list_display`;
* `search_fields`;
* `list_filter`;
* `ordering`;
* `readonly_fields`;
* inlines;
* fieldsets.

O objetivo é evitar que a proprietária precise compreender estrutura técnica.

---

# 55. Documentação no código

Não documentar tudo excessivamente.

Documentar principalmente:

* decisões incomuns;
* regras comerciais;
* comportamentos não óbvios;
* integrações;
* funções complexas.

A documentação principal continuará em `/docs`.

---

# 56. Uso do Codex

Codex será utilizado como implementador auxiliar.

Ele deverá receber:

* Issue específica;
* arquivos relevantes;
* documentação correspondente;
* critérios de conclusão.

### Codex não deverá decidir sozinho:

* arquitetura;
* banco;
* mudança de stack;
* novo framework;
* dependência importante;
* alteração de escopo;
* mudança da metodologia.

Essas decisões deverão ser definidas previamente na documentação.

---

# 57. Instruções para tarefas com Codex

Formato recomendado:

```text
Implementar a Issue [número/título].

Leia antes:
- PRODUCT.md
- docs/02-architecture.md
- docs/03-database.md
- docs/08-development-standards.md

Escopo:
[...]

Não altere arquitetura ou dependências sem necessidade.

Ao finalizar:
- informe arquivos alterados;
- explique decisões relevantes;
- liste testes realizados.
```

---

# 58. Code Review

Toda implementação relevante deverá ser revisada considerando:

* funcionamento;
* clareza;
* duplicação;
* segurança;
* consistência;
* aderência à documentação;
* testes;
* impacto futuro.

O objetivo da revisão não é tornar todo código perfeito antes de funcionar.

É evitar problemas concretos e dívida técnica desnecessária.

---

# 59. Refatoração

Refatorações deverão ocorrer quando houver benefício claro.

Exemplos:

* duplicação;
* arquivo difícil de entender;
* responsabilidade misturada;
* dificuldade para testar;
* bug recorrente.

Não refatorar código funcional somente por preferência estética durante uma tarefa crítica.

---

# 60. Dependências entre Issues

Quando uma tarefa depender de outra, isso deverá ser registrado.

Exemplo:

```text
Implementar carrinho
depende de:
- Product
- ProductOptionGroup
- ProductOption
```

Isso evita iniciar uma tarefa antes de sua base existir.

---

# 61. Não implementar por antecipação

Não deverão ser criados módulos vazios apenas porque poderão existir futuramente.

Exemplos:

```text
payments/
orders/
api/
mobile/
fake_cakes/
```

serão criados somente quando entrarem efetivamente em desenvolvimento.

---

# 62. Controle de escopo

Ao surgir nova ideia:

```text
Ideia
 ↓
Backlog
 ↓
Avaliação futura
```

Não interromper automaticamente o trabalho atual.

Exceções:

* bug crítico;
* segurança;
* requisito que bloqueia desenvolvimento;
* erro arquitetural comprovado.

---

# 63. Versionamento

O projeto utilizará Semantic Versioning como referência.

Formato:

```text
MAJOR.MINOR.PATCH
```

Exemplo:

```text
1.0.0
```

### MAJOR

Mudança incompatível ou grande evolução.

```text
2.0.0
```

### MINOR

Nova funcionalidade compatível.

```text
1.1.0
```

### PATCH

Correção.

```text
1.0.1
```

---

# 64. Changelog

Mudanças relevantes deverão ser registradas em:

```text
CHANGELOG.md
```

Categorias possíveis:

```text
Added
Changed
Fixed
Removed
Security
```

Exemplo:

```markdown
## [1.0.0]

### Added
- Catálogo da Loja de Crochê.
- Carrinho em sessão.
- Integração com WhatsApp.
```

---

# 65. README

O `README.md` deverá permanecer como entrada rápida para o projeto.

Deverá conter futuramente:

* descrição;
* status;
* tecnologias;
* instalação;
* configuração;
* execução;
* links para documentação.

Não duplicar todo o conteúdo de `/docs` dentro do README.

---

# 66. Organização do repositório

Estrutura principal:

```text
Projeto-Monizinha/
│
├── .github/
├── assets/
├── docs/
├── scripts/
├── src/
├── .env.example
├── .gitignore
├── CHANGELOG.md
├── LICENSE
├── PRODUCT.md
├── README.md
└── requirements.txt
```

Arquivos deverão permanecer em seus locais adequados.

Evitar criar arquivos temporários na raiz.

---

# 67. Arquivos temporários

Não versionar:

* `.env`;
* caches;
* arquivos compilados;
* bancos locais temporários;
* configurações da IDE sem necessidade;
* logs;
* credenciais;
* arquivos temporários do sistema.

Esses itens deverão ser tratados pelo `.gitignore`.

---

# 68. Critérios para alterar estes padrões

Este documento poderá ser alterado quando:

* uma regra causar problema real;
* a arquitetura evoluir;
* uma nova ferramenta for adotada;
* houver colaboração com mais desenvolvedores;
* algum padrão estiver inadequado.

Não deverá ser alterado a cada preferência pontual.

---

# 69. Decisões fixadas

1. Código em inglês.
2. Interface em português brasileiro.
3. Python seguirá PEP 8.
4. Classes usarão PascalCase.
5. Python utilizará snake_case.
6. JavaScript utilizará camelCase.
7. URLs utilizarão minúsculas e hífens.
8. Templates serão separados por área.
9. Bootstrap será a base do frontend.
10. JavaScript não substituirá validação de backend.
11. Credenciais ficarão fora do Git.
12. A branch principal será `main`.
13. Commits utilizarão mensagens descritivas.
14. Semantic Versioning será utilizado como referência.
15. Issues representarão tarefas claras.
16. GitHub Projects acompanhará o estado do trabalho.
17. Codex seguirá a arquitetura definida.
18. Dependências externas somente serão adicionadas quando necessárias.
19. Não serão criados módulos futuros sem uso atual.
20. Mudanças metodológicas deverão ser raras e justificadas.

---

# 70. Relação com outros documentos

O escopo está registrado em:

```text
/PRODUCT.md
```

A arquitetura está registrada em:

```text
/docs/02-architecture.md
```

A modelagem está registrada em:

```text
/docs/03-database.md
```

O backlog está registrado em:

```text
/docs/06-backlog.md
```

O roadmap está registrado em:

```text
/docs/07-roadmap.md
```

O deploy será registrado em:

```text
/docs/09-deploy.md
```

O guia de desenvolvimento será registrado em:

```text
/docs/10-developer-guide.md
```

Em caso de conflito:

1. `PRODUCT.md` define o escopo;
2. documentos arquiteturais definem estrutura;
3. este documento define os padrões de implementação.
