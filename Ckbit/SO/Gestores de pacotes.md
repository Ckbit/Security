---
folder: "[[SO]]"
---
Instalar, atualizar e remover pacotes com gestores de pacotes é uma prática fundamental para administrar e manter sistemas Linux. Cada gestor de pacotes facilita a manipulação de softwares e dependências, garantindo que os programas funcionem corretamente e estejam atualizados. Aqui estão alguns dos gestores de pacotes mais comuns e como realizar essas tarefas com eles:

### 1\. APT (Advanced Package Tool) - Usado em distribuições Debian-based (ex.: Ubuntu)

- **Instalar um pacote**:

```bash
sudo apt install nome_do_pacote
```

- **Atualizar um pacote**:

```bash
sudo apt update # Atualiza a lista de pacotes disponíveis
sudo apt upgrade nome_do_pacote # Atualiza o pacote especificado
```

- **Remover um pacote**:

```bash
sudo apt remove nome_do_pacote
```

- **Remover o pacote e arquivos de configuração**:

```bash
sudo apt purge nome_do_pacote
```


### 2\. YUM (Yellowdog Updater, Modified) - Usado em distribuições RHEL-based (ex.: CentOS 7, Fedora)

- **Instalar um pacote**:

```bash
sudo yum install nome_do_pacote
```

- **Atualizar um pacote**:

```bash
sudo yum update nome_do_pacote
```

- **Remover um pacote**:

```bash
sudo yum remove nome_do_pacote
```


### 3\. DNF (Dandified YUM) - Sucessor do YUM em distribuições mais recentes (ex.: Fedora 22+, CentOS 8)

- **Instalar um pacote**:

```bash
sudo dnf install nome_do_pacote
```

- **Atualizar um pacote**:

```bash
sudo dnf update nome_do_pacote
```

- **Remover um pacote**:

```bash
sudo dnf remove nome_do_pacote
```


### 4\. Pacman - Usado no Arch Linux e derivados

- **Instalar um pacote**:

```bash
sudo pacman -S nome_do_pacote
```

- **Atualizar um pacote**:

```bash
sudo pacman -Syu # Atualiza o sistema inteiro, incluindo pacotes específicos
```

- **Remover um pacote**:

```bash
sudo pacman -R nome_do_pacote
```

- **Remover um pacote com dependências órfãs**:

```bash
sudo pacman -Rns nome_do_pacote
```


### 5\. Zypper - Usado no openSUSE

- **Instalar um pacote**:

```bash
sudo zypper install nome_do_pacote
```

- **Atualizar um pacote**:

```bash
sudo zypper update nome_do_pacote
```

- **Remover um pacote**:

```bash
sudo zypper remove nome_do_pacote
```


### Considerações Gerais

- **Atualização do sistema inteiro**: Muitos gestores de pacotes oferecem um comando para atualizar todo o sistema, como sudo apt upgrade (APT), sudo yum update (YUM), sudo dnf upgrade (DNF), e sudo pacman -Syu (Pacman).
- **Gerenciamento de dependências**: Os gestores de pacotes cuidam das dependências automaticamente, instalando-as junto com os pacotes requisitados e removendo-as quando não são mais necessárias.
- **Limpeza de cache**: Após muitas operações, os gestores de pacotes podem acumular cache, e a limpeza periódica ajuda a liberar espaço. Por exemplo, sudo apt clean ou sudo dnf clean all.

Cada gestor de pacotes possui particularidades e opções avançadas para manipulação de repositórios, resolução de dependências e rollback, oferecendo flexibilidade na administração do sistema.

