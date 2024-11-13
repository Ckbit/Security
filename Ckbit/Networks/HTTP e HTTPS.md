---
folder: "[[Networks]]"
---
HTTP (HyperText Transfer Protocol) e HTTPS (HyperText Transfer Protocol Secure) são protocolos de comunicação usados para transferir dados entre um navegador web (cliente) e um servidor web. Eles são os principais responsáveis por permitir que você navegue na internet.

### HTTP

- **Definição**: HTTP é o protocolo de comunicação sem segurança que define como as mensagens são formatadas e transmitidas na web, bem como as ações que servidores e navegadores devem tomar em resposta a diversos comandos.
- **Porta Padrão**: O HTTP utiliza a porta 80.
- **Funcionamento**: As solicitações HTTP são usadas para carregar páginas web, enviando mensagens de solicitação que o servidor responde, geralmente retornando conteúdo como HTML, CSS, imagens, etc.
- **Segurança**: Não é criptografado. Isso significa que qualquer dado trocado entre o cliente e o servidor pode ser interceptado e lido por qualquer pessoa que consiga acessar essa comunicação.

### HTTPS

- **Definição**: HTTPS é a versão segura do HTTP. Ele adiciona uma camada de segurança ao utilizar criptografia através do protocolo TLS (Transport Layer Security) ou SSL (Secure Sockets Layer).
- **Porta Padrão**: O HTTPS utiliza a porta 443.
- **Segurança**: HTTPS garante que as informações trocadas entre o navegador e o servidor estejam criptografadas. Isso significa que os dados estão protegidos contra ataques de intermediários (man-in-the-middle) e são mais seguros para transferir informações confidenciais, como senhas e dados de pagamento.
- **Certificado SSL/TLS**: Para usar HTTPS, o servidor precisa ter um certificado digital emitido por uma autoridade certificadora. Este certificado confirma a identidade do site e permite a criptografia dos dados.

### Diferenças Resumidas

1. **Criptografia**:
  - HTTP: Sem criptografia.
  - HTTPS: Utiliza criptografia para proteger os dados transmitidos.

- **Porta Padrão**:
  - HTTP: Porta 80.
  - HTTPS: Porta 443.

- **Segurança**:
  - HTTP: Vulnerável a ataques de interceptação de dados.
  - HTTPS: Protege os dados contra interceptação e garante a integridade da comunicação.

- **Uso Principal**:
  - HTTP: Pode ser usado para páginas públicas sem necessidade de segurança.
  - HTTPS: Utilizado para transações financeiras, informações sensíveis ou para sites que precisam assegurar a privacidade dos dados dos usuários.


Hoje em dia, o uso de HTTPS se tornou o padrão, e muitos navegadores alertam os usuários quando acessam sites sem a segurança HTTPS, incentivando a navegação em ambientes mais seguros.

