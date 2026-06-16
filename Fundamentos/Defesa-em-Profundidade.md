# 🛡️ Defesa em Profundidade (Defense in Depth)

> **Tags:** #defense-in-depth #layered-security #seguranca #estrategia #controles #defesa

---

## 📌 Conceito

**Defesa em Profundidade** (Defense in Depth) é uma estratégia de segurança que utiliza **múltiplas camadas** de controles de segurança para proteger informações e sistemas. Se uma camada falhar, outras camadas continuam fornecendo proteção.

🎯 **Princípio:** "Não coloque todos os ovos na mesma cesta"

**Analogia:** Como um castelo medieval com múltiplas defesas:

Fosso → Muralha Externa → Portão → Muralha Interna → Torre Central


---

## 🏰 Camadas de Defesa

### Modelo de 7 Camadas


┌──────────────────────────────────────────┐│ 1. Políticas, Procedimentos e Awareness ├──────────────────────────────────────────┤ │ 2. Segurança Física │ ├───────────────────────-──────────────────┤ │ 3. Perímetro de Rede │ ├────────────────────────-─────────────────┤ │ 4. Rede Interna │ ├──────────────────────────────────────────┤ │ 5. Host (Endpoint) │ ├──────────────────────────────────────────┤ │ 6. Aplicação │ ├──────────────────────────────────────────┤ │ 7. Dados │ └──────────────────────────────────────────┘


---

## 1️⃣ Políticas, Procedimentos e Awareness

### Descrição
A **primeira linha de defesa** são as pessoas e processos.

### Controles

#### 📋 Políticas de Segurança
- Política de Senhas
- Política de Uso Aceitável (AUP)
- Política de Classificação de Dados
- Política de Acesso Remoto
- Política de BYOD (Bring Your Own Device)

**Exemplo - Política de Senhas:**
```

- Mínimo 12 caracteres
- Complexidade: maiúsculas, minúsculas, números, símbolos
- Rotação a cada 90 dias
- Não reutilizar últimas 10 senhas
- MFA obrigatório para sistemas críticos

```
---

#### 🎓 Security Awareness Training
- Treinamento inicial (onboarding)
- Treinamento anual obrigatório
- Simulações de phishing
- Newsletters de segurança
- Campanhas de conscientização

**Tópicos importantes:**
- Reconhecer phishing
- Proteção de credenciais
- Engenharia social
- Segurança de dispositivos móveis
- Trabalho remoto seguro

---

#### 📝 Procedimentos Operacionais
- Incident Response Plan
- Disaster Recovery Plan
- Business Continuity Plan
- Change Management
- Backup procedures

---

## 2️⃣ Segurança Física

### Descrição
Proteção **física** de instalações, equipamentos e pessoas.

### Controles

#### 🚪 Controle de Acesso Físico
- Catracas e portas com controle de acesso
- Cartões de proximidade (RFID)
- Biometria (digital, facial, íris)
- Recepcionistas/seguranças
- Visitantes acompanhados

---

#### 📹 Vigilância
- CCTV (Câmeras de segurança)
- Gravação contínua (retenção mínima 30 dias)
- Monitoramento 24/7
- Alarmes de intrusão

---

#### 🔒 Proteção de Equipamentos
- Salas de servidores trancadas
- Racks com fechadura
- Cabo locks para laptops
- Destruição segura de mídias (shredders)
- Controle de entrada/saída de equipamentos

---

#### ⚡ Infraestrutura Crítica
- UPS (No-break)
- Geradores de emergência
- Ar condicionado redundante
- Detecção e supressão de incêndio
- Proteção contra enchentes

---

## 3️⃣ Perímetro de Rede

### Descrição
Proteção da **borda** da rede, onde ela se conecta à internet.

### Controles

#### 🔥 Firewall de Perímetro
**Função:** Filtrar tráfego entre rede interna e externa.

