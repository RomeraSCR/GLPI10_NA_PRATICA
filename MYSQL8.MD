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

```bash
sudo apt update && sudo apt upgrade -y
