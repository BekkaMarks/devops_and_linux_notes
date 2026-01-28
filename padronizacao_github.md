# Entendendo Git

O Git é um sistema de controle de versão distribuído (DVCS). Ele permite acompanhar o histórico de mudanças, recuperar versões anteriores, coordenar o trabalho entre várias pessoas e manter o fluxo de desenvolvimento organizado, tudo isso de forma eficiente e confiável.

## Configurações básicas do Git

Essas configurações são salvas localmente e reutilizadas em cada commit:

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

⚠️ Caso exista um `user.name` definido no escopo local, ele terá prioridade sobre o valor no escopo global. Assim, cada repositório pode sobrescrever as configurações globais, se necessário.

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
- `git init`: cria um repositório Git no diretório atual, gerando uma pasta oculta chamada `.git`.

### 2. Clonar um repositório existente

Quando já existe um repositório remoto criado por você ou outra pessoa, você pode copiá-lo localmente:

```bash
git clone https://exemplo.com/repositorio.git
```

Este comando faz o download do projeto inteiro, incluindo histórico de commits e branches.

## Ciclo de vida no Git (Git Lifecycle)

O ciclo de vida define os diferentes estágios pelos quais um arquivo passa em um projeto Git:

```text
┌────────────────┐  ┌───────────────────────────┐  ┌────────────┐  ┌────────────────────────────┐
│  Rastreamento  │  │    Preparação (staging)   │  │   Commit   │  │ Envio de alterações (push) │
└────────────────┘  └───────────────────────────┘  └────────────┘  └────────────────────────────┘
```

Esses estágios garantem que as alterações sejam processadas de forma sistemática, reduzindo erros e melhorando a colaboração.

#### Principais estágios do ciclo de vida do Git:

1. Diretório de trabalho (Working Directory)
2. Área de preparação (Staging Area)
3. Repositório local (Local Repository)
4. Repositório remoto (Remote Repository)

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
