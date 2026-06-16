
## 📋 Índice Rápido

dataview

```dataview
table without id
  file.link as "Seção",
  tags as "Tags"
from "NMAP"
```

**Tags principais:** #nmap #recon #pentest #blueteam #redteam #nse #evasion #fingerprinting

---
## 👤 Criador

**Gordon Lyon (Fyodor)** - Hacker ético e autor do Nmap desde 1997

> 💡 **Curiosidade:** Fyodor também criou o site Insecure.org e mantém listas como "Top 100 Network Security Tools"

---

## 🚀 Instalação

### Linux

#### Debian/Ubuntu

bash

```bash
sudo apt update && sudo apt install nmap -y
```
#### Red Hat/Fedora/CentOS

bash

```bash
sudo dnf install nmap -y
```

#### Arch Linux

bash

```bash
sudo pacman -S nmap
```

### Verificar instalação

bash

```bash
nmap --version
```

**Tags:** #instalacao #setup

---

## 🎯 Comandos Essenciais - Quick Reference

### 🔥 Top 10 Comandos Mais Usados

|Comando|Descrição|Uso Típico|
|---|---|---|
|`nmap -sS [target]`|SYN Stealth Scan|Reconhecimento silencioso|
|`nmap -sV [target]`|Detecção de versão|Fingerprinting de serviços|
|`nmap -O [target]`|Detecção de SO|Identificar sistema operacional|
|`nmap -A [target]`|Scan agressivo completo|Auditoria completa (barulhento)|
|`nmap -p- [target]`|Todas as 65535 portas|Varredura completa|
|`nmap -sU [target]`|Scan UDP|Detectar serviços UDP|
|`nmap --script vuln [target]`|Scripts de vulnerabilidades|Buscar CVEs conhecidas|
|`nmap -Pn [target]`|Sem ping (bypass firewall)|Alvos com ICMP bloqueado|
|`nmap -T4 [target]`|Timing agressivo|Redes rápidas/confiáveis|
|`nmap -oA [nome] [target]`|Output em todos formatos|Documentação completa|

**Tags:** #comandos #quickref #cheatsheet

---

## Debung e Help

- --packet-trace: Mostra todos os pacotes sendo enviados e recebidos
- --version-trace: Mostra em tempo real quais testes está realizando
- -V: Traz a versão  do NMAP e informações da maquina local
- --iflist: Verificar IP, interface e gateway local
- -v ou -vv: Verbosidade
- -d: Executa o debugging do scan
- --script-help: ajudar de um script NSE

---
## Arquivo

- -iL [arquivo] : Ler os IPs de um arquivo
- --excludefile [arquivo.txt] : Excluir uma lista com os hosts no arquivo da execução

---

## Status da conexão

| Estado               | Resposta TCP   | Resposta UDP     | Causa Principal           |
| -------------------- | -------------- | ---------------- | ------------------------- |
| **open**             | SYN-ACK        | Dados válidos    | Serviço rodando           |
| **closed**           | RST            | ICMP Unreachable | Sem serviço, host ativo   |
| **filtered**         | Nenhuma / ICMP | Nenhuma          | Firewall bloqueando       |
| **open\|filtered**   | Nenhuma        | Nenhuma          | UDP ou scan especial      |
| **closed\|filtered** | Ambíguo        | Ambíguo          | Scan idle (raro)          |
| **unfiltered**       | RST            | N/A              | ACK scan, porta acessível |

**Exemplo**

```
nmap -sS -p 22,80,443,3389 192.168.1.0/24

# Resultados:
22/tcp   open     ssh        ✅ Normal - servidor SSH
80/tcp   closed   http       ⚠️ Apache parado? Investigar
443/tcp  filtered https      🚨 Firewall bloqueando? Verificar regras
3389/tcp filtered ms-wbt-server ✅ Esperado - RDP deve estar filtrado

sudo nmap -sU -p 161 192.168.1.0/24

# Resultados típicos:
161/udp open          snmp     ✅ SNMP respondendo
161/udp open|filtered snmp     ❓ Pode estar aberto ou filtrado
161/udp filtered      snmp     🛡️ Firewall bloqueando


```

