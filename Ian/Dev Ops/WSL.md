### **O que é?**
Se trata de uma funcionalidade do Windows que permite executar ambientes GNU/Linux sem a necessidade de utilizar dual boot ou uma máquina virtual. A vantagem dessa funcionalidade é permitir que o usuário mantenha os dois sistemas operacionais em funcionamento enquanto utiliza todos os recursos do computador.

---
### **Para que serve?**
O objetivo do WSL gira em torno de facilitar o uso de distribuições Linux através do Windows, de modo que o usuário consiga gerenciar várias distribuições simultaneamente, o que possibilita a criação de vários ambiente Linux com acesso a arquivos e diretórios do Windows.

---
### **Como Instalar**
1. O WSL só funciona em SO com **Windows 10** com versão **2004** e com compilação **19041 ou superior** e também é funcional em SO **Windows 11.**
	- Para verificar a **compilação** do seu computador basta fazer o seguinte:
		1. Aperte as teclas **WIN+R**
		2. Digite o seguinte comando: **`winver`**
		3. Feito isso, abri uma tela com informações do Windows e basta checar a data de compilação em frente a versão.
1. Feita a conferência da compilação do seu Windows, basta abrir o **PowerShell** ou o **Prompt de Comando** executando com administrado e executar o seguinte comando:
	```powershell
	wsl --install
	```
3. Após a execução do comando será necessário reiniciar o computador.
4. Feito esse processo, os recursos para utilizar o WSL estarão habilitados e será instalado, por padrão, o **Ubuntu Linux**.
5. Caso queira instalar outras distribuições, como por exemplo o Kali Linux, você pode utilizar o seguinte comando:
	```powershell
	wsl --install kali-linux
	```
	Caso não funcione, é recomendável acessar a página de suporte da distribuição Linux para localizar o passo a passo para instalação da mesma através do WSL.