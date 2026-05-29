# 📘 Documentação da Máquina Virtual Ubuntu Server

## 🎯 Objetivo
Este documento apresenta uma visão simplificada da infraestrutura da máquina virtual Ubuntu Server utilizada no laboratório, com foco em facilitar a consulta por profissionais técnicos e não técnicos.

---

# 🖥️ 1. Informações Gerais do Servidor

## 📋 Identificação

| Item | Informação |
|--------|------------|
| Nome do Servidor | wslinux01 |
| Sistema Operacional | Ubuntu Server 24.04.4 LTS |
| Codinome | Noble |
| Tipo | Máquina Virtual |
| Plataforma de Virtualização | Oracle VirtualBox |

---

# 🏗️ 2. Infraestrutura

## 💻 Recursos de Processamento

| Recurso | Detalhe |
|----------|----------|
| Processador | Intel Core i7-14700K |
| CPUs Disponíveis | 2 vCPUs |
| Socket | 1 |
| Núcleos Utilizados | 2 |

### 📝 Observação
A máquina virtual utiliza apenas uma pequena parcela da capacidade do equipamento físico.

---

## 🧠 Memória

| Recurso | Valor |
|----------|--------|
| Memória Total | 3,8 GB |
| Em Uso | 1,3 GB |
| Disponível | 2,5 GB |
| Swap | 2 GB |

---

## 💾 Armazenamento

### Estrutura dos Discos

| Disco | Capacidade |
|---------|------------|
| Disco Virtual (sda) | 50 GB |
| Partição Boot | 2 GB |
| Partição Sistema | 48 GB |

### Utilização

| Item | Valor |
|--------|--------|
| Espaço Total | 47 GB |
| Utilizado | 11 GB |
| Livre | 35 GB |
| Uso Atual | 24% |

---

# 🌐 3. Rede

## 🔌 Interface de Rede

| Item | Informação |
|--------|------------|
| Interface Principal | enp0s3 |
| Método de Conexão | Bridge |
| DHCP | Habilitado |
| IPv4 Principal | 10.24.82.215 |
| Gateway | 10.24.82.1 |

---

## 🌍 DNS

| Servidor DNS |
|--------------|
| 8.8.8.8 |
| 8.8.4.4 |
| 10.24.40.190 |
| 10.1.1.195 |
| 10.1.1.242 |

### 🔎 Domínios de Pesquisa

- senac.br
- senacsp.edu.br

---

# 🏢 4. Topologia de Rede

## 🔗 Topologia Física

```text
Notebook/PC
     │
     ▼
Switch do Laboratório
     │
     ▼
Windows 11 (Host)
     │
Oracle VirtualBox
     │
     ▼
Ubuntu Server (VM)
```

## 🌐 Topologia Lógica

| Componente | Função |
|------------|---------|
| Switch | Comunicação da rede local |
| Windows 11 | Sistema hospedeiro |
| Ubuntu Server | Servidor virtualizado |
| Rede LAN | 10.24.82.0/24 |
| SSH | Acesso remoto TCP/22 |

### 📌 Observações

✅ A VM está na mesma rede do laboratório.

✅ Pode ser acessada diretamente pelo IP.

✅ Não utiliza NAT nem redirecionamento de portas.

✅ Necessário liberar a porta TCP 22 para acesso SSH.

---

# 🔐 5. Serviços Disponíveis

## 🌍 Serviços Web

| Serviço | Porta |
|----------|--------|
| Apache HTTP | 80 |
| Aplicação Web Secundária | 8888 |
| Tomcat | 8080 |

---

## 🗄️ Banco de Dados

| Serviço | Porta |
|----------|--------|
| MySQL | 3306 |
| MySQL X Protocol | 33060 |

---

## 📊 Monitoramento

| Serviço | Porta |
|----------|--------|
| Grafana | 3000 |
| Prometheus | 9091 |
| Node Exporter | 9100 |

---

## 🔑 Administração

| Serviço | Porta |
|----------|--------|
| SSH | 22 |

---

# ⚙️ 6. Serviços Ativos

## 🟢 Serviços Principais

| Serviço | Finalidade |
|----------|------------|
| Apache2 | Hospedagem Web |
| Tomcat 11 | Aplicações Java |
| MySQL | Banco de Dados |
| Grafana | Dashboards |
| Prometheus | Coleta de Métricas |
| Node Exporter | Métricas do Sistema |
| SSH | Administração Remota |
| Cron | Tarefas Agendadas |
| Rsyslog | Registro de Logs |

---

# 🔒 7. Segurança

## Controles Identificados

| Controle | Status |
|-----------|--------|
| SSH Ativo | ✅ |
| Firewall UFW | ✅ Habilitado |
| Atualizações Automáticas | ✅ Configuradas |
| Resolução DNS | ✅ Configurada |

### Recomendações

- Revisar periodicamente usuários com acesso SSH.
- Validar regras do firewall.
- Monitorar logs do sistema.
- Aplicar atualizações de segurança regularmente.

---

# 📦 8. Aplicações Instaladas

## Principais Componentes

| Categoria | Tecnologia |
|------------|------------|
| Sistema Operacional | Ubuntu 24.04 LTS |
| Servidor Web | Apache 2 |
| Aplicações Java | Tomcat 11 |
| Banco de Dados | MySQL |
| Monitoramento | Grafana |
| Monitoramento | Prometheus |
| Métricas | Node Exporter |
| Runtime JavaScript | Node.js |
| Linguagem Web | PHP 8.3 |

---

# 📈 9. Resumo Executivo

## Ambiente Atual

| Área | Situação |
|--------|-----------|
| Sistema Operacional | ✅ Operacional |
| Rede | ✅ Operacional |
| Armazenamento | ✅ Espaço Disponível |
| Banco de Dados | ✅ Ativo |
| Serviços Web | ✅ Ativos |
| Monitoramento | ✅ Ativo |
| Acesso Remoto | ✅ Disponível |

### Conclusão

O servidor Ubuntu está operacional, integrado à rede do laboratório através de Bridge, oferecendo serviços web, banco de dados, monitoramento e acesso remoto. O ambiente apresenta boa disponibilidade de recursos e estrutura adequada para atividades acadêmicas e laboratoriais.
