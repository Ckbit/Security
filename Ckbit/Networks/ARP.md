---
folder: "[[Networks]]"
---
ARP (Address Resolution Protocol) é um protocolo de rede utilizado para mapear endereços de rede em um ambiente de rede local (LAN). Ele faz a tradução entre endereços IP (camada 3 do modelo OSI) e endereços MAC (Media Access Control, da camada 2). Essa tradução é necessária para que os dispositivos possam se comunicar em redes Ethernet.

Imagine que um computador, com um endereço IP conhecido, queira se comunicar com outro dispositivo dentro da mesma rede local. Para enviar um pacote, ele precisa descobrir o endereço MAC associado ao IP de destino, pois a comunicação em uma rede local é feita utilizando os endereços físicos (MAC). O ARP é responsável por fazer essa resolução.

### Funcionamento do ARP

1. **Broadcast ARP Request**: Quando um dispositivo precisa se comunicar com outro e só conhece o endereço IP de destino, ele envia uma mensagem de solicitação ARP (ARP Request) em broadcast para toda a rede local. Essa solicitação pergunta: "Quem tem o endereço IP X? Por favor, responda com seu endereço MAC".
2. **ARP Reply**: O dispositivo que possui o endereço IP indicado na solicitação responde com um ARP Reply, informando seu endereço MAC.
3. **Tabela ARP**: Cada dispositivo mantém uma tabela ARP, uma espécie de cache onde são armazenados os endereços IP e seus correspondentes endereços MAC. Assim, quando precisa se comunicar novamente com o mesmo dispositivo, não é necessário repetir a solicitação ARP, a menos que a informação no cache tenha expirado.

### Tipos de Mensagens ARP

- **ARP Request**: Solicitação feita para descobrir o endereço MAC associado a um IP.
- **ARP Reply**: Resposta que contém o endereço MAC correspondente ao endereço IP requisitado.

### Vantagens e Limitações

- **Vantagem**: ARP facilita a comunicação entre dispositivos em uma rede local, garantindo que as mensagens sejam roteadas de maneira adequada.
- **Limitação**: O ARP está vulnerável a ataques de segurança, como o ARP Spoofing (envenenamento ARP). Esse tipo de ataque ocorre quando um invasor envia respostas ARP falsas na rede, associando seu próprio endereço MAC ao endereço IP de outro dispositivo, permitindo que ele intercepte ou redirecione o tráfego de rede.

### Exemplos de Uso

Se você estiver conectado a uma rede local e tentar acessar um site hospedado em um servidor na mesma rede, o ARP será usado para resolver o endereço IP do servidor para o endereço MAC, permitindo que os pacotes sejam enviados diretamente ao servidor correto.

O ARP é essencial para a comunicação em redes Ethernet, garantindo a correta entrega dos pacotes de dados ao dispositivo de destino na camada de enlace.

