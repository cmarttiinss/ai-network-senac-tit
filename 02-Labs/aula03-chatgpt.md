# 📘 Documentação Simplificada de Rede

## 🖥️ 1. Informações Gerais do Equipamento

| Item | Informação |
|------|------------|
| 🖥️ Nome do Computador | TIT0728100W11-1 |
| 🌐 Domínio DNS | senacsp.edu.br |
| 🔀 Tipo de Nó | Híbrido |
| 🚫 Roteamento IP | Desativado |
| 🚫 Proxy WINS | Desativado |

### 📄 Resumo
Este computador está conectado ao domínio institucional **senacsp.edu.br**, permitindo integração com os serviços corporativos da organização.

---

# 🌐 2. Adaptadores de Rede

## 🔹 Adaptador Principal (Rede Corporativa)

| Item | Informação |
|------|------------|
| 📌 Adaptador | Intel(R) Ethernet Connection (17) I219-LM |
| 🔗 Endereço MAC | D8-43-AE-E3-D0-CF |
| 📍 Endereço IP | 10.24.82.43 |
| 🧮 Máscara de Rede | 255.255.255.0 |
| 🚪 Gateway Padrão | 10.24.82.1 |
| ⚙️ DHCP | Habilitado |
| 🧭 Servidor DHCP | 10.24.40.190 |
| 🌎 DNS Primário | 10.24.40.190 |
| 🌎 DNS Secundário | 10.1.1.195 |
| 🌎 DNS Terciário | 10.1.1.242 |

### 📄 Resumo
Este é o adaptador responsável pela comunicação do computador com a rede corporativa. O endereço IP foi atribuído automaticamente pelo servidor DHCP e o acesso à internet ocorre através do gateway 10.24.82.1.

---

## 🔹 Adaptador Virtual (VirtualBox)

| Item | Informação |
|------|------------|
| 📌 Adaptador | VirtualBox Host-Only Ethernet Adapter |
| 🔗 Endereço MAC | 0A-00-27-00-00-08 |
| 📍 Endereço IP | 192.168.56.1 |
| 🧮 Máscara de Rede | 255.255.255.0 |
| ⚙️ DHCP | Desabilitado |
| 🚪 Gateway | Não configurado |

### 📄 Resumo
Este adaptador é utilizado exclusivamente para ambientes virtuais criados pelo VirtualBox. Ele não é utilizado para acesso à internet ou rede corporativa.

---

# 🛣️ 3. Rotas de Rede

## 🔹 Rota Principal

| Destino | Gateway |
|----------|----------|
| 🌍 Internet (0.0.0.0/0) | 10.24.82.1 |

### 📄 Resumo
Toda comunicação destinada a redes externas e internet é encaminhada para o gateway padrão 10.24.82.1.

---

## 🔹 Redes Locais Identificadas

| Rede | Finalidade |
|--------|-----------|
| 10.24.82.0/24 | Rede corporativa |
| 192.168.56.0/24 | Rede VirtualBox |
| 127.0.0.0/8 | Comunicação interna do sistema (Loopback) |

### 📄 Resumo
O equipamento possui acesso simultâneo à rede corporativa e a uma rede virtual utilizada para laboratórios ou máquinas virtuais.

---

# 🧭 4. Serviços de Nome (DNS)

| Item | Informação |
|------|------------|
| 🏢 Servidor DNS Principal | TIT-EDUDC01.senacsp.edu.br |
| 📍 IP DNS Principal | 10.24.40.190 |
| 🔎 Teste de Resolução | dns.google |
| 🌎 Resultado | 8.8.8.8 |

### 📄 Resumo
Os testes demonstram que o servidor DNS está funcionando corretamente e consegue traduzir nomes de sites para endereços IP.

---

# 📡 5. Testes de Conectividade

## 🔹 Teste para Google DNS (8.8.8.8)

| Métrica | Resultado |
|----------|-----------|
| 📤 Pacotes Enviados | 4 |
| 📥 Pacotes Recebidos | 4 |
| ❌ Perdas | 0% |
| ⚡ Latência Média | 4 ms |

### 📄 Resumo
A comunicação com a internet apresentou excelente desempenho, sem perda de pacotes.

---

## 🔹 Teste para google.com

| Métrica | Resultado |
|----------|-----------|
| 📤 Pacotes Enviados | 4 |
| 📥 Pacotes Recebidos | 4 |
| ❌ Perdas | 0% |
| ⚡ Latência Média | 4 ms |

### 📄 Resumo
Além do acesso à internet, a resolução de nomes DNS também está funcionando normalmente, permitindo acesso a sites utilizando seus nomes.

---

# 📋 6. Resumo Executivo

| Categoria | Situação |
|------------|-----------|
| 🖥️ Equipamento no domínio corporativo | ✅ Sim |
| 🌐 Comunicação com a rede corporativa | ✅ Operacional |
| 🌍 Acesso à internet | ✅ Operacional |
| 🔎 Resolução DNS | ✅ Operacional |
| 📡 Conectividade externa | ✅ Operacional |
| 🧪 Ambiente VirtualBox | ✅ Configurado |

## 🎯 Conclusão Geral

O computador encontra-se corretamente integrado à infraestrutura de rede da organização. Os testes realizados demonstram:

- ✅ Comunicação normal com a rede corporativa.
- ✅ Acesso à internet funcionando.
- ✅ Resolução de nomes DNS operacional.
- ✅ Nenhuma perda de pacotes identificada.
- ✅ Baixa latência de comunicação.
- ✅ Ambiente virtual disponível para laboratórios e testes.

Esta documentação foi elaborada com linguagem simplificada para facilitar a compreensão por profissionais não especializados em redes de computadores.