---

#### Tipo de scan

   - Footprint
        - Rede - Mapear hosts ativos
   - Fingerprint
        - Ativos - Sistema Operacional e Serviços
    - Enumeração
        - Ação mais intrusiva - Vulnerabilidade

---

## 🔍 Tipos de Varredura (Scan Types)

### 🎭 Varreduras TCP

#### `-sS` - SYN Stealth Scan (Half-Open) 👻

bash

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```bash
nmap -sS 192.168.1.1
```

**Como funciona:**

1. Envia pacote **SYN**
2. Recebe **SYN-ACK** (porta aberta) ou **RST** (porta fechada)
3. Envia **RST** (não completa handshake)

**Vantagens:**

- ✅ Menos detectável (não completa conexão)
- ✅ Mais rápido que `-sT`
- ✅ Evita logs de aplicação

**Desvantagens:**

- ❌ Requer privilégios de root/admin
- ❌ Alguns firewalls detectam padrão SYN

**Cenário Red Team:** Reconhecimento inicial sem deixar rastros em logs de aplicação **Cenário Blue Team:** Testar se IDS/IPS detecta varreduras stealth

**Tags:** #tcp #stealth #redteam

---

#### `-sT` - TCP Connect Scan (Full-Open)

bash

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```bash
nmap -sT 192.168.1.1
```

**Como funciona:**

1. Completa handshake TCP (SYN → SYN-ACK → ACK)
2. Usa chamadas do sistema operacional (connect())

**Vantagens:**

- ✅ Não requer privilégios especiais
- ✅ Funciona em qualquer sistema

**Desvantagens:**

- ❌ Mais lento
- ❌ Gera logs completos
- ❌ Muito detectável

**Cenário:** Use quando não tiver acesso root ou em ambientes onde stealth não importa

**Tags:** #tcp #fullconnect

---

### 📡 Varreduras UDP

#### `-sU` - UDP Scan

bash

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```bash
nmap -sU -p 53,161,500 192.168.1.1
```

**Portas UDP críticas:**

- **53** - DNS
- **161/162** - SNMP
- **500** - IKE (IPSec VPN)
- **123** - NTP
- **69** - TFTP

**Como funciona:**

1. Envia pacote UDP vazio (ou payload específico)
2. Sem resposta = porta **aberta|filtrada**
3. ICMP "Port Unreachable" = porta **fechada**

**⚠️ Importante:** Varreduras UDP são **MUITO LENTAS** (rate limiting ICMP)

**Otimização:**

bash

```bash
# Scan UDP rápido (top 100 portas)
nmap -sU --top-ports 100 192.168.1.0/24

# Scan UDP + versão (mais preciso)
nmap -sU -sV -p 161 192.168.1.1
```

**Tags:** #udp #snmp #dns

---

#### `-sO` - IP Protocol Scan

bash

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```bash
nmap -sO 192.168.1.1
```

**Detecta protocolos suportados:**

- TCP (6)
- UDP (17)
- ICMP (1)
- IGMP (2)
- GRE (47)
- ESP (50) - IPSec
- AH (51) - IPSec

**Uso:** Identificar tunelamento, VPNs, protocolos exóticos

**Tags:** #protocols #ipsec

---

## 🌐 Discovery e Mapeamento de Hosts

### 🎯 Host Discovery (Ping Scan)

#### Rede Local (Layer 2)

bash

```bash
# ARP Discovery (mais eficaz em LAN)
nmap -sn 192.168.1.0/24
```

**Como funciona:**

- Envia ARP requests
- Não pode ser bloqueado por firewall (Layer 2)
- Detecta hosts mesmo com firewall ativo

---
#### DNS

- -n or -R: Executa uma varredura mas não realiza consulta DNS
- --dns-server [server_dns] : Altera o servidor DNS que está sendo utilizado para resolver os nomes de domínio

---

#### Rede Remota (Layer 3)

