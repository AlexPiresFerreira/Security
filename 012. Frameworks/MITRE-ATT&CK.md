
# 🎯 MITRE ATT&CK Framework

> **Tags:** #mitre #attck #framework #tactics #techniques #threat-intelligence #apt

---

## 📌 Visão Geral

**MITRE ATT&CK** (Adversarial Tactics, Techniques, and Common Knowledge) é uma base de conhecimento globalmente acessível sobre **táticas e técnicas** de adversários baseadas em observações do mundo real.

🎯 **Objetivo:** Fornecer uma linguagem comum para descrever comportamentos de atacantes e melhorar a defesa cibernética.

---

## 🌐 Sites Oficiais

- **Site principal:** [attack.mitre.org](https://attack.mitre.org)
- **Navigator:** [mitre-attack.github.io/attack-navigator](https://mitre-attack.github.io/attack-navigator)

---

## 📊 Estrutura do Framework

### Matrizes Disponíveis

| Matriz | Descrição | Foco |
|--------|-----------|------|
| **Enterprise** | Ambientes corporativos | Windows, Linux, macOS, Cloud |
| **Mobile** | Dispositivos móveis | Android, iOS |
| **ICS** | Sistemas de controle industrial | SCADA, ICS, OT |

---

## 🎯 Táticas (Tactics)

As **táticas** representam o **"por quê"** de uma técnica - o objetivo tático do adversário.

### 14 Táticas do ATT&CK Enterprise

┌─────────────────────────────────────────────────────────┐ 
│ 1. Reconnaissance (Reconhecimento)                                            │
│ 2. Resource Development (Desenvolvimento de Recursos)           │
│ 3. Initial Access (Acesso Inicial)                                                      │
│ 4. Execution (Execução)                                                                  │ 
│ 5. Persistence (Persistência)                                                            │
│ 6. Privilege Escalation (Escalação de Privilégios)                            │
│ 7. Defense Evasion (Evasão de Defesa)                                          │
│ 8. Credential Access (Acesso a Credenciais)                                   │
│ 9. Discovery (Descoberta)                                                               │
│ 10. Lateral Movement (Movimentação Lateral)                              │
│ 11. Collection (Coleta)                                                                    │
│ 12. Command and Control (C2)                                                      │
│ 13. Exfiltration (Exfiltração)                                                             │
│ 14. Impact (Impacto)                                                                      │
└─────────────────────────────────────────────────────────┘

---

## 🛠️ Técnicas (Techniques)

As **técnicas** representam o **"como"** - os métodos específicos usados pelos adversários.

### Exemplos de Técnicas por Tática

#### 1️⃣ Reconnaissance (TA0043)

**T1595 - Active Scanning**
- Varredura de portas (Nmap)
- Varredura de vulnerabilidades
- Identificação de serviços

**T1592 - Gather Victim Host Information**
- Coleta de informações sobre hardware
- Identificação de software instalado

**T1589 - Gather Victim Identity Information**
- OSINT em redes sociais
- Coleta de e-mails corporativos

---

#### 2️⃣ Resource Development (TA0042)

**T1583 - Acquire Infrastructure**
- Registro de domínios
- Aluguel de servidores VPS
- Configuração de C2

**T1587 - Develop Capabilities**
- Desenvolvimento de malware customizado
- Criação de exploits
- Preparação de payloads

---

#### 3️⃣ Initial Access (TA0001)

**T1566 - Phishing**
- Spear phishing via e-mail
- Anexos maliciosos
- Links para sites comprometidos

**T1190 - Exploit Public-Facing Application**
- Exploração de vulnerabilidades web
- SQL Injection
- RCE em aplicações expostas

**T1133 - External Remote Services**
- Acesso via VPN comprometida
- RDP exposto
- SSH com credenciais fracas

---

#### 4️⃣ Execution (TA0002)

**T1059 - Command and Scripting Interpreter**
- PowerShell
- Bash/Shell
- Python scripts
- JavaScript

**T1203 - Exploitation for Client Execution**
- Exploits em navegadores
- Documentos Office com macros
- PDF malicioso

---

#### 5️⃣ Persistence (TA0003)

**T1547 - Boot or Logon Autostart Execution**
- Registry Run Keys (Windows)
- Startup Folder
- Cron jobs (Linux)
- Systemd services

**T1053 - Scheduled Task/Job**
- Windows Task Scheduler
- Cron (Linux)
- At (Linux)

**T1136 - Create Account**
- Criação de usuário local
- Criação de usuário de domínio

---

#### 6️⃣ Privilege Escalation (TA0004)

**T1068 - Exploitation for Privilege Escalation**
- Exploits de kernel
- Vulnerabilidades locais
- DLL Hijacking

**T1078 - Valid Accounts**
- Uso de credenciais roubadas
- Pass-the-Hash
- Pass-the-Ticket

---

#### 7️⃣ Defense Evasion (TA0005)

**T1070 - Indicator Removal on Host**
- Limpeza de logs
- Remoção de arquivos temporários
- Timestomping

**T1027 - Obfuscated Files or Information**
- Ofuscação de código
- Criptografia de payloads
- Steganografia

**T1562 - Impair Defenses**
- Desabilitar antivírus
- Parar serviços de segurança
- Modificar regras de firewall

---

#### 8️⃣ Credential Access (TA0006)

**T1003 - OS Credential Dumping**
- Mimikatz (LSASS dump)
- SAM database dump
- /etc/shadow (Linux)

**T1110 - Brute Force**
- Password spraying
- Credential stuffing
- Brute force tradicional

**T1555 - Credentials from Password Stores**
- Navegadores (Chrome, Firefox)
- Gerenciadores de senha
- Keychains (macOS)

---

#### 9️⃣ Discovery (TA0007)

**T1087 - Account Discovery**
- Enumeração de usuários locais
- Enumeração de usuários de domínio
- `net user` (Windows)
- `cat /etc/passwd` (Linux)

**T1018 - Remote System Discovery**
- Varredura de rede
- Ping sweep
- ARP scanning

**T1082 - System Information Discovery**
- `systeminfo` (Windows)
- `uname -a` (Linux)
- Coleta de informações de hardware

---

#### 🔟 Lateral Movement (TA0008)

**T1021 - Remote Services**
- RDP
- SSH
- SMB/Windows Admin Shares
- WinRM

**T1550 - Use Alternate Authentication Material**
- Pass-the-Hash
- Pass-the-Ticket
- Kerberos Golden Ticket

---

#### 1️⃣1️⃣ Collection (TA0009)

**T1560 - Archive Collected Data**
- Compactação de dados
- Preparação para exfiltração

**T1113 - Screen Capture**
- Screenshots
- Gravação de tela

**T1005 - Data from Local System**
- Coleta de documentos
- Acesso a bancos de dados locais

---

#### 1️⃣2️⃣ Command and Control (TA0011)

**T1071 - Application Layer Protocol**
- HTTP/HTTPS
- DNS tunneling
- SMTP

**T1573 - Encrypted Channel**
- TLS/SSL
- SSH tunneling
- VPN

**T1568 - Dynamic Resolution**
- Domain Generation Algorithms (DGA)
- Fast Flux

---

#### 1️⃣3️⃣ Exfiltration (TA0010)

**T1041 - Exfiltration Over C2 Channel**
- Envio via canal C2 estabelecido

**T1567 - Exfiltration Over Web Service**
- Upload para Dropbox, Google Drive
- Pastebin
- GitHub

**T1048 - Exfiltration Over Alternative Protocol**
- FTP
- SMTP
- DNS

---

#### 1️⃣4️⃣ Impact (TA0040)

**T1486 - Data Encrypted for Impact**
- Ransomware
- Criptografia de arquivos

**T1485 - Data Destruction**
- Deletar dados
- Wiper malware

**T1490 - Inhibit System Recovery**
- Deletar backups
- Desabilitar System Restore

---

## 🔗 Relação com Cyber Kill Chain

| Cyber Kill Chain | MITRE ATT&CK |
|------------------|--------------|
| Reconnaissance | Reconnaissance + Resource Development |
| Weaponization | Resource Development |
| Delivery | Initial Access |
| Exploitation | Execution |
| Installation | Persistence + Privilege Escalation |
| C2 | Command and Control |
| Actions on Objectives | Collection + Exfiltration + Impact |

**Diferenças:**
- **Kill Chain:** Modelo **linear** e **simplificado**
- **ATT&CK:** Modelo **não-linear** e **detalhado** (centenas de técnicas)

---


## 🎯 Uso Prático do ATT&CK

### Para Blue Team (Defesa)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-xmlcpulcy" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mapear detecções existentes</span><span>
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>. Identificar técnicas usadas por adversários relevantes
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">2</span><span>. Verificar cobertura de detecção </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>SIEM, EDR</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">3</span><span>. Criar regras de detecção para gaps
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">4</span><span>. Testar detecções com Atomic Red Team
</span></code></pre></div>

**Exemplo:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7kek0ohfw" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Detecção de Mimikatz (T1003.001)</span><span>
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">rule</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Mimikatz_LSASS_Access
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">condition</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> 
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">process.name</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> mimikatz.exe
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">target.process</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> lsass.exe
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">action</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> read_memory
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">severity</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> critical
</span></code></pre></div>

---

### Para Red Team (Ataque)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-euvxssm6t" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Planejar operação ofensiva</span><span>
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>. Escolher táticas e técnicas apropriadas
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">2</span><span>. Selecionar ferramentas </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>Cobalt Strike, Empire</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">3</span><span>. Mapear TTPs para evitar detecção
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">4</span><span>. Documentar técnicas usadas no relatório
</span></code></pre></div>

---

### Para Threat Intelligence

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-jy3qu4nzg" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mapear grupos APT</span><span>
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>. Identificar TTPs de grupos conhecidos
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">2</span><span>. Correlacionar com ataques observados
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">3</span><span>. Atualizar defesas baseado em inteligência
</span></code></pre></div>

### Para Threat Intelligence

**Exemplo - APT29 (Cozy Bear):**
- T1566.001: Spear Phishing Attachment
- T1059.001: PowerShell
- T1055: Process Injection
- T1071.001: Web Protocols (C2)

---

## 🛠️ Ferramentas Relacionadas

### ATT&CK Navigator
Interface visual para mapear cobertura de detecção.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-rhd57ox6j" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar online</span><span>
</span>https://mitre-attack.github.io/attack-navigator/
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou instalar localmente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">git</span><span> clone https://github.com/mitre-attack/attack-navigator.git
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> attack-navigator
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">npm</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">npm</span><span> start
</span></code></pre></div>

---

### Atomic Red Team
Biblioteca de testes para simular técnicas do ATT&CK.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-5kfduotk6" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">IEX</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">IWR</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1&#x27;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>UseBasicParsing</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Install-AtomicRedTeam</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>getAtomics
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar teste</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Invoke-AtomicTest</span><span> T1003</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>001
</span></code></pre></div>

**Site:** [atomicredteam.io](https://atomicredteam.io)

---

### CALDERA
Plataforma de emulação de adversários automatizada.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-umk7w5y52" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">git</span><span> clone https://github.com/mitre/caldera.git
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> caldera
</span><span>pip3 </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> requirements.txt
</span><span>python3 server.py </span><span class="token parameter" style="color:rgb(214, 222, 235)">--insecure</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar: http://localhost:8888</span><span>
</span></code></pre></div>

---
## 📊 Exemplo de Mapeamento - Ataque Real 

### Cenário: Ransomware WannaCry 


| Tática | Técnica | Descrição |
|--------|---------|-----------|
| Initial Access | T1190 | Exploração de SMBv1 (EternalBlue) |
| Execution | T1059.003 | Execução via Windows Command Shell |
| Persistence | T1547.001 | Registry Run Keys |
| Privilege Escalation | T1068 | Exploração de vulnerabilidade local |
| Defense Evasion | T1562.001 | Desabilitar Windows Defender |
| Lateral Movement | T1021.002 | SMB/Windows Admin Shares |
| Impact | T1486 | Criptografia de dados (Ransomware) |

---

## 🔗 Links Relacionados

- [[Cyber-Kill-Chain]]
- [[Malwares]]
- [[Tipos-de-Ataques]]
- [[OSINT-Fundamentos]]
- [[Red-Team-vs-Blue-Team]]

---

## 📚 Referências

- MITRE ATT&CK: [attack.mitre.org](https://attack.mitre.org)
- Atomic Red Team: [atomicredteam.io](https://atomicredteam.io)
- CALDERA: [github.com/mitre/caldera](https://github.com/mitre/caldera)
- ATT&CK Navigator: [mitre-attack.github.io/attack-navigator](https://mitre-attack.github.io/attack-navigator)

---

## 1. Conceitos principais

### IoC — Indicadores de comprometimento

- São informações que ajudam a identificar a presença de um atacante no ambiente.
- Exemplos:
    - IP
    - domínio
    - hash
    - arquivo
    - comportamento suspeito

### Pyramid of Pain

- Mostra quais indicadores causam mais “dor” para o atacante quando você consegue detectá-los.
- Em geral:
    - **hashes** e **IPs** são mais fáceis de trocar
    - **ferramentas** e principalmente **TTPs** são mais valiosas para defesa

### TTP

- **Táticas** → o objetivo do atacante
- **Técnicas** → como ele alcança o objetivo
- **Procedimentos** → o passo a passo específico usado na execução

---

## 2. Casos de uso do ATT&CK

### Detecção e Analytics

- Usado para transformar comportamento de ataque em regras e alertas.
- Ajuda a mapear quais técnicas sua equipe já consegue detectar.

### Threat Intelligence

- Ajuda a analisar campanhas, grupos e técnicas usadas por atacantes.
- Serve para conectar relatórios de ameaça ao ATT&CK.

### Assessment

- Usado para avaliar maturidade e cobertura de defesa.
- Mostra lacunas de visibilidade e detecção.

### Red Team / Blue Team

- **Red Team** simula o adversário.
- **Blue Team** tenta detectar, conter e responder.
- O ATT&CK ajuda os dois lados a falarem a mesma linguagem.

---

## 3. Níveis de maturidade

### Detecção — Nível 1

- Selecionar 2 a 3 técnicas do ATT&CK.
- Identificar fontes de dados.
- Verificar se os dados estão centralizados no SIEM.
- Buscar regras prontas criadas por outros especialistas.
- Fazer testes básicos para validar a detecção.

### Detecção — Nível 2

- Criar a regra de detecção.
- Executar testes.
- Identificar e remover falsos positivos.
- Validar se a detecção funciona corretamente.

### Detecção — Nível 3

- Cobrir variantes de uma técnica.
- Criar mapas de calor de cobertura.
- Refinar eventos para evitar sobrecarga no SIEM.
- Reduzir fadiga de alertas no SOC.

---

## 4. Threat Intelligence

### Nível 1

- Começar com grupos e comportamento geral.

### Nível 2

- Relacionar relatórios com técnicas específicas.
- Cruzar campanhas e TTPs.

### Nível 3

- Fazer análise mais profunda e contextualizada.
- Trabalhar inteligência com maior maturidade.

---

## 5. Emulação de adversários

### Nível 1

- Usar exemplos e testes mais simples.

### Nível 2

- Planejar emulação baseada em técnicas e softwares do ATT&CK.

### Nível 3

- Fazer emulação mais completa e fiel ao adversário.
- Exige maior maturidade operacional.

---

## 6. ATT&CK Navigator

- Ferramenta para **visualizar cobertura**, **lacunas** e **mapas de calor**.
- Útil para:
    - marcar técnicas já detectadas
    - comparar cenários
    - planejar melhorias de defesa

---

# URLs para consulta

## MITRE ATT&CK

- **Framework principal**  
    [https://attack.mitre.org](https://attack.mitre.org/)
    
- **Técnicas Enterprise**  
    [https://attack.mitre.org/techniques/enterprise/](https://attack.mitre.org/techniques/enterprise/)
    
- **Técnica T1078**  
    [https://attack.mitre.org/techniques/T1078/](https://attack.mitre.org/techniques/T1078/)
    
- **Técnica T1199**  
    [https://attack.mitre.org/techniques/T1199/](https://attack.mitre.org/techniques/T1199/)
    
- **Técnica T1203**  
    [https://attack.mitre.org/techniques/T1203/](https://attack.mitre.org/techniques/T1203/)
    
- **Resources**  
    [https://attack.mitre.org/resources/](https://attack.mitre.org/resources/)
    
- **Groups**  
    [https://attack.mitre.org/groups/](https://attack.mitre.org/groups/)
    
- **Software**  
    [https://attack.mitre.org/software/](https://attack.mitre.org/software/)
    
- **Campaigns**  
    [https://attack.mitre.org/campaigns/](https://attack.mitre.org/campaigns/)
    

---

## Pyramid of Pain

- **Artigo original**  
    [https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html)

---

## TTP / Glossário

- **NIST — TTP**  
    [https://csrc.nist.gov/glossary/term/tactics_techniques_and_procedures](https://csrc.nist.gov/glossary/term/tactics_techniques_and_procedures)

---

## Kill Chain / Táticas

- **Lockheed Martin — Cyber Kill Chain**  
    [https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)

---

## Detecção

- **MITRE — Getting Started with ATT&CK Detection**  
    [https://medium.com/mitre-attack/getting-started-with-attack-detection-a8e49e4960d0](https://medium.com/mitre-attack/getting-started-with-attack-detection-a8e49e4960d0)
    
- **SigmaHQ**  
    [https://github.com/SigmaHQ/sigma](https://github.com/SigmaHQ/sigma)
    
- **Exemplo de técnica ligada à detecção**  
    [https://attack.mitre.org/techniques/T1199/](https://attack.mitre.org/techniques/T1199/)
    
- **Documento do DOJ**  
    [https://www.justice.gov/file/1080281/download](https://www.justice.gov/file/1080281/download)
    

---

## Threat Intelligence

- **MITRE — Getting Started with ATT&CK CTI**  
    [https://medium.com/mitre-attack/getting-started-with-attack-cti-4eb205be4b2f](https://medium.com/mitre-attack/getting-started-with-attack-cti-4eb205be4b2f)
    
- **Lifecycle de threat intelligence**  
    [https://www.recordedfuture.com/blog/threat-intelligence-lifecycle-phases](https://www.recordedfuture.com/blog/threat-intelligence-lifecycle-phases)
    
- **Definição de threat intelligence**  
    [https://www.techtarget.com/whatis/definition/threat-intelligence-cyber-threat-intelligence](https://www.techtarget.com/whatis/definition/threat-intelligence-cyber-threat-intelligence)
    
- **Exemplo de grupo**  
    [https://attack.mitre.org/groups/](https://attack.mitre.org/groups/)
    
- **Exemplo de relatório APT37**  
    [https://www2.fireeye.com/rs/848-DID-242/images/rpt_APT37.pdf](https://www2.fireeye.com/rs/848-DID-242/images/rpt_APT37.pdf)
    
- **Exemplo de técnica T1203**  
    [https://attack.mitre.org/techniques/T1203/](https://attack.mitre.org/techniques/T1203/)
    
- **Recorded Future eBook**  
    [https://cyberedgegroup.com/wp-content/uploads/2018/11/Recorded-Future-eBook.pdf](https://cyberedgegroup.com/wp-content/uploads/2018/11/Recorded-Future-eBook.pdf)
    

---

## ATT&CK Navigator

- **Navigator**  
    [https://mitre-attack.github.io/attack-navigator/](https://mitre-attack.github.io/attack-navigator/)

---

## Emulação de adversários

- **MITRE — Getting Started with ATT&CK Red**  
    [https://medium.com/mitre-attack/getting-started-with-attack-red-29f074ccf7e3](https://medium.com/mitre-attack/getting-started-with-attack-red-29f074ccf7e3)
    
- **Atomic Red Team**  
    [https://github.com/redcanaryco/atomic-red-team](https://github.com/redcanaryco/atomic-red-team)
    
- **Software ATT&CK**  
    [https://attack.mitre.org/software/](https://attack.mitre.org/software/)
    
- **APT3 Adversary Emulation Plan**  
    [https://attack.mitre.org/docs/APT3_Adversary_Emulation_Plan.pdf](https://attack.mitre.org/docs/APT3_Adversary_Emulation_Plan.pdf)
    
- **APT3 Field Manual**  
    [https://attack.mitre.org/docs/APT3_Adversary_Emulation_Field_Manual.xlsx](https://attack.mitre.org/docs/APT3_Adversary_Emulation_Field_Manual.xlsx)
    

---

## Assessment

- **MITRE — Getting Started with ATT&CK Assessment**  
    [https://medium.com/mitre-attack/getting-started-with-attack-assessment-cc0b01769cb4](https://medium.com/mitre-attack/getting-started-with-attack-assessment-cc0b01769cb4)

---

## Exemplo de artigo relacionado

- **Unit 42 — new attacks linked to C0d0s0 group**  
    [https://unit42.paloaltonetworks.com/new-attacks-linked-to-c0d0s0-group/](https://unit42.paloaltonetworks.com/new-attacks-linked-to-c0d0s0-group/)