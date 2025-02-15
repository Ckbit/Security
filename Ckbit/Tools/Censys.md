# Ferramenta de Inteligência para Cybersecurity
## 🔍 O que é o Censys?

[Censys](https://search.censys.io/) é uma plataforma de inteligência de ameaças e busca de ativos expostos na internet. Ele fornece varreduras contínuas da internet para identificar dispositivos, certificados TLS/SSL e serviços em execução. Seu objetivo principal é ajudar pesquisadores e profissionais de segurança a monitorar e proteger ativos digitais contra ataques.

---

## 🎯 Principais Funcionalidades

### ✅ Busca de Hosts e Serviços

- Pesquisa por **IP, domínios, ASN e certificados SSL/TLS**.
- Identifica **protocolos e serviços expostos** em servidores e dispositivos.
- Exibe detalhes técnicos, como **banners de serviços, versões e vulnerabilidades conhecidas**.

### 🔑 Monitoramento de Certificados SSL/TLS

- Identifica **certificados digitais ativos e expirados**.
- Verifica a **cadeia de certificação e potenciais riscos de configuração**.

### 🌍 Varredura da Internet

- Indexa **hospedeiros acessíveis na internet**.
- Descobre **portas abertas e serviços rodando** nos sistemas.

### 🚨 Detecção de Vulnerabilidades

- Auxilia na identificação de **sistemas desatualizados**.
- Ajuda a detectar **falhas de segurança conhecidas** (CVE).

### 📡 API para Integração

- Fornece uma API RESTful para **consultas automatizadas**.
- Permite integração com **SIEMs e ferramentas de defesa**.

---

## 🏗️ Como Usar?

### 🔎 Pesquisa Manual no Site

1. Acesse [Censys Search](https://search.censys.io/).
2. Utilize a barra de pesquisa para consultar um **IP, domínio, ASN ou certificado**.
3. Explore os detalhes fornecidos, como **serviços ativos e riscos**.

### 🔥 Consulta via API

Para usar a API, você precisa de uma **chave de API** (é necessário criar uma conta no Censys).

**Exemplo de consulta via cURL:**  
`curl -H "Authorization: Bearer <API_KEY>" "https://search.censys.io/api/v2/hosts/search?q=google.com"`

**Exemplo de consulta via Python:**  
`import requests`  
`API_KEY = "SUA_CHAVE_AQUI"`  
`headers = {"Authorization": f"Bearer {API_KEY}"}`  
`response = requests.get("https://search.censys.io/api/v2/hosts/search?q=google.com", headers=headers)`  
`print(response.json())`

---

## 🛠️ Casos de Uso para Pentesters e Blue Teams

### 🕵️‍♂️ Red Team / Pentesting

- **Footprinting e Reconhecimento**: Descubra ativos e serviços expostos antes de um teste de invasão.
- **Identificação de Superfície de Ataque**: Identifique portas abertas e versões de software vulneráveis.

### 🏰 Blue Team / Defesa

- **Monitoramento de Ativos**: Acompanhe se sua organização tem serviços desprotegidos expostos.
- **Detecção de Vazamentos de Certificados**: Monitore se certificados TLS foram emitidos sem autorização.

---

## ⚠️ Considerações Éticas e Legais

- O Censys é uma ferramenta poderosa e deve ser usada **apenas para fins legítimos e éticos**.
- **Consultar sistemas sem permissão pode violar leis de privacidade e segurança digital** (LGPD, GDPR, CFAA, etc.).
- Utilize para **defesa e proteção de redes próprias ou com autorização expressa do proprietário**.

---

## 🔗 Links Úteis

- 🌐 [Site Oficial](https://censys.io/)
- 📜 [Documentação da API](https://search.censys.io/api)
- 🔬 [Relatórios de Pesquisa](https://censys.io/labs)

---

## 🏁 Conclusão

O **Censys** é uma ferramenta essencial para segurança cibernética, ajudando na identificação de riscos e exposição de ativos na internet. Seu uso adequado pode fortalecer a defesa das redes e melhorar a visibilidade sobre vulnerabilidades.

🔒 **Use com responsabilidade e sempre dentro dos limites legais!** 🚀