bash

```bash
# ICMP Echo + TCP SYN (portas 80/443)
nmap -sn -PE -PS80,443 10.0.0.0/24

# TCP ACK (bypass stateful firewalls)
nmap -sn -PA80,443 10.0.0.0/24

# UDP (portas comuns)
nmap -sn -PU53,161 10.0.0.0/24
```

- -PS: especifica portas TCP para envio de pacotes SYN(remoto)
- -PA: especifica portas TCP para envio de pacotes ACK(remoto)
- -PU:  especifica portas UDP
- -PE: ativa os pacotes ICMP Echo(remoto)


**Combinação recomendada (máxima cobertura):**

bash

```bash
nmap -sn -PE -PS21,22,23,25,80,443 -PA80,443 -PU53,161 10.0.0.0/24
```

---

#### `-Pn` - Sem Ping (Force Scan)

bash

```bash
nmap -Pn -p 22,80,443 192.168.1.1
```

**Quando usar:**

- ✅ Firewall bloqueia ICMP
- ✅ Hosts configurados para não responder ping
- ✅ Ambientes críticos (servidores DMZ)

**⚠️ Atenção:** Mais lento (tenta todas as portas mesmo em hosts inativos)

**Tags:** #discovery #ping #arp

---

### 📍 Traceroute e Geolocalização

bash

```bash
# Traceroute básico
nmap --traceroute 8.8.8.8

# Com geolocalização
nmap --traceroute --script traceroute-geolocation 8.8.8.8
```

**Output esperado:**

```
HOP RTT     ADDRESS
1   1.23 ms gateway (192.168.1.1)
2   5.67 ms 10.0.0.1
3   15.2 ms isp-router.com (200.x.x.x)
    Coordinates: -23.5505, -46.6333 (São Paulo, BR)
```

**Tags:** #traceroute #geolocation

---

## 🔓 Varredura de Portas Avançada

### 🎯 Especificação de Portas

bash

```bash
# Portas específicas
nmap -p 22,80,443 192.168.1.1

# Range
nmap -p 1-1024 192.168.1.1

# Todas as portas (0-65535)
nmap -p- 192.168.1.1

# Top 100 portas mais comuns
nmap --top-ports 100 192.168.1.1

# Portas TCP + UDP simultaneamente
nmap -p T:80,443,U:53,161 192.168.1.1

# Excluir portas específicas
nmap -p 1-1000 --exclude-ports 80,443 192.168.1.1
```

**Top portas**

   sort -t$'\t' -k3 -n -r /usr/share/nmap/nmap-services | less

---

### ⚡ Scan Rápido vs Completo

bash

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```bash
# Fast scan (top 100 portas)
nmap -F 192.168.1.1

# Scan completo (todas as portas)
nmap -p- 192.168.1.1

# Scan sequencial (não randomizado)
nmap -r -p 1-1000 192.168.1.1
```

**Comparação de tempo:**

|Método|Portas|Tempo Médio|
|---|---|---|
|`-F`|100|~10 segundos|
|Default|1000|~30 segundos|
|`-p-`|65535|~20 minutos|
|`-p- -T5`|65535|~5 minutos|
**Porta do sistema linux**

   $ cat /etc/services


---

### 🎭 Source Port Spoofing

bash

Copiar![](data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A)

```bash
# Usar porta 53 como origem (bypass alguns firewalls)
nmap -g 53 192.168.1.1

# Ou
nmap --source-port 53 192.168.1.1
```

**Por que funciona:**

- Alguns firewalls permitem tráfego de portas "confiáveis" (53, 80, 443)
- Administradores esquecem de filtrar porta de origem

**Tags:** #ports #evasion #spoofing

---

## 🔬 Fingerprinting e Detecção de Serviços

### 🏷️ Detecção de Versão (`-sV`)

bash


```bash
# Detecção básica
nmap -sV 192.168.1.1

# Intensidade máxima (mais testes)
nmap -sV --version-intensity 9 192.168.1.1

# Todos os métodos disponíveis
nmap -sV --version-all 192.168.1.1

# Debug (ver testes em tempo real)
nmap -sV --version-trace 192.168.1.1
```

