# ![Logo](https://i.ibb.co/wpjxtkf/glpi.png)  
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

# Guia de Instalação e Configuração do GLPI 10.0.17 

Este guia apresenta, de forma clara e detalhada, o processo de instalação e configuração do `GLPI 10.0.17.` O GLPI é um software open source amplamente utilizado para a gestão de ativos de TI, controle de chamados, inventário de hardware e software, além de outras funcionalidades que tornam a administração de infraestruturas de TI mais eficiente e organizada.

Com este manual, você terá todas as etapas necessárias para colocar o GLPI em funcionamento, desde os requisitos iniciais até as configurações avançadas, garantindo uma implementação bem-sucedida.

---

## 1. Acessar maquina criada no passo anterior 

Neste guia, utilizaremos o **Termius** como IDE para acesso ssh ao servidor Oracle Linux 9.5, Caso prefira outro software de acesso ssh, os passos são similares e podem ser adaptados conforme necessário.  

1. **Inicie o Termius**:  
   - Clique na **"Maquina-Virtual"** criada para iniciar a  conexão

## **Instalação do GLPI 10.0.17**  

### 1. **Acessar diretorio apache**

Navegue até o diretorio root do apache que é o `/var/www/html/`.

```bash
   cd /var/www/html/
```

### 2. **Dowload do GLPI**

Faça o dowload do GLPI mais atualizado no site oficial (https://glpi-project.org/downloads/).
Para baixar diretamente no oracle linux usaremos o comando wget link:

```bash
  sudo wget https://github.com/glpi-project/glpi/releases/download/10.0.17/glpi-10.0.17.tgz
```
Use o comando ls -lha para listar o diretorio:

```bash
  ls -lha
```

### 3. **Extrair pasta GLPI**

Faça o dowload do GLPI mais atualizado no site oficial (https://glpi-project.org/downloads/).
Para baixar diretamente no oracle linux usaremos o comando wget link:

```bash
  sudo tar -xvzf glpi-10.0.17.tgz
```
Use o comando rm para remover o arquivo tgz:

```bash
  sudo rm glpi-10.0.17.tgz
```
### 4. **Configurar permissões**

Atribua as permissões adequadas para o GLPI funcionar corretamente. Use os comandos abaixo para garantir que o servidor web (Apache) tenha acesso:

```bash
    sudo chown -R apache:apache /var/www/html/glpi
    sudo chmod -R 755 /var/www/html/glpi
```
Use o comando rm para remover o arquivo tgz:

```bash
  sudo rm glpi-10.0.17.tgz
```
### 5. **Configurar o Selinux**

Configurar caminho de instalação no Selinux

```bash
    sudo semanage fcontext -a -t httpd_sys_rw_content_t '/var/www/html/glpi(/.*)?'
    sudo restorecon -Rv /var/www/html/glpi/
```
Ative as dependencias:

```bash
    sudo getsebool httpd_can_network_connect
    sudo getsebool httpd_can_network_connect_db
    sudo getsebool httpd_can_sendmail
```

### 5. **Criar arquivo do Apache**

Crie o arquivo glpi.conf:

```bash
    sudo nano /etc/httpd/conf.d/glpi.conf
```

Exemplo de configuração disponibilizada pela GLPI-Project:

```bash
    <VirtualHost *:80>
        ServerName servername.localhost

        DocumentRoot /var/www/html/glpi/public

        # If you want to place GLPI in a subfolder of your site (e.g. your virtual host is serving multiple applications),
        # you can use an Alias directive. If you do this, the DocumentRoot directive MUST NOT target the GLPI directory itself.
        # Alias "/glpi" "/var/www/glpi/public"

        <Directory /var/www/html/glpi/public>
            Require all granted

            RewriteEngine On

            # Ensure authorization headers are passed to PHP.
            # Some Apache configurations may filter them and break usage of API, CalDAV, ...
            RewriteCond %{HTTP:Authorization} ^(.+)$
            RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

            # Redirect all requests to GLPI router, unless file exists.
            RewriteCond %{REQUEST_FILENAME} !-f
            RewriteRule ^(.*)$ index.php [QSA,L]
        </Directory>
    </VirtualHost>
```

No arquivo /var/www/html/glpi/.htaccess adicione:

```bash
    RewriteBase /
    RewriteEngine On
    RewriteCond %{REQUEST_URI} !^/public
    RewriteRule ^(.*)$ public/index.php [QSA,L]
```

E já podemos acessar o `http://ip-servidor` para prosseguir com a instalação

Siga o passo a passo até a configuração do banco de dados:

   - Servidor: `ip-do-servidor`
   - Usuario: `glpiuser`
   - Senha: (Senha definida na criação do usuario)

Selecione o banco de dados criado na instalação do MYSQL

Ao selecionar o banco de dados e clicar em concluir, aguardar que toda criação das tabelas sejam feitas com sucesso!

Usuario e senha para primeiro acesso:

   - Usuario:`glpi`
   - Senha:`glpi`
   - 
## Suporte

Para suporte, mande um email para romeraguilherme@gmail.com ou entre em contato pelo linkedin.


[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-romera-569801267/)
