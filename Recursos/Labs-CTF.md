

# 🎮 Labs e CTF (Capture The Flag)

> **Tags:** #ctf #labs #pentest #hacking #practice #tryhackme #hackthebox #picoctf #wargames

---

## 📌 Visão Geral

**CTF (Capture The Flag)** são competições de segurança cibernética onde participantes resolvem desafios para encontrar "flags" (strings específicas que comprovam a solução).

🎯 **Objetivo:** Praticar habilidades de hacking ético, pentest e segurança ofensiva/defensiva em ambientes controlados.

---

## 🎯 Tipos de CTF

### 1️⃣ Jeopardy Style

**Formato:** Desafios independentes organizados por categorias.

**Categorias comuns:**
- 🌐 **Web:** SQL Injection, XSS, CSRF, LFI, RFI
- 🔐 **Crypto:** Criptografia, hashes, cifras clássicas
- 🔍 **Forensics:** Análise de memória, disk images, network captures
- 🔄 **Reverse Engineering:** Engenharia reversa de binários
- 💥 **Pwn/Binary Exploitation:** Buffer overflow, ROP chains
- 🕵️ **OSINT:** Open Source Intelligence
- 🔧 **Misc:** Desafios variados (steganography, programming)

**Pontuação:** Cada desafio tem pontos baseados na dificuldade.

**Exemplos:** PicoCTF, Google CTF, DEF CON CTF Quals

---

### 2️⃣ Attack-Defense

**Formato:** Equipes defendem seus próprios servidores enquanto atacam servidores adversários.

**Dinâmica:**
```

1. Cada equipe recebe servidor vulnerável idêntico
2. Defender: Corrigir vulnerabilidades, manter serviços funcionando
3. Atacar: Explorar vulnerabilidades nos servidores adversários
4. Pontos: Defesa bem-sucedida + ataques bem-sucedidos + uptime

```
**Exemplos:** DEF CON CTF Finals, RuCTF

---

### 3️⃣ King of the Hill

**Formato:** Múltiplas equipes competem pelo controle de uma máquina.

**Dinâmica:**
```

1. Explorar máquina vulnerável
2. Obter acesso root
3. Manter controle (kickar outros atacantes)
4. Pontos por tempo de controle

```
**Exemplos:** TryHackMe King of the Hill

---

## 🏆 Principais Plataformas de CTF

### 🟢 TryHackMe

