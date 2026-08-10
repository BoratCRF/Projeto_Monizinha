# Projeto Monizinha — Guia do Desenvolvedor

**Documento:** 10 — Developer Guide
**Versão:** 1.0
**Data:** 10/08/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha

---

## 1. Objetivo

Este documento explica como preparar, executar e desenvolver o Projeto Monizinha em ambiente local.

Ele deverá servir como referência para:

* desenvolvedores;
* manutenção futura;
* retomada do projeto após períodos sem desenvolvimento;
* execução por ferramentas auxiliares como Codex;
* configuração de novas máquinas;
* diagnóstico de problemas básicos de ambiente.

Este documento não substitui os documentos de arquitetura, banco, backlog ou deploy.

Ele descreve **como trabalhar no projeto na prática**.

---

# 2. Antes de começar

Antes de alterar código, ler pelo menos:

```text
PRODUCT.md
docs/01-vision.md
docs/02-architecture.md
docs/03-database.md
docs/04-navigation.md
docs/05-design-system.md
docs/06-backlog.md
docs/07-roadmap.md
docs/08-development-standards.md
```

Para tarefas de produção ou infraestrutura, também ler:

```text
docs/09-deploy.md
```

---

# 3. Fonte oficial das decisões

A documentação do repositório será a principal fonte de verdade do projeto.

Ordem geral de referência:

```text
PRODUCT.md
    ↓
Visão
    ↓
Arquitetura
    ↓
Banco
    ↓
Navegação
    ↓
Design
    ↓
Backlog
    ↓
Roadmap
    ↓
Padrões
    ↓
Deploy
```

Em caso de dúvida sobre escopo, verificar primeiro `PRODUCT.md`.

---

# 4. Escopo atual

## [HUB — VERSÃO 1.0]

Será implementado e publicado.

## [CROCHÊ — VERSÃO 1.0]

Será implementado e publicado.

## [BOLOS FAKE — VERSÃO FUTURA]

Não deverá ser implementado como loja funcional durante a versão 1.0.

Não iniciar funcionalidades exclusivas de Bolos Fake sem mudança oficial de versão ou escopo.

---

# 5. Tecnologias principais

A aplicação utilizará:

```text
Python
Django
PostgreSQL
HTML
CSS
Bootstrap
JavaScript
Git
GitHub
```

Produção utilizará infraestrutura definida em:

```text
docs/09-deploy.md
```

---

# 6. Estrutura principal do repositório

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

# 7. Estrutura planejada do Django

Dentro de `src/`:

```text
src/
│
├── config/
│
├── apps/
│   ├── core/
│   ├── catalog/
│   ├── crochet/
│   └── customer_service/
│
├── templates/
│
├── static/
│
└── manage.py
```

A estrutura deverá seguir `docs/02-architecture.md`.

Não criar aplicações extras sem necessidade real.

---

# 8. Pré-requisitos

Antes de configurar o projeto, deverão estar instalados:

* Git;
* Python;
* PostgreSQL;
* editor de código;
* navegador moderno.

Recomendado:

```text
Visual Studio Code
```

Outros editores poderão ser utilizados normalmente.

---

# 9. Verificar Git

No terminal:

```bash
git --version
```

Resultado esperado:

```text
git version ...
```

Se o comando não for reconhecido, instalar ou corrigir o PATH do Git antes de continuar.

---

# 10. Verificar Python

Executar:

```bash
python --version
```

Caso o Windows utilize o launcher:

```bash
py --version
```

Uma das duas formas deverá retornar a versão instalada.

A versão oficial utilizada pelo projeto será definida durante a configuração do ambiente.

---

# 11. Verificar pip

Executar:

```bash
python -m pip --version
```

ou:

```bash
py -m pip --version
```

Evitar depender apenas do comando:

```bash
pip
```

quando houver múltiplas instalações de Python.

---

# 12. Verificar PostgreSQL

Após instalação, verificar:

```bash
psql --version
```

Se o comando não estiver disponível, poderá ser necessário adicionar o diretório `bin` do PostgreSQL ao PATH.

Também poderá ser utilizado o pgAdmin para tarefas administrativas.

---

# 13. Clonar o repositório

Em uma pasta de projetos:

```bash
git clone https://github.com/BoratCRF/Projeto_Monizinha.git
```

Entrar:

```bash
cd Projeto_Monizinha
```

---

# 14. Verificar repositório

Executar:

```bash
git status
```

Resultado esperado:

```text
On branch main
```

e nenhuma alteração não planejada.

