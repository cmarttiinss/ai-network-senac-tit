# Guia Prático – Importar a Máquina Virtual Ubuntu Server 22.04.4 LTS no Oracle VirtualBox 7.2

## Objetivo
Importar a imagem **UbuntuServer-OnPremises.ova**, configurar a rede em **Modo Bridge (Ponte)** utilizando a rede cabeada do laboratório e iniciar a máquina virtual para acesso remoto via **SSH**.

---

# 📥 Etapa 1 – Localizar a Imagem da Máquina Virtual

1. Acesse a pasta **Downloads** do Windows.
2. Verifique se o arquivo abaixo está disponível:

```text
UbuntuServer-OnPremises.ova
```

3. Não altere o nome do arquivo.

---

# 🖥️ Etapa 2 – Abrir o Oracle VirtualBox

1. Clique no menu **Iniciar**.
2. Procure por **Oracle VirtualBox**.
3. Abra o programa.

---

# 📦 Etapa 3 – Importar a Máquina Virtual

1. No VirtualBox clique em:

**Arquivo → Importar Appliance**

📁

2. Clique em **Selecionar Arquivo**.

3. Navegue até:

```text
Downloads\UbuntuServer-OnPremises.ova
```

4. Clique em **Abrir**.

5. Clique em **Próximo**.

6. Revise as configurações apresentadas.

7. Clique em **Concluir (Finish)**.

⏳ Aguarde a importação da máquina virtual.

---

# ⚙️ Etapa 4 – Configurar a Rede em Modo Bridge (Ponte)

1. Selecione a máquina virtual importada.

2. Clique em:

**Configurações (Settings)** ⚙️

3. Clique em **Rede (Network)**.

4. Verifique se o:

☑ Adaptador 1 está habilitado.

5. Em **Conectado a:** selecione:

```text
Placa em Modo Bridge (Bridged Adapter)
```

6. Em **Nome**, escolha a placa de rede cabeada do laboratório.

Exemplo:

```text
Intel Ethernet
Realtek PCIe GbE
```

7. Mantenha as demais configurações padrão.

8. Clique em **OK**.

✅ Rede configurada.

---

# ▶️ Etapa 5 – Iniciar a Máquina Virtual

1. Selecione a máquina virtual.

2. Clique em:

▶ **Iniciar (Start)**

3. Aguarde o carregamento do Ubuntu Server.

---

# 🌐 Etapa 6 – Verificar o Endereço IP

Após o login no Ubuntu, execute:

```bash
ip addr
```

ou

```bash
hostname -I
```

Exemplo de resultado:

```text
192.168.1.150
```

Anote o endereço IP exibido.

---

# 🔐 Etapa 7 – Testar o Serviço SSH

Verifique se o serviço SSH está ativo:

```bash
sudo systemctl status ssh
```

Status esperado:

```text
active (running)
```

---

# 💻 Etapa 8 – Acessar via SSH

No Windows:

1. Abra o **PowerShell**.

2. Execute:

```bash
ssh usuario@IP_DO_SERVIDOR
```

Exemplo:

```bash
ssh aluno@192.168.1.150
```

3. Digite a senha quando solicitada.

4. Confirme a chave SSH digitando:

```text
yes
```

5. Pressione **Enter**.

✅ Acesso remoto realizado com sucesso.

---

# ✅ Checklist Final

- ☑ Oracle VirtualBox aberto
- ☑ Arquivo UbuntuServer-OnPremises.ova localizado
- ☑ Máquina virtual importada
- ☑ Rede configurada em Bridge (Ponte)
- ☑ Adaptador conectado à rede cabeada
- ☑ Máquina virtual iniciada
- ☑ Endereço IP identificado
- ☑ Serviço SSH ativo
- ☑ Conexão SSH testada

---

## Resultado Esperado

Ao final da atividade a máquina virtual Ubuntu Server 22.04.4 LTS estará importada no Oracle VirtualBox 7.2, conectada à rede local do laboratório através do modo Bridge (Ponte) e pronta para acesso remoto utilizando SSH.