**Tipos:**
- Stateful Firewall
- Next-Generation Firewall (NGFW)
- Web Application Firewall (WAF)

**Regras básicas:**
```

# Default deny (negar tudo por padrão)

deny all

# Permitir apenas o necessário

allow tcp any -> 80,443 (web) allow tcp any -> 25 (smtp) allow udp any -> 53 (dns)

```
---

#### 🛡️ IDS/IPS (Intrusion Detection/Prevention System)
**IDS:** Detecta e alerta sobre atividades suspeitas
**IPS:** Detecta e **bloqueia** atividades suspeitas

**Ferramentas:**
- Suricata
- Snort
- Zeek (Bro)

**Assinaturas:**
```

# Exemplo Suricata - Detectar SQL Injection

alert http any any -> any any (msg:"SQL Injection Attempt"; content:"' OR '1'='1"; http_uri; classtype:web-application-attack; sid:1000001; rev:1;)

```
---

#### 🌐 DMZ (Demilitarized Zone)
**Conceito:** Zona intermediária entre internet e rede interna.

**Arquitetura:**
```

Internet │ ▼ ┌─────────┐ │Firewall1│ (Externo) └─────────┘ │ ▼ ┌─────────┐ │ DMZ │ (Servidores públicos: Web, Email, DNS) └─────────┘ │ ▼ ┌─────────┐ │Firewall2│ (Interno) └─────────┘ │ ▼ Rede Interna

```
**Servidores na DMZ:**
- Web servers
- Mail servers
- DNS público
- FTP servers
- VPN gateways

---

#### 🔐 VPN (Virtual Private Network)
**Função:** Conexão segura e criptografada para acesso remoto.

**Tipos:**
- **Site-to-Site:** Conecta redes inteiras
- **Remote Access:** Conecta usuários individuais

**Protocolos:**
- IPSec
- SSL/TLS (OpenVPN)
- WireGuard

---

#### 🚫 DDoS Protection
**Controles:**
- Rate limiting
- CDN (Cloudflare, Akamai)
- Scrubbing centers
- Anycast network

---

## 4️⃣ Rede Interna

### Descrição
Proteção **dentro** da rede corporativa.

### Controles

#### 🔀 Segmentação de Rede (VLANs)
**Conceito:** Dividir a rede em segmentos isolados.

**Exemplo de segmentação:**
```

VLAN 10: Servidores (192.168.10.0/24)
VLAN 20: Workstations (192.168.20.0/24) 
VLAN 30: Convidados (192.168.30.0/24) 
VLAN 40: IoT (192.168.40.0/24) 
VLAN 50: Gerência (192.168.50.0/24)

```
**Regras de firewall entre VLANs:**
```

# Workstations podem acessar servidores

allow VLAN20 -> VLAN10 (tcp/443, tcp/3389)

# Convidados APENAS internet

allow VLAN30 -> Internet deny VLAN30 -> VLAN10,20,40,50

# IoT isolado

deny VLAN40 -> VLAN10,20,30,50

```
---

#### 🔒 NAC (Network Access Control)
**Função:** Controlar quais dispositivos podem se conectar à rede.

**Verificações:**
- Dispositivo gerenciado pela empresa?
- Antivírus atualizado?
- Sistema operacional atualizado?
- Certificado digital válido?

**Ações:**
- ✅ Permitir acesso total
- ⚠️ Acesso limitado (quarentena)
- ❌ Bloquear acesso

**Soluções:**
- Cisco ISE
- Aruba ClearPass
- PacketFence

---

#### 🔐 802.1X (Port-Based Authentication)
**Função:** Autenticação de dispositivos antes de permitir acesso à rede.

**Componentes:**
- **Supplicant:** Dispositivo que quer se conectar
- **Authenticator:** Switch/AP
- **Authentication Server:** RADIUS (ex: FreeRADIUS, Microsoft NPS)

