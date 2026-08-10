# Projeto Monizinha — Deploy e Infraestrutura

**Documento:** 09 — Deploy
**Versão:** 1.0
**Data:** 10/08/2026
**Projeto:** Projeto Monizinha
**Produto público:** Artes de Monizinha

---

## Status por área

* **[HUB — VERSÃO 1.0]** Será publicado.
* **[CROCHÊ — VERSÃO 1.0]** Será publicado.
* **[BOLOS FAKE — VERSÃO FUTURA]** Não possuirá fluxo comercial publicado na versão 1.0.

---

# 1. Objetivo

Este documento define a estratégia de deploy e infraestrutura do Projeto Monizinha.

Seu objetivo é estabelecer:

* como o projeto sairá do ambiente local para produção;
* onde a aplicação Django será hospedada;
* como o PostgreSQL será disponibilizado;
* como arquivos estáticos serão servidos;
* como imagens enviadas pelo Django Admin serão armazenadas;
* como variáveis de ambiente serão configuradas;
* como migrations serão executadas;
* como o GitHub participará do fluxo;
* quais verificações deverão ser realizadas antes e depois de cada deploy;
* quais limitações dos planos gratuitos precisam ser consideradas.

O objetivo inicial permanece manter o custo obrigatório em:

```text
R$ 0
```

---

# 2. Arquitetura de produção

A arquitetura planejada será:

```text
Usuário
   │
   ▼
HTTPS
   │
   ▼
Web Service
Django + Gunicorn
   │
   ├── Arquivos estáticos
   │
   ├── Serviço externo de mídia
   │
   └── PostgreSQL
```

O GitHub funcionará como origem oficial do código.

```text
Computador local
      │
      ▼
Git
      │
      ▼
GitHub
      │
      ▼
Render
      │
      ▼
Aplicação Django
```

---

# 3. Serviços planejados

A produção utilizará serviços distintos por responsabilidade.

## Aplicação

Planejamento inicial:

```text
Render Web Service
```

Responsável por executar:

* Python;
* Django;
* Gunicorn;
* templates;
* views;
* regras de negócio;
* sessões;
* integração com o banco.

---

## Banco de dados

Banco oficial:

```text
PostgreSQL
```

O banco poderá ser hospedado fora do mesmo provedor da aplicação caso isso seja necessário para manter a operação gratuita.

A aplicação deverá depender de uma variável:

```text
DATABASE_URL
```

Isso permitirá trocar o provedor do PostgreSQL sem alterar a lógica do projeto.

---

## Arquivos estáticos

Incluem:

* CSS;
* JavaScript;
* ícones;
* arquivos estáticos do Django Admin.

Poderão ser servidos pela própria aplicação com uma solução apropriada para produção.

---

## Mídia

Inclui:

* fotos dos produtos;
* imagens adicionais;
* imagens de categorias;
* conteúdo enviado pelo Django Admin.

Esses arquivos não deverão depender do disco temporário do Web Service.

---

# 4. Render

O Render será utilizado inicialmente para executar a aplicação Django.

### Vantagens

* suporte a Python;
* compatibilidade com Django;
* integração com GitHub;
* HTTPS;
* deploy automático;
* domínio gratuito;
* configuração por variáveis de ambiente;
* logs;
* facilidade de uso;
* possibilidade de evolução para planos pagos.

---

# 5. Limitação do Web Service gratuito

O serviço gratuito poderá entrar em estado de suspensão após determinado período sem requisições.

Na prática:

```text
Site sem acessos
       │
       ▼
Serviço suspenso
       │
       ▼
Novo visitante
       │
       ▼
Servidor inicia novamente
       │
       ▼
Página é carregada
```

A primeira requisição após suspensão poderá levar um tempo significativamente maior que as seguintes.

### Consequência para a versão 1.0

Essa limitação será aceita inicialmente por causa do objetivo de custo zero.

### Futuro

Caso o volume comercial torne a espera prejudicial, será avaliado:

* plano pago;
* outro provedor;
* mudança de infraestrutura.