---

# 15. Atualizar o repositório

Antes de iniciar um novo trabalho:

```bash
git pull origin main
```

Isso reduz o risco de trabalhar sobre uma versão antiga.

---

# 16. Ambiente virtual

O projeto deverá utilizar ambiente virtual Python.

Na raiz do repositório:

```bash
python -m venv .venv
```

ou:

```bash
py -m venv .venv
```

A pasta:

```text
.venv/
```

não deverá ser versionada.

---

# 17. Ativar ambiente virtual no Windows

PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Prompt de Comando:

```cmd
.venv\Scripts\activate.bat
```

Quando ativado, normalmente aparecerá:

```text
(.venv)
```

antes do caminho no terminal.

---

# 18. Erro de execução de scripts no PowerShell

Caso o PowerShell bloqueie a ativação do ambiente virtual, verificar a política de execução.

Uma alternativa é utilizar temporariamente o Prompt de Comando.

Não alterar políticas de segurança do sistema sem compreender o impacto.

---

# 19. Desativar ambiente virtual

Quando necessário:

```bash
deactivate
```

---

# 20. Atualizar pip

Com o ambiente ativo:

```bash
python -m pip install --upgrade pip
```

---

# 21. Instalar dependências

Quando `requirements.txt` estiver definido:

```bash
python -m pip install -r requirements.txt
```

Todas as dependências do projeto deverão ser instaladas dentro do ambiente virtual.

---

# 22. Verificar dependências

Para listar:

```bash
python -m pip list
```

Para verificar uma dependência específica:

```bash
python -m pip show Django
```

---

# 23. Criar `.env`

Copiar:

```text
.env.example
```

para:

```text
.env
```

No Windows poderá ser feito manualmente pelo Explorer ou terminal.

O `.env` conterá os valores reais do ambiente local.

---

# 24. Segurança do `.env`

Nunca executar:

```bash
git add .env
```

O arquivo deverá estar ignorado pelo `.gitignore`.

Confirmar:

```bash
git status
```

O `.env` não deverá aparecer como arquivo novo para commit.

---

# 25. Estrutura inicial do `.env`

Exemplo:

```text
SECRET_KEY=
DEBUG=True
DATABASE_URL=
ALLOWED_HOSTS=localhost,127.0.0.1
CSRF_TRUSTED_ORIGINS=
WHATSAPP_NUMBER=
```

Os valores reais serão definidos na configuração.

---

# 26. Criar banco PostgreSQL local

O projeto utilizará PostgreSQL também em desenvolvimento.

Exemplo conceitual:

```text
Database:
projeto_monizinha

User:
monizinha_user
```

A senha deverá ser definida localmente.

Não copiar credenciais para a documentação.

---

# 27. Criar banco pelo PostgreSQL

Exemplo utilizando `psql`:

```sql
CREATE DATABASE projeto_monizinha;
```

Criar usuário:

```sql
CREATE USER monizinha_user WITH PASSWORD 'SENHA_LOCAL';
```

Conceder acesso:

```sql
GRANT ALL PRIVILEGES ON DATABASE projeto_monizinha TO monizinha_user;
```

Os comandos poderão ser adaptados conforme a versão e configuração local do PostgreSQL.

---

# 28. `DATABASE_URL`

A conexão poderá ser representada como:

```text
postgresql://USUARIO:SENHA@HOST:PORTA/BANCO
```

Exemplo conceitual:

```text
postgresql://monizinha_user:senha@localhost:5432/projeto_monizinha
```

A senha real não deverá ser registrada neste documento.

---

# 29. Testar PostgreSQL

Uma forma de testar:

```bash
psql -U monizinha_user -d projeto_monizinha
```

ou utilizar pgAdmin.

Antes de culpar o Django por problemas de banco, confirmar primeiro que o PostgreSQL está ativo e acessível.

---

# 30. Criar projeto Django

Quando a Issue correspondente for iniciada, criar o projeto dentro de `src/`.

A estrutura final deverá respeitar:

```text
src/config/
src/manage.py
```

O comando exato dependerá do diretório atual.

Evitar criar:

```text
src/src/
```

por engano.

---

# 31. Verificar estrutura após criação

Depois de criar Django, confirmar:

```text
src/
├── config/
└── manage.py
```

Antes de continuar.

---

# 32. Criar apps

Os apps serão criados conforme entrarem em desenvolvimento.

Planejados para a versão 1.0:

```text
core
catalog
crochet
customer_service
```

