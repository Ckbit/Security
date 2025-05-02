Durante o processo de envio e recepção de e-mails, existe uma série de protocolos que são utilizados para validar a veracidade do e-mail, sendo eles o **`DMARC`**, **`DKIM`** e **`SPF`**

### **DMARC**
**`DMARC`** é sigla para **Domain-base Message Authentication, Reporting and Conformance**. O mesmo funciona com um método de autenticação de mensagens de e-mail, onde o mesmo serve como instruções para o servidor receptor sobre como proceder após a verificação do **`SPF`** e do **`DKIM`**.

Durante a recepção de um e-mail, o servidor receptor faz uma validação do e-mail através do **`SPF`** e **`DKIM`**. Caso o e-mail do remetente venha a ser recusado, o servidor **`DMARC`** do destinatário (receptor) consulta o a política que foi definida no **`DMARC`** do remetente para orientar-se em relação a tratativa do e-mail. As instruções mais comuns são:
- **Rejeitar**: 