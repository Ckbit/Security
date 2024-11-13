---
folder: "[[SO]]"
---
No Linux, a estrutura de diretórios é organizada de forma hierárquica, iniciando pelo diretório raiz (/). Cada diretório serve a um propósito específico e armazena diferentes tipos de arquivos e dados do sistema. Vamos explorar os diretórios principais:

1. **/** (Raiz): É o ponto de partida de todos os diretórios no sistema Linux. A partir do diretório raiz, todos os outros diretórios são acessíveis.
2. **/home**: Contém os diretórios pessoais dos usuários do sistema. Cada usuário possui seu próprio espaço em /home/nome\_do\_usuario, onde são armazenados seus documentos, configurações pessoais e outros arquivos.
3. **/etc**: Armazena arquivos de configuração do sistema e dos programas instalados. Aqui são encontradas as configurações de rede, de serviços, de usuários, e de praticamente todos os componentes do sistema.
4. **/var**: Contém arquivos que mudam constantemente, como logs do sistema, arquivos de spool de impressoras, e dados dinâmicos. Por exemplo, os arquivos de log ficam em /var/log.
5. **/tmp**: Diretório destinado a arquivos temporários. Programas utilizam este espaço para armazenar arquivos transitórios, e geralmente o conteúdo deste diretório é apagado automaticamente durante o processo de reinicialização do sistema.
6. **/usr**: Abriga arquivos de usuários e programas do sistema. Inclui bibliotecas, documentação, e aplicativos. É dividido em subdiretórios como /usr/bin (binários de programas), /usr/lib (bibliotecas), e /usr/share (dados compartilhados).
7. **/bin**: Contém binários essenciais necessários para que o sistema seja inicializado e funcione em modo de usuário único. Exemplos são os comandos básicos como ls, cp, mv, etc.
8. **/sbin**: Similar ao /bin, mas contém binários administrativos, usados para manutenção do sistema, que geralmente requerem permissões elevadas.
9. **/lib**: Armazena as bibliotecas essenciais necessárias para que os programas em /bin e /sbin funcionem.
10. **/dev**: Diretório que contém arquivos de dispositivos. Esses arquivos representam interfaces para vários dispositivos do sistema, como discos rígidos (/dev/sda), terminais, etc.
11. **/mnt** e **/media**: São usados para montar sistemas de arquivos temporários, como discos externos, pendrives e outras mídias removíveis.

Essa estrutura hierárquica e organizada facilita o gerenciamento e manutenção do sistema, proporcionando uma separação clara entre os diferentes tipos de arquivos e seus propósitos.