- --version-intensity [0-9] : Quando maior a intensidade, mais testes são realizados para tentar obter uma resposta conclusiva
- --version-all: Todos os métodos disponíveis de detecção, incluindo os mais demorados
    - nmap-sevice & version.db
    - /usr/share/nmap
 
**Como funciona:**

1. Conecta na porta
2. Envia probes específicos do protocolo
3. Analisa banner/resposta
4. Compara com `nmap-service-probes`

**Exemplo de output:**

```
PORT    STATE SERVICE VERSION
22/tcp  open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
80/tcp  open  http    Apache httpd 2.4.41 ((Ubuntu))
3306/tcp open  mysql  MySQL 5.7.38-0ubuntu0.18.04.1
```

---

### 🖥️ Detecção de Sistema Operacional (`-O`)

bash


```bash
# Detecção básica (requer root)
sudo nmap -O 192.168.1.1

# Forçar tentativa mesmo com baixa confiança
sudo nmap -O --osscan-guess 192.168.1.1

# Limitar tentativas
sudo nmap -O --max-os-tries 2 192.168.1.1
```

**Técnicas utilizadas:**

- **TTL (Time To Live):** Windows=128, Linux=64, Cisco&UNIX=255
- **Tamanho da janela TCP**
- **Flags TCP ativas**
- **Ordem das opções TCP**
- **Comportamento com pacotes malformados**

**Exemplo de output:**

```
Device type: general purpose
Running: Linux 5.X
OS CPE: cpe:/o:linux:linux_kernel:5
OS details: Linux 5.0 - 5.4
Network Distance: 1 hop
```

**Base de dados:** `/usr/share/nmap/nmap-os-db`

**Tags:** #fingerprinting #os #versioning

---

### 🚀 Scan Agressivo (`-A`)

bash


```bash
nmap -A 192.168.1.1
```

**Ativa simultaneamente:**

- `-O` (detecção de SO)
- `-sV` (versão de serviços)
- `--script=default` (scripts NSE padrão)
- `--traceroute`

**⚠️ ATENÇÃO:** Muito barulhento! Gera muitos logs e alertas.

**Uso recomendado:** Auditoria interna autorizada, não em Red Team stealth

**Tags:** #aggressive #audit

---


## 🥷 Técnicas de Evasão e Stealth

### 🧩 Fragmentação de Pacotes

bash

```bash
# Fragmentação padrão (8 bytes)
nmap -f 192.168.1.1

# MTU customizado (múltiplo de 8)
nmap --mtu 16 192.168.1.1
nmap --mtu 24 192.168.1.1
```

**Como funciona:**

- Divide pacotes em fragmentos menores
- Alguns firewalls/IDS não remontam fragmentos corretamente
- Pode bypassar regras de inspeção

**⚠️ Desvantagem:** Mais lento e pode ser descartado por alguns sistemas

**Tags:** #evasion #fragmentation

---

### 🎭 IP Spoofing (Decoy)

bash

```bash
# Decoys aleatórios
nmap -D RND:10 192.168.1.1

# Decoys específicos
nmap -D 192.168.1.50,192.168.1.51,ME,192.168.1.52 192.168.1.1

# Spoof de IP específico (requer configuração avançada)
nmap -S 192.168.1.100 -e eth0 -Pn 192.168.1.1
```

   - -D [IP, IP, IP, etc| RND [valor]] : Permite o envio do scan através de vários endereços IPs
   - -S [IP] : Realiza o Spoof do endereço original
   - -e [interface] : Determina a interface de saída
   - -Pn: Cancela o ping e não aparecer vestigios do ip verdadeiro

**Como funciona:**

- Envia pacotes de múltiplos IPs simultaneamente
- Dificulta identificar o atacante real
- `ME` = seu IP real (misturado com decoys)

**⚠️ Limitação:** Você não receberá as respostas dos decoys

