# Terminal Commands for fullstack course



## install commands

`sudo amazon-linux-extras install nginx1.12`: install nginx

`sudo amazon-linux-extras install postgresql9.6`: install psql

`sudo yum install git`: install git 

`sudo curl https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash`: install nvm

`npm install pm2 -g`: install pm2 globally 


## Basic commands
`sudo nano`: The text editor used in the Linux AMI 2.   

`sudo rm name-of-directory`: remove directory 

`cd name-of-directory`: change to directory

`ssh i- “keypair.pem” ec2-user@public-ip-address`: ssh into linux instance.  

`sudo chmod 777`: give write permission to directory

`ls`: list files and folders in pwd

`pwd`: present working directory


## npm/node commands
`node -v`: node version

`npm -v`: npm version 

`nvm -v`: node version manager version  

`nvm ls remote`: node versions available for download 


## pm2 commands


`pm2 list`: list all running processes

`pm2 stop app 0`: stop app with id 0 

`pm2 delete app 0`: delete app with id 0 

`pm2 restart app 0`: restart app with id 0 

`pm2 start app.js -i max`: start app.js with max number of threads available


## nginx commands

`sudo systemctl restart nginx`: Restart nginx. After you modify the nginx.conf file you will need to restart nginx using this command otherwise your updates will not take place 

`sudo nano nginx.conf`: edit nginx file

`sudo nano /var/log/nginx/error.log`: access error log

`sudo nginx -t`: test nginx

```
    server {
        listen       80 default_server;
        listen       [::]:80 default_server;
        server_name  localhost;


        # Load configuration files for the default server block.
        include /etc/nginx/default.d/*.conf;

        location / {
                root /react-prod5/build;
                index index.html;                
                try_files $uri /index.html;

        }

        location /api/ {
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Host $http_host;
                proxy_set_header X-NginX-Proxy true;
                proxy_pass http://10.0.1.187:3000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;

        }
```