A arquitetura não deverá depender de comportamentos exclusivos do Render.

---

# 6. PostgreSQL e Render

O PostgreSQL continuará sendo o banco oficial do Projeto Monizinha.

Entretanto, o banco gratuito do Render não será tratado como armazenamento permanente da produção.

Portanto:

```text
Render = aplicação Django
```

não significa obrigatoriamente:

```text
Render = PostgreSQL definitivo
```

---

# 7. Estratégia para o banco gratuito

A escolha definitiva do provedor do PostgreSQL gratuito deverá obedecer aos seguintes critérios:

* PostgreSQL real;
* custo inicial R$ 0;
* persistência adequada;
* conexão externa permitida;
* compatibilidade com Django;
* armazenamento suficiente;
* disponibilidade aceitável;
* documentação;
* possibilidade de exportação;
* possibilidade de migração;
* credenciais via URL.

A escolha deverá ser validada no momento da configuração da infraestrutura.

Não será acoplado código específico a um provedor.

---

# 8. Portabilidade do PostgreSQL

A aplicação deverá utilizar configurações compatíveis com PostgreSQL padrão.

Evitar depender de recursos exclusivos do fornecedor de hospedagem sem necessidade.

Fluxo futuro de migração deverá ser possível:

```text
PostgreSQL Provedor A
        │
        ▼
Backup
        │
        ▼
PostgreSQL Provedor B
        │
        ▼
Atualizar DATABASE_URL
```

Isso reduz dependência de fornecedor.

---

# 9. Ambiente local

O ambiente de desenvolvimento possuirá suas próprias configurações.

Exemplo:

```text
DEBUG=True
```

Banco:

```text
PostgreSQL local
```

ou outro PostgreSQL utilizado exclusivamente para desenvolvimento.

---

# 10. Ambiente de produção

Produção deverá utilizar:

```text
DEBUG=False
```

Além disso:

* `SECRET_KEY` própria;
* PostgreSQL de produção;
* `ALLOWED_HOSTS`;
* HTTPS;
* configuração de CSRF;
* armazenamento persistente de mídia;
* arquivos estáticos preparados;
* logging.

---

# 11. Variáveis de ambiente

Nenhum segredo deverá estar no código.

Variáveis planejadas:

```text
SECRET_KEY
DEBUG
DATABASE_URL
ALLOWED_HOSTS
CSRF_TRUSTED_ORIGINS
WHATSAPP_NUMBER
```

Caso necessário:

```text
MEDIA_STORAGE_URL
MEDIA_STORAGE_KEY
MEDIA_STORAGE_SECRET
MEDIA_STORAGE_NAME
```

Os nomes definitivos dependerão do serviço escolhido.

---

# 12. `.env`

No computador local poderá existir:

```text
.env
```

Esse arquivo deverá estar listado em:

```text
.gitignore
```

Nunca deverá ser enviado ao GitHub.

---

# 13. `.env.example`

O repositório conterá:

```text
.env.example
```

Exemplo:

```text
SECRET_KEY=
DEBUG=True
DATABASE_URL=
ALLOWED_HOSTS=
CSRF_TRUSTED_ORIGINS=
WHATSAPP_NUMBER=
```

Sem valores sensíveis.

---

# 14. `SECRET_KEY`

Em desenvolvimento poderá existir uma chave exclusiva do ambiente local.

Produção utilizará outra chave.

Nunca deverá existir no repositório público.

A troca da chave não deverá exigir alteração de código.

---

# 15. `DEBUG`

Desenvolvimento:

```text
DEBUG=True
```

Produção:

```text
DEBUG=False
```

O deploy não será considerado válido caso a aplicação pública esteja com debug ativado.

---

# 16. `ALLOWED_HOSTS`

Produção deverá permitir somente os hosts necessários.

Inicialmente poderá incluir o endereço do Render.

Exemplo conceitual:

```text
projeto-monizinha.onrender.com
```

Quando houver domínio próprio, ele será adicionado.

---

# 17. `CSRF_TRUSTED_ORIGINS`

