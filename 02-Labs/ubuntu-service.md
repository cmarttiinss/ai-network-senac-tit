# 🖥️ Documentação do Servidor Ubuntu — 10.24.82.213

> **Classificação:** Uso Interno — Confidencial
> **Data:** Maio / 2026 | **Versão:** 1.0

---

# PARTE 1 — Inventário de Serviços Ativos

## 📋 Tabela Consolidada de Serviços e Portas

| Serviço | Descrição | Porta(s) | Protocolo | Acesso Externo |
|---|---|---|---|---|
| 🔒 **SSH** | Acesso remoto seguro ao servidor | `22` | TCP | ⚠️ Sim |
| 🌐 **Apache2** | Servidor web | `80`, `8888` | TCP | ⚠️ Sim |
| 📊 **Prometheus** | Coleta e monitoramento de métricas | `9091` | TCP | ⚠️ Sim |
| 📈 **Grafana** | Painel visual de monitoramento | `3000` | TCP | ⚠️ Sim |
| ☕ **Tomcat** | Servidor de aplicações Java | `8080` | TCP | ⚠️ Sim |
| 🗄️ **MySQL** | Banco de dados relacional | `3306`, `33060` | TCP | 🚨 Sim |
| 📡 **Node Exporter** | Exporta métricas do sistema para o Prometheus | `9100` | TCP | ✅ Interno |
| 🌍 **DNS local** | Resolução de nomes de rede | `53` | TCP/UDP | ✅ Interno |
| 🔌 **DHCP** | Gerenciamento de rede | `68` | UDP | ✅ Interno |

### ⚠️ Observações Importantes

| # | Observação |
|---|---|
| 1 | A porta **8888** está aberta no Apache2 — identificada como acesso ao **GLPI Help Desk**, mas não aparece como serviço registrado no sistema. |
| 2 | A porta **3306** do **MySQL** está exposta externamente — isso representa um **risco crítico** de segurança. |
| 3 | O **WordPress** não foi identificado nem como serviço nem como porta no levantamento, mas está presente na infraestrutura. |
| 4 | O **Node Exporter** (porta 9100) comunica-se apenas internamente com o Prometheus — comportamento correto. |

---

# PARTE 2 — Melhorias de Otimização e Hardening

> 🟥 **Alta** — Ação imediata | 🟨 **Média** — Curto prazo | 🟩 **Baixa** — Melhoria complementar

---

## 🔒 1. OpenSSH Server — Porta `22`

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 1.1 | Desabilitar login direto como root (`PermitRootLogin no`) | 🟥 Alta | Autenticação |
| 1.2 | Usar autenticação somente por chave SSH (`PasswordAuthentication no`) | 🟥 Alta | Autenticação |
| 1.3 | Alterar a porta padrão 22 para uma porta não convencional (ex.: `2222`) | 🟥 Alta | Exposição |
| 1.4 | Restringir acesso SSH por IP via firewall (UFW/iptables) | 🟥 Alta | Controle de Acesso |
| 1.5 | Instalar e configurar o **Fail2Ban** para bloquear IPs com tentativas repetidas | 🟥 Alta | Proteção |
| 1.6 | Limitar tentativas de login falhas (`MaxAuthTries 3`) | 🟥 Alta | Autenticação |
| 1.7 | Configurar timeout de inatividade (`ClientAliveInterval 300`) | 🟨 Média | Sessão |
| 1.8 | Usar somente SSH protocolo 2 (desabilitar versões legadas) | 🟥 Alta | Criptografia |
| 1.9 | Habilitar log detalhado de conexões para auditoria (`LogLevel VERBOSE`) | 🟨 Média | Auditoria |
| 1.10 | Revisar e remover contas de usuário com acesso SSH desnecessário | 🟨 Média | Governança |

---

