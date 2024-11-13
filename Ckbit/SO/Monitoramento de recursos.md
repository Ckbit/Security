---
folder: "[[SO]]"
---
### Linux

No Linux, existem diversas ferramentas disponíveis para monitorar o uso de recursos como CPU, memória, rede e disco. Algumas delas são:

1. **top**:
  - É uma ferramenta nativa para monitorar o uso da CPU, memória, processos em execução e carga do sistema.
  - Para usá-la, basta abrir o terminal e digitar top.

- **htop**:
  - É uma versão mais amigável do top com interface colorida e uma navegação mais intuitiva.
  - Para instalá-la, você pode rodar sudo apt install htop (Debian/Ubuntu) e depois digitar htop para executá-la.

- **vmstat**:
  - Mostra informações sobre processos, memória, swap, I/O, e CPU.
  - Execute vmstat 1 para obter atualizações a cada segundo.

- **iostat**:
  - Utilizada para monitorar estatísticas de entrada/saída do sistema, incluindo uso de disco.
  - Pode ser instalada com sudo apt install sysstat e usada com iostat.

- **free**:
  - Para monitorar o uso de memória. Digite free -m no terminal para visualizar o uso da RAM em megabytes.

- **nmon**:
  - Ferramenta poderosa para monitoramento de recursos, incluindo CPU, memória, rede, e disco.
  - Pode ser instalada com sudo apt install nmon e executada com nmon.

- **netstat** e **iftop**:
  - netstat fornece informações sobre conexões de rede e portas abertas.
  - iftop é útil para visualizar em tempo real o tráfego de rede em cada interface.

- **sar**:
  - Outra ferramenta da coleção sysstat, sar é utilizada para coletar dados de desempenho do sistema ao longo do tempo.
  - Muito útil para análise de performance histórica.


### Windows

No Windows, também existem várias formas de monitorar o uso de recursos do sistema:

1. **Gerenciador de Tarefas**:
  - Ferramenta padrão para monitorar o uso de CPU, memória, disco, rede e processos.
  - Pode ser aberto pressionando Ctrl + Shift + Esc ou clicando com o botão direito na barra de tarefas e selecionando “Gerenciador de Tarefas”.

- **Monitor de Recursos (Resource Monitor)**:
  - Dá uma visão mais detalhada dos recursos do sistema, incluindo CPU, memória, disco e rede.
  - Pode ser acessado através do Gerenciador de Tarefas na aba "Desempenho" clicando em "Abrir Monitor de Recursos".

- **Performance Monitor (PerfMon)**:
  - Ferramenta avançada que permite criar gráficos, registrar logs, e visualizar dados detalhados de desempenho do sistema.
  - Para acessá-lo, pressione Win + R, digite perfmon e pressione Enter.

- **PowerShell**:
  - Pode ser usado para obter informações detalhadas sobre o sistema.
  - Por exemplo, para monitorar a CPU, digite Get-Counter '\\Processor(\_Total)\\% Processor Time' no PowerShell.

- **WMIC (Windows Management Instrumentation Command-line)**:
  - Oferece várias informações sobre o sistema.
  - Para ver o uso da CPU, você pode digitar wmic cpu get loadpercentage.

- **Process Explorer**:
  - Parte do pacote Sysinternals, é um substituto avançado para o Gerenciador de Tarefas, com informações detalhadas sobre processos e recursos do sistema.
  - Pode ser baixado do site da Microsoft.

- **Tasklist e Taskkill**:
  - Ferramentas de linha de comando para listar (tasklist) e terminar (taskkill) processos no sistema.


### Resumo

- **Linux**: Utiliza comandos como top, htop, free, iostat, entre outros, para monitorar diversos recursos.
- **Windows**: Conta com o **Gerenciador de Tarefas**, **Resource Monitor**, **PerfMon**, além de comandos via **PowerShell**.

Essas ferramentas são muito úteis tanto para administradores de sistemas quanto para usuários que precisam entender o desempenho do sistema e identificar gargalos ou problemas de recursos.