Os domínios HTTPS utilizados pela aplicação deverão ser configurados quando necessário.

Exemplo conceitual:

```text
https://projeto-monizinha.onrender.com
```

Quando houver domínio próprio:

```text
https://artesdemonizinha.com.br
https://www.artesdemonizinha.com.br
```

---

# 18. Dependências de produção

O projeto deverá possuir dependências necessárias para execução em produção.

Possíveis dependências:

```text
Django
psycopg
gunicorn
whitenoise
Pillow
```

Além das dependências relacionadas ao armazenamento de mídia, caso necessárias.

As versões serão definidas quando o ambiente for configurado.

---

# 19. Gunicorn

A aplicação Django será executada em produção através de um servidor WSGI apropriado.

Planejamento:

```text
Gunicorn
```

Fluxo:

```text
Render
  │
  ▼
Gunicorn
  │
  ▼
Django
```

O servidor de desenvolvimento:

```text
python manage.py runserver
```

não será utilizado como servidor de produção.

---

# 20. Comando de inicialização

O comando dependerá da estrutura final dentro de `src/`.

Exemplo conceitual:

```text
gunicorn config.wsgi:application
```

O caminho definitivo deverá ser confirmado após a criação real do projeto Django.

Não copiar esse comando para o Render antes de validar a estrutura.

---

# 21. Build

Antes da inicialização da aplicação, será necessário:

* instalar dependências;
* preparar arquivos estáticos;
* executar tarefas de build necessárias.

Fluxo conceitual:

```text
pip install
     │
     ▼
collectstatic
     │
     ▼
Django pronto
```

Migrations serão tratadas de maneira controlada.

---

# 22. Build script

Poderá ser criado:

```text
scripts/build.sh
```

ou:

```text
build.sh
```

dependendo da organização escolhida no momento da configuração.

Possíveis operações:

```bash
pip install -r requirements.txt
python src/manage.py collectstatic --noinput
python src/manage.py migrate
```

A localização e inclusão das migrations no build deverão ser avaliadas antes da configuração definitiva.

---

# 23. Migrations

Migrations pertencem ao código do projeto.

Deverão ser versionadas no Git.

Fluxo:

```text
Alterar model localmente
        │
        ▼
makemigrations
        │
        ▼
Revisar
        │
        ▼
Commit
        │
        ▼
Deploy
        │
        ▼
migrate produção
```

Não criar migrations diretamente em produção.

---

# 24. Cuidados com migrations

Antes de migrations importantes:

* revisar alteração;
* considerar dados existentes;
* verificar campos obrigatórios;
* evitar perda de dados;
* possuir backup quando necessário.

Migrations destrutivas exigirão cuidado especial após o lançamento.

---

# 25. Arquivos estáticos

Arquivos estáticos incluem:

```text
CSS
JavaScript
Bootstrap local, se utilizado
Bootstrap Icons local, se utilizado
Django Admin assets
Imagens fixas da interface
```

O Django deverá possuir:

```text
STATIC_URL
STATIC_ROOT
```

configurados adequadamente.

---

# 26. `collectstatic`

Antes da execução em produção deverá ocorrer:

```bash
python manage.py collectstatic --noinput
```

O processo reunirá os arquivos estáticos no diretório de produção definido.

---

# 27. WhiteNoise

WhiteNoise poderá ser utilizado para servir arquivos estáticos diretamente pela aplicação Django.

Objetivo:

* simplificar a infraestrutura;
* evitar um serviço adicional para CSS e JavaScript;
* funcionar adequadamente para o volume inicial.

WhiteNoise não será utilizado para armazenar uploads de usuários ou produtos.

---

# 28. Static x Media

É essencial manter essa distinção.

## Static

Faz parte do código:

```text
CSS
JS
ícones
logo fixo
imagens da interface
```

## Media

É enviado através da aplicação:

```text
fotos dos produtos
galeria
imagens cadastradas no Admin
imagens de categorias
```

Static pode ser recriado a partir do Git.

Media não.

---

# 29. Persistência de mídia

