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

### 1. **Atualizar o Sistema**

Primeiro, atualize os repositórios do sistema e os pacotes instalados:

```bash
  sudo dnf update -y
```

### 2. **Instalar o PHP 8.2 e seus módulos necessários**

```bash
   sudo dnf install -y php php-cli php-fpm php-mysqlnd php-xml php-mbstring php-json php-common php-gd php-imap php-curl php-zip php-soap php-intl php-opcache
```





### **Dica Importante no virtualbox**  
- para ter acesso ao usuario root utilize `su -` com a senha definida na instalação senha padrão `changeme`.  
- É recomendável que crie um novo usuario para acesso externo e utilize aplicativos ssh como (Putty/Termius).


---

###  **Configurações Adicionais**

Faça acesso a maquina utilizando ssh com o usuario criado e ip da maquina para prosseguir com a ativação do firewall do Oracle linux


### **Dica Final**  
- Escolha o modo de rede mais adequado ao seu cenário (NAT ou Bridge).  
- Para ambientes de produção, é recomendável usar **IPs estáticos** para evitar mudanças de endereço que possam afetar a conectividade.  

Sua máquina virtual agora está pronta para prosseguir com a instalação!

 - [👉Proximo passo](https://github.com/RomeraSCR/GLPI10_NA_PRATICA/blob/main/PASSO3-APACHE-PHP.md)


## Suporte

Para suporte, mande um email para romeraguilherme@gmail.com ou entre em contato pelo linkedin.


[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-romera-569801267/)
