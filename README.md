# Wazuh - Instalação em amabiente Linux

Este documento descreve a instalação do Wazuh em ambiente Linux de forma manual e profissional, incluindo arquitetura e opção com Docker.

O Wazuh é uma solução SIEM utilizada para monitoramento de segurança, detecção de intrusão e análise de logs em tempo real.

---

# 🏗️ Arquitetura da Solução

A solução é composta por:

- Wazuh Server (Manager)
- Indexador (OpenSearch)
- Dashboard Web
- Agentes instalados nos endpoints

Fluxo:

Agente → Wazuh Manager → Indexador → Dashboard

---

# 🧰 Pré-requisitos

- Ubuntu Server 22.04+ ou equivalente
- Mínimo 8GB RAM (recomendado 16GB)
- CPU com 4 cores ou mais
- Acesso root/sudo
- Acesso à internet

---

# ⚙️ Atualização do sistema

```bash
sudo apt update && sudo apt upgrade -y
```

---

# 📦 Instalação de dependências

```bash
sudo apt install curl unzip wget apt-transport-https gnupg -y
```

---

# 🔐 Instalação do Wazuh (modo manual - enterprise)

## 1. Download do instalador

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh
chmod +x wazuh-install.sh
```

---

## 2. Instalação completa (modo distribuído simplificado)

```bash
sudo ./wazuh-install.sh -a
```

---

# 🌐 Acesso ao Dashboard

Após instalação:

```
https://IP_DO_SERVIDOR
```

---

# 🔑 Credenciais iniciais

- Usuário: admin  
- Senha: gerada automaticamente na instalação  

---

# 🖥️ Instalação do agente Linux

```bash
wget https://packages.wazuh.com/4.x/apt/pool/main/w/wazuh-agent/wazuh-agent.deb
```

```bash
sudo WAZUH_MANAGER='IP_DO_SERVIDOR' dpkg -i wazuh-agent.deb
```

```bash
sudo systemctl enable wazuh-agent
sudo systemctl start wazuh-agent
```

---

# 🧪 Validação

- Dashboard acessível via HTTPS  
- Agentes conectados  
- Logs sendo recebidos  
- Alertas ativos  

---

# 🐳 Versão Docker (Lab rápido)

## Instalação do Docker

```bash
sudo apt install docker.io docker-compose -y
sudo systemctl enable docker
sudo systemctl start docker
```

---

## Docker Compose (Wazuh Stack)

```yaml
version: '3.7'

services:
  wazuh:
    image: wazuh/wazuh:latest
    container_name: wazuh-manager
    ports:
      - "1514:1514"
      - "1515:1515"
      - "55000:55000"
```

---

## Subir ambiente

```bash
docker-compose up -d
```

---

# 📊 Conclusão

A solução Wazuh foi implantada com sucesso em ambiente Linux, incluindo opção manual e containerizada.

O ambiente está pronto para:

- monitoramento de segurança
- análise de logs
- detecção de ameaças
- integração com infraestrutura corporativa

---

# 🚀 Integração do laboratório

Este projeto faz parte de um ambiente completo de infraestrutura:

- GLPI (ITSM / chamados)
- Zabbix (monitoramento)
- Wazuh (segurança SIEM)
