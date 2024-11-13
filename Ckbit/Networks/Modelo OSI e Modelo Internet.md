---
folder: "[[Networks]]"
---
**Modelo OSI (Open Systems Interconnection)**

O modelo OSI é um modelo de referência para redes de computadores desenvolvido pela ISO (International Organization for Standardization) em 1984. Ele descreve como diferentes sistemas de redes se comunicam entre si, dividindo essa comunicação em **7 camadas**, onde cada uma delas desempenha uma função específica. É um modelo teórico, mas muito útil para entender como as redes funcionam e para facilitar a padronização dos protocolos.

### Camadas do Modelo OSI

1. **Camada 1: Física (Physical Layer)**
  - **Função:** Esta é a camada responsável pela transmissão de dados brutos (bits) por meio de um meio físico, como cabos de cobre, fibra óptica, ou sinais sem fio. Ela define especificações de hardware, como conectores e voltagem.
  - **Exemplos:** Cabos Ethernet, conectores, interfaces de rede, sinais elétricos.

- **Camada 2: Enlace de Dados (Data Link Layer)**
  - **Função:** Garante a transferência de dados entre dispositivos na mesma rede, detectando e corrigindo erros de transmissão. Ela cria "quadros" para organizar os bits e endereça os dispositivos na rede local.
  - **Divisão:** Pode ser subdividida em duas subcamadas: **LLC (Logical Link Control)** e **MAC (Media Access Control)**.
  - **Exemplos:** Switches, Protocolo Ethernet, Wi-Fi (802.11).

- **Camada 3: Rede (Network Layer)**
  - **Função:** Responsável por determinar a rota que os dados seguirão para alcançar o destino, possibilitando a comunicação entre redes distintas. Esta camada utiliza endereçamento lógico (endereços IP).
  - **Exemplos:** Roteadores, protocolo IP (Internet Protocol).

- **Camada 4: Transporte (Transport Layer)**
  - **Função:** Fornece comunicação de ponta a ponta, garantindo a confiabilidade dos dados e que os pacotes cheguem na ordem correta. Ela também faz o controle de fluxo e a correção de erros.
  - **Protocolos: TCP (Transmission Control Protocol)**, que é confiável, e **UDP (User Datagram Protocol)**, que é mais rápido, mas não garante a entrega.

- **Camada 5: Sessão (Session Layer)**
  - **Função:** Gerencia e controla o estabelecimento, a manutenção e o encerramento de sessões entre dois dispositivos. Uma "sessão" pode ser uma série de trocas de dados, como um login ou uma transferência de arquivo.
  - **Exemplos:** Controle de diálogo, sincronização.

- **Camada 6: Apresentação (Presentation Layer)**
  - **Função:** Esta camada é responsável pela tradução dos dados para um formato compreensível pelas camadas superiores. Também faz compressão e criptografia de dados, para que possam ser transmitidos de maneira mais eficiente e segura.
  - **Exemplos:** Criptografia SSL, compressão de dados (ZIP).

- **Camada 7: Aplicação (Application Layer)**
  - **Função:** É a camada mais próxima do usuário, fornecendo a interface para comunicação e suporte aos aplicativos. Ela lida com os protocolos de comunicação necessários para as atividades específicas dos usuários, como navegação web e envio de e-mails.
  - **Exemplos:** HTTP (para navegação web), SMTP (para envio de e-mails), FTP (para transferência de arquivos).


**Resumo das Funções do Modelo OSI:**

- Camadas 1 a 4 são responsáveis por mover os dados pela rede.
- Camadas 5 a 7 são responsáveis pela interação entre o usuário e a rede, permitindo que as aplicações funcionem corretamente.

---

**Modelo de Internet (ou Modelo TCP/IP)**

O modelo TCP/IP, também chamado de **Modelo de Internet**, foi desenvolvido pelo Departamento de Defesa dos Estados Unidos e é utilizado na comunicação da Internet. Ele descreve um conjunto de protocolos padronizados que permitem a comunicação entre computadores, e é mais simples que o modelo OSI, com apenas **4 camadas**.

### Camadas do Modelo TCP/IP

1. **Camada 1: Acesso à Rede (Network Access Layer)**
  - **Função:** Equivalente à combinação das camadas Física e Enlace do Modelo OSI. Ela lida com os protocolos de hardware para transmitir dados, incluindo o controle dos meios de transmissão.
  - **Exemplos:** Ethernet, Wi-Fi, PPP.

- **Camada 2: Internet**
  - **Função:** Corresponde à camada de Rede do OSI, e é responsável por definir o endereçamento e o roteamento dos pacotes. Esta camada utiliza o protocolo IP.
  - **Exemplos:** Protocolo IP, ICMP (para diagnóstico, como ping).

- **Camada 3: Transporte**
  - **Função:** Equivalente à camada de Transporte do OSI. Ela garante a comunicação entre o emissor e o receptor, utilizando o **TCP** (para comunicação confiável) ou **UDP** (para comunicação rápida e não confiável).
  - **Exemplos:** TCP, UDP.

- **Camada 4: Aplicação**
  - **Função:** Esta camada combina as funções das camadas de Aplicação, Apresentação e Sessão do Modelo OSI. Ela gerencia a comunicação entre as aplicações de usuário e os protocolos para diferentes serviços.
  - **Exemplos:** HTTP, SMTP, FTP, DNS (para resolução de nomes).


**Resumo das Funções do Modelo TCP/IP:**

- Ele possui apenas 4 camadas, simplificando algumas das divisões do Modelo OSI.

---

**Comparação entre o Modelo OSI e o Modelo TCP/IP**

|Aspecto|Modelo OSI|Modelo TCP/IP|
|-------|----------|-------------|
|**Número de Camadas**|7|4|
|**Uso**|Teórico, referência para aprendizagem|Prático, utilizado amplamente na Internet|
|**Divisão das Funções**|Funções distribuídas em camadas detalhadas|Funções agrupadas em menos camadas|
|**Complexidade**|Mais complexo, detalhado e segmentado|Mais simplificado e prático|
|**Criação**|Desenvolvido pela ISO|Desenvolvido pelo Departamento de Defesa dos EUA|
|**Camada de Aplicação**|Dividida em 3 camadas (Sessão, Apresentação, Aplicação)|Agrupada em uma única camada de Aplicação|
|**Roteamento e Rede**|Funções de roteamento são responsabilidade da Camada 3 (Rede)|Responsabilidade da camada Internet|

- **Nível de Abstração**: O modelo OSI é mais detalhado, enquanto o TCP/IP é mais prático e diretamente relacionado à implementação.
- **Confiabilidade**: O TCP/IP foi projetado levando em consideração a confiabilidade em um ambiente de comunicação real, como a Internet, onde se utiliza principalmente o protocolo TCP para garantir que os dados cheguem na ordem correta.
- **Foco de Aplicação**: O modelo OSI é usado como referência educacional e para entender a estrutura dos protocolos de rede, enquanto o modelo TCP/IP é o que realmente está em operação no dia a dia da comunicação na Internet.

Ambos os modelos são importantes: o **modelo OSI** é útil para **entender conceitos teóricos** e como a comunicação pode ser estruturada, enquanto o **modelo TCP/IP** é o que possibilita a **comunicação real na Internet**, sendo mais direto e eficiente para implementações.

