O **Wireshark** é uma ferramenta de análise de tráfego de rede (sniffer) de código aberto, usada para capturar, filtrar e analisar pacotes de dados que trafegam em uma rede. É amplamente utilizado por profissionais de redes e cibersegurança para depurar problemas, monitorar o tráfego e identificar vulnerabilidades.

### Visão Geral do Wireshark

- **Interface Gráfica**: O Wireshark possui uma interface gráfica amigável que permite visualizar os pacotes capturados em tempo real.
- **Filtros de Captura e Exibição**: É possível usar filtros para capturar apenas o tráfego de interesse e também para exibir pacotes específicos de uma captura maior.
- **Detalhes dos Pacotes**: Ele permite analisar os pacotes em diferentes camadas, como Ethernet, IP, TCP, UDP e até o nível de aplicação, dependendo do protocolo.

### Como Usar o Wireshark

#### 1\. Instalando

- Primeiro, baixe e instale o Wireshark em [wireshark.org](https://www.wireshark.org/). Ele é compatível com Windows, Linux e macOS.

#### 2\. Capturando Pacotes

- Abra o Wireshark.
- Selecione a **interface de rede** (ex: Ethernet, Wi-Fi) da qual deseja capturar pacotes.
- Clique em **Start** para iniciar a captura.

#### 3\. Parar Captura

- Clique no botão **Stop** (quadrado vermelho) quando terminar a captura.

### Controles e Comandos Básicos

#### Filtros de Captura

- Antes de iniciar a captura, você pode usar filtros para reduzir o número de pacotes capturados.
  - Exemplos de filtros de captura:
    - tcp port 80 - captura pacotes TCP que usam a porta 80.
    - host 192.168.1.1 - captura apenas pacotes envolvendo o host 192.168.1.1.


#### Filtros de Exibição

- Depois de capturar os pacotes, você pode usar filtros de exibição para encontrar pacotes específicos.
  - Exemplos de filtros de exibição:
    - ip.addr == 192.168.1.1 - mostra pacotes com o endereço IP especificado.
    - tcp - mostra apenas pacotes TCP.
    - http - mostra pacotes HTTP.


#### Navegação e Análise de Pacotes

- **Janela de Pacotes Capturados**: Mostra todos os pacotes capturados.
- **Janela de Detalhes do Pacote**: Ao selecionar um pacote, ele será detalhado em camadas, mostrando informações de nível Ethernet, IP, TCP, etc.
- **Janela de Bytes do Pacote**: Mostra os bytes do pacote em hexadecimal.

### Controles e Comandos Avançados

#### Análise Avançada

- **Seguir Fluxo TCP/UDP**: Clique com o botão direito em um pacote, selecione "Follow" > "TCP Stream" para ver a conversa completa entre o cliente e o servidor.
- **Estatísticas**:
  - Acesse o menu **Statistics** para visualizar gráficos e relatórios.
  - Por exemplo, **Statistics > Protocol Hierarchy** mostra o percentual de pacotes para cada protocolo.


#### Filtros Avançados

- Combinações de Filtros:
  - ip.src == 192.168.1.1 && tcp.port == 443 - exibe pacotes de um IP específico na porta 443.
  - !(dns) - exclui pacotes DNS.


#### Captura Remota

- O Wireshark suporta captura remota usando um comando específico em roteadores ou switches que possuam a função **Remote Packet Capture (RPCAP)**.

#### Scripts TShark

- O **TShark** é a versão de linha de comando do Wireshark, útil para automação e análise em servidores.
  - Exemplos:
    - tshark -i eth0 -w captura.pcap - captura pacotes da interface eth0 e salva em um arquivo .pcap.
    - tshark -r captura.pcap -T fields -e ip.src -e ip.dst - lê o arquivo de captura e exibe os endereços IP de origem e destino.


### Dicas Importantes

- **Execute como Administrador**: Para capturar pacotes em todas as interfaces, o Wireshark precisa ser executado com privilégios de administrador.
- **Filtros Reduzem o Ruído**: Capturar tudo pode ser muito volumoso, então use filtros para se concentrar nos pacotes que realmente são do seu interesse.
- **Evite Redes Públicas**: Ao capturar pacotes em redes públicas, tome cuidado com a privacidade e possíveis problemas legais.

O Wireshark é uma ferramenta extremamente poderosa e, quando bem utilizada, pode fornecer uma visão profunda sobre a comunicação na rede, ajudando na solução de problemas e auditorias de segurança.









Cores do WireShark



No Wireshark, os pacotes capturados são destacados em cores diferentes para facilitar a identificação rápida dos tipos de tráfego e dos protocolos que estão sendo usados. Cada cor possui um significado específico, permitindo aos usuários identificar rapidamente o que está acontecendo na rede, sem precisar olhar os detalhes de cada pacote individualmente. A seguir, vou falar sobre algumas das cores comuns e o que elas geralmente representam:

### Principais Cores dos Pacotes no Wireshark e Seus Significados

1. **Verde Claro**
  - Geralmente é usado para **pacotes TCP**.
  - Ajuda a identificar as conexões TCP que estão estabelecidas na rede.

- **Azul Claro**
  - Representa **pacotes UDP**.
  - Estes são pacotes que utilizam o protocolo de datagrama de usuário, geralmente sem necessidade de conexão como o TCP (usado em DNS, VoIP, etc.).

- **Rosa/Coral**
  - Pacotes de **HTTP** ou outras comunicações do tipo **aplicação**, incluindo SSL/TLS.
  - Usado para identificar tráfego de navegação na web ou de outros protocolos de camada de aplicação.

- **Amarelo Claro**
  - Frequentemente usado para **retransmissões TCP** e **problemas de atraso**, como um pacote retransmitido por não receber um ACK (Acknowledgment) do pacote original.
  - Ajuda a destacar possíveis problemas de rede, como perda de pacotes.

- **Roxo**
  - Tipicamente usado para pacotes de **DNS**.
  - É útil para ver consultas e respostas de DNS na rede.

- **Cinza Claro**
  - Representa pacotes **ICMP** (usados no ping, por exemplo).
  - Destaca pacotes que estão relacionados a mensagens de erro ou solicitações de diagnóstico.

- **Preto ou Vermelho Escuro**
  - Geralmente indica **pacotes TCP com erro** ou **falhas na conexão**.
  - Por exemplo, pacotes que apresentam falha na conexão, como **RST** (reset), são destacados nessa cor para indicar problemas potenciais.

- **Laranja**
  - Podem ser **pacotes ARP** (Address Resolution Protocol).
  - ARP é utilizado para resolver endereços IP em endereços MAC, e é bastante comum em redes locais.


Essas cores ajudam a distinguir rapidamente os diferentes tipos de tráfego e identificar possíveis problemas de rede, como retransmissões, resets de conexão, ou pacotes que precisem de mais atenção.

### Personalização das Cores

As cores padrão no Wireshark são atribuídas automaticamente, mas é possível personalizá-las de acordo com a preferência do usuário:

1. Vá até o menu **View** e selecione **Coloring Rules**.
2. Ali, você pode ver todas as regras de coloração aplicadas e criar suas próprias regras para destacar certos tipos de pacotes de maneira personalizada.

As cores são uma ferramenta visual poderosa no Wireshark e ajudam os analistas a identificar rapidamente o tipo de tráfego e possíveis problemas.

