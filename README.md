<p align="center">
<img src="https://cwmkt.com.br/wp-content/uploads/2023/08/logo-github-cwmkt.svg" alt="DispZap Whats Marketing" width="240" />
<p align="center">Seja bem-vindo ao Guia de atualização do n8n, nodejs e quepasa 🚀</p>
</p>
  
<p align="center">
<img src="https://whatsapp.com/favicon.ico" alt="WhatsAPP-logo" width="32" />
<span>Grupo WhatsaAPP: </span>
<a href="https://link.cwmkt.com.br/grupo-whats" target="_blank">Grupo</a>
</p>

<hr />
<hr />


**Manual de Instalação ChatWoot**

sudo apt update && apt upgrade -y
</p>
wget https://get.chatwoot.app/linux/install.sh
</p>
chmod +x install.sh
</p>
./install.sh --install
</p>
Use as opções abaixo
</p>
yes
</p>
chatwoot.dominio.com.br
</p>
contato@dominio.com.br
</p>
yes para todos
</p>
<hr />

**Alterando Idioma e ativando sua tela de cadastro**

</p>
cd /home/chatwoot/chatwoot
</p>
nano .env
</p>
Altere a linha
</p>
DEFAULT_LOCALE=pt_BR
</p>
ENABLE_ACCOUNT_SIGNUP=true
</p>
sudo systemctl restart chatwoot.target
</p>
Acesse: seudominio.com.br
</p>
Faça seu cadastro
</p>

<hr />

**Habilitando configurações ocultas do Chatwoot**

</p>
No banco de dados PostgreSQL
</p>
sudo -u postgres psql
</p>
\c chatwoot_production
</p>
update installation_configs set locked = false;
</p>
\q
</p>

<hr />

**NOMES CHATWOOT TERMOS E POLITICA DE PRIVACIDADE**

**Acesse super Admin**
</p>
https://seudominio.com.br/super_admin
</p>
Opção>installation_configs
</p>
LOGO
</p>
LOGO_THUMBNAIL
</p>
NOMES CHATWOOT:
</p>
Alterando nomes na plataforma
</p>
INSTALLATION_NAME
</p>
BRAND_NAME
</p>
TERMOS E POLITICA DE PRIVACIDADE
</p>
TERMS_URL
</p>
PRIVACY_URL
</p>
BRAND_URL
</p>
WIDGET_BRAND_URL

<hr />
<hr />

**Instalando CodeChat**

</p>
cd
</p>
sudo apt update && apt upgrade -y
</p>
git clone https://github.com/code-chat-br/whatsapp-api.git
</p>
cd whatsapp-api
</p>
cd src
</p>
mv dev-env.yml env.yml
</p>
nano env.yml
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
cd ..
</p>
npm i
</p>
npm run build
</p>
pm2 start 'npm run start' --name Codechat
</p>
sudo nano /etc/nginx/sites-available/codechat
</p>

```
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
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>

**EXECUTE COMANDO ABAIXO PARA NÃO CAIR QUANDO REINICIAR A VPS**

</p>
sudo pm2 startup ubuntu -u root && sudo pm2 startup ubuntu -u root --hp /root && sudo pm2 save
</p>
</p>

<hr />
<hr />

**Instalando Integrador**

</p>
cd
</p>
sudo apt update && apt upgrade -y
</p>
git clone https://github.com/w3nder/chatwoot-codechat
</p>
cd chatwoot-codechat
</p>
nano .env
</p>

 ```
PORT = 1234
CHATWOOT_ACCOUNT_ID = NUMEROCONTACHATWOOT
CHATWOOT_TOKEN = TOKENDOCHATWOOT
CHATWOOT_BASE_URL = https://chatwoot.seusite.com.br
CODECHAT_BASE_URL = https://codechat.seusite.com.br
CODECHAT_API_KEY = t8OOEeISKzpmc3jjcMqBWYSaJsafdefer
TOSIGN=true
IMPORT_MESSAGES_SENT=true
 ```

</p>
npm install pm2 -g
</p>
npm install
</p>
npm run build
</p>
pm2 start dist/app.js --name conector
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
</p>
EXECUTE COMANDO ABAIXO PARA NÃO CAIR QUANDO REINICIAR A VPS
</p>
sudo pm2 startup ubuntu -u root && sudo pm2 startup ubuntu -u root --hp /root && sudo pm2 save
</p>

<hr />
<hr />

**Conectando Caixa de Entrada**

</p>
WEBHOOK CHATWOOT:
</p>
Adicione essa url no seu Chatwoot
</p>
https://conector.site/webhook/chatwoot
</p>
Crie um contato chamado BOT
</p>
Adicione numero telefone ao mesmo
</p>
+123456
</p>
Chame contato BOT escreva 
</p>
/iniciar
</p>



**Pronto tudo Funcionando**




