---
folder: "[[Domains and IP Addresses]]"
---
O Shodan é um motor de busca especializado que permite a descoberta de dispositivos conectados à Internet, como servidores, câmeras de segurança, roteadores, entre outros. Diferente de buscadores tradicionais, como o Google, o Shodan rastreia não o conteúdo web, mas informações de infraestrutura de redes e dispositivos que respondem a portas específicas. Ele é amplamente utilizado em cibersegurança para realizar varreduras de rede, descoberta de vulnerabilidades e avaliação de exposição pública de sistemas.

### Funcionalidades do Shodan

1. **Pesquisa por IP e porta**: Shodan permite buscas específicas por IPs e portas, possibilitando aos usuários listar dispositivos que respondem em determinadas portas e protocolos. Comando de exemplo:
   ```sh
   shodan host <IP_DO_ALVO>
   ```
   Esse comando retorna detalhes sobre um IP específico, incluindo portas abertas, banners de serviços e possíveis vulnerabilidades.

2. **Filtros avançados de pesquisa**: Shodan permite filtros específicos como "country", "city", "port", "hostname", "org" (organização), e "os" (sistema operacional). Exemplo de comando:
   ```sh
   shodan search "apache country:BR"
   ```
   Esse exemplo busca por servidores Apache localizados no Brasil.

3. **Exposição de vulnerabilidades**: A partir dos banners coletados, Shodan consegue identificar vulnerabilidades conhecidas nos serviços ativos de um dispositivo. Essas vulnerabilidades são relacionadas a CVEs (Common Vulnerabilities and Exposures), permitindo uma análise preliminar de segurança de sistemas expostos.

4. **API do Shodan**: A API permite integrar a funcionalidade do Shodan em outras ferramentas e scripts. É útil para automatizar tarefas de descoberta e análise de vulnerabilidades. Exemplo de uso da API:
   ```python
   import shodan

   api = shodan.Shodan('YOUR_API_KEY')
   result = api.search('nginx')
   for service in result['matches']:
       print(service['ip_str'], service['port'])
   ```
   Esse script em Python lista todos os IPs que têm servidores Nginx, junto com a porta que respondem.

### Exemplos de Utilização em Cibersegurança
- **Auditorias de Segurança**: Identificar se dispositivos internos estão inadvertidamente expostos à internet.
- **Testes de Penetração**: Descobrir serviços expostos de uma organização-alvo.
- **Defesa Proativa**: Empresas monitoram suas próprias exposições públicas para detectar infraestruturas que possam estar vulneráveis.

### Shodan CLI e Consultas Comuns
Para utilizar o Shodan na linha de comando, é necessário instalar o cliente:
```sh
pip install shodan
shodan init <API_KEY>
```
Após a inicialização, alguns comandos comuns são:
- **Verificação de IP**:
  ```sh
  shodan host <IP>
  ```
- **Consulta global**:
  ```sh
  shodan search "Apache country:US"
  ```
- **Download de dados de pesquisa**:
  ```sh
  shodan download <FILENAME> <QUERY>
  ```

Essas funcionalidades permitem que o Shodan seja uma ferramenta poderosa para profissionais de segurança, auxiliando na descoberta de vulnerabilidades e na avaliação de exposição de infraestruturas conectadas à Internet. 