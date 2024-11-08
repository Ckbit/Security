### **<span style="color: #A39EED;">O que é?</span>**
O Docker é um **serviço de virtualização** onde é possível gera uma **Imagem** onde essa imagem contém todas as informações necessárias para executar e configurar determinadas aplicações, onde essa imagem ficará armazenada em um **Container** que opera de forma independente dos outros processos da nossa máquina, somente contendo as imagens alocadas com as aplicações.

---
### **<span style="color: #A39EED;">Para que serve?</span>**

---
### **<span style="color: #A39EED;">O que é a Imagem?</span>**
A imagem se trata de um arquivo onde são armazenados os dados necessários para **instalar, executar e configurar** determinadas aplicações, como exemplo o MySQL.

---
### **<span style="color: #A39EED;">O que é o Container?</span>**
O container é um servidor de virtualização que opera no SO do computador, onde dentro do mesmo ficam contidas as imagens que foram geradas. Cada container opera do modo autônomo com relação ao servidor onde está alocado e com relação a cada container alocado. O mesmo não utiliza dos recursos alocados no servidor, ficando apenas destinado a utilização das imagens que foram alocadas.

Ainda aprofundando sobre o container, o mesmo seria indiretamente uma imagem. O que o diferencia de uma imagem é que o mesmo executa todas as funções que foram definidas nos arquivos de imagem que foram salvas dentro do mesmo. Então as imagens armazenam as configurações e o container executa essas informações enquanto mantém as imagens armazenadas.

---
### **<span style="color: #A39EED;">O que é o Dockerfiles?</span>**
O Dockerfile serve para armazenar todas as informações, como configurações, processos, etc. que são necessárias para gerar a imagem que será armazenada no container.

---
### **<span style="color: #A39EED;">O que são os Registros?</span>**
Os registros se tratam de hub's onde as imagens criadas e utilizadas ficam armazenadas, para que assim vários usuários ou os funcionários de uma determinada empresa tenham acesso a essas imagens. 

---
### **<span style="color: #A39EED;">Como Instalar no Linux</span>**
1. Executar os comandos para adicionar a chave GPG do Docker:
	```bash
	sudo apt-get update
	sudo apt-get install ca-certificates curl
	sudo install -m 0755 -d /etc/apt/keyrings
	sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
	sudo chmod a+r /etc/apt/keyrings/docker.asc
	```

	Ou o seguinte comando caso você esteja acessando com o usuário root:
	```bash
	apt-get update
	apt-get install ca-certificates curl
	install -m 0755 -d /etc/apt/keyrings
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
	chmod a+r /etc/apt/keyrings/docker.asc
	```

2. Executar o comando para adicionar o repositório (apt) de atualizações do docker:

	```bash
	echo\
	  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
	  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
	  sudo tee /etc/apt/sources.list.d/docker;list > /dev/null
	sudo apt-get update
	```

3. Finalizado as configurações iniciais, executar o seguinte comando para instalar a versão mais recente do Docker:
	```bash
	sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
	```

4. Finalizando todo o processo, para confirmar se as configurações e a instalação foram realizadas com sucesso, basta executar o comando a seguir:
	```bash
	sudo docker run hello-world
	```
---
### **<span style="color: #A39EED;">Comandos</span>**
#### **<span style="color: #A39EED;">docker ps</span>**
- Lista os containers **em execução** na máquina e as imagens vinculadas a ele.
	```docker
	docker ps
	```
#### **<span style="color: #A39EED;">docker ps -a</span>**
- Lista os containers **já executados** na máquina e as imagens vinculadas a ele.
	```docker
	docker ps -a
	```
#### **<span style="color: #A39EED;">docker run |imagem|</span>**
- Serve para executar a imagem dentro do docker, porém esse comando somente executa e não mantém a imagem em execução. Exemplo:
	```docker
	docker run hello-world
	```
#### **<span style="color: #A39EED;">docker run -it |imagem|</span>**
- Serve para manter a imagem em execução na máquina. O **'it'** server para indiciar a interação com uma imagem. Um exemplo seria:
	```docker
	docker run -it ubuntu bash
	``````
#### **<span style="color: #A39EED;">docker stop |ID|</span>**
- Serve para finalizar um container que esteja em execução.
	```docker
	docker stop ID
	```
#### **<span style="color: #A39EED;">docker start |ID|</span>**
- Serve para inicializar um container que foi encerrado anteriormente.
	```docker
	docker strat ID
	```
#### **<span style="color: #A39EED;">docker exec -it |ID|</span>**
- Serve para executar um container que está em serviço no momento.
	```docker
	docker exec -it ID
	```
