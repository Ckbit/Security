---
folder: "[[SO]]"
---
No Linux, o sistema de permissões de arquivos é fundamental para garantir a segurança e a organização de arquivos e diretórios, permitindo definir quem pode ler, escrever ou executar cada item. Dois comandos principais são usados para gerenciar essas permissões: chmod e chown.

### 1\. chmod - Alterar Permissões de Arquivos

O comando chmod (change mode) é usado para modificar as permissões de arquivos e diretórios. As permissões são divididas em três grupos:

1. **Usuário (owner)**: O dono do arquivo.
2. **Grupo (group)**: Usuários que pertencem ao grupo associado ao arquivo.
3. **Outros (others)**: Todos os demais usuários.

Cada grupo pode ter três tipos de permissões:

- **Leitura (r)**: Permite visualizar o conteúdo (4).
- **Escrita (w)**: Permite modificar o conteúdo (2).
- **Execução (x)**: Permite executar o arquivo (se for um programa ou script) (1).

Você pode definir permissões usando dois métodos:

#### Método Numérico

O método numérico usa valores somados para cada permissão. Por exemplo:

- chmod 755 arquivo:
  - **7** (4+2+1): Usuário pode ler, escrever e executar.
  - **5** (4+1): Grupo pode ler e executar.
  - **5** (4+1): Outros podem ler e executar.


#### Método Simbólico

O método simbólico usa letras para definir permissões:

- chmod u+x arquivo: Adiciona permissão de execução para o usuário.
- chmod g-w arquivo: Remove permissão de escrita do grupo.
- chmod o=r arquivo: Define permissão de leitura para outros, removendo as demais.

### 2\. chown - Alterar Proprietário e Grupo

O comando chown (change owner) é usado para alterar o proprietário e/ou o grupo de um arquivo ou diretório. Ele segue o formato:

- chown \[opções\] usuário\[:grupo\] arquivo

Por exemplo:

- chown maria arquivo: Transfere a posse do arquivo para o usuário "maria".
- chown maria:desenvolvedores arquivo: Transfere a posse para "maria" e associa o arquivo ao grupo "desenvolvedores".

### Exemplos Práticos

1. **Tornar um script executável para todos**:

```bash
chmod 755 script.sh
```

Permite que o dono tenha controle total e os outros possam apenas ler e executar.

2. **Alterar dono e grupo de um diretório**:

```bash
chown ana:financeiro /diretorio
```

Define "ana" como proprietária do diretório e "financeiro" como grupo associado.


### Opções Úteis

- **\-R**: O modificador \-R pode ser usado para aplicar recursivamente a mudança a todos os arquivos e subdiretórios. Por exemplo:

```bash
chmod -R 755 /meu_diretorio
```

Aplica permissões de leitura, escrita e execução ao dono e de leitura e execução para todos os outros, a todos os arquivos e subdiretórios de /meu\_diretorio.


Estes comandos são poderosos e ajudam a garantir que somente as pessoas autorizadas possam interagir com os arquivos de uma determinada forma. Entender as permissões é essencial para administrar sistemas Linux com segurança e eficiência.