Não criar `fake_cakes` durante a versão 1.0 apenas para deixar vazio.

---

# 33. Registrar apps

Apps criados deverão ser adicionados às configurações apropriadas do Django.

Exemplo conceitual:

```python
INSTALLED_APPS = [
    ...
    "apps.core",
    "apps.catalog",
    "apps.crochet",
]
```

O caminho real deverá corresponder à estrutura final.

---

# 34. Executar comandos Django

Como `manage.py` ficará dentro de `src/`, poderá ser utilizado:

```bash
python src/manage.py ...
```

a partir da raiz.

Ou:

```bash
cd src
python manage.py ...
```

É importante escolher uma forma consistente durante cada etapa.

---

# 35. Verificar configuração do Django

Executar:

```bash
python src/manage.py check
```

Resultado esperado:

```text
System check identified no issues
```

ou avisos conhecidos que deverão ser analisados.

---

# 36. Criar migrations

Após criar ou alterar models:

```bash
python src/manage.py makemigrations
```

---

# 37. Revisar migrations

Antes de aplicar:

* verificar os arquivos gerados;
* confirmar models afetados;
* verificar campos;
* verificar relações;
* identificar operações destrutivas.

Migrations não deverão ser tratadas como arquivos descartáveis.

---

# 38. Aplicar migrations

Executar:

```bash
python src/manage.py migrate
```

---

# 39. Verificar estado das migrations

Executar:

```bash
python src/manage.py showmigrations
```

Migrations aplicadas aparecerão marcadas.

---

# 40. Criar superusuário

Depois de configurar banco e autenticação:

```bash
python src/manage.py createsuperuser
```

Informar:

* username;
* e-mail, quando solicitado;
* senha.

A senha não deverá ser salva no Git.

---

# 41. Executar servidor local

```bash
python src/manage.py runserver
```

A aplicação normalmente estará disponível em:

```text
http://127.0.0.1:8000/
```

---

# 42. Parar servidor

No terminal:

```text
Ctrl + C
```

---

# 43. Django Admin

O Admin deverá estar disponível em:

```text
http://127.0.0.1:8000/admin/
```

Utilizar a conta de superusuário local.

---

# 44. Fluxo básico de desenvolvimento

Antes de uma tarefa:

```text
git pull
   ↓
ativar .venv
   ↓
verificar Issue
   ↓
ler documentação relevante
   ↓
desenvolver
   ↓
testar
   ↓
git status
   ↓
git diff
   ↓
commit
   ↓
push
```

---

# 45. Trabalhar com Issues

Antes de implementar uma funcionalidade:

1. identificar a Issue;
2. verificar labels;
3. verificar milestone;
4. verificar dependências;
5. mover para `Em Desenvolvimento`.

Durante o trabalho, manter o escopo da Issue.

---

# 46. Não misturar tarefas

Evitar implementar em um único commit:

```text
Carrinho
+
Página Sobre
+
Deploy
+
Refatoração do banco
```

Cada alteração deverá estar associada a um objetivo claro.

---

# 47. Verificar mudanças

Antes de commit:

```bash
git status
```

Depois:

```bash
git diff
```

Para arquivos já adicionados ao stage:

```bash
git diff --staged
```

---

# 48. Adicionar arquivos

Para arquivo específico:

```bash
git add caminho/do/arquivo
```

Exemplo:

```bash
git add src/apps/catalog/models.py
```

Adicionar tudo somente quando tiver certeza do conteúdo:

```bash
git add .
```

---

# 49. Commit

Formato:

```bash
git commit -m "tipo: descrição"
```

Exemplo:

```bash
git commit -m "feat: add product model"
```

---

# 50. Push

```bash
git push origin main
```

Se estiver trabalhando em branch:

```bash
git push origin nome-da-branch
```

---

# 51. Criar branch

Quando necessário:

```bash
git checkout -b feature/product-catalog
```

ou, em versões recentes do Git:

```bash
git switch -c feature/product-catalog
```

---

# 52. Voltar para main

```bash
git switch main
```

ou:

```bash
git checkout main
```

Depois:

```bash
git pull origin main
```

---

# 53. Não apagar alterações sem revisar

Antes de utilizar comandos como:

```text
git reset
git restore
git clean
```

confirmar o que será perdido.

Evitar comandos destrutivos copiados sem compreender seu efeito.

---

# 54. Testes automatizados

Para executar todos os testes:

```bash
python src/manage.py test
```

Para app específico:

```bash
python src/manage.py test apps.catalog
```

