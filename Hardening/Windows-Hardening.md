
# 🪟 Windows Hardening (Fortalecimento de Segurança)

> **Tags:** #windows #hardening #security #baseline #cis-benchmark #group-policy

---

## 📌 Visão Geral

**Windows Hardening** é o processo de fortalecer a segurança do sistema operacional Windows através da **configuração segura**, **remoção de funcionalidades desnecessárias** e **aplicação de controles de segurança**.

🎯 **Objetivo:** Reduzir a superfície de ataque e minimizar vulnerabilidades.

---

## 🎯 Princípios de Hardening

### 1. Least Privilege (Menor Privilégio)
Usuários e processos devem ter apenas as permissões **mínimas necessárias**.

### 2. Defense in Depth (Defesa em Profundidade)
Múltiplas camadas de segurança.

### 3. Secure by Default
Configurações seguras desde a instalação.

### 4. Minimize Attack Surface
Desabilitar serviços e funcionalidades não utilizadas.

---

## 🔧 Hardening Básico

### 1️⃣ Atualizações e Patches

#### Windows Update

powershell

##### Verificar atualizações disponíveis

Get-WindowsUpdate

##### Instalar todas as atualizações

Install-WindowsUpdate -AcceptAll -AutoReboot

##### Configurar Windows Update (GPO)

Computer Configuration > Administrative Templates > Windows Components > Windows Update ☑ Configure Automatic Updates: Enabled ☑ Auto download and schedule the install


---

#### WSUS (Windows Server Update Services)
**Para ambientes corporativos:**
```

Servidor WSUS centralizado ↓ Distribui atualizações aprovadas ↓ Clientes Windows

```
---

### 2️⃣ Antivírus e Antimalware

#### Windows Defender
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wv6uohtno" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar status</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-MpComputerStatus</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar definições</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Update-MpSignature</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan completo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Start-MpScan</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ScanType FullScan
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Configurar proteção em tempo real</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-MpPreference</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DisableRealtimeMonitoring </span><span class="token" style="color:rgb(255, 88, 116)">$false</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar proteção contra ransomware (Controlled Folder Access)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-MpPreference</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>EnableControlledFolderAccess Enabled
</span></code></pre></div>

**Configurações recomendadas (GPO):**
```

Computer Configuration > Administrative Templates > Windows Components > Windows Defender Antivirus ☑ Turn off Windows Defender Antivirus: Disabled ☑ Real-time Protection: Enabled ☑ Behavior Monitoring: Enabled ☑ Cloud-delivered Protection: Enabled

```
---

### 3️⃣ Firewall

#### Windows Firewall
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-eq7srbaoy" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar status</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-NetFirewallProfile</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar firewall em todos os perfis</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-NetFirewallProfile</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Profile Domain</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Public</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Private </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Enabled True
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bloquear conexões de entrada por padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-NetFirewallProfile</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Profile Domain</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Public</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Private </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DefaultInboundAction Block
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir conexões de saída por padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-NetFirewallProfile</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Profile Domain</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Public</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Private </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DefaultOutboundAction Allow
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar regra de firewall</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-NetFirewallRule</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DisplayName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Bloquear Telnet&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Direction Inbound `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Protocol TCP `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>LocalPort 23 `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Action Block
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar regras ativas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-NetFirewallRule</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Where-Object</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(214, 222, 235)">$_</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Enabled </span><span class="token" style="color:rgb(127, 219, 202)">-eq</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;True&quot;</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

### 4️⃣ Contas de Usuário

#### Desabilitar Conta Administrator
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2ajus4oxn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar conta Administrator padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Disable-LocalUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Administrator&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Renomear conta Administrator</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Rename-LocalUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Administrator&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>NewName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Admin_Oculto&quot;</span><span>
</span></code></pre></div>

---

#### Desabilitar Conta Guest
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0j22cpfnt" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">Disable-LocalUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Guest&quot;</span><span>
</span></code></pre></div>

---

#### Política de Senhas Fortes
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-mxxg7zwt4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Via GPO</span><span>
</span>Computer Configuration &gt; Windows Settings &gt; Security Settings &gt; Account Policies &gt; Password Policy
<!-- -->
<!-- -->Configurações recomendadas:
<!-- -->  ☑ Enforce password history: 24 passwords
<!-- -->  ☑ Maximum password age: 90 days
<!-- -->  ☑ Minimum password age: 1 day
<!-- -->  ☑ Minimum password length: 14 characters
<!-- -->  ☑ Password must meet complexity requirements: Enabled
<span>  ☑ Store passwords </span><span class="token" style="color:rgb(127, 219, 202)">using</span><span> reversible encryption: Disabled
</span></code></pre></div>

---

#### Account Lockout Policy
```

