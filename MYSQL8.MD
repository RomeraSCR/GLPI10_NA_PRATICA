# Instalação e Configuração do MySQL 8.1.0

Este guia cobre o processo de instalação e configuração do MySQL 8.1.0 em servidores Linux (Oracle/Ubuntu-Server). Ideal para projetos que exigem uma base de dados robusta e escalável.

---

## **Pré-requisitos**
1. **Servidor Linux Atualizado**: Oracle Linux, Ubuntu Server ou outra distribuição compatível.
2. **Acesso ao Terminal**: Via SSH usando ferramentas como **Putty**, **Termius** ou terminal nativo.
3. **Privilegios de root ou sudo** para executar comandos administrativos.

---

## **Passo a Passo**

### **1. Atualizar o Sistema**
Certifique-se de que o servidor está atualizado antes de instalar o MySQL.

```bash
sudo apt update && sudo apt upgrade -y

---
2. Adicionar o Repositório do MySQL
Baixe e configure o repositório oficial do MySQL para garantir a instalação da versão mais recente (8.1.0).

wget https://dev.mysql.com/get/mysql-apt-config_0.8.26-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.26-1_all.deb
Durante a configuração, selecione MySQL 8.1 no menu interativo.

---

Atualize o cache de pacotes:

sudo apt update

3. Instalar o MySQL 8.1
Após configurar o repositório, instale o MySQL com o comando:

sudo apt install mysql-server -y
4. Iniciar e Verificar o Serviço
Certifique-se de que o MySQL está ativo e funcionando.

sudo systemctl start mysql
sudo systemctl enable mysql
sudo systemctl status mysql
5. Configurar o MySQL (mysql_secure_installation)
Para garantir segurança, execute o assistente de configuração inicial:

sudo mysql_secure_installation
Configure uma senha forte para o usuário root.
Desative o acesso remoto do usuário root.
Remova o banco de dados de teste.
Recarregue as tabelas de privilégios.
6. Criar Banco de Dados e Usuário
Acesse o MySQL com o usuário root e crie o banco de dados e o usuário necessários para o seu projeto (exemplo: GLPI).

sudo mysql -u root -p
No prompt do MySQL, execute:

CREATE DATABASE glpi CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
CREATE USER 'glpi_user'@'localhost' IDENTIFIED BY 'sua_senha_forte';
GRANT ALL PRIVILEGES ON glpi.* TO 'glpi_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
7. Configurar o Firewall (Opcional)
Caso o MySQL precise ser acessado remotamente, permita conexões na porta padrão 3306.

No Ubuntu:

sudo ufw allow 3306
sudo ufw reload
Verificação da Instalação
Teste a conexão ao banco de dados:
mysql -u glpi_user -p
Certifique-se de que o banco de dados glpi está listado:
SHOW DATABASES;
Referências
Documentação Oficial do MySQL
GLPI Project
Este guia foi elaborado para simplificar a instalação e configuração do MySQL 8.1.0, permitindo que você inicie seus projetos rapidamente. Caso encontre problemas, não hesite em buscar ajuda na comunidade MySQL.