O caminho poderá variar conforme a estrutura final dos apps.

---

# 55. Testar funcionalidade manualmente

Além dos testes automatizados, verificar no navegador:

* fluxo esperado;
* mensagens;
* campos;
* responsividade;
* erros;
* navegação.

Testes manuais não substituem automaticamente os testes de regras críticas.

---

# 56. Testar Models

Priorizar:

* criação;
* validações;
* constraints;
* relacionamentos;
* produtos ativos;
* slugs;
* opções.

---

# 57. Testar carrinho

Validar pelo menos:

* adicionar item;
* alterar quantidade;
* remover;
* produto inativo;
* opção inválida;
* carrinho vazio;
* sessão.

---

# 58. Testar WhatsApp

Validar:

* número correto;
* encoding;
* acentos;
* quebras de linha;
* vários produtos;
* várias opções;
* campos opcionais;
* desktop;
* celular.

---

# 59. Testar permissões

Criar contas de teste representando:

* superusuário;
* proprietária;
* colaboradora.

Confirmar que cada perfil possui somente as permissões necessárias.

---

# 60. Frontend

Toda implementação visual deverá ser verificada pelo menos em:

```text
Mobile
Desktop
```

Quando possível:

```text
Tablet
```

---

# 61. Bootstrap

Bootstrap será a base visual.

Evitar recriar manualmente componentes que já são adequadamente resolvidos pelo framework.

Ao mesmo tempo, utilizar os estilos definidos em:

```text
docs/05-design-system.md
```

para evitar aparência genérica.

---

# 62. Static

Durante desenvolvimento, arquivos estáticos ficarão nas estruturas apropriadas do projeto.

Exemplos:

```text
static/css/
static/js/
static/images/
```

Não colocar fotos de produtos permanentes dentro de static.

---

# 63. Media

Fotos cadastradas no Admin são mídia.

Em desenvolvimento poderá existir:

```text
media/
```

local.

Essa pasta não representa a solução de produção.

Produção seguirá `docs/09-deploy.md`.

---

# 64. Dados de desenvolvimento

Não utilizar dados pessoais reais quando não forem necessários.

Criar:

* produtos fictícios;
* nomes fictícios;
* mensagens de teste;
* imagens autorizadas.

---

# 65. Produtos reais

Quando o catálogo estiver funcional, dados reais poderão ser cadastrados para preparação do lançamento.

Antes disso, dados fictícios podem facilitar testes.

---

# 66. Shell do Django

Para testes rápidos:

```bash
python src/manage.py shell
```

Exemplo de uso:

```python
from apps.catalog.models import Product
Product.objects.all()
```

O caminho dependerá da estrutura real definida.

---

# 67. Limpar terminal não corrige problema

Quando surgir erro:

1. ler traceback;
2. identificar primeiro erro relevante;
3. verificar arquivo;
4. verificar linha;
5. reproduzir;
6. corrigir causa.

Evitar modificar várias partes do projeto simultaneamente tentando “ver se funciona”.

---

# 68. Erros de banco

Verificar na ordem:

1. PostgreSQL está iniciado?
2. banco existe?
3. usuário existe?
4. senha está correta?
5. `DATABASE_URL` está correta?
6. porta está correta?
7. migrations foram aplicadas?
8. Django consegue conectar?

---

# 69. Erros de migration

Antes de apagar migration:

* verificar histórico;
* verificar banco;
* verificar se já foi compartilhada;
* verificar se já foi usada em produção.

Durante desenvolvimento inicial existem mais opções de correção, mas apagar migrations não deverá virar solução padrão.

---

# 70. Erros de import

Verificar:

* ambiente virtual ativo;
* dependência instalada;
* caminho correto;
* nome do módulo;
* `INSTALLED_APPS`;
* package Python.

---

# 71. Erros de template

Verificar:

* caminho;
* `TEMPLATES`;
* herança;
* nome do template;
* contexto;
* tags Django;
* namespace da URL.

---

# 72. Erros de static

Verificar:

* `{% load static %}`;
* caminho;
* `STATIC_URL`;
* localização do arquivo;
* cache do navegador.

Em produção também verificar `collectstatic`.

---

# 73. Erros de media

Verificar:

* configuração do storage;
* upload;
* URL;
* permissões;
* existência do arquivo.

Não confundir media com static.

---

# 74. Erros de sessão

Para o carrinho, verificar:

* middleware de sessão;
* cookies;
* estrutura dos dados;
* serialização;
* expiração;
* chave utilizada.

---

# 75. Segurança durante desenvolvimento

