---
folder: "[[BackDoor]]"
---

## Como Criar uma Backdoor com o Discord

### Configuração do Discord

1. Crie um servidor pessoal no Discord.
2. Acesse o site de desenvolvedores: [discord.com/developers/applications](https://discord.com/developers/applications).
3. Crie um novo aplicativo clicando em "New Application".
4. Escolha um nome para o bot (apenas você verá este nome e terá acesso a ele).
5. Gere o Token do Bot: vá na aba "Bot" na barra lateral, clique em "Reset Token" e copie o token gerado.
6. Ative as permissões do bot:
    - Na aba "Bot", em "Privileged Gateway Intents", ative as três opções.
    - Em "Bot Permissions", selecione "Administrator".
7. Configurações de OAuth2:
    - Na aba "OAuth2", ative "applications.commands" e "Bot".
    - Mais abaixo, selecione "Administrator" e copie a URL gerada.
8. Adicione o Bot ao seu Servidor: usando a URL copiada, adicione o bot ao servidor pessoal criado.

### Configuração do Discord RAT 2.0

1. Prepare os Arquivos:
    - Coloque o **release.rar** em uma pasta excluída do antivírus e extraia os arquivos.
2. Execute o Builder: abra o "builder.exe" e siga as instruções:
    - No primeiro campo, cole o token do bot.
    - No segundo campo, insira o ID do servidor (no Discord, clique com o botão direito no servidor e copie o ID).
    - Clique em **Build** para finalizar.