Computer Configuration > Windows Settings > Security Settings > Account Policies > Account Lockout Policy

Configurações recomendadas: ☑ Account lockout duration: 30 minutes ☑ Account lockout threshold: 5 invalid attempts ☑ Reset account lockout counter after: 30 minutes

```
---

### 5️⃣ User Account Control (UAC)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0t1wsosai" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar nível de UAC</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-ItemProperty</span><span> HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name ConsentPromptBehaviorAdmin
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Configurar UAC para nível máximo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name ConsentPromptBehaviorAdmin </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 2
</span></code></pre></div>

**Via GPO:**
```

Computer Configuration > Windows Settings > Security Settings > Local Policies > Security Options ☑ User Account Control: Behavior of the elevation prompt for administrators: Prompt for consent ☑ User Account Control: Run all administrators in Admin Approval Mode: Enabled

```
---

## 🔒 Hardening Avançado

### 1️⃣ Desabilitar Serviços Desnecessários

#### Serviços Comuns a Desabilitar

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9tm3nxxxo" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar serviços em execução</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-Service</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Where-Object</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(214, 222, 235)">$_</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Status </span><span class="token" style="color:rgb(127, 219, 202)">-eq</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Running&quot;</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar serviços desnecessários</span><span>
</span><span></span><span class="token" style="color:rgb(214, 222, 235)">$servicesToDisable</span><span> = @</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;RemoteRegistry&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>        </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Registro Remoto</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;RemoteAccess&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>          </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Roteamento e Acesso Remoto</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;WMPNetworkSvc&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>         </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Compartilhamento de Rede do Windows Media Player</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;XblAuthManager&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>        </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Xbox Live</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;XblGameSave&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>           </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Xbox Live</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;XboxNetApiSvc&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>         </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Xbox Live</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Fax&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>                   </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Fax</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Browser&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>               </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Navegador de Computadores</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;SSDPSRV&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>               </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Descoberta SSDP</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">&quot;upnphost&quot;</span><span>               </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Host de Dispositivo UPnP</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">foreach</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(214, 222, 235)">$service</span><span> in </span><span class="token" style="color:rgb(214, 222, 235)">$servicesToDisable</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">Stop-Service</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(214, 222, 235)">$service</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Force </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ErrorAction SilentlyContinue
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">Set-Service</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(214, 222, 235)">$service</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>StartupType Disabled </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ErrorAction SilentlyContinue
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Desabilitado: </span><span class="token" style="color:rgb(214, 222, 235)">$service</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

### 2️⃣ Desabilitar Protocolos Inseguros

#### SMBv1 (Vulnerável a EternalBlue)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ug68mkqsl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar SMBv1</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Disable-WindowsOptionalFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Online </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FeatureName SMB1Protocol </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>NoRestart
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar status</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-WindowsOptionalFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Online </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FeatureName SMB1Protocol
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Via Registry</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name SMB1 </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span class="token" style="color:rgb(130, 170, 255)">Type</span><span> DWORD </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 0
</span></code></pre></div>

---

#### LLMNR e NetBIOS
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0nyny3z8v" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar LLMNR via GPO</span><span>
</span>Computer Configuration &gt; Administrative Templates &gt; Network &gt; DNS Client
<!-- -->  ☑ Turn off multicast name resolution: Enabled
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar NetBIOS via PowerShell</span><span>
</span><span></span><span class="token" style="color:rgb(214, 222, 235)">$adapters</span><span> = </span><span class="token" style="color:rgb(130, 170, 255)">Get-WmiObject</span><span> Win32_NetworkAdapterConfiguration </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Where-Object</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(214, 222, 235)">$_</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>IPEnabled </span><span class="token" style="color:rgb(127, 219, 202)">-eq</span><span> </span><span class="token" style="color:rgb(255, 88, 116)">$true</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">foreach</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(214, 222, 235)">$adapter</span><span> in </span><span class="token" style="color:rgb(214, 222, 235)">$adapters</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token" style="color:rgb(214, 222, 235)">$adapter</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SetTcpipNetbios</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>2</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 2 = Disable NetBIOS over TCP/IP</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

#### WDigest (Armazena senhas em texto claro na memória)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1q0pthmth" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar WDigest</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name UseLogonCredential </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 0
</span></code></pre></div>

---

### 3️⃣ BitLocker (Criptografia de Disco)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-t66t1p0xz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar se BitLocker está disponível</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-BitLockerVolume</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar BitLocker no drive C:</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Enable-BitLocker</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>MountPoint </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>EncryptionMethod XtsAes256 </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>UsedSpaceOnly </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>RecoveryPasswordProtector
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Backup da chave de recuperação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Backup-BitLockerKeyProtector</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>MountPoint </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>KeyProtectorId </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">Get-BitLockerVolume</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>MountPoint </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>KeyProtector</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>0</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>KeyProtectorId
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar status</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-BitLockerVolume</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>MountPoint </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:&quot;</span><span>
</span></code></pre></div>

---

### 4️⃣ AppLocker (Application Whitelisting)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-a8xo6xgog" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar regras padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-AppLockerPolicy</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>RuleType Publisher</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Path</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Hash </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>User Everyone </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Optimize </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Set-AppLockerPolicy</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar regra para bloquear executáveis em Downloads</span><span>
</span><span></span><span class="token" style="color:rgb(214, 222, 235)">$rule</span><span> = </span><span class="token" style="color:rgb(130, 170, 255)">New-AppLockerPolicy</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>RuleType Path </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:\Users\*\Downloads\*&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>User Everyone </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Action Deny
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-AppLockerPolicy</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>PolicyObject </span><span class="token" style="color:rgb(214, 222, 235)">$rule</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Merge
</span></code></pre></div>

**Via GPO:**
```

