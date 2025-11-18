<h1>Grupos e Usuários (Linux)</h1>

<p>No Linux, um usuário (user) é uma conta que representa uma pessoa, serviço ou processo dentro do sistema. Cada usuário possui um identificador numérico único (UID), um diretório pessoal, um shell padrão e um conjunto específico de permissões. Essa estrutura organiza e separa as atividades de cada conta, tornando o sistema mais seguro e fácil de administrar, pois limita o acesso apenas ao que foi permitido.</p>

<p>A existência de vários usuários é especialmente útil em ambientes onde várias pessoas utilizam o mesmo computador ou servidor. Em empresas, cada funcionário pode acessar recursos compartilhados sem interferir nos arquivos dos colegas. Em escolas, contas separadas garantem a privacidade de materiais, notas e atividades de alunos e professores. Em servidores, equipes como desenvolvimento, banco de dados e suporte trabalham com permissões específicas, evitando acessos indevidos.</p>

<p>Uma forma simples de visualizar isso é imaginar o computador como uma casa: você é o administrador, responsável por todas as portas, mas pode permitir que outras pessoas entrem apenas nos cômodos necessários. No Linux funciona da mesma forma — cada usuário tem seu próprio espaço protegido, e o administrador decide o que pode ser acessado ou não. Essa organização traz privacidade, controle e segurança para qualquer ambiente.</p>

<h3>As informações do usuário são armazenadas em:</h3>

<table>
    <tbody>
        <tr>
          <td>/etc/passwd</td>
          <td>Detalhes básicos da conta.</td>
        </tr>
         <tr>
            <td>/etc/shadow</td>
            <td>Senhas criptografadas.</td>
        </tr>
          <tr>
            <td>/etc/group</td>
            <td>Informações sobre associação a grupos.</td>
          </tr>
    </tbody>
</table>

<p>Quando um usuário executa um comando, acessa um arquivo ou realiza tarefas administrativas, o Linux verifica esses arquivos para decidir se permite ou nega a ação.</p>


<h2>Tipos de Usuário</h2>

<form>
    <ol>
        <li>
            <strong>Root</strong>:
            <ul>
                <li>
                   O usuário root (UID 0) tem permissão de executar <strong>qualquer ação</strong>, incluíndo: Instalar ou remover software, alterar arquivos do sistema, editar os dados de qualquer usuário, reiniciar servições do sistetam, etc. <strong>O acesso root deve ser tratado com cuidado, pois um único erro pode comprometer o sistema</strong>.<br><br>
                </li>
            </ul>
        </li>
        <li>
            <strong>Regular</strong>
            <ul>
              <li>
                São criadas para funionários, desenvolvedores, equipes de suporte ou qualquer pessoa que precise de acesso controlado. Essas contas possuem seu próprio diretório pessoal, podem armazenar arquivos, executar apliativos pemitidos e não é possível realizar modificações e configurações do sistema. <strong>Suas ações são limitadas por questões de segurança</strong>.<br><br>
              </li>
          </ul>
        </li>
       <li>
          <strong>Usuários do sistema</strong>:
        <ul>
          <li>
             Esses usuários não se destinam ao login. Eles são criados por serviços e aplicativos para executar processos com segurança. Por exemplo: MySQL para bancos de dados, www-dados para servidores web, daemon para tarefas em segundo plano.<br><br>
            </li>
          </ul>
        </li>
    </ol>
</form>

<h2>Criando Usuários</h2>

<p>Formas comuns de se criar usuários no Linux:</p>

<table>
    <tbody>
        <tr>
          <td><strong>useradd name</strong></td>
          <td>Ferramenta de linha de comando básico e direto para adicionar novos usuários ao sistema, mas não fornece uma interface interativa e amigável durante o processo.</td>
        </tr>
        <tr>
          <td><strong>useradd -m name</strong></td>
          <td>Cria o usuário e também cria o diretório home (por exemplo /home/name) caso não exista, copiando os arquivos padrão de /etc/skel e ajustando a propriedade/permissões. O comando não define senha automaticamente
          </td>
        </tr>
         <tr>
            <td><strong>adduser name</strong></td>
            <td>Ferramenta amigável e interativa para criar novos usuário ao sistema. Ele apresenta uma série de pergntas durante o processo de criação, como o nome completo do usuário, senha, grupos adicionais , tornando a tarefa mais simples para iniciantes.<br> O adduser também cuida automaticamente de várias configurações padrão, como a criação de uma pasta inicial para o usuário em /home e a atribuição de um shell padrão.
            </td>
        </tr>
    </tbody>
</table>
<form>
  <ol>
    <ul>
      <li>
        ⚠️ Importante: os comandos mencionados precisam ser executados com privilégios de administrador (sudo ou root), pois criar, modificar ou remover usuários altera partes críticas do sistema.<br><br>
      </li>
    </ul>
    <ul>
     <li>
        ⚠️ Para o comando useradd, lembre-se de criar uma senha <strong>'sudo passwd name'</strong>, a home <strong>'sudo mkdir /home/name'</strong> e o grupo <strong>'sudo chown name:name /home/neme'</strong>
      </li>
    </ul>
  </ol>
</form>

<h4> Possíveis erros:</h4>

<table>
  <thead>
        <th>Erro</th>
        <th>Possível Solução</th>
    </thead>
    <tbody>
        <tr>
          <td>useradd name</td>
          <td>...
          </td>
        </tr>
         <tr>
            <td>adduser name</td>
            <td>
              ...
            </td>
        </tr>
    </tbody>
</table>
<form>
  <ol>
    <ul>
      <li>
        ...
      </li>
    </ul>
  </ol>
</form>



<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
https://dev.to/diogoizele/grupos-e-usuarios-em-linux-o-que-voce-precisa-saber-4lp9
https://blog.scalefusion.com/pt/gerenciamento-de-usu%C3%A1rios-Linux/