Mesmo localmente:

* não versionar segredos;
* não compartilhar senhas;
* não colocar credenciais em screenshots;
* não desabilitar proteções permanentemente para “resolver” erro.

---

# 76. Atualizar dependências

Não atualizar tudo automaticamente no meio de uma funcionalidade sem necessidade.

Quando houver atualização:

1. identificar motivo;
2. testar;
3. atualizar `requirements.txt`;
4. registrar alteração;
5. verificar deploy.

---

# 77. Adicionar nova dependência

Antes:

* verificar necessidade;
* confirmar manutenção;
* avaliar tamanho;
* verificar compatibilidade;
* analisar impacto no deploy.

Depois registrar em:

```text
requirements.txt
```

---

# 78. Atualizar documentação

Alterações deverão refletir na documentação quando modificarem:

* arquitetura;
* banco;
* navegação;
* escopo;
* padrão visual;
* deploy;
* fluxo relevante.

Pequenos detalhes internos não exigem alteração em vários documentos.

---

# 79. CHANGELOG

Atualizar quando houver mudança relevante destinada a uma versão.

Não é necessário registrar cada commit individual.

---

# 80. README

O README deverá permanecer curto e operacional.

Quando o ambiente estiver funcional, deverá possuir:

* descrição;
* requisitos;
* instalação;
* execução;
* documentação.

O guia completo continuará aqui.

---

# 81. Uso do Codex

Antes de solicitar implementação ao Codex:

1. criar ou selecionar Issue;
2. garantir que documentação está atualizada;
3. informar escopo;
4. informar arquivos relevantes;
5. informar critérios de conclusão.

---

# 82. Prompt base para Codex

Exemplo:

```text
Implemente a Issue: [TÍTULO].

Antes de alterar código, leia:

- PRODUCT.md
- docs/02-architecture.md
- docs/03-database.md
- docs/08-development-standards.md

Leia também qualquer documento diretamente relacionado à Issue.

Siga somente o escopo definido.

Não altere:
- arquitetura;
- stack;
- dependências importantes;
- modelagem;
- estrutura de apps;
- escopo de versão;

sem necessidade técnica comprovada.

Ao finalizar:

1. informe arquivos alterados;
2. explique decisões relevantes;
3. liste testes realizados;
4. informe qualquer pendência.
```

---

# 83. Revisar trabalho do Codex

Nunca assumir que uma alteração está correta apenas porque foi gerada automaticamente.

Revisar:

* `git diff`;
* arquivos afetados;
* migrations;
* dependências;
* segurança;
* testes;
* escopo.

Executar o projeto antes do commit quando possível.

---

# 84. Situação inesperada com Codex

Se o Codex sugerir:

```text
React
Docker
Redis
Celery
nova API
novo banco
microserviços
alteração de arquitetura
```

isso não deverá ser aceito automaticamente.

Comparar com a documentação primeiro.

Essas tecnologias poderão ser utilizadas futuramente quando houver necessidade real.

---

# 85. Fluxo ideal de uma Issue

```text
Backlog
   │
   ▼
Próxima Sprint
   │
   ▼
Ler documentação
   │
   ▼
Em Desenvolvimento
   │
   ▼
Implementar
   │
   ▼
Testar
   │
   ▼
Revisão
   │
   ▼
Testes
   │
   ▼
Commit / Push
   │
   ▼
Concluído
```

---

# 86. Quando uma Issue não está pronta

Não iniciar se faltar decisão crítica sobre:

* comportamento;
* modelagem;
* dependência;
* entrada;
* saída;
* segurança.

Consultar primeiro os documentos existentes.

Se a documentação não resolver, registrar a decisão antes da implementação quando o impacto for relevante.

---

# 87. Quando uma Issue está grande demais

Exemplo:

```text
Implementar toda Loja de Crochê
```

Deverá ser dividida.

Exemplo:

```text
Criar catálogo
Criar página de produto
Criar opções
Criar carrinho
Criar finalização
Integrar WhatsApp
```

---

# 88. Evitar overengineering

Não criar antecipadamente:

* interfaces abstratas sem uso;
* repositories desnecessários;
* services vazios;
* APIs internas sem consumidor;
* múltiplas camadas para operações simples;
* arquiteturas distribuídas.

A estrutura deverá crescer conforme a necessidade.

---

# 89. Refatoração

Uma refatoração deverá ter objetivo concreto.

Exemplos:

```text
Remover duplicação
Separar responsabilidade
Facilitar teste
Corrigir acoplamento
Simplificar manutenção
```

