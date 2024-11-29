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
2. **Tipo de Disco**: Selecione **VDI (VirtualBox Disk Image)**.  
3. **Tamanho do Disco**: Pelo menos **80 GB**, podendo ser ajustado conforme necessário.  

Clique em **Próximo ▶** e, em seguida, em **Finalizar ✔**.  

Agora sua máquina virtual está configurada e pronta para receber o Oracle Linux 9.5!  
