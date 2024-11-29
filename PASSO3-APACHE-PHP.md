# ![Logo](https://i.ibb.co/hM1bC3X/2.png)  
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

# Guia de Instalação e Configuração do PHP8.2 e Apache 

Este guia detalha o processo de instalação e configuração do **PHP8.2 e Apache**, um dos softwares necessários para a instalação do **GLPI 10**, garantindo um ambiente estável e seguro.  

---

## 1. Acessar maquina criada no passo anterior 

Neste guia, utilizaremos o **Termius** como IDE para acesso ssh ao servidor Oracle Linux 9.5, Caso prefira outro software de acesso ssh, os passos são similares e podem ser adaptados conforme necessário.  

1. **Inicie o Termius**:  
   - Clique em **"New Host"** para criar um acesso a uma nova máquina virtual.  

  

2. **Defina os Parâmetros da Máquina**:  

   - **Adress**: `127.0.0.1` (ip definido para obter use `ifconfig`).  
   - **Label**: GLPITST (Nome de exibição)  
   - **username**: acessossh (Ou usuario definido na criação)  
   - **senha**: (Senha definida na criação anterior). 

   ![App Screenshot](https://i.ibb.co/Pw08007/Screenshot-2.jpg) 

   Clique em **Connect ▶**.

## **Instalação do PHP8.2**  

### 1. **Verificar os Repositórios Disponíveis:**

Primeiro, vamos verificar se os repositórios do Oracle Linux estão configurados corretamente para o PHP 8.2:

```bash
  sudo dnf repolist
```

### 2. **Habilitar o Repositório Remi:**

Se o repositório Remi não estiver habilitado, instale e habilite o repositório Remi para obter versões mais recentes do PHP:

```bash
    sudo dnf install -y dnf-utils
    sudo dnf install -y https://rpms.remirepo.net/enterprise/remi-release-9.rpm
```

### 3. **Agora, habilite o repositório Remi:**

```bash
    sudo dnf module enable php:remi-8.2 -y
```

### 4. **Instalar o PHP 8.2:**

```bash
    sudo dnf install -y php php-cli php-fpm php-mysqlnd php-xml php-mbstring php-json php-common php-gd php-imap php-curl php-zip php-soap php-intl php-opcache php-ldap php-imagick php-bcmath
```

### 5. **Verificar a Versão Instalável do PHP:**

```bash
    php -v
```

### 5. **Edite o arquivo `php.ini`**

```bash
    sudo nano /etc/php.ini
```

Faça as seguintes configurações 

```bash
    max_execution_time = 300
    upload_max_filesize = 100M
    post_max_size = 100M
    memory_limit = 512M
```

Após feito as alterações reinicie o PHP

```bash
    sudo systemctl restart php-fpm
```

---

## **Instalação do Apache**  

### 1. **Atualizar o Sistema**

Antes de instalar qualquer pacote, é sempre recomendável atualizar o sistema para garantir que você tenha as versões mais recentes de todos os pacotes.

```bash
  sudo dnf update -y
```

### 2. **Instalar o Apache (httpd)**

Para instalar o Apache no Oracle Linux 9.5, você pode usar o DNF, que é o gerenciador de pacotes padrão:

```bash
  sudo dnf install httpd -y
```

### 3. **Iniciar e Habilitar o Apache**

Após a instalação, inicie o serviço do Apache e configure-o para iniciar automaticamente ao inicializar o sistema.

```bash
    sudo systemctl start httpd
    sudo systemctl enable httpd
```

### 4. **Verificar o Status do Apache**

Verifique se o Apache está rodando corretamente:

```bash
    sudo systemctl status httpd
```

Se o Apache estiver ativo e em execução, você verá uma saída semelhante a esta:

```bash
    ● httpd.service - The Apache HTTP Server
   Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; vendor preset: disabled)
   Active: active (running) since Thu 2024-11-28 15:33:32 UTC; 1min 25s ago
     Docs: man:httpd.service(8)
 Main PID: 1385 (httpd)
   Status: "Started, listening on: port 80"
    Tasks: 213 (limit: 11544)
   Memory: 16.5M
   CGroup: /system.slice/httpd.service
           ├─1385 /usr/sbin/httpd -DFOREGROUND
           ├─1390 /usr/sbin/httpd -DFOREGROUND
           ├─1391 /usr/sbin/httpd -DFOREGROUND
           └─1392 /usr/sbin/httpd -DFOREGROUND
```

Tente acessar no navegador `http://ip-do-servidor` se a instalação tiver correta é para aparecer a pagina padrão Apache.
 
Seu servidor web está pronto para prosseguir com o proximo passo!

 - [👉Proximo passo](https://github.com/RomeraSCR/GLPI10_NA_PRATICA/blob/main/PASSO4-MYSQL-SERVER.md)


## Suporte

Para suporte, mande um email para romeraguilherme@gmail.com ou entre em contato pelo linkedin.


[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-romera-569801267/)