**Cenário:** Ofuscar origem em logs de firewall

**Tags:** #evasion #spoofing #decoy

---

### 🎨 MAC Address Spoofing

bash

```bash
# Spoof com MAC específico
nmap --spoof-mac AA:BB:CC:DD:EE:FF 192.168.1.1

# Spoof com fabricante
nmap --spoof-mac Cisco 192.168.1.1
nmap --spoof-mac Dell 192.168.1.1
nmap --spoof-mac Apple 192.168.1.1

# MAC aleatório
nmap --spoof-mac 0 192.168.1.1
```

**Fabricantes comuns:**

- `Cisco` - Equipamentos de rede
- `Dell` - Servidores
- `Apple` - Dispositivos corporativos
- `Samsung` - Smartphones

**Tags:** #evasion #mac #spoofing

---

### 🏴 Manipulação de Flags TCP

bash

```bash
# Flags customizadas
nmap --scanflags URGACKPSHRSTSYNFIN 192.168.1.1

# Xmas scan (FIN, PSH, URG)
nmap -sX 192.168.1.1

# FIN scan
nmap -sF 192.168.1.1

# NULL scan (sem flags)
nmap -sN 192.168.1.1
```

**Flags TCP:**

- `URG` - Urgent
- `ACK` - Acknowledgment
- `PSH` - Push
- `RST` - Reset
- `SYN` - Synchronize
- `FIN` - Finish

**Como funciona:**

- Pacotes com flags incomuns podem bypassar firewalls
- Sistemas respondem diferentemente a flags malformadas

**Tags:** #evasion #tcp #flags

---

### ⏱️ Timing e Cadência

bash

```bash
# Paranoid (mais lento, menos detectável)
nmap -T0 192.168.1.1

# Sneaky
nmap -T1 192.168.1.1

# Polite
nmap -T2 192.168.1.1

# Normal (padrão)
nmap -T3 192.168.1.1

# Aggressive (rápido, mais detectável)
nmap -T4 192.168.1.1

# Insane (muito rápido, muitos falsos positivos)
nmap -T5 192.168.1.1
```

   - Intervalo entre pacotes
   - Quantidade de threads simultâneas
   - Tempo de resposta esperado
   - Número de retransmissões

**Comparação:**

| Timing | Intervalo entre Probes | Timeout     | Uso              |
| ------ | ---------------------- | ----------- | ---------------- |
| T0     | 5 minutos              | Longo       | Evasão máxima    |
| T1     | 15 segundos            | Longo       | Evasão alta      |
| T2     | 0.4 segundos           | Normal      | Evasão moderada  |
| T3     | Normal                 | Normal      | Uso geral        |
| T4     | Rápido                 | Curto       | Redes confiáveis |
| T5     | Muito rápido           | Muito curto | LANs rápidas     |

---

### 🎛️ Controle Fino de Timing

bash

```bash
# Intervalo mínimo entre pacotes (milissegundos)
nmap --scan-delay 1000ms 192.168.1.1

# Intervalo máximo
nmap --max-scan-delay 2000ms 192.168.1.1

# Taxa máxima de pacotes por segundo
nmap --max-rate 10 192.168.1.1

# Taxa mínima
nmap --min-rate 100 192.168.1.1

# Timeout por host
nmap --host-timeout 30m 192.168.1.1

# Paralelismo
nmap --min-parallelism 10 --max-parallelism 100 192.168.1.1

# Determinar grupo minimo e maximo de host scaneado paralelamenmte 
nmap --min-hostgroup 50 --max-hostgroup 100 192.168.0.0/16

# Determinar minimo e maximo de pacotes por segundos 
nmap --min-rate 500 --max-rate 1000 192.168.0.0/16

```

- --min-parallelism: Número mínimo de porta escameados em paralelo
- --max-parallelism: Número máximo de porta escameados em paralelo
- --host-timeout [valor] : Tempo máximo de análise por host

**Exemplo**

