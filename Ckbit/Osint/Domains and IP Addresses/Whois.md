---
folder: "[[Domains and IP Addresses]]"
---
Whois é um serviço de consulta que oferece detalhes de registros de domínios, redes e endereços IP, essencial para coleta de informações durante processos de reconhecimento em testes de segurança e investigações. Aqui está uma visão detalhada do funcionamento, comandos e tipos de consultas disponíveis:

### 1. O que é o Whois?
O Whois é um protocolo que permite consultar uma base de dados com informações sobre registros de domínios e endereços IP, fornecendo detalhes como:
- Nome e dados de contato do proprietário do domínio (ou organização).
- Informações sobre o registrador.
- Data de criação, atualização e expiração do domínio.
- Servidores DNS associados ao domínio.

Esses dados são úteis para conhecer detalhes sobre o responsável pelo domínio, identificar a localização de uma infraestrutura, e até mesmo para relacionar possíveis vulnerabilidades associadas ao domínio ou servidor.

### 2. Como Funciona?
O protocolo Whois utiliza portas específicas, geralmente a porta 43 (TCP), para enviar e receber informações de um servidor Whois. O processo envolve:
1. Enviar uma consulta para um servidor Whois autorizado.
2. Receber a resposta com informações detalhadas.

Cada registrador possui seu próprio servidor Whois (ex: `whois.verisign-grs.com` para domínios `.com`), e por isso a consulta pode variar de acordo com o TLD do domínio (como `.com`, `.net`, etc.).

### 3. Comandos Básicos para Consultas Whois

#### 3.1 Usando o Terminal
Em sistemas Unix-like (Linux e macOS), o comando básico é `whois`, que vem pré-instalado. Em sistemas Windows, é possível usar clientes de linha de comando ou realizar consultas online.

- **Consulta Básica**
  ```bash
  whois example.com
  ```
  Esse comando retorna as informações do domínio `example.com`.

- **Consulta Específica por Servidor Whois**
  ```bash
  whois -h whois.verisign-grs.com example.com
  ```
  Útil para direcionar a consulta a um servidor específico, caso o domínio use um TLD que exija servidor Whois dedicado.

- **Exibir Informações de Rede para um IP**
  ```bash
  whois 192.168.1.1
  ```
  Permite verificar informações de rede e designação de blocos de IP, úteis para descobrir o ASN (Sistema Autônomo) e o detentor do endereço IP.

#### 3.2 Ferramentas Whois no Kali Linux
O Kali Linux, uma distribuição popular para testes de penetração, possui ferramentas de coleta de informações, incluindo o `whois`. Há um capítulo específico no material OSCP sobre uso de ferramentas como Whois para reconhecimento passivo.

### 4. Tipos de Consulta Whois

#### 4.1 Consulta Recursiva e Não-Recursiva
- **Recursiva**: Ao consultar um domínio, um servidor Whois pode redirecionar a consulta para servidores secundários que possuem informações mais detalhadas.
- **Não-recursiva**: A consulta permanece no servidor Whois inicial, retornando apenas as informações disponíveis ali.

#### 4.2 Consultas Diretas ao Registrador
Alguns registradores, como `whois.godaddy.com`, fornecem APIs ou interfaces diretas para consultar informações, muitas vezes úteis quando o protocolo Whois padrão falha.

### 5. Privacidade e Whois
Devido à privacidade, muitos registradores agora mascaram as informações pessoais dos proprietários de domínios. Isso é feito através de serviços de proxy ou pelo GDPR, dificultando a coleta de informações específicas de contato sem ordem judicial.

### 6. Scripts e Automatização
Para quem realiza análises constantes, é possível criar scripts em Bash ou Python que automatizam consultas Whois, filtram informações e armazenam dados para análises futuras.

Exemplo em Python:
```python
import subprocess

# Função para consultar Whois
def consulta_whois(dominio):
    resultado = subprocess.run(["whois", dominio], capture_output=True, text=True)
    return resultado.stdout

# Exemplo de uso
dominio = "example.com"
print(consulta_whois(dominio))
```

### 7. Limitações e Contornos
Consultas Whois estão sujeitas a limites de taxa (rate limiting), onde muitos pedidos em um curto período podem bloquear o IP do solicitante. Em cenários de análise massiva, é recomendado o uso de proxies rotativos e serviços pagos para contornar essa limitação.

### Conclusão
A consulta Whois é essencial para a coleta passiva de informações durante testes de penetração e investigações de segurança. Ela permite traçar um perfil preliminar do alvo sem a necessidade de interação direta, o que pode alertar o sistema alvo. O domínio `OSCP OffSec Penetration Testing with Kali Linux` possui detalhes específicos sobre o uso do Whois para a coleta inicial de informações e pode servir como referência.