
# 👥 Hackers e Teams (Red, Blue, Purple)

> **Tags:** #hackers #redteam #blueteam #purpleteam #pentest #ethical-hacking #security-teams

---

## 📌 Visão Geral

No contexto de segurança cibernética, os profissionais são frequentemente categorizados por "chapéus" (hats) baseados em suas intenções e atividades.

---

## 🎩 Tipos de Hackers

### ⚪ White Hat (Hacker Ético)

**Definição:** Profissionais de segurança que usam suas habilidades para **proteger** sistemas e identificar vulnerabilidades **legalmente**.

**Atividades:**
- Pentesting autorizado
- Bug bounty hunting
- Auditoria de segurança
- Desenvolvimento de ferramentas defensivas
- Consultoria em segurança

**Características:**
- ✅ Trabalham com **autorização**
- ✅ Seguem **código de ética**
- ✅ **Divulgação responsável** de vulnerabilidades
- ✅ Certificações profissionais (OSCP, CEH, etc)

**Exemplos:**
- Pesquisadores de segurança
- Pentesters
- Analistas de segurança
- Bug bounty hunters

---

### ⚫ Black Hat (Hacker Malicioso)

**Definição:** Indivíduos que exploram vulnerabilidades para **ganho pessoal** ou **causar danos**, violando leis.

**Atividades:**
- Roubo de dados
- Fraude financeira
- Ransomware
- Espionagem industrial
- Venda de exploits

**Características:**
- ❌ Agem **sem autorização**
- ❌ **Violam leis**
- ❌ Motivação: lucro, vingança, ideologia
- ❌ Podem fazer parte de grupos criminosos

**Consequências:**
- Prisão
- Multas pesadas
- Processos civis

---

### 🎩 Grey Hat

**Definição:** Hackers que operam em uma **zona cinzenta** entre ético e malicioso.

**Atividades:**
- Descobrir vulnerabilidades **sem autorização**
- Divulgar vulnerabilidades publicamente (às vezes sem avisar o vendor)
- Hackear por curiosidade (sem intenção maliciosa)

**Características:**
- ⚠️ Agem sem autorização (ilegal)
- ⚠️ Não têm intenção maliciosa direta
- ⚠️ Podem divulgar vulnerabilidades publicamente
- ⚠️ Zona ética ambígua

**Exemplo:**
- Hacker descobre vulnerabilidade, avisa a empresa publicamente no Twitter sem dar tempo para patch

---

### 🟢 Green Hat (Iniciante)

**Definição:** Hackers **iniciantes** que estão aprendendo.

**Características:**
- 📚 Em fase de aprendizado
- 🔧 Usam ferramentas prontas
- 🎯 Motivação: aprender hacking
- ⚠️ Podem causar danos acidentalmente

---

### 🔵 Blue Hat (Testadores Externos)

**Definição:** Profissionais **externos** contratados para testar segurança antes de lançamentos.

**Atividades:**
- Testes de segurança pré-lançamento
- Bug bounty events
- Validação de correções

**Exemplo:**
- Microsoft BlueHat Conference

---

### 🔴 Red Hat (Vigilantes)

**Definição:** Hackers que **atacam black hats** para desmantelar suas operações.

**Atividades:**
- Contra-ataques a criminosos
- Derrubada de servidores C2
- Sabotagem de operações criminosas

**⚠️ Nota:** Ainda é **ilegal** em muitas jurisdições.

---

### 🎭 Hacktivistas

**Definição:** Hackers motivados por **causas políticas ou sociais**.

**Atividades:**
- Defacing de sites governamentais
- DDoS contra alvos específicos
- Vazamento de dados (doxing)
- Operações de protesto

**Exemplos:**
- Anonymous
- LulzSec

---

## 🎯 Security Teams

### 🔴 Red Team (Ataque)

**Definição:** Equipe que simula **atacantes reais** para testar as defesas de uma organização.

**Objetivo:** Identificar falhas de segurança através de ataques simulados.

#### Atividades

##### 🔍 Reconhecimento (OSINT)
- Coleta de informações públicas
- Mapeamento de infraestrutura
- Identificação de funcionários
- Análise de redes sociais

##### 🚪 Acesso Inicial
- Phishing (spear phishing)
- Exploração de vulnerabilidades públicas
- Engenharia social
- Physical security testing

##### 💻 Pós-Exploração
- Escalação de privilégios
- Movimentação lateral
- Persistência
- Exfiltração de dados

