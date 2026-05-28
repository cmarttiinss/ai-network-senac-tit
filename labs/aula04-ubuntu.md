# 📘 Documentação da Máquina Virtual Ubuntu

## 🎯 Visão Geral

Este documento apresenta um resumo da máquina virtual **wslinux01**, organizado de forma simples e visual para facilitar consultas rápidas.

---

# 🖥️ 1. Informações Gerais do Servidor

## 📂 Identificação

| Item | Informação |
|--------|------------|
| Nome do servidor | wslinux01 |
| Sistema Operacional | Ubuntu 24.04.4 LTS |
| Codinome | Noble |
| Tipo | Servidor Linux |
| Status Geral | ✅ Operacional |

---

# ⚙️ 2. Recursos de Hardware

## 🧠 Processador

| Item | Valor |
|--------|--------|
| Modelo | Intel Core i7-14700K |
| CPUs Disponíveis | 2 |
| Soquetes | 1 |
| Núcleos Utilizados | 2 |

### Observação
💡 Ambiente adequado para laboratórios, testes e aplicações de pequeno porte.

---

## 💾 Memória

| Item | Valor |
|--------|--------|
| Memória Total | 3,8 GB |
| Em Uso | 1,3 GB |
| Livre | 1,5 GB |
| Disponível | 2,5 GB |
| Swap | 2,0 GB |
| Uso da Swap | 0% |

### Status
✅ Consumo de memória dentro da normalidade.

---

# 💽 3. Armazenamento

## 📦 Estrutura de Disco

| Disco | Tamanho |
|---------|----------|
| sda | 50 GB |

### Partições

| Partição | Função | Tamanho |
|------------|----------|----------|
| sda1 | Sistema | 1 MB |
| sda2 | Boot | 2 GB |
| sda3 | Dados do sistema | 48 GB |

---

## 📊 Utilização

| Ponto de Montagem | Tamanho | Utilizado | Livre | Uso |
|------------------|----------|-----------|--------|------|
| / | 47 GB | 11 GB | 35 GB | 24% |
| /boot | 2 GB | 200 MB | 1,6 GB | 11% |

### Status
✅ Espaço em disco com ampla capacidade disponível.

---

# 🌐 4. Rede

## 🔌 Interface de Rede

| Interface | Status |
|------------|----------|
| enp0s3 | ✅ Ativa |

### Endereços IP Identificados

| Tipo | Endereço |
|--------|------------|
| Principal | 10.24.82.215 |
| Secundário | 10.24.82.47 |
| Outro registro identificado | 10.24.82.213 |

---

## 🚪 Gateway

| Configuração | Valor |
|-------------|--------|
| Gateway Padrão | 10.24.82.1 |

---

## 🌍 DNS

| Serviço | Endereço |
|----------|------------|
| DNS Google | 8.8.8.8 |
| DNS Google | 8.8.4.4 |
| DNS Interno | 10.24.40.190 |
| DNS Interno | 10.1.1.195 |
| DNS Interno | 10.1.1.242 |

### Domínios de Pesquisa

- senac.br
- senacsp.edu.br

---

# 🔐 5. Serviços Disponíveis

## 🌍 Serviços Web

| Serviço | Porta | Status |
|-----------|---------|----------|
| Apache | 80 | ✅ Ativo |
| Apache Alternativo | 8888 | ✅ Ativo |
| Tomcat 11 | 8080 | ✅ Ativo |

---

## 🗄️ Banco de Dados

| Serviço | Porta | Status |
|-----------|---------|----------|
| MySQL | 3306 | ✅ Ativo |
| MySQL X Protocol | 33060 | ✅ Ativo |

---

## 📈 Monitoramento

| Serviço | Porta | Finalidade |
|-----------|---------|-------------|
| Grafana | 3000 | Dashboards |
| Prometheus | 9091 | Coleta de métricas |
| Node Exporter | 9100 | Métricas do servidor |

---

## 🔒 Administração Remota

| Serviço | Porta |
|-----------|---------|
| SSH | 22 |

### Status
✅ Acesso remoto habilitado.

---

# 🔧 6. Configuração de Rede

## 📋 Resumo

| Configuração | Valor |
|--------------|--------|
| DHCP IPv4 | Habilitado |
| DHCP IPv6 | Desabilitado |
| IP Configurado | 10.24.82.215/24 |
| Gateway | 10.24.82.1 |
| DNS Preferencial | 8.8.8.8 |
| DNS Secundário | 8.8.4.4 |

---

# 🚀 7. Serviços do Sistema

## ✅ Serviços Ativos

- Apache Web Server
- MySQL
- Tomcat 11
- Grafana
- Prometheus
- Node Exporter
- SSH
- Cron
- Syslog
- Network Manager
- Resolved DNS
- Timesync

### Avaliação

🟢 Todos os serviços principais encontram-se ativos.

---

# 🛡️ 8. Segurança e Atualizações

## Atualizações Automáticas

| Item | Situação |
|---------|-----------|
| Unattended Upgrades | ✅ Ativado |
| Atualizações Pendentes | Sim |
| Verificação de Segurança | Ativa |

### Pacotes identificados para atualização

- vim
- vim-common
- vim-runtime
- vim-tiny
- xxd
- libgcrypt20

---

# 📌 9. Resumo Executivo

| Categoria | Situação |
|------------|------------|
| Sistema Operacional | 🟢 Saudável |
| Processador | 🟢 Normal |
| Memória | 🟢 Normal |
| Disco | 🟢 Espaço disponível |
| Rede | 🟢 Operacional |
| Banco de Dados | 🟢 Ativo |
| Serviços Web | 🟢 Ativos |
| Monitoramento | 🟢 Ativo |
| Segurança | 🟡 Existem atualizações pendentes |

---

## ✅ Conclusão

A máquina virtual encontra-se operacional, com recursos adequados para atividades de laboratório e aplicações de infraestrutura. Os principais serviços de rede, banco de dados, monitoramento e acesso remoto estão ativos. A única recomendação imediata é realizar a atualização dos pacotes pendentes para manter o ambiente atualizado e seguro.
