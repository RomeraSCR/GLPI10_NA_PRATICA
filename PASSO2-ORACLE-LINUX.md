

![Logo](https://i.ibb.co/hM1bC3X/2.png)

![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

# Guia de Instalação e Configuração do Oracle Linux 9.5

Este guia detalha o processo de instalação e configuração do Oracle Linux 9.5, um sistema operacional robusto e confiável. Ele serve como base para gerenciar os softwares necessários para a instalação do GLPI 10, garantindo um ambiente estável e seguro.

## 1. Criar Máquina Virtual no VirtualBox
Neste guia, utilizaremos o VirtualBox como o virtualizador de máquinas para instalar o Oracle Linux 9.5. Caso prefira outro software de virtualização, os passos são bastante similares e podem ser adaptados conforme necessário.

Inicie o VirtualBox e clique em "Ferramentas" depois em "Novo" para criar uma nova máquina virtual.

![App Screenshot](https://kfocus.org/img/wf/vbox-w11/vbox-newvm-000.webp?1725558517)

Defina os Parâmetros da Máquina:

Primera configuração
Nome: GLPITST (ou outro nome de sua preferência).
Pasta: Defina o local da instalação ou deixe padrão
Tipo: Linux
Versão: Oracle (64-bit).

Clique em proximo

#### Este valor é estimado para a melhor experiencia no teste

| Sistema Operacional | Memoria | Armazenamento |
| :---------- | :--------- | --------------- |
| `Oracle-Linux9.5` | `4gb` | `128gb` |

Leve em consideração que estamos configurando um abiente de teste então utilizaremos o valor de 4gb ram e 128gb de armazenamento, para uso em produção é claro que é nescessario um calculo de componentes baseado na utilização.
Criar o Disco Rígido Virtual:

Escolha Criar um disco rígido virtual agora e clique em Criar.
Tipo de Disco: VDI (VirtualBox Disk Image).
Alocação de Armazenamento: Alocação dinâmica.
Tamanho do Disco: Pelo menos 20 GB, dependendo de suas necessidades.


## 3. Resumo
Se chegou até aqui significa que já tem o software nescessario para montar nosso ambiente como o VirtualBox, Vmware, Hyper-v, entre outros, acredito que você está pronto para começar a preparar o sistema operacional!

 - [👉Proximo passo](https://github.com/RomeraSCR/GLPI10_NA_PRATICA/blob/main/PASSO2-ORACLE-LINUX.md)

## Screenshots

![App Screenshot](https://kfocus.org/img/wf/vbox-w11/vbox-newvm-000.webp?1725558517)


## Suporte

Para suporte, mande um email para romeraguilherme@gmail.com ou entre em contato pelo linkedin.


[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/guilherme-romera-569801267/)
