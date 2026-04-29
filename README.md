# Instalação do Wazuh em Ambiente Linux

Este documento descreve o passo a passo da instalação do Wazuh em ambiente Linux, utilizado para monitoramento de segurança, análise de logs e detecção de ameaças.

O Wazuh é uma plataforma SIEM open source utilizada para segurança e monitoramento de infraestrutura.

---

## 🧰 Pré-requisitos

Antes de iniciar, o servidor deve atender aos seguintes requisitos:

- Sistema Linux 64 bits (Ubuntu recomendado)
- Mínimo 4GB de RAM (ideal 8GB ou mais)
- Acesso root ou sudo
- Conexão com internet

---

## ⚙️ Atualização do sistema

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 📦 Download do instalador

```bash
curl -sO https://packages.wazuh.com/4.8/wazuh-install.sh
```

---

## 🔐 Permissão de execução

```bash
chmod +x wazuh-install.sh
```

---

## 🚀 Instalação do Wazuh

```bash
sudo ./wazuh-install.sh -a
```

---

## 🌐 Acesso ao painel

Após a instalação, acesse no navegador:

```
https://IP_DO_SERVIDOR
```

---

## 🔑 Credenciais iniciais

- Usuário: admin  
- Senha: gerada automaticamente durante a instalação  

---

## 📡 Instalação do agente Linux

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

## 🧪 Validação da instalação

A instalação será considerada concluída quando:

- Dashboard estiver acessível via navegador
- Agente estiver conectado ao servidor
- Logs estiverem sendo recebidos corretamente

---

## 📊 Conclusão

O Wazuh foi instalado com sucesso e está operacional para monitoramento de segurança e análise de eventos.

---

## 🚀 Portfólio

Este projeto faz parte de um laboratório de infraestrutura contendo:

- GLPI (ITSM / chamados)
- Zabbix (monitoramento)
- Wazuh (segurança / SIEM)
