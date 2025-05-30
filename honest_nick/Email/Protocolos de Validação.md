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
	v=DMARC1; p=quarentine; pct=100; rua=mailto:eu@meudominio.com.br
	```

Em todos os casos o e-mail nem sempre será rejeitado. Mesmo que o e-mail não passe na verificação do **`SPF`** e do **`DKIM`**, o servidor de destino pode relevar a política do **`DMARC`** e ainda aceitar o e-mail levando em conta outros fatores, como reputação do IP/domínio, conteúdo do e-mail e dentre outros.

### **Tags do DMARC**

Logo abaixo estão listadas a tags que são utilizadas no **`DMARC`** :

| **Tag** | **Função**                                  | **Obrigatório** | **Valores**                    |
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

Logo abaixo temos um exemplo de registro DMARC completo:

```bash
v=DMARC1; p=reject; rua=mailto:dmarc-rua@seudominio.com; ruf=mailto:dmarc-ruf@seudominio.com; pct=100; adkim=s; aspf=r; sp=quarantine
```
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

## **SPF**

**`SPF`** é a sigla para **Sender Policy Framework**. O mesmo serve como um mecanismo de segurança onde o proprietário do domínio define quais os servidores de IP estão autorizados a enviar e-mails pelo seu nome.

Ele é o protocolo utilizado para validar a identidade do remetente, evitando a falsificação do remetente (spoofing).

O `SPF` contém um registro um registro **`DNS`** que lista todos os servidores que tem acesso para enviar e-mails pelo seu domínio. 
	**Ex**.: O domínio `meudominio.com.br` tem configurado no registro `SPF` para que somente o IP `179.206.83.7` tem acesso para enviar os e-mails utilizando seu domínio.

### **Mecanismos, Modificadores e Qualificadores do SPF**

Para configuração do **`SPF`**, são configurados uma série de fatores, sendo eles **Mecanismos**, **Modificadores** e **Qualificadores**

#### **Mecanismos**

Os mecanismos são a principal fonte de configurado do `SPF`. Eles são as regras responsáveis por determinas **quais servidores ou IPs podem fazer o envio dos e-mails através do domínio**.

Logo abaixo estão listadas a mecanismos que são utilizadas na configuração do registro **`SPF`** :

| **Mecanismo** | **Função**                                                       | **Obrigatório** | **Valores**                               |
| ------------- | ---------------------------------------------------------------- | --------------- | ----------------------------------------- |
| `v`           | Versão do SPF                                                    | Sim             | `v=spf1`                                  |
| `ip4`         | Permitir o envio a partir de um IP ou faixa IPv4                 | Não             | `ip4:<IP>` ou `ip4:<IP>/<CIDR>`           |
| `ip6`         | Permitir o envio a partir de um IP ou faixa IPv6                 | Não             | `ip6:<IP>` ou `ip6:<IP>/<CIDR>`           |
| `a`           | Permite se o IP resolver para um registro A/AAAA do domínio      | Não             | `a` ou `a:sub.dominio.com`                |
| `mx`          | Permite envio pelos IPs dos registros MX do domíno               | Não             | `mx` ou `mx:sub.dominio.com`              |
| `include`     | Usa a política SPF de outro domínio (como Google, Outlook, etc.) | Não             | `include:dominio.com`                     |
| `exists`      | Verifica se um domínio existe                                    | Não             | `exists:%{i}.dominio.com`                 |
| `all`         | Aplica uma política a todos os IPs restantes                     | Sim             | `all` (usado no final dos qualificadores) |

#### **Modificadores**

Os **modificadores** são **complementos especiais**. Ele **modificam o comportamento da política SPF** ou adicionam **informações adicionais**.

| **Modificador** | **Função**                                     | **Obrigatório** | **Valores**                  |
| --------------- | ---------------------------------------------- | --------------- | ---------------------------- |
| `redirect`      | Redireciona toda a política para outro domínio | Não             | `redirect=outro.dominio.com` |
| `exp`           | Mensagem explicativa (aparece em erros SPF)    | Não             | `exp=mensagem.dominio.com`   |

Dentro da configuração do `SPF` só pode haver 1 modificador`redirect` e `exp`.

#### **Qualificadores**

Os **qualificadores** são **prefixos opcionais**que indicam **como tratar os mecanismos** se eles forem correspondidos.

| **Qualificador** | **Ação em resposta ao mecanismo** | **Exemplo**    |
| ---------------- | --------------------------------- | -------------- |
| `+`              | Pass (aceita)                     | `+ip4:1.2.3.4` |
| `-`              | Fail (rejeita o e-mail)           | `-all`         |
| `~`              | SoftFail (aceita com suspeita)    | `~all`         |
| `?`              | Neutral (nenhuma recomendação)    | `?all`         |

#### **Conclusão**

Com todas essas configurações definidas, o servidor já estará configurado para validação `SPF`, lembrando que o `SPF` não passa por uma validação completa dos mecanismos. 

Quando um e-mail chega no servidor de recepção, o mesmo inicia a validação do `SPF` do servidor de origem verificando os mecanismos configurados da esquerda para a direita. Caso o e-mail esteja de acordo com a configuração do primeiro mecanismo, o mesmo é aceito pelo `SPF` e, caso não seja aceito, o servidor continuará testando os demais mecanismos até chegar no mecanismo `all`que dirá ao servidor de recepção o resultado final do teste. Por exemplo:

```bash
v=spf1 ip4:192.0.2.10 include:_spf.exemplo.com -all
```

Nessa configuração do `SPF` o servidor de destino fará a seguinte validação:
- Se o IP do remente for **`192.0.02.10`**: **PASSA** no primeiro mecanismo. Caso não verifica o próximo mecanismo;
- Se o IP do remente estiver listado em **`_spf.exemplo.com`**: **PASSA** no segundo mecanismo. Caso não, passa para o próximo mecanismo;
- Caso todos os mecanismos **FALHEM**: cai no mecanismo `-all` -> Falha (e-mail rejeitado).

Considerando que a validação é feita para cada mecanismo presente na configuração do `SPF`, ter vários mecanismos configurados poder se ruim, já que durante a validação só podem ser consultados 10 registros DNS, o que pode complicar o gerenciamento e aumentar as chances de erro, como `includes` que contenham IPs desatualizados e afins.

Então após a validação do `SPF` o servidor de recepção fará a tratativa do e-mail com base na configuração `DMARC`, seja em caso de aceite ou recusa pelo `SPF`.

---
## **DKIM**

**`DKIM`** é a sigla para **DomainKeys Identified Mail** e se trata de um **método de autenticação** para os e-mail **baseado em criptografia**, permitindo que o servidor de envio do e-mail **assine digitalmente** algumas partes da mensagem, garantindo que o conteúdo do e-mail **não tenha sido alterado** e que ele realmente foi enviado com **autorização do domínio remetente**.

Diferente do **`SPF`** que garante a segurança que o caminho de envio (IP), o `DKIM` protege diretamente o conteúdo e-mail, garantindo que o **corpo do e-mail e cabeçalhos importantes não tenham sido alterados** e de que a mensagem **está autorizada a ser enviada** por aquele domínio.