**Fluxo:**
```

1. Dispositivo conecta ao switch
2. Switch solicita credenciais (EAP)
3. Switch encaminha para RADIUS
4. RADIUS valida credenciais
5. Switch libera ou bloqueia acesso

```
---

#### 🕵️ Network Monitoring
**Ferramentas:**
- SIEM (Splunk, ELK, Wazuh)
- NetFlow/sFlow analysis
- Network behavior analysis (NBA)

**Métricas monitoradas:**
- Largura de banda
- Conexões suspeitas
- Tráfego anômalo
- Varreduras de portas

---

## 5️⃣ Host (Endpoint)

### Descrição
Proteção de **dispositivos individuais** (desktops, laptops, servidores).

### Controles

#### 🦠 Antivírus/Antimalware
**Tipos:**
- **Signature-based:** Detecta malware conhecido
- **Heuristic:** Detecta comportamento suspeito
- **Sandboxing:** Executa arquivos em ambiente isolado

**Soluções:**
- Windows Defender
- Kaspersky
- Bitdefender
- ESET

---

#### 🛡️ EDR/XDR (Endpoint Detection and Response)
**Função:** Detecção avançada e resposta a ameaças em endpoints.

**Capacidades:**
- Monitoramento contínuo
- Detecção de IOCs
- Análise comportamental
- Resposta automatizada (isolamento)

**Soluções:**
- CrowdStrike Falcon
- SentinelOne
- Microsoft Defender for Endpoint
- Carbon Black

---

#### 🔒 Host-Based Firewall
**Função:** Firewall no próprio dispositivo.

**Exemplos:**
- Windows Firewall
- iptables (Linux)
- pf (BSD/macOS)

**Configuração básica (Windows):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-02m8zm5aa" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bloquear tudo por padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-NetFirewallProfile</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Profile Domain</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Public</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>Private </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DefaultInboundAction Block
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir apenas o necessário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-NetFirewallRule</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DisplayName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Allow RDP&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Direction Inbound </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Protocol TCP </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>LocalPort 3389 </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Action Allow
</span></code></pre></div>

---

#### 🔐 Disk Encryption
**Função:** Criptografar dados em repouso.

**Soluções:**
- **Windows:** BitLocker
- **macOS:** FileVault
- **Linux:** LUKS

**Benefício:** Proteção em caso de roubo/perda do dispositivo.

---

#### 🔄 Patch Management
**Função:** Manter sistemas atualizados.

**Processo:**
```

1. Identificar patches disponíveis
2. Testar em ambiente de homologação
3. Agendar janela de manutenção
4. Aplicar patches
5. Verificar sucesso
6. Documentar

```
**Ferramentas:**
- WSUS (Windows Server Update Services)
- SCCM (System Center Configuration Manager)
- Ansible
- Puppet

---

#### 🚫 Application Whitelisting
**Função:** Permitir apenas aplicações aprovadas.

**Soluções:**
- AppLocker (Windows)
- SELinux (Linux)
- Application Control Policies

**Exemplo AppLocker:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">xml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wuod27ejn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-xml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">&lt;!-- Permitir apenas executáveis assinados pela Microsoft --&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">FilePublisherRule</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">Conditions</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span>    </span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">FilePublisherCondition</span><span class="token" style="color:rgb(127, 219, 202)"> </span><span class="token" style="color:rgb(173, 219, 103);font-style:italic">PublisherName</span><span class="token attr-equals" style="color:rgb(199, 146, 234)">=</span><span class="token" style="color:rgb(199, 146, 234)">&quot;</span><span class="token" style="color:rgb(255, 203, 139)">O=MICROSOFT CORPORATION*</span><span class="token" style="color:rgb(199, 146, 234)">&quot;</span><span class="token" style="color:rgb(127, 219, 202)"> </span><span class="token" style="color:rgb(199, 146, 234)">/&gt;</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">Conditions</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">FilePublisherRule</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span></code></pre></div>

---

