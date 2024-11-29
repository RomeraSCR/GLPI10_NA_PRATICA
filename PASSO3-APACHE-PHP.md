# ![Logo](https://i.ibb.co/hM1bC3X/4.png)  
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
2. **Instalar o PHP 8.2 e seus módulos necessários**
```bash
   sudo dnf install -y php php-cli php-fpm php-mysqlnd php-xml php-mbstring php-json php-common php-gd php-imap php-curl php-zip php-soap php-intl php-opcache
```





### **Dica Importante no virtualbox**  
- para ter acesso ao usuario root utilize `su -` com a senha definida na instalação senha padrão `changeme`.  
- É recomendável que crie um novo usuario para acesso externo e utilize aplicativos ssh como (Putty/Termius).

### **Comandos para Criar usuario e alterar senha**

Crie um novo usuário: Substitua acessossh pelo nome que deseja dar ao usuário:

```bash
  adduser acessossh
```


Defina a senha para o novo usuário: Substitua acessossh pelo nome do usuário criado (Senha tem que satisfazer os padrões de segurança):
```bash
   passwd acessossh
```
     
Adicione o usuário ao grupo sudo: Isso permitirá que o usuário execute comandos administrativos:
```bash
   usermod -aG wheel acessossh
```

Verifique se o usuário foi adicionado corretamente ao grupo sudo:
```bash
   groups acessossh
```

Por final altere a senha do usuario root(Senha tem que satisfazer os padrões de segurança):
```bash
   passwd root
```

## **Configurar a Rede e acesso SSH**

Para garantir que a máquina virtual possa se comunicar com o host ou acessar a rede externa, é necessário configurar corretamente o adaptador de rede no VirtualBox. Aqui estão as opções mais comuns:

---
 
### **Configuração em Modo Bridge**  
No modo Bridge, a máquina virtual será tratada como um dispositivo físico na mesma rede do host. Isso permite acesso direto a outros dispositivos na rede local.  

### **Testar a Conexão**:  
   - Verifique a conectivi.dade com outro dispositivo da rede ou com a internet.
   - Usando Comando `ping 8.8.8.8` Retorna a comunicação com o Google e Ao usar o `ifconfig` retorna as configurações da interface de rede.

---

###  **Configurações Adicionais**

Faça acesso a maquina utilizando ssh com o usuario criado e ip da maquina para prosseguir com a ativação do firewall do Oracle linux

Iniciar e ativar o firewall do Oracle Linux:
```bash
sudo systemctl start firewalld
sudo systemctl enable firewalld
```

Liberar Porta 80 para HTTP (Apache):
```bash
   sudo firewall-cmd --zone=public --add-port=80/tcp --permanent
```
     
Liberar Porta 443 para HTTPS (Apache):
```bash
   sudo firewall-cmd --zone=public --add-port=443/tcp --permanent
```

Liberar Porta 3306 para MySQL/MariaDB:
```bash
   sudo firewall-cmd --zone=public --add-port=3306/tcp --permanent
```

Aplicar as Alterações no Firewalld:
```bash
   sudo firewall-cmd --reload
```

Verificar as Regras do Firewalld:
```bash
   sudo firewall-cmd --list-all
```

### **Dica Final**  
- Escolha o modo de rede mais adequado ao seu cenário (NAT ou Bridge).  
- Para ambientes de produção, é recomendável usar **IPs estáticos** para evitar mudanças de endereço que possam afetar a conectividade.  

Sua máquina virtual agora está pronta para prosseguir com a instalação!

 - [👉Proximo passo](https://github.com/RomeraSCR/GLPI10_NA_PRATICA/blob/main/PASSO3-APACHE-PHP.md)


## Suporte

Para suporte, mande um email para romeraguilherme@gmail.com ou entre em contato pelo linkedin.


[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-romera-569801267/)