##### 📊 Relatório
- Documentação detalhada
- Evidências (screenshots, logs)
- Recomendações de remediação
- Apresentação executiva

---

#### Ferramentas Red Team

##### Reconhecimento

- Nmap
- Masscan
- theHarvester
- Shodan
- Maltego

##### Exploração

- Metasploit
- Cobalt Strike
- Empire/PowerShell Empire
- Covenant

##### Pós-Exploração

- Mimikatz
- BloodHound
- CrackMapExec
- Impacket

##### C2 (Command & Control)

- Cobalt Strike
- Sliver
- Mythic

```
---

#### Metodologias Red Team

##### PTES (Penetration Testing Execution Standard)
```

1. Pre-engagement Interactions
2. Intelligence Gathering
3. Threat Modeling
4. Vulnerability Analysis
5. Exploitation
6. Post Exploitation
7. Reporting

##### OSSTMM (Open Source Security Testing Methodology Manual)
- Foco em testes sistemáticos e repetíveis

---

### 🔵 Blue Team (Defesa)

**Definição:** Equipe responsável por **defender** a infraestrutura contra ataques.

**Objetivo:** Detectar, responder e mitigar ameaças.

#### Atividades

##### 🛡️ Prevenção
- Hardening de sistemas
- Patch management
- Configuração de firewalls/IPS
- Implementação de controles de segurança

##### 👁️ Monitoramento
- SIEM (Security Information and Event Management)
- IDS/IPS
- EDR/XDR
- Log analysis

##### 🔍 Detecção
- Threat hunting
- Análise de anomalias
- Correlação de eventos
- IOC matching

##### 🚨 Resposta a Incidentes
- Contenção
- Erradicação
- Recuperação
- Lições aprendidas

---

#### Ferramentas Blue Team

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-8uo6lim83" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SIEM</span><span>
</span>- Splunk
<span>- ELK Stack </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>Elasticsearch, Logstash, Kibana</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>- Wazuh
<!-- -->- Graylog
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># IDS/IPS</span><span>
</span>- Suricata
<!-- -->- Snort
<span>- Zeek </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>Bro</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># EDR/XDR</span><span>
</span>- CrowdStrike Falcon
<!-- -->- SentinelOne
<span>- Microsoft Defender </span><span class="token" style="color:rgb(127, 219, 202)">for</span><span> Endpoint
</span>- Carbon Black
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Network Monitoring</span><span>
</span>- Wireshark
<!-- -->- tcpdump
<!-- -->- NetworkMiner
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Threat Intelligence</span><span>
</span>- MISP
<!-- -->- OpenCTI
<!-- -->- ThreatConnect
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Forensics</span><span>
</span>- Autopsy
<span>- Volatility </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>memory forensics</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>- FTK Imager
</code></pre></div>

---

#### Frameworks Blue Team

##### NIST Cybersecurity Framework
```

1. Identify
2. Protect
3. Detect
4. Respond
5. Recover

```
##### MITRE ATT&CK (Defensive Use)
- Mapear detecções existentes
- Identificar gaps de cobertura
- Priorizar investimentos em segurança

---

### 🟣 Purple Team (Colaboração)

**Definição:** **Colaboração** entre Red Team e Blue Team para melhorar as defesas.

**Objetivo:** Maximizar a eficácia de ambos os times através de feedback contínuo.

#### Como Funciona
```

┌─────────────┐ ┌─────────────┐ │ Red Team │ ←────→ │ Blue Team │ │ (Ataque) │ │ (Defesa) │ └─────────────┘ └─────────────┘ │ │ └───────────┬───────────┘ │ ┌──────▼──────┐ │ Purple Team │ │(Colaboração)│ └─────────────┘

```
#### Atividades Purple Team

##### 🎯 Exercícios Coordenados
1. **Red Team** executa ataque específico
2. **Blue Team** tenta detectar
3. **Análise conjunta:**
   - O que funcionou?
   - O que falhou?
   - Como melhorar?

##### 📊 Validação de Controles
- Testar regras de SIEM
- Validar alertas de IDS/IPS
- Verificar eficácia de EDR

##### 🔧 Melhoria Contínua
- Ajustar detecções
- Criar novas regras
- Atualizar playbooks

---

#### Ferramentas Purple Team