**Site:** [tryhackme.com](https://tryhackme.com/)

**Nível:** Iniciante a Avançado

**Características:**
- ✅ **Guiado:** Rooms com instruções passo a passo
- ✅ **Navegador:** Máquinas acessíveis via navegador (OpenVPN opcional)
- ✅ **Paths:** Trilhas de aprendizado estruturadas
- ✅ **Gratuito + Premium**

**Paths Recomendados:**
```

Iniciante:

- Complete Beginner
- Pre Security
- Introduction to Cyber Security

Intermediário:

- Offensive Pentesting
- Cyber Defense
- Web Fundamentals

Avançado:

- Red Teaming
- SOC Level 1

```
**Rooms Populares:**
- **OWASP Top 10:** Vulnerabilidades web
- **Metasploit:** Framework de exploração
- **Nmap:** Scanning de rede
- **Burp Suite:** Web application testing
- **Blue:** Incident response
- **Ice:** Windows exploitation

---

### 🟠 Hack The Box

**Site:** [hackthebox.com](https://www.hackthebox.com/)

**Nível:** Intermediário a Avançado

**Características:**
- ✅ **Realista:** Máquinas simulam ambientes reais
- ✅ **Comunidade:** Fóruns, writeups (após resolver)
- ✅ **Ranking:** Sistema de pontos e rankings globais
- ✅ **Gratuito + VIP**

**Categorias de Máquinas:**
```

Active Machines (20):

- Máquinas ativas (não pode publicar writeups)
- Renovadas semanalmente

Retired Machines (300+):

- Máquinas antigas (writeups permitidos)
- Acesso apenas VIP

Challenges:

- Desafios específicos (crypto, web, forensics, etc)

Pro Labs:

- Ambientes corporativos simulados (AD, redes complexas)

```
**Dificuldades:**
- 🟢 Easy
- 🟡 Medium
- 🟠 Hard
- 🔴 Insane

**Máquinas Recomendadas (Easy):**
- **Lame:** Exploração básica
- **Legacy:** SMB vulnerável
- **Blue:** EternalBlue (MS17-010)
- **Netmon:** PRTG Network Monitor
- **Jerry:** Tomcat exploitation

---

### 🔵 PicoCTF

**Site:** [picoctf.org](https://picoctf.org/)

**Nível:** Iniciante

**Características:**
- ✅ **Educacional:** Focado em estudantes
- ✅ **Progressivo:** Desafios aumentam gradualmente em dificuldade
- ✅ **Gratuito**
- ✅ **Anual:** Competição principal uma vez por ano

**Categorias:**
- General Skills
- Cryptography
- Web Exploitation
- Forensics
- Binary Exploitation
- Reverse Engineering

---

### 🟣 OverTheWire

**Site:** [overthewire.org](https://overthewire.org/wargames/)

**Nível:** Iniciante a Avançado

**Características:**
- ✅ **SSH-based:** Acesso via SSH
- ✅ **Progressivo:** Cada nível ensina conceito novo
- ✅ **Gratuito**
- ✅ **Linux-focused**

**Wargames Recomendados:**

#### Bandit (Iniciante)
**Foco:** Comandos básicos de Linux

**Níveis:** 0-33

**Conceitos:**
- Navegação de diretórios
- Manipulação de arquivos
- Redirecionamento
- Pipes
- Permissões

**Exemplo:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-534atxvwa" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bandit Level 0</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ssh</span><span> bandit0@bandit.labs.overthewire.org </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2220</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Senha: bandit0</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Encontrar senha do próximo nível</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> readme
</span></code></pre></div>

---

#### Natas (Web)
**Foco:** Vulnerabilidades web

**Níveis:** 0-33

**Conceitos:**
- HTML/JavaScript
- SQL Injection
- XSS
- Command Injection
- File inclusion

---

#### Leviathan (Iniciante)
**Foco:** Exploração básica de binários

---

#### Krypton (Crypto)
**Foco:** Criptografia clássica

---

### 🔴 Root-Me

**Site:** [root-me.org](https://www.root-me.org/)

**Nível:** Iniciante a Avançado

**Características:**
- ✅ **Desafios variados:** 400+ challenges
- ✅ **Ranking global**
- ✅ **Gratuito**
- ✅ **Multilíngue:** Francês/Inglês

**Categorias:**
- App-Script
- App-System
- Cracking
- Cryptanalysis
- Forensic
- Network
- Programming
- Realist
- Steganography
- Web-Client
- Web-Server

---

### 🟡 VulnHub

**Site:** [vulnhub.com](https://www.vulnhub.com/)

**Nível:** Todos

**Características:**
- ✅ **VMs para download:** Executar localmente (VirtualBox/VMware)
- ✅ **Gratuito**
- ✅ **Comunidade:** Writeups disponíveis

**Máquinas Recomendadas:**
```

Iniciante:

- Mr-Robot: 1
- Basic Pentesting: 1
- Kioptrix: Level 1

Intermediário:

- Stapler: 1
- SickOs: 1.2
- PwnLab: init

Avançado:

- Vulnix
- Lord Of The Root

```
---

### 🟢 PortSwigger Web Security Academy

**Site:** [portswigger.net/web-security](https://portswigger.net/web-security)

**Nível:** Iniciante a Avançado

**Características:**
- ✅ **Focado em Web:** Vulnerabilidades web
- ✅ **Labs interativos:** Burp Suite integrado
- ✅ **Gratuito**
- ✅ **Certificação:** Burp Suite Certified Practitioner

**Tópicos:**
- SQL Injection
- XSS
- CSRF
- Clickjacking
- CORS
- XXE
- SSRF
- Authentication
- Access Control
- Business Logic
- WebSockets

---

### 🔵 CTFtime

**Site:** [ctftime.org](https://ctftime.org/)

**Descrição:** Calendário de CTFs e ranking de equipes.

**Uso:**
- Ver CTFs futuros
- Acompanhar rankings
- Encontrar writeups

---

## 🛠️ Ferramentas Essenciais para CTF

### Reconhecimento
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7k6ixxik8" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Nmap</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sC</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sV</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-oN</span><span> scan.txt </span><span class="token" style="color:rgb(247, 140, 108)">10.10</span><span>.10.10
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gobuster (directory bruteforce)</span><span>
</span><span>gobuster </span><span class="token" style="color:rgb(130, 170, 255)">dir</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> http://10.10.10.10 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-w</span><span> /usr/share/wordlists/dirb/common.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Nikto (web scanner)</span><span>
</span><span>nikto </span><span class="token parameter" style="color:rgb(214, 222, 235)">-h</span><span> http://10.10.10.10
</span></code></pre></div>

---

### Exploração Web
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-6o58h57p7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Burp Suite (GUI)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Interceptar e modificar requisições HTTP</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SQLMap (SQL Injection)</span><span>
</span><span>sqlmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;http://10.10.10.10/page.php?id=1&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dbs</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># XSStrike (XSS)</span><span>
</span><span>python3 xsstrike.py </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;http://10.10.10.10/search?q=test&quot;</span><span>
</span></code></pre></div>

---

### Exploração de Sistemas
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-6585m0ijx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Metasploit</span><span>
</span>msfconsole
<!-- -->use exploit/windows/smb/ms17_010_eternalblue
<span></span><span class="token" style="color:rgb(255, 203, 139)">set</span><span> RHOSTS </span><span class="token" style="color:rgb(247, 140, 108)">10.10</span><span>.10.10
</span>exploit
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SearchSploit (buscar exploits)</span><span>
</span><span>searchsploit apache </span><span class="token" style="color:rgb(247, 140, 108)">2.4</span><span>.49
</span></code></pre></div>

---

### Privilege Escalation
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4dky5wbnp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># LinPEAS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wget</span><span> https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> +x linpeas.sh
</span>./linpeas.sh
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Windows</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># WinPEAS</span><span>
</span><span>.</span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>winPEASx64.exe
</span></code></pre></div>

---

### Criptografia
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-tx8v7syhl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># CyberChef (online)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># https://gchq.github.io/CyberChef/</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># John the Ripper (password cracking)</span><span>
</span><span>john </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>wordlist</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>usr</span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>share</span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>wordlists</span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>rockyou</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>txt </span><span class="token" style="color:rgb(130, 170, 255)">hash</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Hashcat (GPU cracking)</span><span>
</span><span>hashcat </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>m </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>a </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">hash</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>txt rockyou</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>txt
</span></code></pre></div>

---

### Steganografia
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ng23o3otw" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Steghide</span><span>
</span><span>steghide extract </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sf</span><span> imagem.jpg
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Binwalk</span><span>
</span><span>binwalk </span><span class="token parameter" style="color:rgb(214, 222, 235)">-e</span><span> arquivo.jpg
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Strings</span><span>
</span><span>strings arquivo.jpg </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> flag
</span></code></pre></div>

---

### Forensics
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-or791o35a" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Volatility (memory forensics)</span><span>
</span><span>volatility </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> memory.dump imageinfo
</span><span>volatility </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> memory.dump </span><span class="token parameter" style="color:rgb(214, 222, 235)">--profile</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>Win7SP1x64 pslist
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Wireshark (network analysis)</span><span>
</span>wireshark capture.pcap
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Autopsy (disk forensics)</span><span>
</span>autopsy
</code></pre></div>

---

## 📝 Metodologia para Resolver CTFs

### 1️⃣ Reconhecimento
```

1. Ler descrição do desafio
2. Identificar categoria (web, crypto, forensics, etc)
3. Coletar informações iniciais
    - Nmap scan
    - Gobuster/Dirbuster
    - Verificar código-fonte (view-source)

```
---

### 2️⃣ Enumeração
```

1. Listar todos os serviços/portas
2. Identificar versões de software
3. Buscar vulnerabilidades conhecidas (SearchSploit, CVE)
4. Enumerar usuários, diretórios, arquivos

```
---

### 3️⃣ Exploração
```

1. Testar vulnerabilidades identificadas
2. Explorar manualmente ou com ferramentas
3. Obter acesso inicial (shell)

```
---

### 4️⃣ Privilege Escalation
```

1. Enumerar sistema (LinPEAS, WinPEAS)
2. Identificar vetores de escalação:
    - SUID binaries
    - Sudo misconfiguration
    - Kernel exploits
    - Scheduled tasks
3. Explorar e obter root/administrator

```
---

### 5️⃣ Capturar Flag
```

1. Localizar flag (geralmente em /root/flag.txt ou C:\Users\Administrator\flag.txt)
2. Submeter flag
3. Documentar passos (writeup)

```
---

## 📚 Recursos de Aprendizado

### Writeups
- **Medium:** Buscar "CTF writeup [nome do desafio]"
- **GitHub:** Repositórios de writeups
- **0xdf.gitlab.io:** Writeups de Hack The Box
- **IppSec (YouTube):** Vídeos de HTB

---

### Canais do YouTube
- **IppSec:** Walkthroughs de Hack The Box
- **John Hammond:** CTFs, malware analysis
- **LiveOverflow:** Binary exploitation, CTFs
- **NetworkChuck:** Iniciante-friendly

---

### Livros
- **The Hacker Playbook 3** - Peter Kim
- **Penetration Testing** - Georgia Weidman
- **Web Application Hacker's Handbook** - Dafydd Stuttard

---

### Wordlists
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0v8uvwjkl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SecLists (essencial!)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">git</span><span> clone https://github.com/danielmiessler/SecLists.git
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># RockYou (senhas)</span><span>
</span>/usr/share/wordlists/rockyou.txt
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Dirb (diretórios web)</span><span>
</span>/usr/share/wordlists/dirb/common.txt
</code></pre></div>

---

## 🏅 Certificações Relacionadas

- **OSCP** (Offensive Security Certified Professional)
- **eJPT** (eLearnSecurity Junior Penetration Tester)
- **CEH** (Certified Ethical Hacker)
- **PNPT** (Practical Network Penetration Tester)

---

## 🔗 Links Relacionados

- [[Nmap]]
- [[Metasploit]]
- [[Burp-Suite]]
- [[OSINT-Fundamentos]]
- [[Esteganografia]]
- [[Certificacoes-Recomendadas]]

---

## 📚 Referências

- TryHackMe: [tryhackme.com](https://tryhackme.com/)
- Hack The Box: [hackthebox.com](https://www.hackthebox.com/)
- PicoCTF: [picoctf.org](https://picoctf.org/)
- OverTheWire: [overthewire.org](https://overthewire.org/)
- CTFtime: [ctftime.org](https://ctftime.org/)