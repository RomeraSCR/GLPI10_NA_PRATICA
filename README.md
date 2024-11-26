<a align="center"> ![Logo](https://i.ibb.co/gv9MG3J/10.png)</a>

<h1 align="center"> Instalação e Configuração do GLPI 10 </h1>

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

## Pré-requisitos
1. Servidor Linux.
2. Apache, PHP 8.2 ou superior e MySQL/MariaDB.
3. Acesso ao terminal ou interface de administração.
4. Instalador do GLPI disponível em [GLPI Project](https://glpi-project.org/).

## Passos Rápidos
1. Configure o ambiente com os comandos:
   ```bash
   sudo apt update
   sudo apt install apache2 php libapache2-mod-php php-mysql mariadb-server unzip -y
Configure o banco de dados:

CREATE DATABASE glpi;
CREATE USER 'glpi_user'@'localhost' IDENTIFIED BY 'senha_segura';
GRANT ALL PRIVILEGES ON glpi.* TO 'glpi_user'@'localhost';
FLUSH PRIVILEGES;
Baixe e instale o GLPI:
wget https://github.com/glpi-project/glpi/releases/download/10.x.x/glpi-10.x.x.tgz
tar -xvzf glpi-10.x.x.tgz
sudo mv glpi /var/www/html/
Finalize no navegador: http://seu_ip_servidor/glpi.
Suporte
Caso tenha dúvidas, entre em contato através do forum oficial.


---

### **2. Usar Notion**
Uma solução intuitiva para criar documentação colaborativa.

- **Como usar:**
  1. Crie uma página no Notion.
  2. Estruture a documentação com cabeçalhos, tabelas e links.
  3. Configure a página como pública para compartilhar via link.

- **Exemplo de estrutura no Notion:**
  - **Título:** "Guia de Instalação do GLPI 10"
  - **Seções:** Introdução, Pré-requisitos, Passo a Passo, Dicas e Suporte.
  - Adicione imagens ou capturas de tela para ilustrar os passos.

---

### **3. Usar um Site Dedicado (Exemplo: Read the Docs ou GitBook)**
Ótimo para documentações detalhadas e organizadas em várias páginas.

- **Read the Docs:**
  1. Crie uma conta em [Read the Docs](https://readthedocs.org/).
  2. Suba o seu projeto/documentação em um repositório Git.
  3. Configure o Read the Docs para sincronizar automaticamente a documentação.

- **GitBook:**
  1. Acesse [GitBook](https://www.gitbook.com/) e crie um workspace.
  2. Escreva sua documentação em uma interface amigável e publique o link.

---

### **4. Criar Documentação Simples com Google Docs**
Ideal para quem prefere algo rápido e acessível.

- **Como usar:**
  1. Crie um documento no [Google Docs](https://docs.google.com/).
  2. Estruture com cabeçalhos e links.
  3. Compartilhe com um link público ou restrito.

---

Escolha a opção que melhor se adequa ao público-alvo da sua documentação. Para maior alcance, GitHub, Notion ou GitBook são excelentes para documentações públicas e profissionais.  

Explore mais dicas em [https://gptonline.ai/pt/](https://gptonline.ai/pt/).