Computer Configuration > Windows Settings > Security Settings > Application Control Policies > AppLocker

Configurar regras:

1. Executable Rules
2. Windows Installer Rules
3. Script Rules
4. Packaged app Rules

```
---

### 5️⃣ Credential Guard

**Requisitos:**
- Windows 10 Enterprise/Education ou Windows Server 2016+
- UEFI com Secure Boot
- Virtualization extensions (Intel VT-x ou AMD-V)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0k3l30cps" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar Credential Guard</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Enable-WindowsOptionalFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Online </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FeatureName IsolatedUserMode </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>NoRestart
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Enable-WindowsOptionalFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Online </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FeatureName HypervisorPlatform </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>NoRestart
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Via Registry</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SYSTEM\CurrentControlSet\Control\Lsa&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name LsaCfgFlags </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 1
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Restart-Computer</span><span>
</span></code></pre></div>

---

### 6️⃣ Windows Defender Application Guard

**Isolamento de navegador:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-t8hjcr4fy" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar Application Guard</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Enable-WindowsOptionalFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Online </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FeatureName Windows-Defender-ApplicationGuard </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>NoRestart
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Restart-Computer</span><span>
</span></code></pre></div>

---

### 7️⃣ Audit Policies (Auditoria)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2iyexcgj7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Via GPO</span><span>
</span>Computer Configuration &gt; Windows Settings &gt; Security Settings &gt; Advanced Audit Policy Configuration
<!-- -->
<!-- -->Habilitar auditoria para:
<!-- -->  ☑ Account Logon
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit Credential Validation: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span>  ☑ Account Management
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit User Account Management: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit Security </span><span class="token" style="color:rgb(130, 170, 255)">Group</span><span> Management: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span>  ☑ Logon/Logoff
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit Logon: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit Logoff: Success
</span>  ☑ Object Access
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit File System: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>para pastas críticas</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>  ☑ Policy Change
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit Audit Policy Change: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span>  ☑ Privilege Use
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit Sensitive Privilege Use: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span>  ☑ System
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit Security System Extension: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span> Audit System Integrity: Success</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> Failure
</span></code></pre></div>

---

### 8️⃣ PowerShell Logging

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-fi8y58mfw" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar Script Block Logging via GPO</span><span>
</span>Computer Configuration &gt; Administrative Templates &gt; Windows Components &gt; Windows PowerShell
<!-- -->  ☑ Turn on PowerShell Script Block Logging: Enabled
<!-- -->  ☑ Turn on PowerShell Transcription: Enabled
<!-- -->  ☑ Turn on Module Logging: Enabled
</code></pre></div>

**Verificar logs:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7t3vrcln2" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">Get-WinEvent</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>LogName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Microsoft-Windows-PowerShell/Operational&quot;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Where-Object</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(214, 222, 235)">$_</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Id </span><span class="token" style="color:rgb(127, 219, 202)">-eq</span><span> 4104</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

## 🛡️ Proteção Contra Ataques Comuns

### 1️⃣ Proteção Contra Mimikatz

#### Credential Guard (já mencionado)
Protege credenciais na memória.

#### Protected Users Group
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-gcq7lgl2l" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar usuários ao grupo Protected Users</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Add-ADGroupMember</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Protected Users&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Members </span><span class="token" style="color:rgb(173, 219, 103)">&quot;usuario_admin&quot;</span><span>
</span></code></pre></div>

**Proteções do grupo:**
- Não pode usar NTLM
- Não pode usar DES ou RC4 em Kerberos
- Credenciais não são armazenadas em cache
- Não pode delegar credenciais (CredSSP)

---

### 2️⃣ Proteção Contra Pass-the-Hash

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-av2bubaf5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar LM Hash</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SYSTEM\CurrentControlSet\Control\Lsa&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name NoLMHash </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 1
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Limitar uso de contas locais para acesso remoto</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name LocalAccountTokenFilterPolicy </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 0
</span></code></pre></div>

---

### 3️⃣ Proteção Contra Kerberoasting

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-p2wlpm6ai" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar senhas fortes para contas de serviço (25+ caracteres)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar Managed Service Accounts (MSA) ou Group Managed Service Accounts (gMSA)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar gMSA</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-ADServiceAccount</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;svc_app&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DNSHostName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;svc_app.domain.local&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>PrincipalsAllowedToRetrieveManagedPassword </span><span class="token" style="color:rgb(173, 219, 103)">&quot;AppServers&quot;</span><span>
</span></code></pre></div>

---

### 4️⃣ Proteção Contra Ransomware

#### Controlled Folder Access
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-uin9jvxlf" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-MpPreference</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>EnableControlledFolderAccess Enabled
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar pasta protegida</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Add-MpPreference</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ControlledFolderAccessProtectedFolders </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:\Dados_Importantes&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar aplicação permitida</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Add-MpPreference</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ControlledFolderAccessAllowedApplications </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:\Program Files\App\app.exe&quot;</span><span>
</span></code></pre></div>

---

## 📋 CIS Benchmarks para Windows

### CIS Benchmark - Windows 10 Enterprise

**Download:** [cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks/)

**Principais recomendações:**

#### 1. Account Policies
```

