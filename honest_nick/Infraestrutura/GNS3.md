[https://www.youtube.com/watch?v=AuokrRQVTEw](https://www.youtube.com/watch?v=AuokrRQVTEw)

[![YouTube](https://a.slack-edge.com/80588/img/unfurl_icons/youtube.png)](https://www.youtube.com/)[YouTube](https://www.youtube.com/) | [Technical Xpress](https://www.youtube.com/@technicalxpress9988)

[GNS3 Tutorial - Full Setup Guide for Beginners - A to Z](https://www.youtube.com/watch?v=AuokrRQVTEw) 

[https://www.gns3.com/](https://www.gns3.com/)


![:chave_inglesa:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f527.png) **1. GNS3 (Graphical Network Simulator 3)** — Recomendado  

- **Prós**:
    - Simula redes reais com imagens de sistemas operacionais (Cisco IOS, pfSense, Mikrotik, etc.).
    - Suporte total a topologias com failover, roteadores, switches gerenciáveis e firewalls redundantes.
    - Permite usar **pfSense** (ótimo para simular firewalls com failover).
- **Requisitos**:
    - Requer boa quantidade de RAM e CPU.
    - Recomendável instalar o GNS3 VM (VirtualBox ou VMware) para desempenho ideal.

![:globo_com_meridianos:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f310.png) **2. EVE-NG (Emulated Virtual Environment Next Generation)**  

- **Prós**:
    - Ambiente profissional usado por empresas e para certificações.
    - Suporta múltiplas VMs, ideal para simular firewalls com **CARP** (no pfSense), **VRRP**, **HSRP** etc.
    - Interface web intuitiva.
- **Contras**:
    - Curva de aprendizado maior que o GNS3.
    - Precisa configurar as imagens ISO/OVF manualmente.

![:tijolos:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f9f1.png) **3. Cisco Packet Tracer** (limitado)  

- **Prós**:
    - Muito fácil de usar e didático.
    - Ideal para ensino e provas de certificações Cisco (CCNA).
- **Contras**:
    - Não suporta imagens reais ou sistemas operacionais completos.
    - Não tem suporte direto para simular firewalls reais (como pfSense).
    - Não simula failover real entre firewalls.