## 🌐 2. Apache2 HTTP Server — Portas `80` e `8888`

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 2.1 | Habilitar **HTTPS** (TLS 1.2/1.3) e redirecionar todo HTTP para HTTPS | 🟥 Alta | Criptografia |
| 2.2 | Obter certificado SSL válido (ex.: **Let's Encrypt**) | 🟥 Alta | Criptografia |
| 2.3 | Desabilitar listagem de diretórios (`Options -Indexes`) | 🟥 Alta | Privacidade |
| 2.4 | Ocultar versão do Apache nos cabeçalhos (`ServerTokens Prod`) | 🟨 Média | Privacidade |
| 2.5 | Configurar cabeçalhos de segurança HTTP: `X-Frame-Options`, `HSTS`, `CSP` | 🟥 Alta | Proteção Web |
| 2.6 | Restringir a porta `8888` somente a IPs internos — ou fechar se não estiver em uso | 🟥 Alta | Exposição |
| 2.7 | Desabilitar módulos Apache não utilizados (`mod_status`, `mod_info`, `mod_autoindex`) | 🟨 Média | Superfície |
| 2.8 | Configurar limites de requisição para mitigar ataques DoS (`mod_evasive`) | 🟨 Média | Disponibilidade |
| 2.9 | Habilitar **ModSecurity** (WAF) para proteção contra SQL Injection e XSS | 🟥 Alta | Proteção Web |
| 2.10 | Confirmar que os processos Apache rodam com `www-data` sem privilégios elevados | 🟨 Média | Privilégio Mínimo |

---

## ☕ 3. Apache Tomcat Server — Porta `8080`

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 3.1 | Colocar o Tomcat atrás de um **proxy reverso** (Apache/Nginx) — nunca expor a porta 8080 diretamente | 🟥 Alta | Arquitetura |
| 3.2 | Desabilitar o **Tomcat Manager App** em produção ou restringi-lo a IPs internos | 🟥 Alta | Controle de Acesso |
| 3.3 | Alterar ou remover as **credenciais padrão** do Tomcat Manager (`admin/admin`, `tomcat/tomcat`) | 🟥 Alta | Autenticação |
| 3.4 | Desabilitar a porta de shutdown do Tomcat (`port="-1"` no `server.xml`) | 🟥 Alta | Exposição |
| 3.5 | Remover aplicações de exemplo padrão (`examples`, `ROOT`, `docs`) em produção | 🟨 Média | Superfície |
| 3.6 | Rodar o Tomcat com usuário dedicado sem privilégios de root (usuário `tomcat`) | 🟥 Alta | Privilégio Mínimo |
| 3.7 | Habilitar HTTPS via conector SSL ou via proxy reverso com terminação TLS | 🟥 Alta | Criptografia |
| 3.8 | Manter o Tomcat e as aplicações Java atualizadas | 🟨 Média | Atualização |
| 3.9 | Configurar cabeçalhos HTTP de segurança via proxy reverso | 🟨 Média | Proteção Web |
| 3.10 | Habilitar logging de acessos e erros para auditoria de incidentes | 🟨 Média | Auditoria |

---

## 🗄️ 4. MySQL Server — Portas `3306` e `33060`

> 🚨 **Atenção crítica:** as portas do MySQL estão expostas externamente. Isso deve ser corrigido com urgência.

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 4.1 | **Bloquear as portas 3306 e 33060 no firewall imediatamente** | 🟥 Alta | Firewall |
| 4.2 | Vincular o MySQL somente ao endereço local (`bind-address = 127.0.0.1`) | 🟥 Alta | Exposição |
| 4.3 | Remover acesso remoto do usuário root — acesso somente local ou via túnel SSH | 🟥 Alta | Autenticação |
| 4.4 | Criar usuários com permissões mínimas necessárias por aplicação | 🟥 Alta | Privilégio Mínimo |
| 4.5 | Executar `mysql_secure_installation` (remove usuários anônimos e banco de testes) | 🟥 Alta | Configuração |
| 4.6 | Utilizar senhas fortes e rotacioná-las periodicamente | 🟥 Alta | Autenticação |
| 4.7 | Configurar **backups automáticos diários** com testes periódicos de restauração | 🟥 Alta | Disponibilidade |
| 4.8 | Habilitar criptografia em trânsito entre aplicação e MySQL (SSL/TLS) | 🟨 Média | Criptografia |
| 4.9 | Habilitar logs de auditoria para registrar queries sensíveis e acessos administrativos | 🟨 Média | Auditoria |
| 4.10 | Manter o MySQL atualizado com os patches de segurança mais recentes | 🟨 Média | Atualização |

---

## 📈 5. Grafana Server — Porta `3000`

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 5.1 | **Alterar as credenciais padrão** `admin/admin` imediatamente | 🟥 Alta | Autenticação |
| 5.2 | Habilitar HTTPS ou colocar o Grafana atrás de proxy reverso com TLS | 🟥 Alta | Criptografia |
| 5.3 | Restringir acesso à porta `3000` somente a IPs da rede interna via firewall | 🟥 Alta | Controle de Acesso |
| 5.4 | Habilitar **autenticação multifator (MFA)** para usuários administradores | 🟥 Alta | Autenticação |
| 5.5 | Desabilitar registro público de novos usuários (`allow_sign_up = false`) | 🟥 Alta | Controle de Acesso |
| 5.6 | Desabilitar acesso anônimo (`auth.anonymous.enabled = false`) | 🟥 Alta | Autenticação |
| 5.7 | Configurar RBAC para limitar o que cada usuário pode visualizar | 🟨 Média | Privilégio Mínimo |
| 5.8 | Manter o Grafana atualizado (patches de segurança frequentes) | 🟨 Média | Atualização |
| 5.9 | Habilitar logs de auditoria para rastrear alterações em dashboards | 🟨 Média | Auditoria |
| 5.10 | Revisar e remover dashboards e usuários inativos periodicamente | 🟩 Baixa | Governança |

---

## 📊 6. Prometheus Server — Porta `9091`

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 6.1 | Restringir acesso à porta `9091` somente a IPs internos via firewall | 🟥 Alta | Controle de Acesso |
| 6.2 | Habilitar **autenticação básica** no Prometheus para proteger a interface web | 🟥 Alta | Autenticação |
| 6.3 | Configurar TLS para criptografar a comunicação com Grafana e demais clientes | 🟨 Média | Criptografia |
| 6.4 | Desabilitar endpoints de administração desnecessários da API | 🟨 Média | Superfície |
| 6.5 | Garantir que o Prometheus rode com usuário dedicado sem privilégios de root | 🟨 Média | Privilégio Mínimo |
| 6.6 | Configurar retenção de dados adequada (`--storage.tsdb.retention.time`) | 🟩 Baixa | Capacidade |
| 6.7 | Manter o Prometheus atualizado com correções de segurança | 🟨 Média | Atualização |
| 6.8 | Criar alertas de disponibilidade e uso de recursos para o próprio Prometheus | 🟩 Baixa | Disponibilidade |

---

## 📡 7. Node Exporter — Porta `9100` (somente local)

> ✅ **Status atual:** comunicação apenas interna entre Node Exporter e Prometheus — comportamento correto.

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 7.1 | Confirmar que a porta `9100` está **bloqueada externamente** no firewall | 🟥 Alta | Exposição |
| 7.2 | Configurar o Node Exporter para escutar somente no endereço local (`--web.listen-address=127.0.0.1:9100`) | 🟥 Alta | Configuração |
| 7.3 | Habilitar TLS e autenticação básica entre Prometheus e Node Exporter | 🟨 Média | Criptografia |
| 7.4 | Rodar com usuário dedicado `node_exporter` sem permissões de root | 🟨 Média | Privilégio Mínimo |
| 7.5 | Desabilitar coletores desnecessários para reduzir exposição de informações | 🟩 Baixa | Superfície |
| 7.6 | Manter o Node Exporter atualizado | 🟩 Baixa | Atualização |

---

## 🎫 8. GLPI Help Desk — Porta `8888` (via Apache2)

> ⚠️ **Observação:** O GLPI não aparece como serviço registrado no sistema — identificado apenas pela porta `8888` do Apache2. Deve ser documentado e auditado formalmente.

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 8.1 | **Documentar formalmente** a porta `8888` como sendo destinada ao GLPI | 🟥 Alta | Governança |
| 8.2 | Habilitar HTTPS — nunca operar um sistema de help desk via HTTP puro | 🟥 Alta | Criptografia |
| 8.3 | Restringir acesso à porta `8888` somente a IPs da rede interna ou via VPN | 🟥 Alta | Controle de Acesso |
| 8.4 | Manter o GLPI sempre atualizado (histórico de vulnerabilidades críticas em versões antigas) | 🟥 Alta | Atualização |
| 8.5 | Remover ou proteger o arquivo `install.php` após a instalação | 🟥 Alta | Configuração |
| 8.6 | Habilitar **MFA** para usuários administradores do GLPI | 🟥 Alta | Autenticação |
| 8.7 | Alterar o caminho padrão de acesso (trocar `/glpi` por outro caminho) | 🟨 Média | Obscuridade |
| 8.8 | Configurar backup automático do banco de dados utilizado pelo GLPI | 🟨 Média | Disponibilidade |
| 8.9 | Restringir permissões de arquivos e pastas do GLPI no servidor (`chmod 750`) | 🟨 Média | Sistema de Arquivos |
| 8.10 | Revisar perfis e permissões de usuários no GLPI (princípio do menor privilégio) | 🟨 Média | Privilégio Mínimo |

---

## 🌍 9. CMS WordPress — Porta `80` / `443` (via Apache2)

> ⚠️ **Observação:** O WordPress não foi identificado como serviço nem como porta no levantamento do sistema. Deve ser auditado e incluído formalmente no inventário de aplicações.

| # | Recomendação | Prioridade | Categoria |
|---|---|---|---|
| 9.1 | Garantir operação exclusiva via **HTTPS** — redirecionar todo HTTP para HTTPS | 🟥 Alta | Criptografia |
| 9.2 | Manter o núcleo do WordPress, temas e plugins **sempre atualizados** | 🟥 Alta | Atualização |
| 9.3 | Habilitar **2FA** para todos os usuários com perfil Administrador | 🟥 Alta | Autenticação |
| 9.4 | Proteger o arquivo `wp-config.php` com permissões restritivas (`chmod 400`) | 🟥 Alta | Sistema de Arquivos |
| 9.5 | Desabilitar o editor de arquivos pelo painel admin (`DISALLOW_FILE_EDIT = true`) | 🟥 Alta | Configuração |
| 9.6 | Instalar plugin de segurança (**Wordfence** ou **Sucuri**) para monitoramento e WAF | 🟥 Alta | Proteção Web |
| 9.7 | Limitar tentativas de login em `/wp-login.php` e considerar mudar o caminho de login | 🟥 Alta | Autenticação |
| 9.8 | Configurar **backups diários automáticos** (arquivos + banco), armazenados fora do servidor | 🟥 Alta | Disponibilidade |
| 9.9 | Remover temas e plugins inativos — mesmo desativados podem conter vulnerabilidades | 🟨 Média | Superfície |
| 9.10 | Bloquear o arquivo `xmlrpc.php` se não for necessário (vetor comum de ataques) | 🟨 Média | Exposição |
| 9.11 | Alterar o prefixo padrão das tabelas do banco de dados (padrão `wp_`) | 🟨 Média | Banco de Dados |
| 9.12 | Ocultar a versão do WordPress removendo a meta tag `generator` do HTML | 🟩 Baixa | Privacidade |

---

## 📌 Resumo de Prioridades por Serviço

| Serviço | 🟥 Alta | 🟨 Média | 🟩 Baixa | Total |
|---|---|---|---|---|
| 🔒 OpenSSH | 6 | 4 | 0 | 10 |
| 🌐 Apache2 | 5 | 5 | 0 | 10 |
| ☕ Tomcat | 5 | 5 | 0 | 10 |
| 🗄️ MySQL | 7 | 3 | 0 | 10 |
| 📈 Grafana | 6 | 3 | 1 | 10 |
| 📊 Prometheus | 2 | 4 | 2 | 8 |
| 📡 Node Exporter | 2 | 2 | 2 | 6 |
| 🎫 GLPI | 6 | 4 | 0 | 10 |
| 🌍 WordPress | 8 | 4 | 1 | 13 |
| **Total** | **47** | **34** | **6** | **87** |

---

> 📝 **Nota final:** As ações de Alta prioridade, especialmente o bloqueio das portas do MySQL, configuração de HTTPS, troca de credenciais padrão e instalação do Fail2Ban, devem ser tratadas com urgência. A segurança é um processo contínuo — recomenda-se revisão periódica desta documentação e varreduras regulares de vulnerabilidades.
