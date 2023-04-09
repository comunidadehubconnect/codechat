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

**Instalando CodeChat**

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
</p>
sudo certbot --nginx
</p>
sudo service nginx restart
</p>

----------------------------------------------------------------------------

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
