<p align="center">
	<img src="https://github.com/code-chat-br/whatsapp-api/raw/main/public/images/code.png" alt="Quepasa-logo" width="500" />	
	<p align="center">Este código é uma implementação do Baileys , como um serviço RestFull Api, que controla as funções do whatsapp </p>
</p>
<hr />
<p align="left">
	<img src="https://telegram.org/favicon.ico" alt="Telegram-logo" width="32" />
	<span>Grupo Telegram: </span>
	<a href="https://t.me/unoapi" target="_blank">Grupo</a>
</p>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP: </span>
	<a href="https://chat.whatsapp.com/KOc9il7AdQVCG06fTmG3Uh" target="_blank">Grupo</a>
</p>

----------------------------------------------------------------------------

</p>

**Gostou do Tutorial? Faça sua Contribuição**

<img src="https://github.com/EngajamentoFlow/quepasa/blob/main/Contribui%C3%A7%C3%A3o.png" alt="Quepasa-logo" width="200" />
</p>

**PIX CNPJ**

```
45959142000119	
```


----------------------------------------------------------------------------

----------------------------------------------------------------------------

Manual ChatWoot+Conector+CodeChat

Vamos precisar de 3 subdomínios

1º Chatwoot
chatwoot.dominio.com.br

2º Conector
conector.dominio.com.br

3º CodeChat
codechat.dominio.com.br

----------------------------------------------------------------------------

Manual de Instalação ChatWoot

sudo apt update && sudo apt upgrade y
wget https://get.chatwoot.app/linux/install.sh
chmod +x install.sh
./install.sh --install

Use as opções abaixo.

yes
chatwoot.dominio.com.br
contato@dominio.com.br
yes
yes

----------------------------------------------------------------------------

Instalando CodeChat

git clone https://github.com/code-chat-br/whatsapp-api.git

cd whatsapp-api

cp chatwoot-codechat/dev-env.yml chatwoot-codechat/env.yml

nano .env

Altere Linha 72

URL: https://conector.site/webhook/codechat

Altere Linha 73

ENABLED: false
para
ENABLED: true

npm i
npm run start
pm2 start 'npm run start:prod' --name codechat

sudo nano /etc/nginx/sites-available/codechat

server {

  server_name codechat.dominio.com.br;

  location / {

    proxy_pass http://127.0.0.1:8080;

    proxy_http_version 1.1;

    proxy_set_header Upgrade $http_upgrade;

    proxy_set_header Connection 'upgrade';

    proxy_set_header Host $host;

    proxy_set_header X-Real-IP $remote_addr;

    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_cache_bypass $http_upgrade;

    proxy_buffering off;

    proxy_cache off;

  }

  }

sudo ln -s /etc/nginx/sites-available/codechat /etc/nginx/sites-enabled


----------------------------------------------------------------------------

Instalando Integrador

git clone https://github.com/w3nder/chatwoot-codechat

cd chatwoot-codechat

nano .env

PORT = 1234
CHATWOOT_ACCOUNT_ID = NUMEROCONTACHATWOOT
CHATWOOT_TOKEN = TOKENDOCHATWOOT
CHATWOOT_BASE_URL = URLDOCHATWOOT

CODECHAT_BASE_URL = URLCODECHAT
CODECHAT_API_KEY = TOKENCODECHAT

# SE DESEJA ASSINAR O A MENSAGEM COM O NOME DO USUÁRIO MUDE PARA true
TOSIGN=true

npm install
npm run build
pm2 start dist/app.js --name NOMEQUEDESEJAR

sudo nano /etc/nginx/sites-available/conector

server {

  server_name conector.dominio.com.br;

  location / {

    proxy_pass http://127.0.0.1:1234;

    proxy_http_version 1.1;

    proxy_set_header Upgrade $http_upgrade;

    proxy_set_header Connection 'upgrade';

    proxy_set_header Host $host;

    proxy_set_header X-Real-IP $remote_addr;

    proxy_set_header X-Forwarded-Proto $scheme;

    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_cache_bypass $http_upgrade;

    proxy_buffering off;

    proxy_cache off;

  }

  }

sudo ln -s /etc/nginx/sites-available/conector /etc/nginx/sites-enabled

sudo certbot --nginx
sudo service nginx restart

----------------------------------------------------------------------------

Primeira parte da Instalação Finalizadas

Acesse:

chatwoot.dominio.com.br

Faça os cadastros

----------------------------------------------------------------------------

Conectando Caixa de Entrada

WEBHOOK CHATWOOT:

Adicione essa url no seu Chatwoot

https://conector.site/webhook/chatwoot

Crie um contato chatmado BOT

Adicione numero telefone ao mesmo

+123456

Chame contato BOT escreva 

/iniciar

Pronto para usar

Comandos Disponíveis:

/iniciar Este comando irá criar uma nova instância e gerar um QR code para você escanear com o WhatsApp. Você poderá conectar-se à instância e começar a usar o bot.

/status Este comando irá verificar o status da instância e retornar informações atualizadas sobre o estado da conexão.

/desconectar Este comando irá desconectar o WhatsApp da instância, encerrando a conexão.

----------------------------------------------------------------------------

----------------------------------------------------------------------------
</p>

**Gostou do Tutorial? Faça sua Contribuição**

<img src="https://github.com/EngajamentoFlow/quepasa/blob/main/Contribui%C3%A7%C3%A3o.png" alt="Quepasa-logo" width="200" />
</p>

**PIX CNPJ**

```
45959142000119	
```
----------------------------------------------------------------------------
