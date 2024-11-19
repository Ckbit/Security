---
folder: "[[Tools]]"
---

#### **1. Introdução ao Burp Suite**
O **Burp Suite** é uma ferramenta de teste de segurança para aplicações web amplamente utilizada por profissionais de segurança. Desenvolvida pela PortSwigger, é conhecida por sua capacidade de realizar testes de penetração manuais e automatizados. Sua função principal é ajudar a identificar e explorar vulnerabilidades em aplicações web.

- **Funcionalidades Principais**:
  - **Interceptação de Tráfego**: Permite capturar e modificar requisições entre o cliente e o servidor.
  - **Scan Automático**: Identifica vulnerabilidades conhecidas automaticamente.
  - **Ferramentas de Ataque**: Inclui funcionalidades como brute force, fuzzing e exploração de falhas.
  - **Extensibilidade**: Oferece suporte para scripts personalizados em Python (via Burp Extender).

- **Aplicações**:
  - Identificação de falhas de segurança em aplicações web.
  - Testes de penetração em APIs.
  - Validação de correções em aplicações web.

#### **2. Falhas que Podem ser Exploradas com o Burp Suite**
Com o Burp Suite, você pode explorar as seguintes vulnerabilidades comuns:
- **SQL Injection (SQLi)**: Exploração de entradas malvalidadas para manipular consultas SQL.
- **Cross-Site Scripting (XSS)**: Injeção de scripts maliciosos em páginas vulneráveis.
- **Cross-Site Request Forgery (CSRF)**: Execução de ações indesejadas em aplicações autenticadas.
- **Injeção de Comandos**: Execução de comandos no sistema operacional do servidor.
- **Exposição de Dados Sensíveis**: Interceptação de informações transmitidas inseguramente.
- **Path Traversal**: Acesso a arquivos sensíveis no sistema de arquivos do servidor.
- **Fuzzing de API**: Teste de endpoints de APIs para descobrir comportamentos não documentados ou vulnerabilidades.

#### **3. Abas do Burp Suite**
O Burp Suite é organizado em várias abas, cada uma com funcionalidades específicas. Aqui está uma explicação detalhada de cada aba:

---

##### **3.1. Target**
- **Objetivo**: Mapear o escopo do teste.
- **Funcionalidades**:
  - **Site Map**: Lista os recursos do alvo como páginas, parâmetros e respostas.
  - **Scope**: Configuração para filtrar requisições no escopo definido.
- **Uso Comum**:
  - Identificar áreas sensíveis e endpoints da aplicação.
  - Preparar o terreno para exploração em outras abas.

##### **3.2. Proxy**
- **Objetivo**: Interceptar e manipular requisições HTTP/S.
- **Funcionalidades**:
  - **Intercept**: Permite pausar e modificar requisições em tempo real.
  - **HTTP History**: Histórico de requisições capturadas.
- **Uso Comum**:
  - Alterar cabeçalhos ou parâmetros em requisições.
  - Verificar como os dados estão sendo processados pelo servidor.

##### **3.3. Intruder**
- **Objetivo**: Automação de ataques, como brute force e fuzzing.
- **Funcionalidades**:
  - **Positions**: Define os parâmetros para ataque.
  - **Payloads**: Configura valores para teste.
  - **Options**: Define configurações avançadas, como manipulação de cookies.
- **Exemplo de Uso**:
  ```plaintext
  Explorar vulnerabilidades de SQL Injection:
  Payloads: ' OR '1'='1; DROP TABLE users; --
  ```
  O Intruder executa várias combinações para identificar respostas anômalas.

##### **3.4. Repeater**
- **Objetivo**: Enviar requisições personalizadas e verificar respostas.
- **Funcionalidades**:
  - Reenvio manual de requisições HTTP.
  - Alteração de parâmetros para exploração de vulnerabilidades.
- **Uso Comum**:
  - Testar manualmente entradas para identificar comportamentos vulneráveis.
  - Validar vulnerabilidades encontradas.

##### **3.5. Scanner** (Versão Profissional)
- **Objetivo**: Identificar vulnerabilidades automaticamente.
- **Funcionalidades**:
  - Análise de segurança passiva e ativa.
  - Relatórios detalhados de vulnerabilidades.
- **Uso Comum**:
  - Automatizar parte do processo de identificação de falhas.
  - Identificar rapidamente problemas de segurança em grandes aplicações.

##### **3.6. Decoder**
- **Objetivo**: Decodificar ou codificar dados.
- **Funcionalidades**:
  - Suporte para Base64, URL-encoding, HTML-encoding, entre outros.
  - Análise de dados criptografados.
- **Uso Comum**:
  - Decodificar tokens ou dados transmitidos em formato não-legível.
  - Explorar vulnerabilidades baseadas em encoding.

##### **3.7. Comparer**
- **Objetivo**: Comparar respostas ou requisições HTTP.
- **Funcionalidades**:
  - Comparação visual para identificar diferenças.
- **Uso Comum**:
  - Determinar se mudanças feitas em uma requisição afetam a resposta.
  - Analisar respostas em cenários de fuzzing.

##### **3.8. Sequencer**
- **Objetivo**: Avaliar a entropia de tokens.
- **Funcionalidades**:
  - Coleta de tokens.
  - Análise estatística para determinar previsibilidade.
- **Uso Comum**:
  - Testar a aleatoriedade de IDs de sessão ou outros tokens.

##### **3.9. Extender**
- **Objetivo**: Personalizar o Burp Suite.
- **Funcionalidades**:
  - Suporte para extensões em Java, Python, e Ruby.
  - Integração com APIs externas.
- **Uso Comum**:
  - Adicionar ferramentas personalizadas.
  - Automatizar tarefas específicas.

##### **3.10. Dashboard**
- **Objetivo**: Monitorar atividades do Burp Suite.
- **Funcionalidades**:
  - Visualização de scans e alertas em tempo real.
  - Logs detalhados de atividades.
- **Uso Comum**:
  - Monitorar o progresso de tarefas automatizadas.
  - Analisar relatórios de vulnerabilidades.

---