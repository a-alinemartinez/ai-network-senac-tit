Procedimento objetivo para **importar, ajustar e operar** sua VM no Oracle VM VirtualBox no Windows 11.

---

#Segue um procedimento direto e operacional para importar e preparar sua VM no Oracle VM VirtualBox no Windows 11.

---

# 🖥️ Importar imagem OVA (Ubuntu Server)

### 📥 1. Abrir o VirtualBox <br>

* Clique no menu Iniciar
* Abra **Oracle VM VirtualBox**

---

### 📦 2. Importar Appliance<br>

* Clique em **Arquivo** → **Importar Appliance**
* Clique em 📂 **Selecionar arquivo**
* Navegue até:

  ```
  Downloads\UbuntuServer-OnPremises.ova
  ```
* Clique em **Avançar**

---

### ⚙️ 3. Revisar configurações<br>

* Verifique:

  * Nome da VM
  * Memória RAM (não alterar, salvo orientação)
  * CPU (não alterar)
* Clique em **Importar**

⏳ Aguarde a conclusão (pode levar alguns minutos)

---

# 🌐 Configurar Rede em modo Bridge (Ponte)<br>

### 🔧 4. Abrir configurações da VM

* Selecione a VM importada
* Clique em **Configurações**

---

### 🌍 5. Ajustar adaptador de rede<br>

* Vá em **Rede**
* Em **Adaptador 1**:

Configure:

* ✔️ Marcar: **Habilitar Placa de Rede**
* 🔁 Conectado a: **Placa em modo Bridge**
* 📡 Nome: selecionar a placa de rede cabeada
  (Ex: *Ethernet*, *Realtek*, *Intel(R) Ethernet*)

---

### ⚠️ Observação importante<br>

* NÃO usar Wi-Fi
* Escolher a interface **cabeada do laboratório**

---

### 💾 6. Salvar

* Clique em **OK**

---

# ▶️ Iniciar a Máquina Virtual<br>

### 🚀 7. Executar a VM<br>

* Selecione a VM
* Clique em **Iniciar**

---

# 🔐 Acesso via SSH<br>

### 🖥️ 8. Identificar IP da VM

Dentro da VM, execute:

```bash
ip a
```

ou

```bash
hostname -I
```

Anote o IP (ex: `192.168.x.x`)

---

### 🌐 9. Conectar via SSH (no Windows)<br>

No terminal do Windows (Prompt ou PowerShell):

```bash
ssh usuario@IP
```

Exemplo:

```bash
ssh aluno@192.168.0.10
```

---

### 🔑 10. Autenticação<br>

* Digite a senha fornecida pelo professor
* Acesso liberado ✅

---

# ✅ Resultado esperado<br>

* VM rodando normalmente
* IP na mesma rede do laboratório
* Acesso remoto via SSH funcionando

---

# 🧠 Dica técnica (importante)<br>

O modo **Bridge** faz com que a VM:

* Receba IP do mesmo DHCP da rede local
* Seja visível como um computador real na rede

---

Se quiser, posso te ajudar a:

* Testar conectividade (ping/ssh)
* Resolver erro de rede
* Criar snapshot da VM para backup

Só me diga 👍


--- 

Segundo Prompt

Procedimento objetivo para **importar, ajustar e operar** sua VM no Oracle VM VirtualBox no Windows 11.

---

# 🧩 1. Importar a imagem OVA

📁 Arquivo: `Downloads\UbuntuServer-OnPremises.ova`

1. Abra o **VirtualBox**
2. **📂 Arquivo → Importar Appliance**
3. **📁 Escolher arquivo** → selecione o `.ova`
4. **➡️ Próximo**
5. Revise os parâmetros
6. **✅ Importar**

⏱️ Aguarde a criação da VM

---

# ⚙️ 2. Otimizar configurações (recomendado para seu hardware)

Seu host: **i7-14700K + 32 GB RAM + NVMe** → permite ajustes mais agressivos.

