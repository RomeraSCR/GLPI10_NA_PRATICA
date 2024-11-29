# ![Logo](https://i.ibb.co/hM1bC3X/2.png)  
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

# Guia de Instalação e Configuração do Oracle Linux 9.5  

Este guia detalha o processo de instalação e configuração do **Oracle Linux 9.5**, um sistema operacional robusto e confiável. Ele serve como base para gerenciar os softwares necessários para a instalação do **GLPI 10**, garantindo um ambiente estável e seguro.  

---

## 1. Criar Máquina Virtual no VirtualBox  

Neste guia, utilizaremos o **VirtualBox** como virtualizador para instalar o Oracle Linux 9.5. Caso prefira outro software de virtualização, os passos são similares e podem ser adaptados conforme necessário.  

1. **Inicie o VirtualBox**:  
   - Clique em **"Ferramentas"** e, em seguida, em **"Novo"** para criar uma nova máquina virtual.  

   ![App Screenshot](https://kfocus.org/img/wf/vbox-w11/vbox-newvm-000.webp?1725558517)  

2. **Defina os Parâmetros da Máquina**:  

   - **Nome**: `GLPITST` (ou outro nome de sua preferência).  
   - **Pasta**: Escolha o local de instalação ou deixe o padrão.  
   - **Tipo**: Linux.  
   - **Versão**: Oracle (64-bit).  

   Clique em **Próximo ▶**.


3. **Defina os Parâmetros de usuario e senha**:  

   - **Usuario**: `vboxuser` (esse usuario é padrão considere mudar).  
   - **Senha**: `changeme` (senha padrão fornecida pelo virtualbox) 
   - **Nome do Servidor**: Padrão.  
   - **Nome do Dominio**: Padrão.

   Clique em **Próximo ▶**.

---

### **Configuração de Recursos**  

Para este guia, estamos configurando um ambiente de **teste**, então utilizaremos:  

- **Memória RAM**: **4 GB (4096 MB)**.  
- **Armazenamento**: **128 GB**.  
- **Processadores Lógicos**: Máximo disponível, respeitando os limites do host.  

**Nota**: Para um ambiente de **produção**, calcule os recursos necessários com base na carga de trabalho prevista.  

| Sistema Operacional | Memória | Armazenamento |  
|:--------------------|:--------|:--------------|  
| `Oracle-Linux9.5`   | `4 GB`  | `128 GB`      |  

---

### **Criar o Disco Rígido Virtual**  

1. Escolha **Criar um disco rígido virtual agora** e clique em **Criar**.   
2. **Tamanho do Disco**: Pelo menos **80 GB**, podendo ser ajustado conforme necessário.  

Clique em **Próximo ▶** e, em seguida, em **Finalizar ✔** Após feito isso a inicialização da maquina começara a instalação.   

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
