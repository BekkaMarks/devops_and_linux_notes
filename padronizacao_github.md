# Entendendo Git
O git nada mais é do que um sistema de controle de versão distribuída (DVCS). Ele permite acompamnhar histórico de mudanças,
recuperar versões anteriores, coordenar o trabalho entre várias pessoas e mantendo o fluxo de desenvolvimento organizado, tudo isso de forma eficiente e confiável.

## Configurações básicas de git

Essas configurações são registradas localmente e reutilizadas em cada commit.
```bash
git config --global user.name "Seu Nome"
git config --global user.email "email@exemplo.com"
```

Para verificar todas as configurações atualmente aplicadas:
```bash
git config --list
```

## Observação Técnica:

O Git carrega as configurações seguindo a seguinte ordem de prioridade (da mais alta para a mais baixa):

> --local — configurações específicas do repositório atual
> 
> --global — configurações do usuário
> 
> --system — configurações do sistema

⚠️ Caso exista um user.name definido no escopo local, ele terá prioridade sobre o valor definido no escopo global.

Isso significa que cada repositório pode sobrescrever as configurações globais, se necessário.

## Iniciando um repositório

Um repositóro no Git é uma estrutura que contém todo o histórico e metadados do seu projeto. 

Formas de obter um repositório:

Inicializar um novo repositório
```bash
mkdir nome-do-projeto 
cd nome-do-projeto 
git init
```
<strong>mkdir</strong>: comando que cria o diretório (make directory). <br>
<strong>cd</strong>: comando do terminal para mudar e acessar o diretório alvo (change directory). <br>
<strong>git init</strong>: é um comando que cria um repositório a partir do diretório que foi declarado.
E dentro deste diretório ele cria uma pasta oculta com o nome .git com todos os dados de controle de versão

### 📚 Referências Utilizadas na Construção deste Material:
https://git-scm.com/install/linux<br> 
https://medium.com/@hitoshyamamoto/git-na-pr%C3%A1tica-um-guia-completo-e-explicado-para-iniciantes-7cdaf1914e1f<br>
https://git-scm.com/docs/git-config<br>
https://stackoverflow.com/questions/60202175/what-is-the-difference-between-global-and-local-configuration-in-git
