### **Como instalar o MySQL no Ubuntu**

Para realizar a instalação do MySQL em um servidor Ubuntu basta seguir os seguintes comandos:

1. Esse comando será utilizado para instalar o MySQL:

```bash
sudo apt instal mysql-server
```

2. Assim que instalado, você deverá utilizar o seguinte comando para iniciar o serviço: 

```bash
sudo service mysql start
```

3. Feito isso o MySQL já estará instalado.

### **Configurando o MySQL**

Após a instalação, será necessário acessar o terminal do MySQL para alterar algumas configurações para o método de autenticação, devido a um erro no script **mysql_secure_installation**. Esse script serve para definir alguns parâmetros de segurança do MySQL e para permitir o gerenciamento de usuários que terão acesso ao usuário root. Seguem os comandos:

1. Acessar o terminal:
```bash
sudo mysql
```

2. Utilizar o comando **ALTER USER** para mudar o método de autenticação do usuário **root** para um método de requisição de senha:
```mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'sua_senha';
```

3. Sair do terminal de configuração
```mysql
exit
```

Feito isso já será possível executar o script de segurança através do seguinte comando:

```bash
sudo mysql_secure_instalation
```

Caso você queira mudar o método de autenticação do usuário root para o modo que era anteriormente, basta executar os seguintes comandos:

1. Acessar novamente o terminal:
```bash
sudo mysql -u root -p
```

2. Executar novamente o comando **ALTER USER**:
```bash
ALTER USER 'root'@'localhost' IDENTIFIED WITH auth_socket;
```

Caso alguma etapa do processo gere algum erro, você pode verificar manual de instalação [clicando aqui](https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-20-04)