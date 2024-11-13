---
folder: "[[SO]]"
---
No Linux, os conceitos de "usuários" e "grupos" são fundamentais para a gestão de permissões e a segurança do sistema.

### Usuários

No Linux, um **usuário** é uma entidade que pode fazer login e operar no sistema. Cada usuário tem um **identificador único (UID)** e um conjunto de permissões que definem o que ele pode acessar. Existem diferentes tipos de usuários:

1. **Usuário root**: É o superusuário do sistema, que tem todas as permissões possíveis. Pode modificar qualquer arquivo, configurar o sistema e gerenciar outros usuários.
2. **Usuários normais**: São os usuários comuns do sistema. Eles têm restrições impostas pelo sistema para evitar que possam modificar configurações críticas.
3. **Usuários do sistema**: São contas de usuários criadas para processos e serviços do sistema, como o servidor web ou o serviço de banco de dados. Esses usuários geralmente não têm login permitido.

Cada usuário tem seu diretório pessoal, tipicamente localizado em /home/username, onde seus arquivos e configurações pessoais são armazenados.

### Grupos

Um **grupo** é uma coleção de usuários que compartilham certas permissões. Cada grupo tem um identificador único (GID). Os grupos são usados para facilitar a administração das permissões:

- **Grupos primários e suplementares**: Cada usuário pertence a um grupo primário e pode pertencer a múltiplos grupos suplementares. O grupo primário é atribuído ao criar o usuário, e o usuário pertence a ele por padrão.
- **Permissões de grupo**: Arquivos e diretórios no Linux têm três níveis de permissão (para o proprietário, o grupo e outros) e três tipos de permissões (leitura, escrita e execução). Definir um grupo específico para um diretório ou arquivo facilita que todos os membros desse grupo possam ter acesso apropriado.

### Gerenciamento de Usuários e Grupos

- **Adicionar usuário**: Para adicionar um usuário, pode-se usar o comando useradd ou adduser. Exemplo:

```bash
sudo adduser nome_usuario
```

- **Adicionar grupo**: Pode-se criar um grupo com o comando groupadd:

```bash
sudo groupadd nome_grupo
```

- **Adicionar usuário a um grupo**: Para adicionar um usuário a um grupo, usa-se o comando usermod:

```bash
sudo usermod -aG nome_grupo nome_usuario
```


### Arquivos Importantes

- **/etc/passwd**: Contém informações sobre todos os usuários do sistema, incluindo seus nomes de login e UID.
- **/etc/group**: Contém informações sobre todos os grupos.
- **/etc/shadow**: Armazena as senhas dos usuários em formato criptografado.

### Exemplos de Uso

As permissões e associações de grupos são fundamentais em um ambiente colaborativo, pois permitem que arquivos e pastas sejam compartilhados apenas entre determinados grupos de usuários. Por exemplo, um projeto de software poderia ter um grupo para desenvolvedores que permite acesso de leitura e escrita em certos diretórios, enquanto o restante dos usuários tem apenas acesso de leitura ou nenhum acesso.

Essa estrutura flexível de usuários e grupos permite um controle detalhado sobre o que cada pessoa ou serviço pode fazer no sistema, aumentando a segurança e o gerenciamento eficiente de recursos.

