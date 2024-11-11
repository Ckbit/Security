Para identificar e explorar as vulnerabilidades comuns em PHP, existem várias ferramentas e técnicas que podem ser aplicadas tanto para análise estática do código quanto para testes dinâmicos no ambiente de execução. Abaixo detalho como identificar cada vulnerabilidade e quais ferramentas são úteis tanto para encontrá-las quanto para explorá-las.

### 1. Injeção de SQL (SQL Injection)

**Como Identificar:**
- Verifique entradas de usuários não validadas que são diretamente passadas para consultas SQL.
- Busque consultas SQL construídas concatenando strings, especialmente ao usar dados externos como `$_GET`, `$_POST` ou `$_REQUEST`.

**Ferramentas:**
- **SQLMap**: Automatiza a detecção e exploração de injeções SQL. Identifica tipos de bancos de dados e extrai dados vulneráveis.
  ```bash
  sqlmap -u "http://target.com/page.php?id=1" --dbs
  ```
- **Burp Suite**: Permite interceptar e modificar solicitações HTTP, testando manualmente a injeção SQL e executando scans automáticos.
  - Usando o **Intruder** no Burp, envie payloads SQL maliciosos para ver se a aplicação responde com erros de banco de dados.

### 2. Injeção de Comandos (Command Injection)

**Como Identificar:**
- Analise o código PHP para ver onde entradas de usuário são passadas para funções como `system()`, `exec()`, `passthru()`, `shell_exec()` ou `popen()` sem sanitização.
- Tente inserir comandos usando operadores como `;`, `&&`, `|` para verificar se o sistema executa múltiplos comandos concatenados.

**Ferramentas:**
- **Commix**: Automatiza a exploração de injeções de comando. Ele tenta várias técnicas de injeção para determinar se há execução de comando arbitrária.
  ```bash
  commix --url="http://target.com/page.php?param=value"
  ```
- **Burp Suite + Repeater**: Teste manualmente a inserção de payloads de comando e observe as respostas.

### 3. Inclusão de Arquivo Remoto e Local (RFI/LFI)

**Como Identificar:**
- Verifique a presença de `include`, `require`, `include_once` e `require_once` no código PHP que aceitam entradas de usuário.
- Teste URLs que recebem parâmetros com caminhos de arquivos (`/page.php?file=xyz`), inserindo valores como `../../etc/passwd` (LFI) ou URLs externas (RFI).

**Ferramentas:**
- **FIMAP**: Ferramenta automatizada para explorar falhas de inclusão de arquivo (RFI/LFI).
  ```bash
  fimap -u "http://target.com/page.php?file=xyz"
  ```
- **Metasploit**: Oferece módulos para explorar LFI/RFI em aplicações PHP.
- **Burp Suite**: Utilize o **Intruder** para testar automaticamente diferentes payloads de inclusão de arquivo.

### 4. Cross-Site Scripting (XSS)

**Como Identificar:**
- Verifique o código PHP onde entradas de usuário são refletidas diretamente na resposta HTTP sem sanitização, especialmente em campos de formulário ou parâmetros GET/POST.
- Teste com scripts básicos como `<script>alert('XSS')</script>` para ver se o código é executado no navegador.

**Ferramentas:**
- **XSSer**: Ferramenta automatizada para testar XSS em formulários, cabeçalhos HTTP e cookies.
  ```bash
  xsser --url "http://target.com/page.php?param=value"
  ```
- **OWASP ZAP (Zed Attack Proxy)**: Detecta automaticamente vulnerabilidades XSS e permite inspeção detalhada dos pedidos.
- **Burp Suite + Intruder/Repeater**: Envie scripts personalizados e observe a resposta para identificar reflexões de XSS.

### 5. Cross-Site Request Forgery (CSRF)

**Como Identificar:**
- Analise as requisições de formulários e ações sensíveis (como exclusão ou edição de dados) para verificar a ausência de tokens CSRF ou validação de origem.
- Teste manipulando o HTML da página para enviar requisições forjadas sem autenticação.

**Ferramentas:**
- **OWASP ZAP**: Oferece ferramentas para detectar falta de proteção CSRF em formulários e requisições.
- **CSRF PoC Generator (Burp Suite)**: Gera automaticamente um código HTML malicioso para testar CSRF em ações não protegidas.

### 6. Exposição de Informações Sensíveis

**Como Identificar:**
- Verifique a aplicação em busca de funções como `phpinfo()` ou arquivos de configuração que podem ser acessados externamente.
- Analise arquivos públicos em busca de dados como senhas, credenciais de banco de dados e informações de servidor.

**Ferramentas:**
- **DirBuster/Gobuster**: Ferramentas para varredura de diretórios e arquivos escondidos que possam conter informações sensíveis.
  ```bash
  gobuster dir -u http://target.com -w /path/to/wordlist.txt
  ```
- **Nikto**: Analisa o servidor web para detectar arquivos e configurações vulneráveis.
  ```bash
  nikto -h http://target.com
  ```

### Exemplo Completo de Exploração com SQLMap e Burp Suite

Para consolidar, vejamos um fluxo básico de exploração de uma vulnerabilidade de SQL Injection usando o **SQLMap** e **Burp Suite**:
1. **Interceptar e Identificar**: Use o **Burp Suite** para interceptar a solicitação HTTP onde há parâmetros suspeitos de injeção SQL.
2. **Copiar Solicitação**: Copie a solicitação bruta interceptada para o SQLMap:
   ```bash
   sqlmap -r request.txt --dbs
   ```
3. **Explorar Bancos de Dados**: SQLMap listará os bancos de dados disponíveis; selecione o que deseja explorar.
4. **Extração de Dados**: Continuar com `--tables`, `--columns` e `--dump` para extrair dados sensíveis, como credenciais.

Essas práticas e ferramentas fornecem uma abordagem robusta para identificar e explorar vulnerabilidades comuns em aplicações PHP. Caso queira mais informações sobre uma técnica específica ou queira um exemplo prático para outra vulnerabilidade, posso ajudar.