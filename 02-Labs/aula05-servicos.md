# 🖥️ Aula 05 — Serviços no Ubuntu Server

> Guia de referência rápida para gerenciamento do Apache e MySQL em ambiente Ubuntu.

---

## 📁 Document Root Padrão

Localização: `/var/www/html`

| Permissões       | Proprietário         | Tamanho | Última Modificação | Item             |
|------------------|----------------------|---------|--------------------|------------------|
| `drwxr-xr-x`    | www-data / www-data  | 4.0K    | Dec 04 08:49       | 📂 glpi           |
| `-rw-r--r--`     | root / root          | 11K     | Feb 14 00:30       | 📄 index.html     |
| `drwxrwsr-x`    | www-data / www-data  | 4.0K    | Feb 24 00:32       | 📂 outlawgames    |
| `drwxrwsr-x`    | www-data / www-data  | 4.0K    | Feb 24 00:33       | 📂 protectpetz    |
| `drwxrwsr-x`    | root / www-data      | 4.0K    | Feb 14 00:35       | 📂 senactit       |
| `drwxrwsr-x`    | www-data / www-data  | 4.0K    | May 21 01:00       | 📂 wp             |

---

## 🌐 Apache — Configuração de Sites

### Sites Disponíveis (`sites-available`)

| 📄 Arquivo de Configuração |
|---------------------------|
| `000-default.conf`        |
| `default-ssl.conf`        |

### ✅ Sites Ativos (`sites-enabled`)

| 📄 Arquivo de Configuração | Status     |
|---------------------------|------------|
| `000-default.conf`        | ✅ Ativo   |

---

## 📌 Document Roots Configurados

| 🔧 Arquivo de Configuração                              | 📁 Document Root              |
|---------------------------------------------------------|-------------------------------|
| `/etc/apache2/conf-available/glpi.conf`                 | `/var/www/html/glpi/public`   |
| `/etc/apache2/sites-available/000-default.conf`         | `/var/www/html`               |
| `/etc/apache2/sites-available/default-ssl.conf`         | `/var/www/html`               |

---

## ⚙️ Status Geral do Apache — Virtual Hosts

| Propriedade         | Valor                                  |
|---------------------|----------------------------------------|
| 🔌 VirtualHost `*:8888` | `localhost` → `/etc/apache2/conf-enabled/glpi.conf:16` |
| 🔌 VirtualHost `*:80`   | `localhost` → `/etc/apache2/sites-enabled/000-default.conf:1` |
| 📂 ServerRoot        | `/etc/apache2`                        |
| 📂 DocumentRoot      | `/var/www/html`                       |
| 📋 ErrorLog          | `/var/log/apache2/error.log`          |
| 🔒 PidFile           | `/var/run/apache2/apache2.pid`        |
| 👤 User              | `www-data` (id=33)                    |
| 👥 Group             | `www-data` (id=33)                    |

---

## 🗄️ MySQL — Comandos Essenciais

### 1️⃣ Conectar como Root

```bash
sudo mysql -u root -p
```

> 💡 Após a autenticação, o prompt mudará para `mysql>`

---

### 2️⃣ Listar Bancos de Dados

```sql
SHOW DATABASES;
```

**Saída esperada:**

| Database           |
|--------------------|
| information_schema |
| mysql              |
| performance_schema |
| sys                |
| seu_banco_aqui     |

---

### 3️⃣ Sair do MySQL

```sql
EXIT;
```

---

## 🗂️ Resumo de Comandos Rápidos

| 🔧 Ação                          | 💻 Comando                        |
|----------------------------------|-----------------------------------|
| Listar arquivos no document root | `ls -lh /var/www/html`            |
| Ver sites disponíveis            | `ls /etc/apache2/sites-available` |
| Ver sites ativos                 | `ls /etc/apache2/sites-enabled`   |
| Ver todos os document roots      | `grep -r "DocumentRoot" /etc/apache2` |
| Ver status do Apache             | `sudo apache2ctl -S`              |
| Conectar ao MySQL como root      | `sudo mysql -u root -p`           |
| Listar bancos de dados           | `SHOW DATABASES;`                 |
| Sair do MySQL                    | `EXIT;`                           |