Não interromper funcionalidade crítica para “embelezar” código sem benefício relevante.

---

# 90. Compatibilidade com versão futura

Preparar o projeto para crescer não significa implementar agora tudo que poderá existir.

Exemplo correto:

```text
Product possui relação com Store.
```

Isso permite múltiplas lojas.

Exemplo desnecessário agora:

```text
Criar toda aplicação fake_cakes vazia.
```

---

# 91. Desenvolvimento da versão 1.0

A ordem macro permanece:

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
Crochê
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
```

---

# 92. Após a documentação

Quando este documento estiver concluído, a fase de documentação inicial estará encerrada.

O próximo passo não será criar outro documento.

O próximo passo será:

```text
PREPARAÇÃO DO AMBIENTE DE DESENVOLVIMENTO
```

Começando por:

```text
Verificar Python
Verificar Git
Verificar PostgreSQL
Criar .venv
Criar arquivos-base necessários
Instalar dependências
Criar projeto Django
```

A execução deverá seguir as Issues e o backlog.

---

# 93. Primeiro objetivo técnico

O primeiro marco técnico será conseguir executar:

```bash
python src/manage.py runserver
```

com:

* Django configurado;
* PostgreSQL conectado;
* nenhuma migration pendente inesperada;
* aplicação acessível localmente.

---

# 94. Segundo objetivo técnico

Depois:

```text
Django Admin funcional
```

com:

* Store;
* Category;
* Product;
* ProductImage;
* ProductOptionGroup;
* ProductOption;
* FAQ;
* SiteSettings.

---

# 95. Terceiro objetivo técnico

Depois:

```text
Hub funcional
```

---

# 96. Quarto objetivo técnico

Depois:

```text
Loja de Crochê funcional
```

até chegar ao:

```text
WhatsApp
```

---

# 97. Critério para ambiente pronto

O ambiente local estará considerado pronto quando:

* Git funcionar;
* Python funcionar;
* ambiente virtual funcionar;
* dependências estiverem instaladas;
* PostgreSQL estiver acessível;
* Django conectar ao banco;
* migrations puderem executar;
* servidor local iniciar;
* Admin puder abrir.

---

# 98. Critério para uma máquina nova estar pronta

Em uma nova máquina, deve ser possível:

```text
Clonar
   ↓
Criar .venv
   ↓
Instalar requirements
   ↓
Criar .env
   ↓
Configurar PostgreSQL
   ↓
Migrate
   ↓
Runserver
```

Sem depender de arquivos secretos presentes em outra máquina.

---

# 99. Decisões fixadas

1. A documentação será a principal referência técnica.
2. O código será desenvolvido dentro de `src/`.
3. O projeto utilizará ambiente virtual.
4. Dependências serão instaladas via `requirements.txt`.
5. O banco local será PostgreSQL.
6. Configurações sensíveis ficarão no `.env`.
7. `.env` não será versionado.
8. Migrations serão versionadas.
9. Django Admin será utilizado na versão 1.0.
10. GitHub Issues organizará tarefas executáveis.
11. GitHub Projects acompanhará o andamento.
12. Código gerado pelo Codex será revisado.
13. Codex não deverá alterar decisões estruturais por conta própria.
14. Testes críticos serão executados antes da conclusão das funcionalidades.
15. Hub e Crochê são as áreas da versão 1.0.
16. Bolos Fake permanece como versão futura.
17. Não haverá criação antecipada de módulos sem uso.
18. A preparação do ambiente será a próxima fase após a documentação.

---

# 100. Relação com outros documentos

Escopo:

```text
/PRODUCT.md
```

Visão:

```text
/docs/01-vision.md
```

Arquitetura:

```text
/docs/02-architecture.md
```

Banco:

```text
/docs/03-database.md
```

Navegação:

```text
/docs/04-navigation.md
```

Design:

```text
/docs/05-design-system.md
```

Backlog:

```text
/docs/06-backlog.md
```

Roadmap:

```text
/docs/07-roadmap.md
```

Padrões:

```text
/docs/08-development-standards.md
```

Deploy:

```text
/docs/09-deploy.md
```

Este documento:

```text
/docs/10-developer-guide.md
```

Em caso de conflito:

1. `PRODUCT.md` define o escopo;
2. arquitetura e banco definem estrutura;
3. backlog e roadmap definem trabalho e evolução;
4. padrões definem como desenvolver;
5. deploy define produção;
6. este documento explica como executar o processo na prática.
