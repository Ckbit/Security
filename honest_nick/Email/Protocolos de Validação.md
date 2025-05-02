Durante o processo de envio e recepção de e-mails, existe uma série de protocolos que são utilizados para validar a veracidade do e-mail, sendo eles o **`DMARC`**, **`DKIM`** e **`SPF`**

## **DMARC**
**`DMARC`** é sigla para **Domain-base Message Authentication, Reporting and Conformance**. O mesmo funciona com um método de autenticação de mensagens de e-mail, onde o mesmo serve como instruções para o servidor receptor sobre como proceder após a verificação do **`SPF`** e do **`DKIM`**.

Durante a recepção de um e-mail, o servidor receptor faz uma validação do e-mail através do **`SPF`** e **`DKIM`**. Caso o e-mail do remetente venha a ser recusado, o servidor **`DMARC`** do destinatário (receptor) consulta o a política que foi definida no **`DMARC`** do remetente para orientar-se em relação a tratativa do e-mail. As instruções mais comuns são:
- **Reject**: Nessa política o e-mail será rejeitado e não chegará ao destinatário. Geralmente é retornado um erro `SMTP 550` de recusa DMARC.
	```bash
	v=DMARC1; p=reject; pct=100; rua=mailto:eu@meudominio.com.br
	```

- **None**: Nessa outra o e-mail será aceita pelo destinatário como se não tivesse DMARC configurado, mas o servidor de destino tomará outras medidas para direcionar ele ou não a caixa de SPAM, como o conteúdo do e-mail, reputação do IP, blacklists, etc.
	```bash
	v=DMARC1; p=none; pct=100; rua=mailto:eu@meudominio.com.br
	```

- **Quarentine**: Nessa situação o e-mail ainda é aceito, mas será tratado como suspeito (possível fishing, vírus, etc.). Geralmente ele será direcionado para a caixa de SPAM/lixo eletrônico e, em alguns casos, será administrado por um sistema de controle do servidor como o Microsoft 365 Security ou o Google Admin.
	```bash
	v=DMARC1; p=reject; pct=100; rua=mailto:eu@meudominio.com.br
	```

Em todos os casos o e-mail nem sempre será rejeitado. Mesmo que o e-mail não passe na verificação do **`SPF`** e do **`DKIM`**, o servidor de destino pode relevar a política do **`DMARC`** e ainda aceitar o e-mail levando em conta outros fatores, como reputação do IP/domínio, conteúdo do e-mail e dentre outros.

### **Tags do DMARC**
Logo abaixo estão listadas a tagas que são utilizadas no **`DMARC`** :

| **Tag** | **Significado**                             | **Obrigatório** | **Valores**                    |
| ------- | ------------------------------------------- | --------------- | ------------------------------ |
| `v`     | Versão                                      | Sim             | `v=DMARC1`                     |
| `p`     | Política de alinhamento                     | Sim             | `none`, `quarentine`,`reject`  |
| `rua`   | URI para relatórios agregados (resumido)    | Não             | `mailto:relatorio@exemplo.com` |
| `ruf`   | URI para relatórios forenses (detalhado)    | Não             | `mailto:forense@exemplo.com`   |
| `pct`   | Percentual de mensagens aplicado à política | Não             | `0` a `100`                    |
| `adkin` | Alinhamento de DKIM                         | Não             | `r` (relaxed), `s` (sricted)   |
| `aspf`  | Alinhamento de SPF                          | Não             | `r` (relaxed), `s` (sricted)   |
| `fo`    | Opções de geração de relatórios forenses    | Não             | `0`,`1`,`d`,`s`                |
| `sp`    | Política para subdomínios                   | Não             | `none`, `quarentine`,`reject`  |

#### **RUA e RUF**

O `RUA` serve para configurar uma forma resumida e estatística do tráfego de e-mail que está usando o domínio.
O mesmo é enviado com frequência e seu conteúdo tipicamente contém:
- Quantidade de mensagens recebidas;
- Resultados de testes `SPF` e `DKIM`;
- IP's que enviaram e-mails;
- Nome do domínio usado;
- Política aplica (`none`, `quarentine`,`reject`).
Geralmente ele é mais utilizado para detectar padrões de envio, facilitando a verificação de envios indevidos ou abusivos do domínio.

Já o `RUF` é uma forma similar de configuração, porém ele apresentar detalhes mais específico e imediatos dos e-mails que falharam na autenticação `DMARC`.
O mesmo tem envio quase imediato, contendo geralmente:
- Cabeças completos da mensagem de recusa;
- Corpo da mensagem;
- Resultado dos testes `SPF`, `DKIM` e `DMARC`;
- IP e domínio de origem.
Ele é mais utilizado para investigar tentativas suspeitas de falsificação (spoofing) ou ataques.

---

### **SPF**
**`SPF`** é a sigla para **Sender Policy Framework**. O mesmo serve como um mecanismo de segurança onde o proprietário do domínio define quais os servidores de IP estão autorizados a enviar e-mails pelo seu nome.

Ele é o protocolo utilizado para validar a identidade do remetente, evitando a falsificação do remetente (spoofing).