1.1.1 - Enforce password history: 24+ 1.1.2 - Maximum password age: 365 or fewer 1.1.3 - Minimum password age: 1+ 1.1.4 - Minimum password length: 14+ 1.1.5 - Password complexity: Enabled

```
#### 2. Local Policies
```

2.2.1 - Access this computer from network: Administrators 2.2.2 - Act as part of OS: No one 2.2.3 - Adjust memory quotas: Administrators, LOCAL SERVICE, NETWORK SERVICE

```
#### 3. Windows Firewall
```

9.1.1 - Domain Profile: Enabled 9.2.1 - Private Profile: Enabled 9.3.1 - Public Profile: Enabled

```
---

## 🔍 Verificação de Conformidade

### CIS-CAT (CIS Configuration Assessment Tool)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-5c8xh4qxq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar CIS-CAT</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\CIS-</span><span class="token" style="color:rgb(130, 170, 255)">CAT</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>bat </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>a </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>s
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar relatório HTML</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\CIS-</span><span class="token" style="color:rgb(130, 170, 255)">CAT</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>bat </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>a </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>s </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>html
</span></code></pre></div>

---

### Microsoft Security Compliance Toolkit

**Download:** [microsoft.com/en-us/download/details.aspx?id=55319](https://www.microsoft.com/en-us/download/details.aspx?id=55319)

**Ferramentas incluídas:**
- Policy Analyzer
- LGPO (Local Group Policy Object)
- Security baselines

---

## 🚀 Script de Hardening Automatizado

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-egmqqqh0s" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Windows-Hardening-Script.ps1</span><span>
</span>
<span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;=== Windows Hardening Script ===&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Green
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 1. Atualizar Windows Defender</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[1/10] Atualizando Windows Defender...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Update-MpSignature</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 2. Habilitar Firewall</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[2/10] Habilitando Firewall...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-NetFirewallProfile</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Profile Domain</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Public</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Private </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Enabled True
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 3. Desabilitar SMBv1</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[3/10] Desabilitando SMBv1...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Disable-WindowsOptionalFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Online </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FeatureName SMB1Protocol </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>NoRestart
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 4. Desabilitar serviços desnecessários</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[4/10] Desabilitando serviços desnecessários...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(214, 222, 235)">$services</span><span> = @</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;RemoteRegistry&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;XblAuthManager&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;XblGameSave&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">foreach</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(214, 222, 235)">$svc</span><span> in </span><span class="token" style="color:rgb(214, 222, 235)">$services</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">Stop-Service</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(214, 222, 235)">$svc</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Force </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ErrorAction SilentlyContinue
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">Set-Service</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(214, 222, 235)">$svc</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>StartupType Disabled </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ErrorAction SilentlyContinue
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 5. Configurar UAC</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[5/10] Configurando UAC...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name ConsentPromptBehaviorAdmin </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 6. Desabilitar WDigest</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[6/10] Desabilitando WDigest...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name UseLogonCredential </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 0
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 7. Habilitar Controlled Folder Access</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[7/10] Habilitando Controlled Folder Access...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-MpPreference</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>EnableControlledFolderAccess Enabled
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 8. Desabilitar LLMNR</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[8/10] Desabilitando LLMNR...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SOFTWARE\Policies\Microsoft\Windows NT\DNSClient&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name EnableMulticast </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 0
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 9. Configurar auditoria</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[9/10] Configurando auditoria...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span>auditpol </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(130, 170, 255)">set</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>subcategory:</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Logon&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>success:enable </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>failure:enable
</span><span>auditpol </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(130, 170, 255)">set</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>subcategory:</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Logoff&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>success:enable
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 10. Habilitar BitLocker (se disponível)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;[10/10] Verificando BitLocker...&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">Get-Command</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Enable-BitLocker</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ErrorAction SilentlyContinue</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;BitLocker disponível. Considere habilitar manualmente.&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Cyan
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">else</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;BitLocker não disponível nesta edição do Windows.&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Red
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span>
<span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;`n=== Hardening Concluído ===&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Green
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Write-Host</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Reinicie o sistema para aplicar todas as mudanças.&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForegroundColor Yellow
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[Active-Directory]]
- [[CIS-Controls]]
- [[Defesa-em-Profundidade]]
- [[NIST-Cybersecurity]]

---

## 📚 Referências

- CIS Benchmarks: [cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks/)
- Microsoft Security Baselines: [microsoft.com/security/blog/security-baselines](https://www.microsoft.com/security/blog/tag/security-baselines/)
- NIST Windows Security: [nvd.nist.gov](https://nvd.nist.gov/)
- STIG (Security Technical Implementation Guides): [public.cyber.mil/stigs](https://public.cyber.mil/stigs/)
