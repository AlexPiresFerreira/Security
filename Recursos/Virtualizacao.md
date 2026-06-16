
# 🖥️ Virtualização

> **Tags:** #virtualizacao #hypervisor #vm #virtual-machine #type1 #type2 #vmware #virtualbox #kvm

---

## 📌 Visão Geral

**Virtualização** é a tecnologia que permite executar **múltiplos sistemas operacionais** em um único hardware físico, através de **máquinas virtuais (VMs)**.

🎯 **Objetivo:** Otimizar recursos de hardware, isolar ambientes e facilitar testes de segurança.

---

## 🏗️ Tipos de Hypervisors

### Type 1 - Native (Bare Metal)

**Descrição:** Hypervisor roda **diretamente no hardware**, sem sistema operacional host.

**Características:**
- ✅ **Melhor performance** (acesso direto ao hardware)
- ✅ Mais eficiente
- ✅ Usado em **ambientes corporativos** e **datacenters**
- ❌ Mais complexo de configurar

**Exemplos:**
- **VMware ESXi** (gratuito e pago)
- **Microsoft Hyper-V** (Windows Server)
- **Citrix XenServer**
- **KVM** (Kernel-based Virtual Machine - Linux)
- **Proxmox VE** (baseado em KVM, open source)

**Diagrama:**

┌─────────────────────────────────────┐ 
│    OS   │    OS   │    OS   │    OS   │    OS    │ 
├─────────────────────────────────────┤
│ Hypervisor (Type 1)                                   │
├─────────────────────────────────────┤
│ Hardware                                                   │
└─────────────────────────────────────┘


---

### Type 2 - Hosted

**Descrição:** Hypervisor roda **sobre um sistema operacional** host.

**Características:**
- ✅ **Fácil de instalar** e usar
- ✅ Ideal para **desenvolvimento** e **testes**
- ✅ Não requer hardware dedicado
- ❌ Performance inferior ao Type 1
- ❌ Overhead do SO host

**Exemplos:**
- **VirtualBox** (Oracle - gratuito, open source)
- **VMware Workstation** (pago)
- **VMware Player** (gratuito para uso pessoal)
- **Parallels Desktop** (macOS - pago)
- **QEMU** (open source)

**Diagrama:**


┌─────────────────────────────────────┐ 
│             OS │ OS │ OS │ OS │ OS                │
├─────────────────────────────────────┤ 
│ Hypervisor (Type 2)                                   │
├─────────────────────────────────────┤
│ Sistema Operacional Host                         │
├─────────────────────────────────────┤
│ Hardware                                                   │
└─────────────────────────────────────┘


---

## 🆚 Comparação Type 1 vs Type 2

| Característica | Type 1 (Bare Metal) | Type 2 (Hosted) |
|----------------|---------------------|-----------------|
| **Performance** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Facilidade** | ⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Custo** | $$$ | $ (muitos gratuitos) |
| **Uso** | Produção, datacenter | Desenvolvimento, testes |
| **Overhead** | Baixo | Médio/Alto |
| **Exemplos** | ESXi, Hyper-V, KVM | VirtualBox, VMware Workstation |

---

## 🛠️ VirtualBox (Type 2)

### Instalação

#### Windows/macOS
```

1. Baixar de: https://www.virtualbox.org/
2. Instalar executável
3. Instalar Extension Pack (USB 3.0, RDP, etc)

```
#### Linux (Ubuntu/Debian)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-5wvi6w1cu" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar repositório</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> add-apt-repository multiverse
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> update
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar VirtualBox</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> virtualbox virtualbox-ext-pack
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar instalação</span><span>
</span><span>vboxmanage </span><span class="token parameter" style="color:rgb(214, 222, 235)">--version</span><span>
</span></code></pre></div>

---

### Criar VM via GUI
```

1. VirtualBox > New
2. Nome: Kali-Linux
3. Tipo: Linux
4. Versão: Debian (64-bit)
5. RAM: 4096 MB
6. Disco: 50 GB (VDI, dinamicamente alocado)
7. Settings:
    - System > Processor: 2 CPUs
    - Display > Video Memory: 128 MB
    - Network > Adapter 1: NAT ou Bridged
8. Start > Selecionar ISO do Kali Linux

```
---