Arquivos enviados através do Django Admin não deverão depender do armazenamento efêmero da aplicação.

Se forem armazenados apenas no filesystem temporário do Web Service, poderão desaparecer após:

* deploy;
* reinicialização;
* reconstrução;
* substituição da instância.

Portanto, mídia utilizará serviço persistente externo.

---

# 30. Serviço de imagens

A decisão definitiva ainda será feita durante a configuração prática.

O serviço deverá atender:

* plano gratuito;
* Django;
* upload;
* persistência;
* HTTPS;
* entrega rápida;
* organização;
* facilidade para migração.

Cloudinary permanece como candidato, mas a decisão somente será fixada após validar limites e integração atual.

---

# 31. Upload de imagens

Fluxo esperado:

```text
Admin
  │
  ▼
Django
  │
  ▼
Storage configurado
  │
  ▼
Arquivo persistente
  │
  ▼
URL armazenada/referenciada
  │
  ▼
Produto
```

O administrador não deverá precisar utilizar diretamente o painel do provedor de mídia para cadastrar um produto comum.

---

# 32. Domínio inicial

A versão inicial utilizará o domínio gratuito disponibilizado pela plataforma.

Exemplo:

```text
*.onrender.com
```

Isso mantém o custo:

```text
R$ 0
```

---

# 33. Domínio próprio futuro

Quando houver interesse, poderá ser adquirido um domínio próprio.

Exemplo:

```text
artesdemonizinha.com.br
```

A aplicação deverá continuar funcionando sem mudanças arquiteturais.

Alterações esperadas:

* DNS;
* domínio no Render;
* `ALLOWED_HOSTS`;
* `CSRF_TRUSTED_ORIGINS`;
* configurações de SEO;
* canonical URLs.

---

# 34. HTTPS

Produção deverá utilizar HTTPS.

A aplicação não deverá solicitar ou transmitir formulários publicamente através de HTTP simples.

Redirecionamentos e configurações de segurança poderão ser ajustados após validação do funcionamento no ambiente de produção.

---

# 35. Deploy pelo GitHub

Render será conectado ao repositório:

```text
BoratCRF/Projeto_Monizinha
```

A branch de produção será:

```text
main
```

Fluxo:

```text
Commit local
    │
    ▼
Push main
    │
    ▼
GitHub
    │
    ▼
Render detecta alteração
    │
    ▼
Build
    │
    ▼
Deploy
```

---

# 36. Auto Deploy

O deploy automático poderá ser habilitado para a branch principal.

Entretanto, depois que o sistema estiver sendo utilizado comercialmente, alterações relevantes deverão ser testadas antes do push para produção.

A estratégia poderá evoluir futuramente para:

```text
feature branch
      │
      ▼
testes
      │
      ▼
main
      │
      ▼
deploy
```

---

# 37. Primeira configuração do Render

Fluxo planejado:

```text
Render Dashboard
       │
       ▼
New Web Service
       │
       ▼
Conectar GitHub
       │
       ▼
Selecionar Projeto_Monizinha
       │
       ▼
Configurar ambiente Python
       │
       ▼
Configurar Build Command
       │
       ▼
Configurar Start Command
       │
       ▼
Variáveis de ambiente
       │
       ▼
Deploy
```

Os valores exatos somente serão definidos quando o projeto Django existir.

---

# 38. Região

Sempre que possível, aplicação e banco deverão estar geograficamente próximos.

Objetivos:

* reduzir latência;
* melhorar conexão;
* reduzir tempo de consultas.

Caso o banco esteja em outro provedor, isso deverá ser considerado na escolha.

---

# 39. Banco de produção

Nunca utilizar o mesmo banco para:

```text
desenvolvimento
```

e:

```text
produção
```

Deverão existir ambientes separados.

---

# 40. Dados iniciais

Após criar o banco de produção poderão ser necessários:

* Store de Crochê;
* SiteSettings;
* superusuário;
* grupos;
* permissões;
* categorias;
* produtos.

Esses dados poderão ser inseridos:

* pelo Admin;
* por fixture;
* por data migration;
* por comando customizado;

