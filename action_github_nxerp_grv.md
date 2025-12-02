<h1>Funcionamento do Action GitHub – Jira NXErp</h1>

<h3>create-branch.yml</h3>

<strong><em>workflow_dispatch:</em></strong> pode ser acionado via API.

<strong><em>issue_key:</em></strong> define o nome base da branch.

<strong><em>prefix:</em></strong> adiciona o prefixo ao nome da branch, por exemplo:
feature/NL-123 ou bugfix/NL-123.

<strong><em>source_branch:</em></strong> branch de origem (pode ser qualquer branch).

<strong><em>hotfix e version:</em></strong> são dois parâmetros que devem ser enviados juntos.
Se hotfix = true, o source_branch é alterado para ser baseado na versão.

<h3>Geração de token (Bearer)</h3>
No GitHub:
Acesse Developer settings → Personal access tokens → Tokens (classic) → Generate new token → Generate new token (classic).

<h3>create-pr.yml</h3>

<strong><em>issue_key:</strong></em> identifica a branch com base no create-branch.yml. O valor é passado por match, não por comparação de igualdade.

<strong><em>target_branch:</strong></em> branch onde o PR será criado.

<strong><em>description:</strong></em> descrição vinda do Jira.

<strong><em>title:</strong></em> título vindo do Jira.

<strong><em>version:</strong></em> utilizada para backport — transporta o PR para outra versão.

hotfix: se for true, a target_branch muda para se basear na versão.
Porém, o backport não vai para version, e sim para develop.

<h3>Backport</h3>

O backport pega um PR existente, cria uma branch a partir dele e direciona para as versões que devem receber aquela melhoria.
O mesmo processo pode ser feito para a develop (quando há um hotfix e precisamos aplicá-lo também na develop).

https://www.youtube.com/watch?v=r7Va1kPCsKQ
