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

Clique em **Próximo ▶** e, em seguida, em **Finalizar ✔**.  

### **Configurar a Rede da Máquina Virtual**

Para garantir que a máquina virtual possa se comunicar com o host ou acessar a rede externa, é necessário configurar corretamente o adaptador de rede no VirtualBox. Aqui estão as opções mais comuns:

---

### **1. Configuração em Modo NAT**  
O modo NAT (Network Address Translation) é a configuração padrão do VirtualBox e permite que a máquina virtual tenha acesso à internet por meio do host.  

1. **Abra as Configurações da Máquina Virtual**:  
   - No VirtualBox, selecione a máquina criada (`GLPITST`), clique em **Configurações** e depois na aba **Rede**.  

2. **Defina o Adaptador como NAT**:  
   - Certifique-se de que o **Adaptador 1** esteja habilitado e configurado como **NAT**.  

3. **Testar a Conexão**:  
   - Inicie a máquina virtual e teste a conexão com um comando como:
     ```bash
     ping google.com
     ```
   - Se o teste for bem-sucedido, sua máquina está conectada à internet.

---

### **2. Configuração em Modo Bridge**  
No modo Bridge, a máquina virtual será tratada como um dispositivo físico na mesma rede do host. Isso permite acesso direto a outros dispositivos na rede local.  

1. **Abra as Configurações da Máquina Virtual**:  
   - No VirtualBox, selecione a máquina criada (`GLPITST`), clique em **Configurações** e depois na aba **Rede**.  

2. **Defina o Adaptador como Bridge**:  
   - Altere o **Adaptador 1** para o modo **Bridge**.  
   - Selecione o adaptador de rede física do seu computador (por exemplo, Wi-Fi ou Ethernet).

3. **Configurar IP Dinâmico ou Estático**:  
   - **IP Dinâmico (DHCP)**: Por padrão, o DHCP atribuirá um endereço IP à máquina virtual.  
   - **IP Estático**: Configure manualmente o IP no Oracle Linux.  
     Edite o arquivo de configuração da interface de rede:
     ```bash
     sudo nano /etc/sysconfig/network-scripts/ifcfg-enp0s3
     ```
     Exemplo de configuração com IP estático:
     ```bash
     BOOTPROTO=none
     IPADDR=192.168.1.100
     NETMASK=255.255.255.0
     GATEWAY=192.168.1.1
     DNS1=8.8.8.8
     ONBOOT=yes
     ```
     Salve o arquivo e reinicie o serviço de rede:
     ```bash
     sudo systemctl restart network
     ```

4. **Testar a Conexão**:  
   - Verifique a conectivi.dade com outro dispositivo da rede ou com a internet.
   - Usando Comando `ping 8.8.8.8` Retorna a comunicação com o Google e Ao usar o `ifconfig` retorna as configurações da interface de rede.

---

### **Dica Final**  
- Escolha o modo de rede mais adequado ao seu cenário (NAT ou Bridge).  
- Para ambientes de produção, é recomendável usar **IPs estáticos** para evitar mudanças de endereço que possam afetar a conectividade.  

Sua máquina virtual agora está pronta para prosseguir com a instalação!

 - [👉Proximo passo](https://github.com/RomeraSCR/GLPI10_NA_PRATICA/blob/main/PASSO3-APACHE-PHP.md)


## Suporte

Para suporte, mande um email para romeraguilherme@gmail.com ou entre em contato pelo linkedin.


[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-romera-569801267/)
