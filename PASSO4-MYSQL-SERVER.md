# ![Logo](https://i.ibb.co/GvFxS48/mysql.png)  
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

# Guia de Instalação e Configuração do MYSQL8 SERVER 

Este guia detalha o processo de instalação e configuração do **MYSQL8 SERVER**, um dos softwares necessários para a instalação do **GLPI 10**, garantindo um ambiente estável e seguro.  

---

## 1. Acessar maquina criada no passo anterior 

Neste guia, utilizaremos o **Termius** como IDE para acesso ssh ao servidor Oracle Linux 9.5, Caso prefira outro software de acesso ssh, os passos são similares e podem ser adaptados conforme necessário.  

1. **Inicie o Termius**:  
   - Clique na **"Maquina-Virtual"** criada para iniciar a  conexão

## **Instalação do MYSQL8 SERVER**  

### 1. **Atualizar o Sistema**

Antes de iniciar a instalação, é sempre recomendável atualizar o sistema para garantir que todos os pacotes e dependências estejam na versão mais recente.

```bash
  sudo dnf update -y
```

### 2. **Instalar o MySQL Server**

```bash
   sudo dnf install mysql-server -y
```

### 3. **Iniciar e Habilitar o MySQL**

```bash
   sudo systemctl start mysqld
   sudo systemctl enable mysqld
```
### 4. **Verificar o Status do MySQL**

```bash
   sudo systemctl status mysqld
```

### 5. **Obter a Senha Temporária do MySQL Root**

```bash
   sudo grep 'temporary password' /var/log/mysqld.log
```


### **Configurações necessárias**  

### 1. **Acessar o MySQL como usuário root**

Utilize a senha Temporária fornecida na instalação para o primeiro acesso se não tiver senha fornecida na log tenta sem senha.

```bash
  sudo mysql -u root -p
```

### 2. **Alterar senha do usuario root**

Lembre que as senhas devem atender os padrões de segurança fornecidos pelo software.

```bash
   ALTER USER 'root'@'localhost' IDENTIFIED BY 'Senha@master2025';
```

### 3. **Crie banco de dados Exemplo:**

```bash
   CREATE DATABASE glpibd;
```
### 4. **Criar um usuário para o GLPI Exemplo:**

```bash
   CREATE USER 'glpiuser'@'192.168.100.%' IDENTIFIED BY 'Senha@glpi2025';
```

### 5. **Obter a Senha Temporária do MySQL Root**

```bash
   GRANT ALL PRIVILEGES ON glpidb.* TO 'glpiuser'@'192.168.100.%';
```

### 6. **Aplicar as alterações de permissões:**

```bash
   FLUSH PRIVILEGES;
```

### 6. **Sair do MySQL:**

```bash
   EXIT;
```

---


Seu banco de dados está pronta para prosseguir com o proximo passo!

 - [👉Proximo passo](https://github.com/RomeraSCR/GLPI10_NA_PRATICA/blob/main/PASSO5-GLPI10.md)


## Suporte

Para suporte, mande um email para romeraguilherme@gmail.com ou entre em contato pelo linkedin.


[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-romera-569801267/)