### Criar VM via CLI (vboxmanage)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9rtgr5bt4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar VM</span><span>
</span><span>vboxmanage createvm </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--ostype</span><span> Debian_64 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--register</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Configurar RAM e CPU</span><span>
</span><span>vboxmanage modifyvm </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--memory</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">4096</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--cpus</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar disco virtual (50 GB)</span><span>
</span><span>vboxmanage createhd </span><span class="token parameter" style="color:rgb(214, 222, 235)">--filename</span><span> ~/VirtualBox</span><span class="token" style="color:rgb(199, 146, 234)">\</span><span> VMs/Kali-Linux/Kali-Linux.vdi </span><span class="token parameter" style="color:rgb(214, 222, 235)">--size</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">51200</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar controlador SATA</span><span>
</span><span>vboxmanage storagectl </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;SATA Controller&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--add</span><span> sata </span><span class="token parameter" style="color:rgb(214, 222, 235)">--controller</span><span> IntelAhci
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Anexar disco</span><span>
</span><span>vboxmanage storageattach </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--storagectl</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;SATA Controller&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--port</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--device</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--type</span><span> hdd </span><span class="token parameter" style="color:rgb(214, 222, 235)">--medium</span><span> ~/VirtualBox</span><span class="token" style="color:rgb(199, 146, 234)">\</span><span> VMs/Kali-Linux/Kali-Linux.vdi
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar controlador IDE (para ISO)</span><span>
</span><span>vboxmanage storagectl </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;IDE Controller&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--add</span><span> ide
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Anexar ISO</span><span>
</span><span>vboxmanage storageattach </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--storagectl</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;IDE Controller&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--port</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--device</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--type</span><span> dvddrive </span><span class="token parameter" style="color:rgb(214, 222, 235)">--medium</span><span> ~/Downloads/kali-linux-2024.1-amd64.iso
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Configurar rede (NAT)</span><span>
</span><span>vboxmanage modifyvm </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--nic1</span><span> nat
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar VM</span><span>
</span><span>vboxmanage startvm </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span>
</span></code></pre></div>

---

### Configurações de Rede

#### NAT (Network Address Translation)
**Uso:** VM acessa internet através do host.

**Características:**
- ✅ VM acessa internet
- ❌ Host não acessa VM diretamente
- ❌ VMs não se comunicam entre si

---

#### Bridged (Ponte)
**Uso:** VM recebe IP da mesma rede do host.

**Características:**
- ✅ VM aparece como dispositivo separado na rede
- ✅ Host e outras máquinas podem acessar VM
- ✅ VMs se comunicam entre si

---

#### Host-Only
**Uso:** Rede isolada entre host e VMs.

**Características:**
- ✅ Host acessa VMs
- ✅ VMs se comunicam entre si
- ❌ VMs não acessam internet

---

#### Internal Network
**Uso:** Rede isolada apenas entre VMs.

**Características:**
- ✅ VMs se comunicam entre si
- ❌ Host não acessa VMs
- ❌ VMs não acessam internet

---

### Snapshots

**Função:** Salvar **estado atual** da VM para restaurar depois.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-v540arz4b" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar snapshot</span><span>
</span><span>vboxmanage snapshot </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> take </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Clean Install&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar snapshots</span><span>
</span><span>vboxmanage snapshot </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> list
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Restaurar snapshot</span><span>
</span><span>vboxmanage snapshot </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> restore </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Clean Install&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar snapshot</span><span>
</span><span>vboxmanage snapshot </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Kali-Linux&quot;</span><span> delete </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Clean Install&quot;</span><span>
</span></code></pre></div>

**Uso prático:**
```

1. Instalar SO limpo
2. Criar snapshot "Clean Install"
3. Instalar ferramentas
4. Criar snapshot "Tools Installed"
5. Fazer testes (pode quebrar)
6. Restaurar para "Tools Installed"

```
---

### Guest Additions

**Função:** Melhorar integração entre VM e host.

**Recursos:**
- Compartilhamento de clipboard
- Drag and drop de arquivos
- Pastas compartilhadas
- Melhor resolução de tela
- Melhor performance gráfica

**Instalação (Linux):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7m8uepr78" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inserir CD das Guest Additions (Devices &gt; Insert Guest Additions CD)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">mkdir</span><span> /mnt/cdrom
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">mount</span><span> /dev/cdrom /mnt/cdrom
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> /mnt/cdrom
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> ./VBoxLinuxAdditions.run
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">reboot</span><span>
</span></code></pre></div>

---

### Pastas Compartilhadas

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-66x6t1w2x" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar pasta compartilhada (VirtualBox GUI)</span><span>
</span><span>Settings </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> Shared Folders </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> Add
</span><span>  Folder Path: C:</span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>Users</span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>Usuario</span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>Compartilhado
</span>  Folder Name: compartilhado
<!-- -->  Auto-mount: ✓
<!-- -->  Make Permanent: ✓
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar na VM (Linux)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">usermod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-aG</span><span> vboxsf </span><span class="token environment" style="color:rgb(130, 170, 255)">$USER</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Logout e login novamente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> /media/sf_compartilhado/
</span></code></pre></div>

