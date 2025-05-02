Durante o processo de envio e recepção de e-mails, existe uma série de protocolos que são utilizados para validar a veracidade do e-mail, sendo eles o **`DMARC`**, **`DKIM`** e **`SPF`**

### **DMARC**
**`DMARC`** é sigla para **Domain-base Message Authentication, Reporting and Conformance**. O mesmo funciona com um método de autenticação de mensagens de e-mail, onde o mesmo serve como instruções para o servidor receptor sobre como proceder após a verificação do **`SPF`** e do **`DKIM`**.

Durante a recepção de um e-mail, o servidor receptor faz uma validação do e-mail através do **`SPF`** e **`DKIM`**. Caso o e-mail do remetente venha a ser recusado, o servidor **`DMARC`** do destinatário (receptor) consulta o a política que foi definida no **`DMARC`** do remetente para orientar-se em relação a tratativa do e-mail. As instruções mais comuns são:
- **Reject**: Nessa política o e-mail será rejeitado e não chegará ao destinatário. Geralmente é retornado um erro `SMTP 550` de recusa DMARC
- **None**: Nessa outra o e-mail será aceita pelo destinatário como se não tivesse DMARC configurado, mas o servidor de destino tomará outras medidas para direcionar ele ou não a caixa de SPAM, como o conteúdo do e-mail, reputação do IP, blacklists, etc.
- **Quarentine**: Nessa situação o e-mail ainda é aceito, mas será tratado como suspeito (possível fishing, vírus, etc.). Geralmente ele será direcionado para a caixa de SPAM/lixo eletrônico e, em alguns casos, será administrado por um sistema de controle do servidor como o Microsoft 365 Security ou o Google Admin.

Em todos os casos o e-mail nem sempre será rejeitado. Mesmo que o e-mail não passe na verificação do **`SPF`** e do **`DKIM`**, o servidor de destino pode relevar a política do **`DMARC`** e ainda aceitar o e-mail levando em conta outros fatores, como reputação do IP/domínio, conteúdo do e-mail e dentre outros.

### **SPF**
**`SPF`** é a sigla para **Sender Policy Framework**. O mesmo serve como um mecanismo de segurança onde o proprietário do domínio define quais os servidores de IP estão autorizados a enviar e-mails pelo seu nome.

Ele é o protocolo utilizado para validar a identidade do remetente, evitando a falsificação do remetente (spoofing).