---
folder: "[[Public Records and Databases]]"
---
**Google Dorks** é uma técnica de busca avançada que utiliza operadores específicos no Google para encontrar informações que não estão normalmente acessíveis em pesquisas comuns. Essa técnica, quando bem aplicada, permite explorar e filtrar resultados de maneira detalhada, expondo dados que, muitas vezes, são sensíveis ou privados, e que podem estar publicamente acessíveis sem a devida segurança. Veja abaixo um guia detalhado sobre os conceitos e alguns dos operadores mais usados em Google Dorks.

### 1. **O Que São Google Dorks?**
O termo "Google Dorks" surgiu na comunidade de segurança da informação, onde é utilizado para descrever buscas específicas no Google que revelam informações confidenciais, vulnerabilidades e detalhes sobre servidores e sites. O objetivo não é hackear ou invadir, mas sim revelar o que está publicamente exposto. Quando mal utilizado, Google Dorks pode ser uma técnica de “Google Hacking”, mas, na maioria dos casos, é uma ferramenta poderosa para auditores de segurança, pesquisadores de OSINT (Open Source Intelligence) e profissionais de TI.

### 2. **Operadores Comuns Usados no Google Dorks**

#### **Operadores Básicos**
Esses operadores são os mais comuns e podem ser usados em buscas cotidianas para refinar os resultados.

- **"palavra chave"**: Busca por uma frase exata. Útil para encontrar uma sequência específica de palavras.
- **OR**: Busca uma ou outra palavra ou frase. Exemplo: `senha OR password`.
- **-palavra**: Exclui resultados que contenham uma determinada palavra. Exemplo: `admin -site:example.com`.

#### **Operadores Avançados para Google Dorks**

- **site:** – Limita os resultados de busca a um site específico. Exemplo: `site:example.com`.
- **intitle:** – Encontra páginas que tenham uma palavra ou frase específica no título. Exemplo: `intitle:"index of"`.
- **inurl:** – Busca por uma palavra ou frase específica na URL. Exemplo: `inurl:login`.
- **filetype:** – Limita a busca a um tipo de arquivo específico, como PDF, DOCX, etc. Exemplo: `filetype:pdf "relatório financeiro"`.
- **intext:** – Encontra páginas que contenham uma palavra ou frase no conteúdo do texto.
- **allinurl:** – Pesquisa por várias palavras na URL ao mesmo tempo. Exemplo: `allinurl:admin login`.
- **allintitle:** – Busca múltiplas palavras ou frases no título. Exemplo: `allintitle:senha login`.

### 3. **Aplicações Comuns de Google Dorks**

#### **Para Identificar Vulnerabilidades em Sites**
Profissionais de segurança usam Google Dorks para detectar vulnerabilidades, como páginas de login expostas, diretórios de arquivos, bancos de dados SQL, e até arquivos de backup. Exemplos de dorks voltados para vulnerabilidades incluem:
   - `inurl:admin login`
   - `filetype:sql "password"`

#### **Exposição de Documentos Sensíveis**
Às vezes, arquivos sensíveis são carregados em sites sem a devida segurança. Usar operadores como `filetype:` pode revelar PDFs, documentos do Word, planilhas, entre outros. Exemplos:
   - `filetype:xls "confidencial"`
   - `filetype:pdf site:gov.br`

#### **Busca de Painéis de Administração**
Administradores de sistemas que usam URLs comuns como `admin` ou `login` podem ter seus painéis de administração facilmente encontrados. Usar os operadores `inurl:`, `intitle:` e `filetype:` pode ajudar a localizá-los:
   - `intitle:"Admin Login"`
   - `inurl:admin.php`
   - `filetype:php inurl:admin`

#### **Busca de Páginas Indexadas**
Páginas não intencionais podem estar acessíveis e indexadas pelo Google. Termos como "index of" são frequentemente explorados para encontrar diretórios abertos. Exemplos:
   - `intitle:"index of" "backup"`
   - `intitle:"index of" "password"`

### 4. **Exemplos Completos de Google Dorks**

Aqui estão alguns dorks que exemplificam bem as possibilidades dessa técnica:

- `site:gov.br filetype:xls` – Busca por planilhas no domínio de sites governamentais brasileiros.
- `intitle:"index of" "database"` – Encontra páginas com diretórios abertos de banco de dados.
- `inurl:"phpmyadmin" "root"` – Pode revelar instalações do phpMyAdmin com usuários de acesso expostos.
- `"password"` filetype:xls – Localiza documentos do Excel que podem conter senhas.

### 5. **Boas Práticas e Ética ao Utilizar Google Dorks**

É importante lembrar que o uso ético de Google Dorks envolve:
   - **Respeito pela Privacidade**: Apenas buscar informações públicas que não comprometam privacidades individuais.
   - **Uso em Segurança da Informação**: Se for um auditor de segurança ou pesquisador de OSINT, deve-se pedir autorização para verificar sistemas de terceiros.
   - **Não Realizar Atividades Ilegais**: Acesso a informações protegidas ou tentativa de explorar vulnerabilidades sem permissão pode ser considerado crime.

### 6. **Ferramentas que Podem Complementar o Google Dorks**

Existem ferramentas que ajudam a automatizar a pesquisa com dorks, especialmente em auditorias e testes de penetração. Algumas ferramentas populares incluem:

- **DorkMe**: Realiza uma busca automatizada de dorks.
- **GooDork**: Ferramenta Python para busca de dorks.
- **Google Hacking Database (GHDB)**: Mantido pelo site Exploit-DB, o GHDB possui uma coleção de dorks atualizada por pesquisadores de segurança.