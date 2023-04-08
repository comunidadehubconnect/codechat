<p align="center">
	<img src="https://github.com/code-chat-br/whatsapp-api/raw/main/public/images/code.png" alt="Quepasa-logo" width="500" />	
	<p align="center">Este código é uma implementação do Baileys , como um serviço RestFull Api, que controla as funções do whatsapp </p>
</p>
<hr />
<p align="left">
	<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
	<span>Grupo WhatsaAPP: </span>
	<a href="https://chat.whatsapp.com/CwcSUOcgPBL6lJWYyvA0NS
" target="_blank">Grupo</a>
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

**Manual ChatWoot+Conector+CodeChat**

</p>
Vamos precisar de 3 subdomínios
</p>
1º Chatwoot
</p>
chatwoot.dominio.com.br
</p>
2º Conector
</p>
conector.dominio.com.br
</p>
3º CodeChat
</p>
codechat.dominio.com.br
</p>

----------------------------------------------------------------------------

**Manual de Instalação ChatWoot**

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

**Instalando CodeChat**

</p>
git clone https://github.com/code-chat-br/whatsapp-api.git
</p>
cd whatsapp-api
</p>
cp chatwoot-codechat/dev-env.yml chatwoot-codechat/env.yml
</p>
cd src
</p>
nano .env
</p>
Altere Linha 72
</p>
URL: https://conector.site/webhook/codechat
</p>
Altere Linha 73
</p>
ENABLED: false
</p>
para
</p>
ENABLED: true
</p>
npm i
</p>
npm run start
</p>
pm2 start 'npm run start:prod' --name codechat
</p>
sudo nano /etc/nginx/sites-available/codechat
</p>

```


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
  
```

</p>
sudo ln -s /etc/nginx/sites-available/codechat /etc/nginx/sites-enabled
</p>

----------------------------------------------------------------------------

**Instalando Integrador**

</p>
git clone https://github.com/w3nder/chatwoot-codechat
</p>
cd chatwoot-codechat
</p></p>
nano .env
</p>
PORT = 1234
</p>
CHATWOOT_ACCOUNT_ID = NUMEROCONTACHATWOOT
</p>
CHATWOOT_TOKEN = TOKENDOCHATWOOT
</p>
CHATWOOT_BASE_URL = URLDOCHATWOOT
</p>
CODECHAT_BASE_URL = URLCODECHAT
</p>
CODECHAT_API_KEY = TOKENCODECHAT
</p>
TOSIGN=true
</p>
npm install
</p>
npm run build
</p>
pm2 start dist/app.js --name NOMEQUEDESEJAR
</p>
sudo nano /etc/nginx/sites-available/conector
</p>

```

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
  
 ```

</p>
sudo ln -s /etc/nginx/sites-available/conector /etc/nginx/sites-enabled
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>

----------------------------------------------------------------------------

**Primeira parte da Instalação Finalizadas**

</p>
Acesse:
</p>
chatwoot.dominio.com.br
</p>
Faça os cadastros
</p>

----------------------------------------------------------------------------

**Conectando Caixa de Entrada**

</p>
WEBHOOK CHATWOOT:
</p>
Adicione essa url no seu Chatwoot
</p>
https://conector.site/webhook/chatwoot
</p>
Crie um contato chatmado BOT
</p>
Adicione numero telefone ao mesmo
</p>
+123456
</p>
Chame contato BOT escreva 
</p>
/iniciar
</p>
Pronto para usar
</p>
Comandos Disponíveis:
</p>
/iniciar Este comando irá criar uma nova instância e gerar um QR code para você escanear com o WhatsApp. Você poderá conectar-se à instância e começar a usar o bot.
</p>
/status Este comando irá verificar o status da instância e retornar informações atualizadas sobre o estado da conexão.
</p>
/desconectar Este comando irá desconectar o WhatsApp da instância, encerrando a conexão.
</p>

----------------------------------------------------------------------------

**Pronto tudo Funcionando**

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