#### 🔒 Hardening
**Conceito:** Reduzir superfície de ataque do sistema.

**Ações:**
- Desabilitar serviços desnecessários
- Remover software não utilizado
- Configurar permissões restritivas
- Desabilitar protocolos inseguros (SMBv1, TLS 1.0)

**Benchmarks:**
- CIS Benchmarks
- STIG (Security Technical Implementation Guides)

---

## 6️⃣ Aplicação

### Descrição
Proteção de **aplicações** e **código**.

### Controles

#### 🔒 Secure Coding
**Práticas:**
- Input validation
- Output encoding
- Prepared statements (SQL)
- Least privilege
- Error handling seguro

**OWASP Top 10:**
- SQL Injection
- XSS
- Broken Authentication
- Sensitive Data Exposure
- XXE
- Broken Access Control
- Security Misconfiguration
- Insecure Deserialization
- Using Components with Known Vulnerabilities
- Insufficient Logging

---

#### 🧪 Security Testing
**Tipos:**
- **SAST (Static):** Análise de código-fonte
- **DAST (Dynamic):** Análise de aplicação em execução
- **IAST (Interactive):** Combinação de SAST e DAST
- **Penetration Testing:** Testes manuais

**Ferramentas:**
- **SAST:** SonarQube, Checkmarx, Fortify
- **DAST:** Burp Suite, OWASP ZAP, Acunetix

---

#### 🔐 WAF (Web Application Firewall)
**Função:** Proteger aplicações web contra ataques.

**Proteção contra:**
- SQL Injection
- XSS
- CSRF
- File inclusion
- DDoS (Layer 7)

**Soluções:**
- ModSecurity
- Cloudflare WAF
- AWS WAF
- Imperva

---

#### 🔑 Authentication & Authorization
**Controles:**
- MFA (Multi-Factor Authentication)
- SSO (Single Sign-On)
- OAuth 2.0 / OpenID Connect
- RBAC (Role-Based Access Control)
- Session management seguro

---

#### 📝 Logging e Auditoria
**O que logar:**
- Autenticações (sucesso e falha)
- Mudanças de configuração
- Acesso a dados sensíveis
- Erros de aplicação

**Formato:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">json</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ry879ouyd" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-json" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>  </span><span class="token" style="color:rgb(128, 203, 196)">&quot;timestamp&quot;</span><span class="token" style="color:rgb(127, 219, 202)">:</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;2025-12-31T18:45:23Z&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>  </span><span class="token" style="color:rgb(128, 203, 196)">&quot;user&quot;</span><span class="token" style="color:rgb(127, 219, 202)">:</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>  </span><span class="token" style="color:rgb(128, 203, 196)">&quot;action&quot;</span><span class="token" style="color:rgb(127, 219, 202)">:</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;LOGIN_SUCCESS&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>  </span><span class="token" style="color:rgb(128, 203, 196)">&quot;ip&quot;</span><span class="token" style="color:rgb(127, 219, 202)">:</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;192.168.1.50&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>  </span><span class="token" style="color:rgb(128, 203, 196)">&quot;resource&quot;</span><span class="token" style="color:rgb(127, 219, 202)">:</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;/admin/dashboard&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

## 7️⃣ Dados

### Descrição
Proteção dos **dados** em si (último nível de defesa).

### Controles

#### 🔐 Criptografia
**Em repouso (at rest):**
- Disk encryption (BitLocker, LUKS)
- Database encryption (TDE - Transparent Data Encryption)
- File-level encryption

**Em trânsito (in transit):**
- TLS/SSL (HTTPS)
- VPN (IPSec, OpenVPN)
- SSH/SFTP

**Em uso (in use):**
- Homomorphic encryption (pesquisa)
- Secure enclaves (Intel SGX, ARM TrustZone)

---

#### 🏷️ Classificação de Dados
**Níveis:**
- **Público:** Pode ser divulgado publicamente
- **Interno:** Apenas funcionários
- **Confidencial:** Acesso restrito
- **Secreto:** Máxima proteção