1. Selecione a VM → **⚙️ Configurações**

### 🔹 Sistema → Placa-mãe

* RAM: **8192 MB (8 GB)** ✔️ ideal para IA leve/labs
* Chipset: manter padrão (PIIX3)

### 🔹 Sistema → Processador

* CPU: **4 vCPUs** ✔️ (pode usar 6 se permitido)
* ✔️ Habilitar **PAE/NX**

### 🔹 Aceleração

* ✔️ VT-x/AMD-V ativo (normalmente automático)

---

### 🔹 Tela

* Memória de vídeo: **128 MB**
* (sem necessidade de 3D para servidor)

---

### 🔹 Armazenamento

* Controladora: SATA (padrão)
* ✔️ Marcar **SSD** (melhora I/O virtual)
* ✔️ “Usar cache de I/O do host” (se disponível)

---

# 🌐 3. Configurar rede (Bridge - Ponte)

1. **⚙️ Configurações → Rede**

### Adaptador 1:

* ✔️ Habilitar placa de rede
* 🔄 Modo: **Bridge Adapter**
* 🔽 Nome:

  * Escolher placa **Ethernet cabeada**
  * Exemplo:

    ```
    Intel(R) Ethernet Connection (I219-V)
    ```

📌 Não usar Wi-Fi no laboratório (evita falhas de DHCP)

---

# ▶️ 4. Iniciar a VM

1. Selecione a VM
2. Clique **▶️ Iniciar**
3. Aguarde boot do Ubuntu Server

---

# 🔍 5. Descobrir IP da VM

No terminal da VM:

```bash
hostname -I
```

ou:

```bash
ip a
```

📌 Exemplo:

```
192.168.1.150
```

---

# 🔐 6. Acesso SSH remoto

No host (Windows):

```bash
ssh usuario@IP_DA_VM
```

Exemplo:

```bash
ssh aluno@192.168.1.150
```

---

# 🧪 7. Validação rápida

✔️ Testar rede:

```bash
ping 192.168.1.150
```

✔️ Verificar SSH:

```bash
sudo systemctl status ssh
```

Se necessário:

```bash
sudo systemctl enable --now ssh
```

---

# ⚠️ Problemas comuns

### ❌ Sem IP

* Bridge apontando para interface errada
* Cabo desconectado
* DHCP da rede bloqueando

### ❌ SSH não conecta

* Serviço não iniciado
* Firewall da VM:

```bash
sudo ufw allow ssh
```

---

# 🧠 Recomendações técnicas (importante)

✔️ **Snapshots**

* Tire snapshot antes das aulas:

  ```
  Máquina → Tirar Snapshot
  ```

✔️ **Clonagem (se permitido)**

* Evita corromper a base original

✔️ **Não usar NAT para SSH em laboratório**

* Bridge é obrigatório para acesso direto

✔️ **Carga ideal para seu cenário**

* 4 vCPU + 8GB RAM = equilíbrio entre desempenho e estabilidade

---

# ✅ Conclusão

Sim — **vale a pena melhorar as configurações da VM** no seu caso.
Seu hardware suporta isso sem impacto no host e melhora:

* Tempo de resposta
* Execução de serviços
* Testes de IA e redes





| 🔹 Parâmetro        | 📌 Valor            | 📝 Observação                          |
|--------------------|-------------------|--------------------------------------|
| 🌐 Rede            | 10.24.82.0        | Identificação da rede                |
| 🖧 Máscara         | 255.255.255.0     | /24 (até 254 hosts)                  |
| 🚪 Gateway         | 10.24.82.1        | Roteador da rede                     |
| 🔎 DNS             | 10.24.40.190      | Servidor de nomes                    |
| 🖥️ IP Servidor     | 10.24.82.10       | Sugestão (IP fixo)                   |
| 📡 Broadcast       | 10.24.82.255      | Endereço de broadcast                |
| ⚠️ Faixa de Hosts  | 10.24.82.1 - 254  | Endereços válidos                    |



