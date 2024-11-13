---
folder: "[[SO]]"
---
Navegar e manipular arquivos através do terminal é uma habilidade essencial para usuários de sistemas operacionais como Linux e Windows. Abaixo, apresentamos os comandos básicos que permitem realizar essas tarefas em ambos os sistemas.

---

## Linux

### Listar arquivos e diretórios: ls

- **ls**: Lista os arquivos e pastas no diretório atual.
- **ls -l**: Exibe a lista em formato detalhado, mostrando permissões, proprietário, tamanho, etc.
- **ls -a**: Inclui arquivos ocultos na listagem (arquivos que começam com .).
- **ls -lh**: Exibe tamanhos em formato legível (KB, MB, GB).

### Mudar de diretório: cd

- **cd nome\_do\_diretório**: Entra no diretório especificado.
- **cd ..**: Retorna ao diretório anterior.
- **cd /caminho/para/diretório**: Navega para um caminho absoluto.
- **cd ~**: Vai para o diretório home do usuário.

### Copiar arquivos e diretórios: cp

- **cp arquivo\_origem arquivo\_destino**: Copia um arquivo.
- **cp -r diretório\_origem diretório\_destino**: Copia recursivamente um diretório e seu conteúdo.

### Mover ou renomear arquivos e diretórios: mv

- **mv arquivo\_origem arquivo\_destino**: Move ou renomeia um arquivo.
- **mv diretório\_origem diretório\_destino**: Move ou renomeia um diretório.

### Remover arquivos e diretórios: rm

- **rm arquivo**: Remove um arquivo.
- **rm -r diretório**: Remove um diretório e todo o seu conteúdo.
- **Atenção**: Use com cautela, pois não há lixeira; os arquivos são excluídos permanentemente.

---

## Windows

### Usando o Prompt de Comando (CMD)

#### Listar arquivos e diretórios: dir

- **dir**: Lista os arquivos e pastas no diretório atual.
- **dir /a**: Exibe todos os arquivos, incluindo os ocultos.

#### Mudar de diretório: cd

- **cd nome\_do\_diretório**: Entra no diretório especificado.
- **cd ..**: Retorna ao diretório anterior.
- **cd \\caminho\\para\\diretório**: Navega para um caminho absoluto.

#### Copiar arquivos e diretórios: copy e xcopy

- **copy arquivo\_origem arquivo\_destino**: Copia um arquivo.
- **xcopy diretório\_origem diretório\_destino /E /I**: Copia diretórios e subdiretórios, mesmo se vazios.

#### Mover ou renomear arquivos e diretórios: move

- **move arquivo\_origem arquivo\_destino**: Move ou renomeia um arquivo.
- **move diretório\_origem diretório\_destino**: Move ou renomeia um diretório.

#### Remover arquivos e diretórios: del e rmdir

- **del arquivo**: Remove um arquivo.
- **rmdir diretório**: Remove um diretório vazio.
- **rmdir /S diretório**: Remove um diretório e todo o seu conteúdo.

### Usando o PowerShell

O PowerShell permite o uso de comandos similares aos do Linux:

- **ls** ou **Get-ChildItem**: Lista arquivos e diretórios.
- **cd** ou **Set-Location**: Muda de diretório.
- **cp** ou **Copy-Item**: Copia arquivos e diretórios.
- **mv** ou **Move-Item**: Move ou renomeia arquivos e diretórios.
- **rm** ou **Remove-Item**: Remove arquivos e diretórios.

---

## Dicas Adicionais

- **Autocompletar**: Use a tecla Tab para autocompletar nomes de arquivos e diretórios.
- **Histórico de Comandos**: Use as setas para cima e para baixo para navegar pelos comandos anteriores.
- **Permissões (Linux)**: Pode ser necessário usar sudo para executar comandos com privilégios elevados.
- **Ajuda**: Use comando --help ou man comando (no Linux) e comando /? (no Windows) para obter mais informações sobre um comando.

---

## Conclusão

Dominar esses comandos básicos no terminal permite uma navegação e manipulação de arquivos mais eficiente, além de automatizar tarefas e solucionar problemas de forma mais rápida. Pratique regularmente para familiarizar-se com eles e aumentar sua produtividade no dia a dia.

