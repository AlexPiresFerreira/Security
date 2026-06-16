
## 🤖 NSE - Nmap Scripting Engine (APROFUNDADO)

### 📚 Fundamentos do NSE

**Linguagem:** Lua **Localização:** `/usr/share/nmap/scripts/` **Extensão:** `.nse` **Base de dados:** `script.db`

- Verificar os scripts
    - grep [categoria_de_script] /usr/share/nmap/scripts/*

- Localizando e entendendo os scripts
	- $ ls /usr/share/nmap/scripts/  
	- $ ls /usr/share/nmap/scripts/smb*  
	- $ ls /usr/share/nmap/scripts/ftp*  
	- $ grep exploit /usr/share/nmap/scripts/*  
	- $ nmap --script-help=ftp-anon

---

### 🏗️ Estrutura de um Script NSE

lua

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```lua
-- Cabeçalho
description = [[
Descrição do que o script faz
]]

author = "Seu Nome"
license = "Same as Nmap--See https://nmap.org/book/man-legal.html"
categories = {"safe", "discovery"}

-- Regra de execução
portrule = function(host, port)
    return port.protocol == "tcp" and port.number == 80
end

-- Ação principal
action = function(host, port)
    return "Script executado com sucesso!"
end
```

---

### 🎭 Fases de Execução (Rules)

#### 1️⃣ **prerule** - Antes da varredura

lua

```lua
prerule = function()
    -- Executa ANTES de escanear qualquer host
    -- Ex: verificar conectividade, carregar dados
end
```

**Exemplo prático:**

lua

```lua
-- Verificar se temos internet
prerule = function()
    local socket = require "socket"
    local conn = socket.tcp()
    conn:settimeout(5)
    local status = conn:connect("8.8.8.8", 53)
    conn:close()
    return status
end
```

---

#### 2️⃣ **hostrule** - Por host detectado

lua


```lua
hostrule = function(host)
    -- Executa para cada HOST ativo
    -- Ex: scripts de enumeração geral
end
```

**Exemplo prático:**

lua


```lua
-- Executar apenas em hosts Windows
hostrule = function(host)
    return host.os and host.os:match("Windows")
end
```

---

#### 3️⃣ **portrule** - Por porta aberta

lua


```lua
portrule = function(host, port)
    -- Executa para cada PORTA aberta
    -- Mais comum!
end
```

**Exemplo prático:**

lua

```lua
-- Executar apenas em servidores web
local shortport = require "shortport"
portrule = shortport.http
```

---

#### 4️⃣ **postrule** - Após varredura

lua

```lua
postrule = function()
    -- Executa DEPOIS de escanear todos os hosts
    -- Ex: consolidar resultados, gerar relatório
end
```

**Exemplo prático:**

lua


```lua
-- Gerar resumo de vulnerabilidades encontradas
postrule = function()
    local vulns = nmap.registry.vulns or {}
    return string.format("Total de vulnerabilidades: %d", #vulns)
end
```

---

### 📂 Categorias de Scripts

| Categoria   | Descrição                                                                  | Risco      | Exemplo               |
| ----------- | -------------------------------------------------------------------------- | ---------- | --------------------- |
| `safe`      | Não intrusivo, sem risco                                                   | 🟢 Baixo   | `ssh-hostkey`         |
| `intrusive` | Pode crashar serviço                                                       | 🔴 Alto    | `http-sql-injection`  |
| `vuln`      | Detecta vulnerabilidades                                                   | 🟡 Médio   | `smb-vuln-ms17-010`   |
| `exploit`   | Explora vulnerabilidades                                                   | 🔴 Crítico | `ftp-vsftpd-backdoor` |
| `brute`     | Força bruta                                                                | 🔴 Alto    | `ssh-brute`           |
| `discovery` | Coleta informações                                                         | 🟢 Baixo   | `dns-brute`           |
| `auth`      | Testa autenticação                                                         | 🟡 Médio   | `http-auth`           |
| `dos`       | Denial of Service                                                          | 🔴 Crítico | `http-slowloris`      |
| `malware`   | Detecta malware                                                            | 🟢 Baixo   | `http-malware-host`   |
| `version`   | Detecção de versão                                                         | 🟢 Baixo   | `banner`              |
| `default`   | Scripts padrão seguros                                                     | 🟢 Baixo   | Vários                |
| Broadcast   | Script para descobertas em toda a rede                                     |            |                       |
| External    | Script que dependem de serviços externos para funcionar                    |            |                       |
| Fuzzer      | Script para fuzzing, ou seja, para testar entradas aleatórias ou inválidas |            |                       |
|             |                                                                            |            |                       |

---

### 🎯 Executando Scripts NSE

#### Sintaxe Básica

bash


```bash
# Script específico
nmap --script [nome-do-script] [target]

# Categoria inteira
nmap --script [categoria] [target]

# Múltiplos scripts/categorias
nmap --script [script1,script2,categoria] [target]

# Wildcard
nmap --script "http-*" [target]

# Excluir scripts
nmap --script "vuln and not dos" [target]
```

---

#### Exemplos Práticos

bash

```bash
# Scripts padrão (safe)
nmap --script default 192.168.1.1

# Buscar vulnerabilidades
nmap --script vuln 192.168.1.1

# Apenas discovery (sem risco)
nmap --script discovery 192.168.1.1

# Brute force SSH (CUIDADO!)
nmap --script ssh-brute --script-args userdb=users.txt,passdb=pass.txt 192.168.1.1

# Todos scripts HTTP
nmap -p 80,443 --script "http-*" 192.168.1.1

# Vulnerabilidades SMB (EternalBlue, etc)
nmap -p 445 --script "smb-vuln-*" 192.168.1.1
```

---

### 🔧 Argumentos de Scripts (`--script-args`)

bash


```bash
# Sintaxe
nmap --script [script] --script-args [arg1=valor1,arg2=valor2] [target]

# Exemplos
nmap --script http-brute --script-args http-brute.path=/admin 192.168.1.1

nmap --script ssh-brute --script-args userdb=users.txt,passdb=rockyou.txt 192.168.1.1

nmap --script mysql-brute --script-args mysql-brute.timeout=5s 192.168.1.1
```

---

### 📦 Scripts NSE por Protocolo/Serviço

#### 🔐 SSH (Porta 22)

bash


```bash
# Coletar chave do host
nmap -p 22 --script ssh-hostkey 192.168.1.1

# Métodos de autenticação suportados
nmap -p 22 --script ssh-auth-methods 192.168.1.1

# Brute force (use com responsabilidade!)
nmap -p 22 --script ssh-brute --script-args userdb=users.txt,passdb=passwords.txt 192.168.1.1

# Detectar algoritmos fracos
nmap -p 22 --script ssh2-enum-algos 192.168.1.1

# Executar comando via SSH (requer credenciais)
nmap -p 22 --script ssh-run --script-args ssh-run.cmd="uname -a",ssh-run.username=root,ssh-run.password=toor 192.168.1.1
```

**Output esperado (ssh-hostkey):**

```
22/tcp open  ssh
| ssh-hostkey:
|   2048 aa:bb:cc:dd:ee:ff:00:11:22:33:44:55:66:77:88:99 (RSA)
|   256 11:22:33:44:55:66:77:88:99:aa:bb:cc:dd:ee:ff:00 (ECDSA)
|_  256 ff:ee:dd:cc:bb:aa:99:88:77:66:55:44:33:22:11:00 (ED25519)
```

**Tags:** #ssh #brute #authentication

---

#### 📧 SMTP (Porta 25)

bash


```bash
# Comandos suportados
nmap -p 25 --script smtp-commands 192.168.1.1

# Testar open relay (envio de spam)
nmap -p 25 --script smtp-open-relay 192.168.1.1

# Enumerar usuários (VRFY/EXPN)
nmap -p 25 --script smtp-enum-users --script-args smtp-enum-users.methods={VRFY,EXPN} 192.168.1.1

# Enumerar usuários com wordlist
nmap -p 25 --script smtp-enum-users --script-args userdb=users.txt 192.168.1.1

# Detectar vulnerabilidades
nmap -p 25 --script smtp-vuln-* 192.168.1.1
```

**Cenário Red Team:** Enumerar usuários válidos para phishing direcionado

**Tags:** #smtp #email #enumeration

---

#### 📡 SNMP (Porta 161/UDP)

bash

```bash
# Informações básicas
sudo nmap -sU -p 161 --script snmp-info 192.168.1.1

# Brute force community strings
sudo nmap -sU -p 161 --script snmp-brute 192.168.1.1

# Enumerar processos rodando
sudo nmap -sU -p 161 --script snmp-processes --script-args snmpcommunity=public 192.168.1.1

# Enumerar interfaces de rede
sudo nmap -sU -p 161 --script snmp-interfaces --script-args snmpcommunity=public 192.168.1.1

# Enumerar usuários do Windows
sudo nmap -sU -p 161 --script snmp-win32-users --script-args snmpcommunity=public 192.168.1.1

# Enumerar software instalado
sudo nmap -sU -p 161 --script snmp-win32-software --script-args snmpcommunity=public 192.168.1.1
```

**Community strings comuns:**

- `public` (leitura)
- `private` (escrita)
- `admin`
- `manager`

**⚠️ Cenário Aeroporto:** Switches e APs geralmente têm SNMP ativo com community padrão!

**Tags:** #snmp #udp #network

---

#### 📁 FTP (Porta 21)

bash

```bash
# Testar login anônimo
nmap -p 21 --script ftp-anon 192.168.1.1

# FTP bounce attack
nmap -p 21 --script ftp-bounce 192.168.1.1

# Identificar sistema operacional via FTP
nmap -p 21 --script ftp-syst 192.168.1.1

# Brute force
nmap -p 21 --script ftp-brute --script-args userdb=users.txt,passdb=passwords.txt 192.168.1.1

# Listar diretórios (se anônimo permitido)
nmap -p 21 --script ftp-anon --script-args ftp-anon.maxlist=100 192.168.1.1

# Detectar vsftpd backdoor (CVE-2011-2523)
nmap -p 21 --script ftp-vsftpd-backdoor 192.168.1.1
```

**Tags:** #ftp #anonymous #backdoor

---

#### 🌐 HTTP/HTTPS (Portas 80/443)

##### 🔍 Reconhecimento Básico

bash


```bash
# Headers HTTP
nmap -p 80 --script http-headers 192.168.1.1

# Título da página
nmap -p 80 --script http-title 192.168.1.1

# Servidor web e versão
nmap -p 80 --script http-server-header 192.168.1.1

# Métodos HTTP permitidos
nmap -p 80 --script http-methods 192.168.1.1

# Robots.txt
nmap -p 80 --script http-robots.txt 192.168.1.1

# Sitemap.xml
nmap -p 80 --script http-sitemap-generator 192.168.1.1
```

---

##### 📂 Enumeração de Diretórios

bash


```bash
# Enumerar diretórios comuns
nmap -p 80 --script http-enum 192.168.1.1

# Com wordlist customizada
nmap -p 80 --script http-enum --script-args http-enum.displayall,http-enum.basepath=/admin/ 192.168.1.1

# Backup files (.bak, .old, ~)
nmap -p 80 --script http-backup-finder 192.168.1.1

# Git exposed (.git/)
nmap -p 80 --script http-git 192.168.1.1

# SVN exposed (.svn/)
nmap -p 80 --script http-svn-enum 192.168.1.1
```

---

##### 🔐 Autenticação e Sessão

bash

```bash
# Testar autenticação HTTP
nmap -p 80 --script http-auth 192.168.1.1

# Brute force HTTP básico
nmap -p 80 --script http-brute --script-args http-brute.path=/admin/ 192.168.1.1

# Brute force formulário
nmap -p 80 --script http-form-brute --script-args http-form-brute.path=/login.php 192.168.1.1

# Session fixation
nmap -p 80 --script http-cookie-flags 192.168.1.1
```

---

##### 🐛 Vulnerabilidades Web

bash


```bash
# SQL Injection
nmap -p 80 --script http-sql-injection 192.168.1.1

# XSS (Cross-Site Scripting)
nmap -p 80 --script http-stored-xss 192.168.1.1
nmap -p 80 --script http-dombased-xss 192.168.1.1

# CSRF (Cross-Site Request Forgery)
nmap -p 80 --script http-csrf 192.168.1.1

# File upload vulnerabilities
nmap -p 80 --script http-fileupload-exploiter 192.168.1.1

# Shellshock (CVE-2014-6271)
nmap -p 80 --script http-shellshock 192.168.1.1

# Heartbleed (CVE-2014-0160)
nmap -p 443 --script ssl-heartbleed 192.168.1.1
```

---

##### 🔧 CMS e Frameworks

bash

```bash
# WordPress
nmap -p 80 --script http-wordpress-enum 192.168.1.1
nmap -p 80 --script http-wordpress-brute 192.168.1.1
nmap -p 80 --script http-wordpress-users 192.168.1.1

# Joomla
nmap -p 80 --script http-joomla-brute 192.168.1.1

# Drupal
nmap -p 80 --script http-drupal-enum 192.168.1.1

# Apache específico
nmap -p 80 --script http-apache-server-status 192.168.1.1
nmap -p 80 --script http-apache-negotiation 192.168.1.1

# PHP
nmap -p 80 --script http-php-version 192.168.1.1

# Tomcat
nmap -p 8080 --script http-tomcat-manager-brute 192.168.1.1
```

---

##### 🛡️ Headers de Segurança

bash

```bash
# Verificar headers de segurança
nmap -p 80,443 --script http-security-headers 192.168.1.1

# HSTS (HTTP Strict Transport Security)
nmap -p 443 --script http-hsts 192.168.1.1

# CSP (Content Security Policy)
nmap -p 80 --script http-csp 192.168.1.1

# Clickjacking
nmap -p 80 --script http-headers --script-args http-headers.useget 192.168.1.1 | grep -i "x-frame-options"
```

**Headers importantes:**

- `X-Frame-Options: DENY` (anti-clickjacking)
- `X-Content-Type-Options: nosniff`
- `X-XSS-Protection: 1; mode=block`
- `Strict-Transport-Security: max-age=31536000`
- `Content-Security-Policy`

**Tags:** #http #web #vulnerabilities #cms

---

#### 🔒 SSL/TLS (HTTPS - Porta 443)

bash

```bash
# Informações do certificado
nmap -p 443 --script ssl-cert 192.168.1.1

# Enumerar ciphers suportados
nmap -p 443 --script ssl-enum-ciphers 192.168.1.1

# Detectar protocolos inseguros (SSLv2, SSLv3)
nmap -p 443 --script ssl-known-key 192.168.1.1

# Heartbleed (CVE-2014-0160)
nmap -p 443 --script ssl-heartbleed 192.168.1.1

# POODLE (CVE-2014-3566)
nmap -p 443 --script ssl-poodle 192.168.1.1

# DROWN (CVE-2016-0800)
nmap -p 443 --script ssl-drown 192.168.1.1

# CCS Injection (CVE-2014-0224)
nmap -p 443 --script ssl-ccs-injection 192.168.1.1

# Verificar data de expiração
nmap -p 443 --script ssl-cert-intaddr 192.168.1.1

# Certificado autoassinado
nmap -p 443 --script ssl-cert --script-args ssl-cert.pem 192.168.1.1
```

**Output exemplo (ssl-enum-ciphers):**

```
443/tcp open  https
| ssl-enum-ciphers:
|   TLSv1.2:
|     ciphers:
|       TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384 (secp256r1) - A
|       TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256 (secp256r1) - A
|     compressors:
|       NULL
|     cipher preference: server
|   TLSv1.3:
|     ciphers:
|       TLS_AKE_WITH_AES_256_GCM_SHA384 (secp384r1) - A
|_  least strength: A
```

**Grading:**

- **A** - Forte
- **B** - Aceitável
- **C** - Fraco
- **D/F** - Inseguro

**Tags:** #ssl #tls #certificates #encryption

---

#### 🗄️ MySQL (Porta 3306)

bash


```bash
# Informações do servidor
nmap -p 3306 --script mysql-info 192.168.1.1

# Brute force
nmap -p 3306 --script mysql-brute --script-args userdb=users.txt,passdb=passwords.txt 192.168.1.1

# Enumerar bancos de dados (requer credenciais)
nmap -p 3306 --script mysql-databases --script-args mysqluser=root,mysqlpass=toor 192.168.1.1

# Enumerar usuários
nmap -p 3306 --script mysql-users --script-args mysqluser=root,mysqlpass=toor 192.168.1.1

# Executar query
nmap -p 3306 --script mysql-query --script-args mysqluser=root,mysqlpass=toor,query="SELECT version()" 192.168.1.1

# Detectar senhas vazias
nmap -p 3306 --script mysql-empty-password 192.168.1.1

# Audit (verifica configurações inseguras)
nmap -p 3306 --script mysql-audit --script-args mysql-audit.username=root,mysql-audit.password=toor 192.168.1.1
```

**Tags:** #mysql #database #brute

---

#### 🪟 SMB/Windows (Portas 139/445)

bash

```bash
# Informações do sistema
nmap -p 445 --script smb-os-discovery 192.168.1.1

# Enumerar compartilhamentos
nmap -p 445 --script smb-enum-shares 192.168.1.1

# Enumerar usuários
nmap -p 445 --script smb-enum-users 192.168.1.1

# Enumerar domínios
nmap -p 445 --script smb-enum-domains 192.168.1.1

# Brute force
nmap -p 445 --script smb-brute 192.168.1.1

# Vulnerabilidades críticas
nmap -p 445 --script smb-vuln-ms17-010 192.168.1.1  # EternalBlue
nmap -p 445 --script smb-vuln-ms08-067 192.168.1.1  # Conficker
nmap -p 445 --script smb-vuln-cve2009-3103 192.168.1.1

# Todas vulnerabilidades SMB
nmap -p 445 --script "smb-vuln-*" 192.168.1.1

# Segurança do SMB
nmap -p 445 --script smb-security-mode 192.168.1.1
nmap -p 445 --script smb2-security-mode 192.168.1.1
```

**⚠️ EternalBlue (MS17-010):**

- Explorado pelo WannaCry e NotPetya
- Permite RCE (Remote Code Execution)
- Crítico em ambientes Windows desatualizados

**Tags:** #smb #windows #eternalblue #wannacry

---

#### 🌐 DNS (Porta 53)

bash

```bash
# Brute force subdomínios
nmap -p 53 --script dns-brute --script-args dns-brute.domain=example.com 192.168.1.1

# Zone transfer (AXFR)
nmap -p 53 --script dns-zone-transfer --script-args dns-zone-transfer.domain=example.com 192.168.1.1

# Recursão aberta
nmap -p 53 --script dns-recursion 192.168.1.1

# Cache snooping
nmap -p 53 --script dns-cache-snoop --script-args dns-cache-snoop.mode=timed,dns-cache-snoop.domains={google.com,facebook.com} 192.168.1.1

# Enumerar registros
nmap -p 53 --script dns-nsec-enum --script-args dns-nsec-enum.domains=example.com 192.168.1.1
```

**Tags:** #dns #enumeration #axfr

---

#### 🌐 IPv6

bash

```bash
# ICMP Echo (ping)
nmap -6 --script ipv6-node-info fe80::1

# Router Advertisement flood
nmap -6 --script ipv6-ra-flood 2001:db8::1

# Multicast SLAAC
nmap -6 --script ipv6-multicast-slaac ff02::1

# DNS reverso IPv6
nmap -6 --script dns-ip6-arpa-scan 2001:db8::/64

# Descoberta de vizinhos
nmap -6 -sn fe80::/64
```

**Endereços IPv6 importantes:**

- `::1` - Loopback
- `fe80::/10` - Link-local
- `ff02::1` - All nodes multicast
- `ff02::2` - All routers multicast

**Tags:** #ipv6 #multicast

---

#### 🌐 DHCP (Porta 67/UDP)

bash


```bash
# Descobrir servidor DHCP
sudo nmap -sU -p 67 --script dhcp-discover 192.168.1.0/24

# Informações detalhadas
sudo nmap -sU -p 67 --script dhcp-discover --script-args dhcp-discover.mac=AA:BB:CC:DD:EE:FF 192.168.1.1
```

**Output esperado:**

```
67/udp open  dhcps
| dhcp-discover:
|   DHCP Message Type: DHCPOFFER
|   Server Identifier: 192.168.1.1
|   IP Address Lease Time: 1 day
|   Subnet Mask: 255.255.255.0
|   Router: 192.168.1.1
|   Domain Name Server: 8.8.8.8, 8.8.4.4
```

**Tags:** #dhcp #network

---

### 🎨 Criando Seu Próprio Script NSE

#### Exemplo 1: Banner Grabber HTTP Customizado

lua

```lua
-- Cabeçalho
local http = require "http"
local shortport = require "shortport"
local stdnse = require "stdnse"

description = [[
Coleta banner HTTP customizado e extrai informações específicas
]]

author = "Seu Nome"
license = "Same as Nmap"
categories = {"safe", "discovery"}

-- Executar apenas em portas HTTP
portrule = shortport.http

-- Ação
action = function(host, port)
    local response = http.get(host, port, "/")

    if not response or not response.status then
        return "Falha ao conectar"
    end

    local output = {}
    table.insert(output, "Status: " .. response.status)

    -- Extrair Server header
    if response.header.server then
        table.insert(output, "Server: " .. response.header.server)
    end

    -- Extrair título da página
    local title = response.body:match("<title>(.-)</title>")
    if title then
        table.insert(output, "Título: " .. title)
    end

    -- Verificar headers de segurança
    if not response.header["x-frame-options"] then
        table.insert(output, "⚠️ X-Frame-Options ausente (vulnerável a clickjacking)")
    end

    if not response.header["strict-transport-security"] then
        table.insert(output, "⚠️ HSTS ausente")
    end

    return stdnse.format_output(true, output)
end
```

**Salvar como:** `/usr/share/nmap/scripts/http-custom-banner.nse`

**Executar:**

bash

```bash
nmap -p 80 --script http-custom-banner 192.168.1.1
```

---

#### Exemplo 2: Verificador de Portas Backdoor

lua

```lua
local nmap = require "nmap"
local shortport = require "shortport"
local stdnse = require "stdnse"

description = [[
Verifica se portas comuns de backdoor estão abertas
]]

author = "Seu Nome"
license = "Same as Nmap"
categories = {"safe", "malware"}

-- Portas suspeitas
local backdoor_ports = {
    31337, -- Back Orifice
    12345, -- NetBus
    54321, -- Back Orifice 2000
    1243,  -- SubSeven
    6667,  -- IRC Bot
    6666,  -- IRC Bot
    4444,  -- Metasploit default
    5555,  -- Android Debug Bridge
}

hostrule = function(host)
    return true
end

action = function(host)
    local output = {}
    local found = false

    for _, port_num in ipairs(backdoor_ports) do
        local port_state = nmap.get_port_state(host, {number=port_num, protocol="tcp"})

        if port_state and port_state.state == "open" then
            found = true
            table.insert(output, string.format("🚨 Porta %d ABERTA (backdoor suspeito!)", port_num))
        end
    end

    if not found then
        return "✅ Nenhuma porta de backdoor comum detectada"
    end

    return stdnse.format_output(true, output)
end
```

---

#### Exemplo 3: Detector de Honeypot

lua


```lua
local http = require "http"
local stdnse = require "stdnse"
local shortport = require "shortport"

description = [[
Tenta detectar se o alvo é um honeypot baseado em comportamentos suspeitos
]]

author = "Seu Nome"
license = "Same as Nmap"
categories = {"safe", "intrusive"}

portrule = shortport.http

action = function(host, port)
    local indicators = {}
    local score = 0

    -- Teste 1: Tempo de resposta muito rápido
    local start_time = stdnse.clock_ms()
    local response = http.get(host, port, "/")
    local end_time = stdnse.clock_ms()
    local response_time = end_time - start_time

    if response_time < 1 then
        score = score + 2
        table.insert(indicators, "Tempo de resposta suspeito: " .. response_time .. "ms")
    end

    -- Teste 2: Todos os diretórios existem
    local test_paths = {"/admin", "/backup", "/test", "/asdfghjkl"}
    local all_exist = true

    for _, path in ipairs(test_paths) do
        local test_response = http.get(host, port, path)
        if not test_response or test_response.status ~= 200 then
            all_exist = false
            break
        end
    end

    if all_exist then
        score = score + 3
        table.insert(indicators, "Todos os diretórios testados existem (comportamento anormal)")
    end

    -- Teste 3: Headers genéricos demais
    if response and response.header.server == "Apache" then
        score = score + 1
        table.insert(indicators, "Server header muito genérico")
    end

    -- Conclusão
    local output = {}
    table.insert(output, "Score de Honeypot: " .. score .. "/10")

    if score >= 5 then
        table.insert(output, "🍯 PROVÁVEL HONEYPOT!")
    elseif score >= 3 then
        table.insert(output, "⚠️ Comportamento suspeito")
    else
        table.insert(output, "✅ Provavelmente legítimo")
    end

    for _, indicator in ipairs(indicators) do
        table.insert(output, "  - " .. indicator)
    end

    return stdnse.format_output(true, output)
end
```

---

### 🔄 Atualizar Base de Scripts

bash

```bash
# Atualizar script.db
sudo nmap --script-updatedb

# Verificar scripts disponíveis
ls /usr/share/nmap/scripts/ | wc -l

# Buscar script específico
ls /usr/share/nmap/scripts/ | grep -i http

# Ver descrição de um script
nmap --script-help http-title
```

---

### 📚 Recursos para Aprender NSE

1. **Documentação Oficial:** https://nmap.org/book/nse.html
2. **NSE Library:** https://nmap.org/nsedoc/
3. **Scripts Existentes:** Leia scripts em `/usr/share/nmap/scripts/` para aprender
4. **Lua Tutorial:** https://www.lua.org/pil/

**Tags:** #nse #scripting #lua #automation

---
