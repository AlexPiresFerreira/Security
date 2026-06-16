
# ⚔️ Tipos de Ataques Cibernéticos

> **Tags:** #ataques #ameacas #seguranca #ddos #phishing #malware #sql-injection

---

## 📌 Visão Geral

Classificação dos principais tipos de ataques cibernéticos organizados por categoria.

---

## 🌐 Ataques de Rede

### DDoS / DoS (Denial of Service)
**Descrição:** Sobrecarregam sistemas ou redes com tráfego excessivo, tornando serviços indisponíveis.

**Diferença:**
- **DoS:** Ataque de um único dispositivo
- **DDoS:** Ataque distribuído de múltiplos dispositivos (botnets)

**Impacto:** Disponibilidade

**Contramedidas:**
- Rate limiting
- WAF (Web Application Firewall)
- CDN (Cloudflare, Akamai)
- Monitoramento de tráfego

---

### Man-in-the-Middle (MitM)
**Descrição:** Interceptação e possível alteração de comunicação entre duas partes.

**Técnicas:**
- ARP Spoofing
- DNS Spoofing
- Session Hijacking

**Contramedidas:**
- HTTPS/TLS
- VPN
- Certificados digitais
- HSTS

---

### Sniffing
**Descrição:** Captura de tráfego de rede para interceptar dados sensíveis.

**Ferramentas:**
- Wireshark
- tcpdump
- Ettercap

**Contramedidas:**
- Criptografia (TLS/SSL)
- VPN
- Segmentação de rede

---

## 🌐 Ataques Web

### SQL Injection
**Descrição:** Injeção de comandos SQL maliciosos para manipular bancos de dados.

**Exemplo:**

sql ' OR '1'='1' --

**Impacto:**
- Roubo de dados
- Modificação de dados
- Bypass de autenticação

**Contramedidas:**
- Prepared Statements
- ORM (Object-Relational Mapping)
- WAF
- Input validation

---

### XSS (Cross-Site Scripting)
**Descrição:** Injeção de scripts maliciosos em sites para atacar usuários.

**Tipos:**
- **Reflected XSS:** Script refletido na resposta
- **Stored XSS:** Script armazenado no servidor
- **DOM-based XSS:** Manipulação do DOM

**Exemplo:**

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">html</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-g1b8ejx8t" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-html" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">script</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span class="token script language-javascript" style="color:rgb(130, 170, 255)">alert</span><span class="token script language-javascript" style="color:rgb(199, 146, 234)">(</span><span class="token script language-javascript dom" style="color:rgb(214, 222, 235)">document</span><span class="token script language-javascript" style="color:rgb(199, 146, 234)">.</span><span class="token script language-javascript property-access">cookie</span><span class="token script language-javascript" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">script</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span></code></pre></div>


**Contramedidas:**
- Content Security Policy (CSP)
- Output encoding
- Input sanitization

---

### CSRF (Cross-Site Request Forgery)
**Descrição:** Força usuário autenticado a executar ações não intencionais.

**Contramedidas:**
- CSRF Tokens
- SameSite Cookies
- Verificação de Referer

---

## 💻 Ataques de Sistema

### Buffer Overflow
**Descrição:** Exploração de falhas no armazenamento de dados em memória para executar código malicioso.

**Contramedidas:**
- ASLR (Address Space Layout Randomization)
- DEP (Data Execution Prevention)
- Stack canaries
- Linguagens memory-safe (Rust, Go)

---

### Privilege Escalation
**Descrição:** Obtenção de privilégios elevados no sistema.

**Tipos:**
- **Vertical:** Usuário comum → Admin
- **Horizontal:** Usuário A → Usuário B

**Contramedidas:**
- Princípio do menor privilégio
- Patches atualizados
- Auditoria de permissões

---

## 📧 Ataques Sociais

### Phishing
**Descrição:** Fraude que engana usuários para fornecer dados sensíveis via e-mails falsos ou links maliciosos.

**Variações:**
- **Spear Phishing:** Ataque direcionado a pessoas específicas
- **Whaling:** Focado em altos executivos
- **Vishing:** Phishing por voz (telefone)
- **Smishing:** Phishing por SMS

**Contramedidas:**
- Treinamento de usuários
- Filtros de e-mail
- MFA
- Verificação de remetentes

---

### Engenharia Social
**Descrição:** Manipulação psicológica de pessoas para obter informações ou acesso não autorizado.

**Técnicas:**
- **Pretexting:** Criar cenário falso
- **Baiting:** Oferecer algo atraente
- **Tailgating:** Seguir pessoa autorizada
- **Shoulder Surfing:** Observar digitação
- **Dumpster Diving:** Vasculhar lixo físico/digital

---

## 🔐 Ataques de Credenciais

### Brute Force
**Descrição:** Tentativa sistemática de todas as combinações possíveis de senha.

**Contramedidas:**
- Rate limiting
- Account lockout
- CAPTCHA
- MFA

---

### Password Cracking
**Descrição:** Quebra de senhas usando métodos como:
- **Dictionary Attack:** Lista de palavras comuns
- **Rainbow Tables:** Hashes pré-computados
- **Hybrid Attack:** Combinação de métodos

**Ferramentas:**
- John the Ripper
- Hashcat
- Hydra

---

### Credential Stuffing
**Descrição:** Uso de credenciais vazadas para acessar outras contas.

**Contramedidas:**
- MFA
- Monitoramento de logins suspeitos
- Verificar vazamentos (Have I Been Pwned)

---

## 🦠 Malware (Ver arquivo separado)
[[Malwares]]

---

## 🌐 Ataques Específicos

### DNS Spoofing
**Descrição:** Falsificação de registros DNS para redirecionar tráfego a sites falsos.

**Contramedidas:**
- DNSSEC
- DNS over HTTPS (DoH)
- DNS over TLS (DoT)

---

### ARP Spoofing
**Descrição:** Falsificação de tabelas ARP para interceptar tráfego local.

**Contramedidas:**
- Static ARP entries
- ARP inspection
- Segmentação de rede

---

### WiFi Hacking
**Descrição:** Acesso não autorizado a redes sem fio.

**Técnicas:**
- WPA2 Cracking
- Evil Twin (AP falso)
- Deauth Attack
- WPS Brute Force

**Ferramentas:**
- Aircrack-ng
- Kismet
- Reaver
- Wifite

**Contramedidas:**
- WPA3
- Desabilitar WPS
- MAC filtering (limitado)
- 802.1X

---

### Roubo de Cookies
**Descrição:** Captura de cookies de sessão para sequestrar sessões de usuários.

**Contramedidas:**
- HttpOnly flag
- Secure flag
- SameSite attribute
- Cookie encryption

---

## 🔗 Links Relacionados
- [[Malwares]]
- [[Cyber-Kill-Chain]]
- [[OWASP-Top-10]]
- [[MITRE-ATT&CK]]

---

## 📚 Referências
- OWASP Top 10
- MITRE ATT&CK Framework
- NIST Cybersecurity Framework
