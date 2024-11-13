---
folder: "[[Networks]]"
---
**Port Forwarding** é uma técnica de rede usada para permitir que dispositivos externos se conectem a um dispositivo em uma rede privada por meio de um endereço IP público. Funciona redirecionando tráfego de uma porta específica do roteador para um dispositivo dentro da rede local. Esse método é bastante útil em situações onde você deseja acessar remotamente serviços internos, como servidores de jogos, servidores web ou câmeras de segurança.

### Como Funciona o Port Forwarding

- Quando você configura o port forwarding, você instrui o roteador a encaminhar qualquer solicitação recebida em uma determinada porta para um dispositivo específico na sua rede.
- Por exemplo, se você tiver um servidor web local na porta 80, ao configurar o port forwarding, qualquer solicitação feita ao seu IP público na porta 80 será redirecionada pelo roteador para o dispositivo que hospeda o servidor.

### Riscos do Port Forwarding

1. **Exposição da Rede Interna**: O port forwarding torna um dispositivo dentro da sua rede acessível da internet. Se as portas não forem protegidas adequadamente, qualquer pessoa pode tentar acessar o dispositivo, expondo-o a potenciais ataques.
2. **Aumento da Superfície de Ataque**: Cada porta aberta representa um ponto potencial de entrada para invasores. Se um serviço rodando na porta exposta tiver vulnerabilidades, isso pode ser explorado por atacantes.
3. **Ataques de Força Bruta**: Serviços que exigem autenticação, como câmeras de segurança ou servidores SSH, podem ser alvo de ataques de força bruta, onde um atacante tenta várias combinações de usuário e senha para obter acesso.
4. **Malware e Botnets**: Dispositivos mal configurados e expostos na internet podem ser comprometidos e usados em redes de bots (botnets) para conduzir ataques de DDoS ou disseminar malware.

### Medidas de Segurança

- **Use uma VPN**: Em vez de abrir uma porta diretamente para a internet, o uso de uma VPN pode proporcionar uma conexão segura para acessar sua rede.
- **Firewall e Filtragem de IP**: Configure seu firewall para permitir apenas endereços IP específicos de acessar certas portas.
- **Autenticação Forte**: Utilize autenticação de dois fatores (2FA) e senhas fortes para os serviços acessíveis por port forwarding.
- **Desativar Serviços Desnecessários**: Evite abrir portas para serviços que não sejam estritamente necessários.

Port Forwarding é uma ferramenta poderosa, mas deve ser utilizada com cuidado para evitar comprometer a segurança da rede.