conforme a necessidade.

---

# 41. Superusuário

O superusuário de produção não deverá possuir senha trivial.

Evitar:

```text
admin
admin123
123456
```

A senha nunca deverá aparecer no repositório.

---

# 42. Usuários comerciais

Após validar o Admin:

* criar usuário da proprietária;
* criar usuário da colaboradora;
* configurar grupos;
* atribuir permissões;
* testar acessos.

Não fornecer acesso de superusuário sem necessidade.

---

# 43. Backups

Mesmo em infraestrutura gratuita, dados comerciais não deverão depender de uma única cópia.

Conteúdo importante inclui:

* produtos;
* categorias;
* opções;
* configurações;
* FAQ;
* usuários;
* dados administrativos.

---

# 44. Estratégia inicial de backup

Enquanto não existir backup automatizado adequado, poderão ser realizados backups manuais periódicos do PostgreSQL.

Formato preferencial:

```text
pg_dump
```

Esses arquivos:

* não deverão ser colocados no repositório público;
* deverão ser armazenados em local seguro;
* deverão possuir data;
* deverão ser testáveis para restauração.

---

# 45. Backup de mídia

Banco e imagens são coisas diferentes.

Backup do PostgreSQL não copia automaticamente as fotos externas.

Portanto, o serviço de mídia deverá possuir estratégia própria de preservação ou exportação quando o volume justificar.

---

# 46. Logs

A plataforma de produção deverá permitir visualizar logs da aplicação.

Logs serão utilizados para:

* erros;
* falhas de deploy;
* problemas no banco;
* exceptions;
* comportamento inesperado.

Não deverão expor:

* senhas;
* tokens;
* chaves;
* dados pessoais desnecessários.

---

# 47. Erros de produção

A aplicação deverá possuir:

```text
404.html
403.html
500.html
```

Quando `DEBUG=False`, o visitante não deverá receber traceback interno.

---

# 48. Logging do Django

O logging inicial poderá permanecer simples.

Deverá permitir identificar erros da aplicação.

Uma plataforma externa de monitoramento poderá ser adicionada futuramente se houver necessidade.

---

# 49. Segurança antes do deploy

Antes de publicar:

* `DEBUG=False`;
* chave secreta segura;
* hosts configurados;
* CSRF configurado;
* HTTPS;
* Admin protegido;
* permissões revisadas;
* uploads validados;
* dependências atualizadas;
* nenhum segredo no Git.

---

# 50. Django deployment checklist

Antes do lançamento deverá ser executado:

```bash
python manage.py check --deploy
```

Os avisos deverão ser analisados individualmente.

Não ignorar alertas apenas para conseguir concluir o deploy.

---

# 51. Testes antes do deploy

Antes de publicar uma alteração relevante:

```bash
python manage.py test
```

quando houver testes automatizados correspondentes.

Também deverá haver validação manual dos fluxos críticos.

---

# 52. Checklist pré-deploy

## Código

* branch correta;
* alterações commitadas;
* working tree limpa;
* dependências registradas;
* migrations versionadas.

## Configuração

* variáveis;
* banco;
* static;
* media;
* hosts;
* CSRF.

## Testes

* Django tests;
* Hub;
* catálogo;
* produto;
* carrinho;
* WhatsApp;
* Admin.

---

# 53. Checklist pós-deploy

Após cada deploy importante testar:

### [HUB]

* `/`;
* Sobre;
* FAQ;
* contato;
* privacidade;
* links.

### [CROCHÊ]

* `/croche/`;
* catálogo;
* categoria;
* busca;
* produto;
* opções;
* carrinho;
* finalização.

### Administração

* login;
* produto;
* imagem;
* categoria;
* opções;
* permissões.

### Infraestrutura

* PostgreSQL;
* arquivos estáticos;
* mídia;
* HTTPS.

---

# 54. Teste real do WhatsApp

Deverá ser realizado em:

* computador com WhatsApp Web;
* smartphone.

Validar:

* número;
* acentos;
* quebras de linha;
* espaços;
* caracteres especiais;
* nomes dos produtos;
* opções;
* quantidades.

---

# 55. Testes após suspensão

Como o serviço gratuito pode ficar inativo, deverá ser testado também o comportamento após período sem acesso.

Validar:

* página de carregamento;
* tempo de retorno;
* sessões;
* banco;
* mídia;
* primeiro acesso.

---

# 56. Monitoramento inicial

Nos primeiros dias após publicação, deverão ser observados:

* erros nos logs;
* páginas lentas;
* imagens quebradas;
* erros no carrinho;
* mensagens do WhatsApp;
* problemas no Admin;
* dúvidas da proprietária;
* problemas de celular.

Esses problemas deverão gerar Issues quando necessário.

---

# 57. Rollback

Caso um deploy cause erro grave, deverá ser possível retornar a uma versão estável do código.

Git permite recuperar commits anteriores.

A plataforma de hospedagem poderá também oferecer recursos próprios de rollback.

Migrações de banco exigirão cuidado adicional porque rollback de código não significa automaticamente rollback de schema.

---

# 58. Deploy de migrations destrutivas

Após o lançamento, alterações como:

```text
remover coluna
alterar relacionamento
remover tabela
```

deverão ser tratadas cuidadosamente.

Preferir evolução em etapas quando houver dados reais.

---

# 59. Conteúdo antes do lançamento

O site não deverá ser publicado oficialmente com catálogo vazio.

Antes da divulgação deverão existir:

* categorias reais;
* produtos reais;
* fotos;
* descrições;
* preços ou consulta;
* opções;
* WhatsApp correto;
* redes sociais corretas.

---

# 60. “Bolos Fake — Em breve”

A versão de produção poderá apresentar Bolos Fake como:

```text
Em breve
```

Mas não deverá possuir:

* links quebrados;
* páginas incompletas;
* catálogo vazio público;
* orçamento falso;
* chamadas indicando disponibilidade.

---

# 61. SEO após deploy

Depois que o domínio definitivo estiver conhecido:

* revisar canonical URLs;
* sitemap;
* robots.txt;
* Search Console;
* Open Graph;
* domínio público;
* metadados.

Esses itens não deverão bloquear o deploy comercial básico quando não forem críticos.

---

# 62. Domínio próprio

A aquisição de domínio não é requisito da primeira publicação.

Quando ocorrer, será criada uma Issue específica.

Exemplo:

```text
[DEPLOY] Configurar domínio próprio
```

---

# 63. Mudança de provedor

A aplicação deverá poder sair do Render no futuro.

Para isso:

* código ficará no GitHub;
* banco será PostgreSQL padrão;
* variáveis serão externas;
* mídia será desacoplada;
* domínio será independente;
* dependências serão documentadas.

O Render não deverá aparecer dentro das regras de negócio.

---

# 64. Escalabilidade

A arquitetura inicial não será criada para tráfego massivo.

Caso o crescimento justifique, poderão ser adicionados:

* instância maior;
* cache;
* CDN;
* workers;
* Redis;
* storage dedicado;
* PostgreSQL maior;
* monitoramento;
* load balancing.

Nada disso pertence à versão 1.0.

---

# 65. Disponibilidade

O plano gratuito não oferece a mesma experiência de um serviço comercial pago continuamente ativo.

Isso será aceito enquanto:

* tráfego for baixo;
* custo zero for prioridade;
* o atraso ocasional não impedir significativamente as vendas.

Quando isso mudar, infraestrutura deverá ser reavaliada.

---

# 66. Critério para migrar para plano pago

Uma migração deverá ser considerada quando:

* cold starts prejudicarem clientes;
* vendas dependerem fortemente do site;
* disponibilidade precisar ser maior;
* tráfego crescer;
* limites de banco forem atingidos;
* recursos gratuitos deixarem de atender;
* custo passar a ser justificável comercialmente.

---

# 67. Ambientes futuros

No início existirão principalmente:

```text
Development
Production
```

Futuramente poderá ser criado:

```text
Staging
```

