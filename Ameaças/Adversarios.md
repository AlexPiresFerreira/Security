
# 🎭 Adversários e Atores de Ameaças

> **Tags:** #adversarios #threat-actors #apt #cybercrime #hacktivism #nation-state #insider-threat

---

## 📌 Visão Geral

**Adversários** (ou **Threat Actors**) são indivíduos, grupos ou organizações que representam ameaças à segurança cibernética. Compreender suas motivações, capacidades e táticas é essencial para uma defesa eficaz.

---

## 🎯 Classificação por Motivação

### 💰 Financeiro (Cybercrime)
**Objetivo:** Lucro financeiro

**Atividades:**
- Ransomware
- Fraude bancária
- Roubo de cartões de crédito
- Cryptojacking
- Venda de dados roubados

**Exemplos:**
- Grupos de ransomware (LockBit, REvil, Conti)
- Banking trojans (Zeus, Emotet)
- Carding forums

---

### 🏛️ Espionagem (Nation-State / APT)
**Objetivo:** Roubo de informações estratégicas, propriedade intelectual, segredos governamentais

**Atividades:**
- Espionagem industrial
- Roubo de propriedade intelectual
- Comprometimento de infraestrutura crítica
- Campanhas de desinformação

**Exemplos:**
- APT28 (Fancy Bear) - Rússia
- APT29 (Cozy Bear) - Rússia
- APT1 (Comment Crew) - China
- Lazarus Group - Coreia do Norte

---

### 🎭 Hacktivismo
**Objetivo:** Protesto político, social ou ideológico

**Atividades:**
- Defacing de sites
- DDoS contra alvos específicos
- Vazamento de dados (doxing)
- Operações de desinformação

**Exemplos:**
- Anonymous
- LulzSec
- Syrian Electronic Army

---

### 🔬 Pesquisa e Educação
**Objetivo:** Aprendizado, pesquisa acadêmica, bug bounty

**Atividades:**
- Pesquisa de vulnerabilidades
- Bug bounty hunting
- Desenvolvimento de exploits (divulgação responsável)
- Educação em segurança

**Exemplos:**
- Pesquisadores de segurança
- Bug bounty hunters
- White hat hackers

---

### 😈 Insider Threat (Ameaça Interna)
**Objetivo:** Variado (vingança, ganho financeiro, espionagem)

**Características:**
- Acesso legítimo ao sistema
- Conhecimento interno
- Difícil de detectar

**Tipos:**
- **Malicioso:** Intenção de causar dano
- **Negligente:** Erro humano, falta de treinamento
- **Comprometido:** Funcionário coagido ou manipulado

**Exemplos:**
- Edward Snowden (NSA)
- Chelsea Manning (WikiLeaks)
- Funcionários insatisfeitos

---

### 🎮 Script Kiddies
**Objetivo:** Diversão, reconhecimento, vandalismo

**Características:**
- Baixa habilidade técnica
- Usam ferramentas prontas
- Ataques oportunistas
- Motivação: ego, diversão

**Atividades:**
- Defacing de sites
- DDoS usando ferramentas prontas
- Uso de exploits públicos

---

## 🌍 APT (Advanced Persistent Threat)

### Definição

**APT** são grupos de atacantes **altamente qualificados**, geralmente patrocinados por **estados-nação**, que realizam operações de **longo prazo** contra alvos específicos.

### Características

- ✅ **Advanced:** Técnicas sofisticadas, zero-days
- ✅ **Persistent:** Operações de longo prazo (meses/anos)
- ✅ **Threat:** Objetivo claro e estratégico
- ✅ **Recursos:** Financiamento robusto
- ✅ **Stealth:** Foco em não ser detectado

---

### Principais Grupos APT

#### 🇷🇺 Rússia

##### APT28 (Fancy Bear / Sofacy)
**Afiliação:** GRU (Inteligência Militar Russa)

**Alvos:**
- Governos (EUA, Europa)
- Militares
- Organizações internacionais (OTAN, OSCE)
- Mídia

**Táticas:**
- Spear phishing
- Exploits zero-day
- Malware customizado (X-Agent, Sofacy)

**Ataques notáveis:**
- DNC hack (2016)
- Ataque à TV5Monde (2015)
- Olympic Destroyer (2018)