```
--min-hostgroup 50           # Pelo menos 50 hosts por vez
--max-hostgroup 100          # No máximo 100 hosts por vez
--min-parallelism 50         # Pelo menos 50 portas por host
--max-parallelism 100        # No máximo 100 portas por host
--min-rate 500               # Mínimo 500 pacotes/segundo
--max-rate 1000              # Mínimo 500 pacotes/segundo
```


**Exemplo stealth completo:**

bash


```bash
nmap -sS -T1 --scan-delay 2000ms --max-rate 5 -f --data-length 25 192.168.1.1
```

**Tags:** #evasion #timing #stealth

---

### 📦 Manipulação de Dados

bash

```bash
# Adicionar dados aleatórios ao pacote
nmap --data-length 25 192.168.1.1

# TTL customizado
nmap --ttl 64 192.168.1.1

# Tamanho de pacote específico
nmap --data-length 100 192.168.1.1
```

- --data-length [valor] : Envia pacotes contendo apenas o cabeçalho (alterar o tamanho do length do pacote)

**Por que funciona:**

- Altera assinatura do pacote
- Dificulta detecção por IDS baseado em tamanho

**Tags:** #evasion #packet

---

### 🔥 Combo Stealth Máximo

bash

```bash
# Red Team Ninja Mode
sudo nmap -sS -Pn -f --mtu 24 --data-length 25 \
  --scan-delay 2000ms --max-rate 5 \
  -D RND:5 --spoof-mac Cisco \
  -p 22,80,443 -T1 \
  --script=banner \
  192.168.1.1
```

**O que faz:**

- `-sS` - SYN stealth
- `-Pn` - Sem ping
- `-f` - Fragmentação
- `--mtu 24` - MTU pequeno
- `--data-length 25` - Padding
- `--scan-delay 2000ms` - 2s entre pacotes
- `--max-rate 5` - Máximo 5 pacotes/segundo
- `-D RND:5` - 5 decoys aleatórios
- `--spoof-mac Cisco` - MAC falso
- `-T1` - Timing sneaky

**⏱️ Tempo estimado:** Várias horas para poucos hosts

**Tags:** #evasion #stealth #redteam #ninja

---
## Uso de Ferramentas Auxiliares e Extensões
  
- Zenmap
- Wireshark
    - IPv6
        - icmpv6.type == 135 : identificar dispositivos que estão respondendo a solicitação de vizinhança
- Metasploit
- Maltego
- Zeek
    - zeek -r [arquivo.pcap]
- Dashboards
    - Kibana
    - Splunk

#### Ferramenta de Parsing

- xsltproc
- libnmap

---

## 📊 Logging e Relatórios

### 📝 Formatos de Saída

bash

```bash
# Normal (leitura humana)
nmap -oN relatorio.txt 192.168.1.0/24

# XML (parsing, SIEM, Metasploit)
nmap -oX relatorio.xml 192.168.1.0/24

# Grepable (grep, awk, sed)
nmap -oG relatorio.gnmap 192.168.1.0/24

# JSON (Python, APIs)
nmap -oJ relatorio.json 192.168.1.0/24

# Todos os formatos (gera 3 arquivos)
nmap -oA relatorio 192.168.1.0/24

# Redirecionar para um arquivo (>)
nmap -sS -p 80,443 192.168.0.0/24 -oX webscan.xml > /dev/null
```

**Arquivos gerados com `-oA`:**

- `relatorio.nmap` (normal)
- `relatorio.gnmap` (grepable)
- `relatorio.xml` (XML)

**Jogar o resultado em um arquivo**

   $ nmap -sn 192.168.90.0/24 -oG hosts.txt  

**Cortar e deixa somente os IPs**

   $ cat hosts.txt | grep "Host" | cut -d " " -f2   > alvos.txt

---

### 🔍 Parsing de Resultados

#### Bash + Grep

bash

```bash
# Extrair apenas IPs com porta 22 aberta
grep "22/open" relatorio.gnmap | awk '{print $2}'

# Contar hosts ativos
grep "Status: Up" relatorio.gnmap | wc -l

# Listar portas abertas por host
grep "Ports:" relatorio.gnmap | cut -d' ' -f2,4-
```