**Controles por nível:**
```

Público:

- Sem criptografia obrigatória
- Sem restrição de compartilhamento

Interno:

- Criptografia em trânsito
- Compartilhamento apenas interno

Confidencial:

- Criptografia em repouso e trânsito
- MFA obrigatório
- Auditoria de acesso

Secreto:

- Criptografia forte
- Acesso apenas com aprovação
- Auditoria detalhada
- DLP ativo

```
---

#### 🚫 DLP (Data Loss Prevention)
**Função:** Prevenir vazamento de dados sensíveis.

**Controles:**
- Bloquear envio de dados sensíveis por e-mail
- Bloquear upload para cloud não autorizado
- Bloquear cópia para USB
- Watermarking de documentos

**Soluções:**
- Symantec DLP
- McAfee DLP
- Microsoft Purview

---

#### 🗑️ Data Retention & Disposal
**Retenção:**
- Definir período de retenção por tipo de dado
- Conformidade com regulamentações (LGPD, GDPR)

**Descarte seguro:**
- **Dados digitais:** Wipe seguro (DoD 5220.22-M)
- **Mídias físicas:** Destruição física (shredding)
- **Certificado de destruição**

---

#### 💾 Backup
**Estratégia 3-2-1:**
- **3** cópias dos dados
- **2** tipos de mídia diferentes
- **1** cópia offsite

**Tipos:**
- **Full:** Backup completo
- **Incremental:** Apenas mudanças desde último backup
- **Differential:** Mudanças desde último full backup

**Testes:**
- Restauração regular (mensal)
- RTO (Recovery Time Objective)
- RPO (Recovery Point Objective)

---

## 🔗 Controles Transversais

### Identity and Access Management (IAM)
- Gestão centralizada de identidades
- Least privilege
- Revisão periódica de acessos
- Offboarding automático

---

### Security Monitoring (SIEM)
- Coleta centralizada de logs
- Correlação de eventos
- Alertas em tempo real
- Dashboards executivos

---

### Incident Response
- Playbooks documentados
- Equipe treinada
- Ferramentas preparadas
- Comunicação definida

---

## 📊 Exemplo Prático - Defesa Contra Ransomware

### Camada 1: Políticas
- ✅ Treinamento anti-phishing
- ✅ Política de backups

### Camada 2: Física
- ✅ Backups offsite em cofre

### Camada 3: Perímetro
- ✅ Firewall bloqueia IPs maliciosos
- ✅ IPS detecta tráfego C2

### Camada 4: Rede
- ✅ Segmentação impede lateral movement
- ✅ Monitoramento detecta anomalias

### Camada 5: Host
- ✅ EDR detecta comportamento de ransomware
- ✅ Antivírus bloqueia executável malicioso

### Camada 6: Aplicação
- ✅ Application whitelisting impede execução
- ✅ Logging registra tentativa

### Camada 7: Dados
- ✅ Backup permite restauração
- ✅ Criptografia protege dados em repouso

**Resultado:** Mesmo se uma camada falhar, outras protegem.

---

## 🎯 Princípios Complementares

### Least Privilege
Usuário tem apenas os acessos **mínimos necessários**.

### Separation of Duties
Nenhuma pessoa tem controle total sobre processo crítico.

### Fail Secure
Em caso de falha, sistema deve **fechar** (negar acesso).

### Defense by Obscurity
**NÃO é defesa real**, mas pode adicionar fricção para atacantes.

---

## 🔗 Links Relacionados

- [[CIA-Triad]]
- [[IAAA]]
- [[NIST-Cybersecurity]]
- [[CIS-Controls]]
- [[Zero-Trust]]

---

## 📚 Referências

- NIST SP 800-53 (Security and Privacy Controls)
- ISO 27001/27002
- CIS Controls
- SANS 20 Critical Security Controls