Fluxo:

```text
Development
     │
     ▼
Staging
     │
     ▼
Production
```

Não será criado staging apenas por formalidade na versão inicial.

---

# 68. CI/CD futuro

GitHub Actions poderá futuramente executar:

* testes;
* lint;
* validações;
* segurança;
* deploy.

Inicialmente isso não será obrigatório.

O Render + GitHub já fornecerá o fluxo básico de deploy.

---

# 69. Dependência do GitHub

O repositório é a fonte oficial do código.

Mudanças feitas diretamente em servidores sem registro no Git não deverão ocorrer.

Regra:

```text
Código em produção deve existir no Git.
```

---

# 70. Git e produção

O deploy deverá sempre apontar para uma referência conhecida.

Principalmente:

```text
main
```

O código local não commitado nunca deverá ser considerado parte oficial da aplicação.

---

# 71. CHANGELOG

Antes de Releases importantes, atualizar:

```text
CHANGELOG.md
```

Exemplo:

```text
1.0.0

Added
- Hub Artes de Monizinha
- Loja de Crochê
- Catálogo
- Carrinho
- WhatsApp
```

---

# 72. Release 1.0

Após validação final poderá ser criada uma Release:

```text
v1.0.0
```

No GitHub.

Isso marcará oficialmente a primeira versão funcional.

---

# 73. Critérios de lançamento da versão 1.0

A aplicação somente deverá ser considerada lançada quando:

* estiver publicamente acessível;
* PostgreSQL funcionar;
* imagens persistirem;
* Admin funcionar;
* Hub funcionar;
* Crochê funcionar;
* carrinho funcionar;
* WhatsApp funcionar;
* celular funcionar;
* `DEBUG=False`;
* erros críticos estiverem resolvidos.

---

# 74. Itens que não bloquearão o lançamento

Não bloquear:

* Bolos Fake;
* domínio próprio;
* dashboard customizada;
* analytics avançado;
* pagamento;
* login de cliente;
* IA;
* API;
* animações;
* SEO avançado.

---

# 75. Decisões fixadas

1. A aplicação Django será inicialmente hospedada no Render.
2. O banco será PostgreSQL.
3. O PostgreSQL poderá utilizar outro provedor.
4. A aplicação utilizará `DATABASE_URL`.
5. O plano gratuito do Render poderá apresentar cold start.
6. Essa limitação será aceita inicialmente.
7. Mídia não ficará no filesystem temporário do Render.
8. Arquivos estáticos poderão utilizar WhiteNoise.
9. Gunicorn será utilizado para executar Django em produção.
10. `runserver` não será utilizado em produção.
11. Credenciais serão variáveis de ambiente.
12. `.env` não será versionado.
13. Migrations serão versionadas.
14. Produção utilizará `DEBUG=False`.
15. HTTPS será obrigatório.
16. Desenvolvimento e produção usarão bancos separados.
17. O código em produção deverá existir no GitHub.
18. A branch principal de produção será `main`.
19. Domínio próprio não é requisito da versão 1.0.
20. Bolos Fake não será publicado como loja funcional.
21. Backup deverá ser considerado desde a primeira versão.
22. A infraestrutura poderá migrar de provedor futuramente.
23. Serviços gratuitos deverão ser usados sem criar dependência arquitetural irreversível.
24. Mudanças de infraestrutura serão feitas somente quando houver necessidade concreta.

---

# 76. Relação com outros documentos

O escopo está registrado em:

```text
/PRODUCT.md
```

A arquitetura está registrada em:

```text
/docs/02-architecture.md
```

O banco está registrado em:

```text
/docs/03-database.md
```

Os padrões estão registrados em:

```text
/docs/08-development-standards.md
```

O guia de configuração local será registrado em:

```text
/docs/10-developer-guide.md
```

Em caso de conflito:

1. `PRODUCT.md` define o produto;
2. `02-architecture.md` define a arquitetura;
3. `03-database.md` define os dados;
4. `08-development-standards.md` define os padrões de desenvolvimento;
5. este documento define produção e deploy.