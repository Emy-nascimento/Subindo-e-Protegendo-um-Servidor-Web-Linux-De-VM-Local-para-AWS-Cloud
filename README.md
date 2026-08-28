# Subindo-e-Protegendo-um-Servidor-Web-Linux-De-VM-Local-para-AWS-Cloud
# 🐧 linux webserver to aws cloud

## 📌 Objetivo
Projeto prático focado na instalação, configuração, hardening básico e análise de logs em um servidor web Linux (Ubuntu Server + Nginx), finalizando com o mapeamento equivalente para arquitetura em nuvem AWS.

---

## ⚙️ Parte 1: Implementação Local (VirtualBox + Ubuntu Server)

### 1. Comandos Utilizados na Configuração
- **Criação de Usuário e Permissões:**
  ```bash
  sudo adduser analista_soc
  sudo usermod -aG sudo analista_soc