##### Atomic Red Team
**Descrição:** Biblioteca de testes para simular técnicas do MITRE ATT&CK.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-69762f68z" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">IEX</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">IWR</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1&#x27;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>UseBasicParsing</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Install-AtomicRedTeam</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>getAtomics
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar teste</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Invoke-AtomicTest</span><span> T1003</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>001  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># LSASS Memory Dump</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Blue Team verifica se detectou</span><span>
</span></code></pre></div>

**Site:** [atomicredteam.io](https://atomicredteam.io)

---

##### CALDERA
**Descrição:** Plataforma de emulação de adversários automatizada (MITRE).

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-b88cjt04g" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">git</span><span> clone https://github.com/mitre/caldera.git
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">cd</span><span> caldera
</span><span>pip3 </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> requirements.txt
</span><span>python3 server.py </span><span class="token parameter" style="color:rgb(214, 222, 235)">--insecure</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Acessar: http://localhost:8888</span><span>
</span></code></pre></div>

**Recursos:**
- Emulação de APTs
- Automação de ataques
- Integração com MITRE ATT&CK

---

##### Infection Monkey
**Descrição:** Ferramenta de simulação de breach e lateral movement.

**Site:** [guardicore.com/infectionmonkey](https://www.guardicore.com/infectionmonkey/)

---

### 🟡 Yellow Team (Builders)

**Definição:** Equipe de **desenvolvedores** que constrói sistemas seguros.

**Atividades:**
- Secure coding
- Code review
- DevSecOps
- Security testing em CI/CD

---

### ⚪ White Team (Árbitros)

**Definição:** Equipe que **gerencia e arbitra** exercícios entre Red e Blue Teams.

**Atividades:**
- Planejamento de exercícios
- Definição de regras de engajamento
- Monitoramento de exercícios
- Avaliação de resultados

---

## 🎮 Exercícios e Competições

### Capture The Flag (CTF)
**Formato:** Competição onde equipes resolvem desafios de segurança.

**Categorias:**
- Web exploitation
- Cryptography
- Forensics
- Reverse engineering
- Binary exploitation

**Plataformas:**
- [CTFtime.org](https://ctftime.org/)
- [PicoCTF](https://picoctf.org/)
- [Hack The Box](https://www.hackthebox.com/)

---

### Red Team vs Blue Team Exercises
**Formato:** Simulação realista de ataque e defesa.

**Duração:** Dias a semanas

**Objetivo:** Testar capacidade de detecção e resposta

---

## 📊 Comparação Red vs Blue vs Purple

| Aspecto | Red Team | Blue Team | Purple Team |
|---------|----------|-----------|-------------|
| **Foco** | Ataque | Defesa | Colaboração |
| **Objetivo** | Encontrar falhas | Proteger sistemas | Melhorar ambos |
| **Mentalidade** | Ofensiva | Defensiva | Cooperativa |
| **Ferramentas** | Exploits, C2 | SIEM, IDS/IPS | Ambos |
| **Resultado** | Relatório de vulnerabilidades | Logs, alertas | Melhoria contínua |

---

## 🎯 Carreira em Security Teams

### Red Team
**Habilidades necessárias:**
- Pentesting
- Exploração de vulnerabilidades
- Programação (Python, PowerShell, C)
- OSINT
- Engenharia social

**Certificações:**
- OSCP (Offensive Security Certified Professional)
- GPEN (GIAC Penetration Tester)
- CRTP (Certified Red Team Professional)

---

### Blue Team
**Habilidades necessárias:**
- Análise de logs
- Incident response
- Threat hunting
- Conhecimento de SIEM
- Análise de malware

**Certificações:**
- GCIH (GIAC Certified Incident Handler)
- GCIA (GIAC Certified Intrusion Analyst)
- CySA+ (CompTIA Cybersecurity Analyst)

---

### Purple Team
**Habilidades necessárias:**
- Conhecimento de Red e Blue Team
- Comunicação eficaz
- Análise de gaps de segurança
- Conhecimento de frameworks (MITRE ATT&CK)

---

## 🔗 Links Relacionados

- [[MITRE-ATT&CK]]
- [[Cyber-Kill-Chain]]
- [[Adversarios]]
- [[OSINT-Fundamentos]]
- [[Nmap]]

---

## 📚 Referências

- MITRE ATT&CK: [attack.mitre.org](https://attack.mitre.org)
- Atomic Red Team: [atomicredteam.io](https://atomicredteam.io)
- CALDERA: [github.com/mitre/caldera](https://github.com/mitre/caldera)
- PTES: [pentest-standard.org](http://www.pentest-standard.org/)