---

#### Python + libnmap

python

```python
from libnmap.parser import NmapParser

# Parsear arquivo XML
report = NmapParser.parse_fromfile("relatorio.xml")

print(f"Hosts escaneados: {len(report.hosts)}")
print(f"Hosts ativos: {len([h for h in report.hosts if h.is_up()])}")

# Iterar sobre hosts
for host in report.hosts:
    if host.is_up():
        print(f"\n[+] {host.address}")

        # Sistema operacional
        if host.os_fingerprinted:
            print(f"    SO: {host.os.osmatches[0].name}")

        # Serviços
        for service in host.services:
            if service.state == "open":
                banner = service.banner if service.banner else "N/A"
                print(f"    {service.port}/{service.protocol} - {service.service} - {banner}")
```

---

#### Python + xml.etree

python

```python
import xml.etree.ElementTree as ET

tree = ET.parse('relatorio.xml')
root = tree.getroot()

for host in root.findall('host'):
    # IP
    addr = host.find('address').get('addr')

    # Status
    status = host.find('status').get('state')

    if status == 'up':
        print(f"\n[+] {addr}")

        # Portas
        for port in host.findall('.//port'):
            port_id = port.get('portid')
            protocol = port.get('protocol')
            state = port.find('state').get('state')

            if state == 'open':
                service_elem = port.find('service')
                service_name = service_elem.get('name') if service_elem is not None else 'unknown'
                print(f"    {port_id}/{protocol} - {service_name}")
```

---

### 📈 Integração com SIEM

#### Splunk

bash

```bash
# Gerar XML e enviar para Splunk
nmap -oX - 192.168.1.0/24 | curl -k -u admin:password \
  https://splunk-server:8088/services/collector/raw \
  -H "Authorization: Splunk YOUR-TOKEN" \
  -d @-
```

---

#### ELK Stack (Elasticsearch)

python

```python
from elasticsearch import Elasticsearch
from libnmap.parser import NmapParser

es = Elasticsearch(['http://localhost:9200'])

report = NmapParser.parse_fromfile("relatorio.xml")

for host in report.hosts:
    if host.is_up():
        doc = {
            'ip': host.address,
            'hostname': host.hostnames[0] if host.hostnames else None,
            'os': host.os.osmatches[0].name if host.os_fingerprinted else None,
            'timestamp': report.started,
            'ports': []
        }

        for service in host.services:
            if service.state == 'open':
                doc['ports'].append({
                    'port': service.port,
                    'protocol': service.protocol,
                    'service': service.service,
                    'version': service.banner
                })

        es.index(index='nmap-scans', document=doc)
```

**Tags:** #logging #reporting #siem #parsing

---

## 🔗 Integração com Outras Ferramentas

### 🦈 Wireshark

bash

```bash
# Capturar tráfego do Nmap
sudo tcpdump -i eth0 -w nmap_traffic.pcap &
TCPDUMP_PID=$!

nmap -sS 192.168.1.1

kill $TCPDUMP_PID

# Analisar no Wireshark
wireshark nmap_traffic.pcap
```

**Filtros Wireshark úteis:**

```
tcp.flags.syn == 1 && tcp.flags.ack == 0   # Pacotes SYN
tcp.flags.reset == 1                        # Pacotes RST
icmp.type == 3                              # ICMP Unreachable
```

---

### 🎯 Metasploit

bash

```bash
# Importar scan Nmap no Metasploit
msfconsole
msf6 > db_import relatorio.xml
msf6 > hosts
msf6 > services

# Usar resultados para exploits
msf6 > use exploit/multi/handler
msf6 > set LHOST 192.168.1.100
msf6 > exploit
```

---

### 🕵️ Maltego

1. Executar Nmap com XML: `nmap -oX scan.xml 192.168.1.0/24`
2. Abrir Maltego
3. Import → Nmap XML
4. Selecionar `scan.xml`
5. Executar transformações

---