---

## 🐧 KVM (Type 1 - Linux)

### Instalação (Ubuntu/Debian)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-x3xi9mscn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar suporte a virtualização</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">egrep</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;(vmx|svm)&#x27;</span><span> /proc/cpuinfo
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Se &gt; 0, CPU suporta virtualização</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar KVM</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils virt-manager
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar usuário ao grupo libvirt</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">usermod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-aG</span><span> libvirt </span><span class="token environment" style="color:rgb(130, 170, 255)">$USER</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">usermod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-aG</span><span> kvm </span><span class="token environment" style="color:rgb(130, 170, 255)">$USER</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar instalação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> systemctl status libvirtd
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">virsh</span><span> list </span><span class="token parameter" style="color:rgb(214, 222, 235)">--all</span><span>
</span></code></pre></div>

---

### Criar VM com virt-manager (GUI)
```

1. Abrir virt-manager
2. File > New Virtual Machine
3. Selecionar ISO
4. RAM: 4096 MB
5. CPUs: 2
6. Disco: 50 GB
7. Finish

```
---

### Criar VM via CLI (virsh)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-kl2gb1njd" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar VM</span><span>
</span><span>virt-install </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> kali-linux </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  </span><span class="token parameter" style="color:rgb(214, 222, 235)">--ram</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">4096</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  </span><span class="token parameter" style="color:rgb(214, 222, 235)">--vcpus</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  </span><span class="token parameter" style="color:rgb(214, 222, 235)">--disk</span><span> </span><span class="token assign-left" style="color:rgb(214, 222, 235)">path</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>/var/lib/libvirt/images/kali.qcow2,size</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">50</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  --os-variant debian11 </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  </span><span class="token parameter" style="color:rgb(214, 222, 235)">--network</span><span> </span><span class="token assign-left" style="color:rgb(214, 222, 235)">bridge</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>virbr0 </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  </span><span class="token parameter" style="color:rgb(214, 222, 235)">--graphics</span><span> vnc </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>  </span><span class="token parameter" style="color:rgb(214, 222, 235)">--cdrom</span><span> /home/user/Downloads/kali-linux-2024.1-amd64.iso
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar VMs</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">virsh</span><span> list </span><span class="token parameter" style="color:rgb(214, 222, 235)">--all</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar VM</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">virsh</span><span> start kali-linux
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Conectar ao console</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">virsh</span><span> console kali-linux
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desligar VM</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">virsh</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">shutdown</span><span> kali-linux
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Forçar desligamento</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">virsh</span><span> destroy kali-linux
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar VM</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">virsh</span><span> undefine kali-linux
</span></code></pre></div>

---

## 🎯 Uso em Segurança da Informação

### Labs de Pentest

**Cenário típico:**
```

Host (Kali Linux físico ou VM) ├─ VM 1: Metasploitable 2 (vulnerável) ├─ VM 2: DVWA (vulnerável) ├─ VM 3: Windows 7 (vulnerável) └─ VM 4: pfSense (firewall)

```
**Rede isolada (Host-Only):**
```

192.168.56.0/24 ├─ 192.168.56.1 (Host - Kali) ├─ 192.168.56.10 (Metasploitable) ├─ 192.168.56.20 (DVWA) └─ 192.168.56.30 (Windows 7)

```
---

### Análise de Malware

**Sandbox isolado:**
```

1. Criar VM Windows limpa
2. Criar snapshot "Clean"
3. Desabilitar rede (ou usar Host-Only)
4. Executar malware
5. Analisar comportamento (Process Monitor, Wireshark)
6. Restaurar snapshot "Clean"

```
---

### Blue Team / SOC

**Ambiente de detecção:**
```

Host ├─ VM 1: SIEM (Splunk, ELK) ├─ VM 2: Windows Server (AD) ├─ VM 3: Windows 10 (endpoint com agent) └─ VM 4: Kali (atacante simulado)

```
---

## 🔗 Links Relacionados

- [[Docker]]
- [[Labs-CTF]]
- [[Kali-Linux]]
- [[Metasploitable]]

---

## 📚 Referências

- VirtualBox: [virtualbox.org](https://www.virtualbox.org/)
- KVM: [linux-kvm.org](https://www.linux-kvm.org/)
- Proxmox: [proxmox.com](https://www.proxmox.com/)
- VMware: [vmware.com](https://www.vmware.com/)
