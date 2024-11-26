Imagem carregada
Nem você sabe fechar um markdown kkk 

O ChatGPT disse:
Ah, percebi o problema! O erro ocorreu porque os blocos de código não foram devidamente encerrados com três backticks (```). Isso é essencial para que o Markdown interprete corretamente os blocos de código. Aqui está a correção:

# Instalação e Configuração do MySQL 8.1.0

Este guia cobre o processo de instalação e configuração do MySQL 8.1.0 em servidores Linux (Oracle/Ubuntu-Server). Ideal para projetos que exigem uma base de dados robusta e escalável.

---

## **Pré-requisitos**
1. **Servidor Linux Atualizado**: Oracle Linux, Ubuntu Server ou outra distribuição compatível.
2. **Acesso ao Terminal**: Via SSH usando ferramentas como **Putty**, **Termius** ou terminal nativo.
3. **Privilégios de root ou sudo** para executar comandos administrativos.

---

## **Passo a Passo**

### **1. Atualizar o Sistema**
Certifique-se de que o servidor está atualizado antes de instalar o MySQL.

#### Para distribuições baseadas no Debian/Ubuntu:
```bash
sudo apt update && sudo apt upgrade -y
Para distribuições baseadas no Red Hat (RHEL)/CentOS:
sudo yum update -y