**MITRE ATT&CK:** [G0007](https://attack.mitre.org/groups/G0007/)

---

##### APT29 (Cozy Bear / The Dukes)
**Afiliação:** SVR (Serviço de Inteligência Externa da Rússia)

**Alvos:**
- Governos ocidentais
- Think tanks
- Setor de saúde (vacinas COVID-19)

**Táticas:**
- Spear phishing sofisticado
- Comprometimento de supply chain
- Malware stealth (WellMess, WellMail)

**Ataques notáveis:**
- SolarWinds (2020)
- DNC hack (2016)
- Ataques a pesquisas de vacinas (2020)

**MITRE ATT&CK:** [G0016](https://attack.mitre.org/groups/G0016/)

---

#### 🇨🇳 China

##### APT1 (Comment Crew)
**Afiliação:** PLA Unit 61398 (Exército de Libertação Popular)

**Alvos:**
- Empresas ocidentais
- Propriedade intelectual
- Infraestrutura crítica

**Táticas:**
- Spear phishing em massa
- RATs (Remote Access Trojans)
- Roubo de propriedade intelectual

**Ataques notáveis:**
- Mandiant Report (2013) - expôs o grupo

**MITRE ATT&CK:** [G0006](https://attack.mitre.org/groups/G0006/)

---

##### APT10 (MenuPass / Stone Panda)
**Afiliação:** Ministério de Segurança do Estado (MSS)

**Alvos:**
- Provedores de serviços gerenciados (MSPs)
- Setor de saúde
- Telecomunicações
- Aeroespacial

**Táticas:**
- Comprometimento de MSPs (supply chain)
- Malware customizado (PlugX, ChChes)
- Living-off-the-land techniques

**Ataques notáveis:**
- Operation Cloud Hopper (2016-2017)

**MITRE ATT&CK:** [G0045](https://attack.mitre.org/groups/G0045/)

---

#### 🇰🇵 Coreia do Norte

##### Lazarus Group (Hidden Cobra)
**Afiliação:** Reconnaissance General Bureau (RGB)

**Alvos:**
- Instituições financeiras
- Exchanges de criptomoedas
- Setor de entretenimento
- Infraestrutura crítica

**Táticas:**
- Wiper malware
- Ransomware (WannaCry)
- Roubo de criptomoedas
- Spear phishing

**Ataques notáveis:**
- Sony Pictures hack (2014)
- WannaCry ransomware (2017)
- Bangladesh Bank heist (US$ 81 milhões, 2016)
- Ronin Network hack (US$ 600 milhões, 2022)

**MITRE ATT&CK:** [G0032](https://attack.mitre.org/groups/G0032/)

---

#### 🇮🇷 Irã

##### APT33 (Elfin)
**Afiliação:** Governo Iraniano

**Alvos:**
- Setor de energia (Arábia Saudita, EUA)
- Aviação
- Petroquímicas

**Táticas:**
- Spear phishing
- Wiper malware (Shamoon)
- Credential harvesting

**Ataques notáveis:**
- Ataques à Saudi Aramco

**MITRE ATT&CK:** [G0064](https://attack.mitre.org/groups/G0064/)

---

##### APT34 (OilRig / Helix Kitten)
**Afiliação:** Governo Iraniano

**Alvos:**
- Oriente Médio (governos, energia)
- Setor financeiro

**Táticas:**
- Spear phishing com temas regionais
- Malware customizado (TwoFace, Bondupdater)
- DNS tunneling

**MITRE ATT&CK:** [G0049](https://attack.mitre.org/groups/G0049/)

---

#### 🇻🇳 Vietnã

##### APT32 (OceanLotus)
**Afiliação:** Governo Vietnamita

**Alvos:**
- Governos do Sudeste Asiático
- Dissidentes vietnamitas
- Empresas estrangeiras

**Táticas:**
- Spear phishing sofisticado
- Malware multiplataforma (Windows, macOS, Linux)
- Watering hole attacks

**MITRE ATT&CK:** [G0050](https://attack.mitre.org/groups/G0050/)

---

## 💰 Grupos de Ransomware

### LockBit
**Modelo:** Ransomware-as-a-Service (RaaS)

**Características:**
- Afiliados (parceiros que executam ataques)
- Criptografia rápida
- Double extortion (criptografia + vazamento)
- Site de vazamento na dark web

**Alvos:** Empresas de todos os tamanhos, setores variados

---

### REvil (Sodinokibi)
**Status:** Desmantelado (2022)

**Características:**
- RaaS
- Ataques de alto perfil
- Exigências de resgate milionárias

**Ataques notáveis:**
- Kaseya VSA (2021) - afetou 1500+ empresas
- JBS Foods (US$ 11 milhões de resgate)

---

### Conti
**Status:** Desmantelado (2022)

**Características:**
- RaaS
- Operação profissional (estrutura corporativa)
- Vazamento de código-fonte (2022)

**Ataques notáveis:**
- Costa Rica (declarou emergência nacional)
- Mais de 1000 vítimas

---

### BlackCat (ALPHV)
**Características:**
- Escrito em Rust (multiplataforma)
- RaaS
- Triple extortion (criptografia + vazamento + DDoS)

---

## 🔗 Recursos para Rastreamento de APTs

### MITRE ATT&CK Groups
**Site:** [attack.mitre.org/groups](https://attack.mitre.org/groups/)

**Recursos:**
- Lista completa de grupos APT
- TTPs (Tactics, Techniques, Procedures)
- Software utilizado

---

### Malpedia
**Site:** [malpedia.caad.fkie.fraunhofer.de](https://malpedia.caad.fkie.fraunhofer.de/)

**Recursos:**
- Catálogo de malware
- Atribuição a grupos
- Análises técnicas

---

### APT Notes
**GitHub:** [github.com/aptnotes/data](https://github.com/aptnotes/data)

**Recursos:**
- Coleção de relatórios de APT
- Papers técnicos
- Atribuição

---

### Threat Actor Map
**Site:** [aptmap.netlify.app](https://aptmap.netlify.app/)

**Recursos:**
- Mapa visual de APTs
- Relações entre grupos
- Aliases

---

## 🎯 Indicadores de Comprometimento (IOCs)

### O que são IOCs?

**IOCs (Indicators of Compromise)** são evidências forenses que indicam que um sistema foi comprometido.

### Tipos de IOCs

#### 🌐 Network-based
- IPs maliciosos
- Domínios C2
- URLs maliciosas
- Padrões de tráfego

#### 💾 Host-based
- Hashes de arquivos (MD5, SHA-256)
- Nomes de arquivos maliciosos
- Registry keys
- Mutexes

#### 📧 Email-based
- Endereços de e-mail
- Assuntos de phishing
- Anexos maliciosos

---

### Exemplo de IOC - APT29 (SolarWinds)

##### Domínios C2

- avsvmcloud[.]com digitalcollege[.]org freescanonline[.]com

#### Hashes (SHA-256)

- 32519b85c0b422e4656de6e6c41878e95fd95026267daab4215ee59c107d6c77 # SUNBURST backdoor

#### Registry Keys

- HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\SolarWindows

#### Processos

SolarWindows.Orion.Core.BusinessLayer.dll

---

## 🛡️ Defesa Contra Adversários

### 1️⃣ Threat Intelligence
- Monitorar feeds de IOCs
- Atualizar IOCs em firewalls/IPS
- Threat hunting proativo

### 2️⃣ Defense in Depth
- Múltiplas camadas de segurança
- Segmentação de rede
- Least privilege

### 3️⃣ Detecção e Resposta
- SIEM/SOAR
- EDR/XDR
- Incident Response Plan

### 4️⃣ Treinamento
- Security awareness
- Phishing simulations
- Red team exercises

---

## 🔗 Links Relacionados

- [[MITRE-ATT&CK]]
- [[Cyber-Kill-Chain]]
- [[Malwares]]
- [[OSINT-Fundamentos]]
- [[Threat-Intelligence]]

---

## 📚 Referências

- MITRE ATT&CK Groups: [attack.mitre.org/groups](https://attack.mitre.org/groups/)
- Mandiant APT Reports: [mandiant.com/resources](https://www.mandiant.com/resources)
- CrowdStrike Adversary Universe: [crowdstrike.com/adversaries](https://www.crowdstrike.com/adversaries/)
- FireEye Threat Research: [fireeye.com/current-threats](https://www.fireeye.com/current-threats.html)
