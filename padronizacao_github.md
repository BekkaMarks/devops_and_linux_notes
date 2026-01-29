# Entendendo Git

O Git é um sistema de controle de versão distribuída (DVCS). Ele permite acompanhar o histórico de mudanças, recuperar versões anteriores, coordenar o trabalho entre várias pessoas e manter o fluxo de desenvolvimento organizado, tudo de forma eficiente e confiável.

## Configurações básicas do Git

Essas configurações ficam registradas localmente e são utilizadas em cada commit.

```bash
git config --global user.name "Seu Nome"
git config --global user.email "email@exemplo.com"
```

Para verificar todas as configurações atuais:

```bash
git config --list
```

## Observação Técnica:
O Git aplica as configurações na seguinte ordem de prioridade (da mais alta para a mais baixa):

- `--local`: específicas do repositório atual
- `--global`: do usuário
- `--system`: do sistema

⚠️ Caso exista um `user.name` definido no escopo local, ele terá prioridade sobre o valor no escopo global.
Essa posição permite que cada repositório sobrescreva as configurações globais, se necessário.
## Iniciando um repositório

Um repositório Git armazena todo o histórico e metadados do seu projeto.

### 1. Inicializar um novo repositório

```bash
mkdir nome-do-projeto
cd nome-do-projeto
git init
```

- `mkdir`: cria um diretório (make directory).
- `cd`: acessa o diretório (change directory).
- `git init`: inicializa um repositório Git no diretório atual. Este comando cria uma pasta oculta chamada`.git`, onde ficam todos os dados de controle de versão.

### 2. Clonar um repositório existente

Quando já existe um repositório remoto, criado por você ou por outra pessoa, é possível cloná-lo para sua máquina, copiando todo o código e histórico.

Esse comando baixa todo o projeto, incluindo o histórico de commits e as ramificações (branches).
```bash
git clone https://exemplo.com/repositorio.git
```

## Ciclo de vida no Git (Git Lifecycle)

O ciclo de vida no Git define os diferentes estágios pelos quais um arquivo passa em um projeto versionado:

```text
┌────────────────┐  ┌───────────────────────────┐  ┌────────────┐  ┌────────────────────────────┐
│  Rastreamento  │——│    Preparação (staging)   │——│   Commit   │——│ Envio de alterações (push) │
└────────────────┘  └───────────────────────────┘  └────────────┘  └────────────────────────────┘
```

Esse ciclo de vida garante que as alterações sejam tratadas de forma sistemática, reduzindo erros e facilitando a colaboração.

#### Os quatro estágios principais no ciclo de vida do Git são:

1. <strong>Diretório de trabalho (Working Directory):</strong> Onde os arquivos são criados e modificados, mas ainda não foram monitorados ou reconhecidos pelo Git.
Comandos usados nesta etapa: 
      - `git status`: Verifica quais arquivos foram modificados ou ainda não estão sendo rastreados.
      - `git diff`: Visualizar alterações feitas no diretório de trabalho.
2. <strong>Área de preparação (Staging Area):</strong> Espaço temporário onde as alterações são adicionadas antes dos commits.
Comandos usados nesta etapa: 
      - git add filename→ Preparar um arquivo específico.
      - git add .→ Preparar todos os arquivos modificados.
      - git reset filename→ Remover um arquivo da área de preparação (movê-lo de volta para o diretório de trabalho).
3. <strong>Repositório local (Local Repository):</strong> Onde é armazenado todas as mudanças e commits.
      - git commit -m "Commit message"→ Salvar as alterações preparadas no repositório local.
      - git log→ Ver histórico de commits.
4. <strong>Repositório remoto (Remote Repository):</strong> Repositório compartilhado que está hospedado em uma plataforma (Github, GitLab e BitBucket) onde são realizados os comandos push e pull entre os colaboradores do repositório.
      - git push origin branch-name→ Enviar commits locais para o repositório remoto.
      - git pull origin branch-name→ Obter e mesclar alterações do repositório remoto.
      - git clone repository-url→ Copie um repositório remoto para o seu sistema local.
    
### Principais comandos do ciclo de vida:

```bash
git add arquivo.txt        # Adiciona arquivos à área de preparação
git commit -m "Mensagem"   # Salva/commita modificações localmente
git push                   # Envia os commits ao repositório remoto
```

---

### Referências Utilizadas

- https://git-scm.com/install/linux
- https://medium.com/@hitoshyamamoto/git-na-pr%C3%A1tica-um-guia-completo-e-explicado-para-iniciantes-7cdaf1914e1f
- https://git-scm.com/docs/git-config
- https://stackoverflow.com/questions/60202175/what-is-the-difference-between-global-and-local-configuration-in-git
- https://www.w3schools.in/git/lifecycle