### 🐍 Python Automation

python

```python
import subprocess
import json

def nmap_scan(target, ports="1-1000"):
    """
    Executa scan Nmap e retorna resultados em JSON
    """
    cmd = [
        "nmap",
        "-sS",
        "-sV",
        "-p", ports,
        "-oX", "-",
        target
    ]

    result = subprocess.run(cmd, capture_output=True, text=True)

    # Parsear XML e converter para dict
    # (usar xml.etree ou libnmap)

    return result.stdout

# Uso
resultado = nmap_scan("192.168.1.1", "22,80,443")
print(resultado)
```

- Python (Biblioteca subprocess, xml.etree.ElementTree, pandas e requests)

---

### 🤖 Ansible Playbook

yaml

```yaml
---
- name: Automated Nmap Scanning
  hosts: scanners
  become: yes

  vars:
    target_network: "10.0.0.0/24"
    output_dir: "/tmp/nmap_results"

  tasks:
    - name: Criar diretório de output
      file:
        path: "{{ output_dir }}"
        state: directory

    - name: Executar Nmap scan
      shell: |
        nmap -sS -sV -p 1-1000 \
          -oA {{ output_dir }}/scan_{{ ansible_date_time.epoch }} \
          {{ target_network }}
      register: nmap_result

    - name: Exibir resumo
      debug:
        msg: "Scan completo. Resultados em {{ output_dir }}"

    - name: Enviar resultados por email
      mail:
        host: smtp.gmail.com
        port: 587
        username: "seu-email@gmail.com"
        password: "sua-senha"
        to: "admin@empresa.com"
        subject: "Nmap Scan - {{ ansible_date_time.date }}"
        body: "Scan completo. Veja anexo."
        attach: "{{ output_dir
```

---
## ntegração com Ferramentas de Inteligência e OSINT

  - MISP

1. Executar uma varredura Nmap com exportação XML.
2. Importar o XML no MISP via interface ou script.
3. Aplicar filtros por severidade, tipologia e recorrência.
4. Associar os ativos a eventos existentes ou criar novos eventos para acompanhamento.

  - Script em Python para verificar se o IP esta em black list (biblioteca PyMISP)

```

from pymisp import ExpandedPyMISP

misp = ExpandedPyMISP(url, key, ssl=False)

result = misp.search(controller='attributes', value='192.168.0.10')

```

  - Maltego

1. Inserção de IPs ou domínios detectados pelo Nmap como "seeds".
2. Execução de transformações como "Resolve to Domain", "Check Reputation", "To ASN Info".
3. Geração de um grafo de relações que pode incluir outras máquinas, endereços associados, entidades jurídicas ou relações técnicas.

  - AbuseIPDB: fornece reputação e histórico de denúncias de IPs. (script em bash)

```

curl -G https://api.abuseipdb.com/api/v2/check \ --data-urlencode "ipAddress=192.168.0.10" \ -H "Key: SUA_CHAVE_AQUI"

```

  - Shodan (script Python)

  ```

import shodan

api = shodan.Shodan('SUA_CHAVE')

host = api.host('192.168.0.10')

print(host['data'])

```

  - VirusTotal(script bash)

```

curl --request GET \ --url https://www.virustotal.com/api/v3/ip_addresses/192.168.0.10 \ --header 'x-apikey: SUA_CHAVE'

```

---

  ## Técnicas Anti-Scan e Blindagem de Rede
 

- Alguns sinais recorrentes observáveis em tráfego de rede incluem:
1. Sequências rápidas de pacotes SYN para múltiplas portas de um mesmo host.
2. Varredura horizontal (mesma porta em múltiplos IPs).
3. Conexões incompletas seguidas de resets, típicas de varreduras stealth.
4. Tentativas sucessivas de conexão em portas comumente associadas a serviços vulneráveis (22, 23, 445, 3389, 5900).
5. Respostas de erro ICMP, como "Destination Unreachable", provocadas por pacotes malformados.

- Honeyports
    - honeyd -d -f honeyd.config -i eth0
