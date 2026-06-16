
# 🔒 IPSec (Internet Protocol Security)

> **Tags:** #ipsec #vpn #encryption #network-security #tunneling #authentication

---

## 📌 Visão Geral

**IPSec** é um conjunto de **protocolos** para proteger comunicações IP através de **autenticação** e **criptografia** de pacotes IP.

🎯 **Objetivo:** Fornecer segurança na camada de rede (Layer 3) do modelo OSI.

**Usos comuns:**
- VPNs site-to-site
- VPNs de acesso remoto
- Proteção de tráfego entre redes

---

## 🏗️ Componentes do IPSec

### 1️⃣ Protocolos de Segurança

#### AH (Authentication Header)
**RFC:** 4302

**Funções:**
- ✅ **Autenticação** do remetente
- ✅ **Integridade** dos dados
- ❌ **NÃO** fornece confidencialidade (sem criptografia)

**Uso:** Raro (ESP é preferível)

**Cabeçalho AH:**

┌─────────────────────────────────────┐ 
│ Next Header | Payload Len | Reserved       │
├─────────────────────────────────────┤
│ Security Parameters Index (SPI)                 │
├─────────────────────────────────────┤ 
│ Sequence Number                                     │
├─────────────────────────────────────┤ 
│ Authentication Data (variável)                   │
└─────────────────────────────────────┘


---

#### ESP (Encapsulating Security Payload)
**RFC:** 4303

**Funções:**
- ✅ **Confidencialidade** (criptografia)
- ✅ **Autenticação** do remetente
- ✅ **Integridade** dos dados
- ✅ **Proteção contra replay**

**Uso:** Mais comum (recomendado)

**Cabeçalho ESP:**

┌─────────────────────────────────────┐
│ Security Parameters Index (SPI)                 │
├─────────────────────────────────────┤ 
│ Sequence Number                                     │
├─────────────────────────────────────┤ 
│ Payload Data (criptografado)                    │
├─────────────────────────────────────┤ 
│ Padding | Pad Length | Next                      │
├─────────────────────────────────────┤
│ Authentication Data (opcional)                  │
└─────────────────────────────────────┘

```
---

### 2️⃣ Modos de Operação

#### Transport Mode (Modo Transporte)
**Uso:** Host-to-host

**Características:**
- Apenas **payload** é protegido
- Cabeçalho IP original permanece
- Menor overhead

**Diagrama:**
```

Antes: 
┌──────────┬──────────┐
│ IP Header │ Payload     │
└──────────┴──────────┘

Depois (ESP):

┌──────────┬─────┬──────────┬─────┐
│ IP Header  │ ESP  │ Payload     │ ESP  │
│ Original     │ Hdr  │(encrypted)│ Trl    │
└──────────┴─────┴──────────┴─────┘


**Exemplo de uso:**
```

Cliente ←──────────────→ Servidor (Transport Mode)

```

---

#### Tunnel Mode (Modo Túnel)
**Uso:** Site-to-site, gateway-to-gateway

**Características:**
- **Pacote IP inteiro** é protegido
- Novo cabeçalho IP é adicionado
- Mais overhead, mas mais seguro

**Diagrama:**
```

Antes: 
┌──────────┬──────────┐
│ IP Header│ Payload  │
└──────────┴──────────┘

Depois (ESP):

┌─────────┬─────┬──────────┬──────────┬─────┐
│New IP   │ ESP │Original  │ Payload  │ ESP │
│ Header  │ Hdr │IP Header │(encrypted)│ Trl│ └─────────┴─────┴──────────┴──────────┴─────┘

```

**Exemplo de uso:**
```

Rede A ←─── Gateway A ←────────→ Gateway B ───→ Rede B (Tunnel Mode)

```
---

### 3️⃣ IKE (Internet Key Exchange)

**Função:** Negociar e estabelecer **Security Associations (SAs)**.

**Versões:**
- **IKEv1** (RFC 2409) - Legado
- **IKEv2** (RFC 7296) - Moderno, recomendado

---

#### Fases do IKE

##### Fase 1: Estabelecer canal seguro (ISAKMP SA)
**Modos:**
- **Main Mode:** 6 mensagens (mais seguro)
- **Aggressive Mode:** 3 mensagens (mais rápido, menos seguro)

**Negociação:**
```

1. Algoritmos de criptografia (AES, 3DES)
2. Algoritmos de hash (SHA-256, SHA-512)
3. Método de autenticação (PSK, certificados)
4. Grupo Diffie-Hellman (DH14, DH15, DH16)

```
---

##### Fase 2: Estabelecer túnel IPSec (IPSec SA)
**Modo:** Quick Mode

**Negociação:**
- Protocolo (ESP ou AH)
- Modo (Transport ou Tunnel)
- Algoritmos de criptografia
- Lifetime (tempo de vida da SA)

---

#### IKEv2 (Recomendado)

**Vantagens sobre IKEv1:**
- ✅ Menos mensagens (4 ao invés de 9)
- ✅ Suporte nativo a NAT-T
- ✅ Mais resistente a DoS
- ✅ Suporte a mobilidade (MOBIKE)
- ✅ Detecção de peer morto (DPD integrado)

**Troca de mensagens IKEv2:**
```

Initiator Responder ││
├──IKE_SA_INIT──────────────>│  
│ (DH, nonces, proposals)    ││ │ 
│<─────IKE_SA_INIT────────────┤
│ (DH, nonces, chosen) │ │ │
├──IKE_AUTH─────────────────>│
│ (ID, Auth, SA, TSi, TSr) │ │ │
│<─────IKE_AUTH───────────────┤ │
 (ID, Auth, SA, TSi, TSr) │ │ │ 
 └────────────────────────────┘

```
---

## 🔐 Algoritmos Criptográficos

### Criptografia (Confidencialidade)

| Algoritmo | Tamanho de Chave | Status | Uso |
|-----------|------------------|--------|-----|
| **DES** | 56 bits | ❌ INSEGURO | Não usar |
| **3DES** | 168 bits | ⚠️ DEPRECADO | Evitar |
| **AES-128** | 128 bits | ✅ SEGURO | Bom |
| **AES-256** | 256 bits | ✅ SEGURO | Recomendado |
| **ChaCha20** | 256 bits | ✅ SEGURO | Moderno |

---

### Integridade (Hash)

| Algoritmo | Tamanho | Status | Uso |
|-----------|---------|--------|-----|
| **MD5** | 128 bits | ❌ INSEGURO | Não usar |
| **SHA-1** | 160 bits | ❌ INSEGURO | Não usar |
| **SHA-256** | 256 bits | ✅ SEGURO | Recomendado |
| **SHA-384** | 384 bits | ✅ SEGURO | Bom |
| **SHA-512** | 512 bits | ✅ SEGURO | Bom |

---

### Diffie-Hellman Groups

| Grupo | Tipo | Bits | Status | Uso |
|-------|------|------|--------|-----|
| **DH1** | MODP | 768 | ❌ INSEGURO | Não usar |
| **DH2** | MODP | 1024 | ❌ INSEGURO | Não usar |
| **DH5** | MODP | 1536 | ⚠️ FRACO | Evitar |
| **DH14** | MODP | 2048 | ✅ SEGURO | Bom |
| **DH15** | MODP | 3072 | ✅ SEGURO | Recomendado |
| **DH16** | MODP | 4096 | ✅ SEGURO | Muito seguro |
| **DH19** | ECC | 256 | ✅ SEGURO | Moderno |
| **DH20** | ECC | 384 | ✅ SEGURO | Moderno |

---

## 🔑 Métodos de Autenticação

### 1️⃣ PSK (Pre-Shared Key)
**Descrição:** Chave compartilhada previamente entre as partes.

**Vantagens:**
- ✅ Simples de configurar
- ✅ Não requer infraestrutura PKI

**Desvantagens:**
- ❌ Não escala bem (cada peer precisa de PSK diferente)
- ❌ Distribuição segura é desafiadora

**Exemplo de configuração (strongSwan):**
```

conn site-to-site authby=secret left=203.0.113.1 leftsubnet=192.168.1.0/24 right=203.0.113.2 rightsubnet=192.168.2.0/24 ike=aes256-sha256-modp2048! esp=aes256-sha256! auto=start

```
**Arquivo de secrets:**
```

# /etc/ipsec.secrets

203.0.113.1 203.0.113.2 : PSK "ChaveSecretaComplexa123!"

```
---

### 2️⃣ Certificados Digitais (RSA/ECDSA)
**Descrição:** Autenticação usando certificados X.509.

**Vantagens:**
- ✅ Escala bem
- ✅ Mais seguro
- ✅ Suporta revogação (CRL, OCSP)

**Desvantagens:**
- ❌ Requer PKI
- ❌ Mais complexo de configurar

**Gerar certificados (OpenSSL):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-03kh84wnr" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># CA (Certificate Authority)</span><span>
</span><span>openssl req </span><span class="token parameter" style="color:rgb(214, 222, 235)">-x509</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-newkey</span><span> rsa:4096 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-keyout</span><span> ca-key.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-out</span><span> ca-cert.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-days</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">3650</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-nodes</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Certificado do Gateway A</span><span>
</span><span>openssl req </span><span class="token parameter" style="color:rgb(214, 222, 235)">-newkey</span><span> rsa:4096 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-keyout</span><span> gatewayA-key.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-out</span><span> gatewayA-req.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-nodes</span><span>
</span><span>openssl x509 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-req</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-in</span><span> gatewayA-req.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-CA</span><span> ca-cert.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-CAkey</span><span> ca-key.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-CAcreateserial</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-out</span><span> gatewayA-cert.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-days</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">365</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Certificado do Gateway B</span><span>
</span><span>openssl req </span><span class="token parameter" style="color:rgb(214, 222, 235)">-newkey</span><span> rsa:4096 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-keyout</span><span> gatewayB-key.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-out</span><span> gatewayB-req.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-nodes</span><span>
</span><span>openssl x509 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-req</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-in</span><span> gatewayB-req.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-CA</span><span> ca-cert.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-CAkey</span><span> ca-key.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-CAcreateserial</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-out</span><span> gatewayB-cert.pem </span><span class="token parameter" style="color:rgb(214, 222, 235)">-days</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">365</span><span>
</span></code></pre></div>

---

### 3️⃣ EAP (Extensible Authentication Protocol)
**Descrição:** Usado principalmente em VPNs de acesso remoto.

**Métodos:**
- **EAP-TLS:** Certificados (mais seguro)
- **EAP-PEAP:** Senha + TLS
- **EAP-TTLS:** Similar ao PEAP

---

## ⚙️ Configuração Prática

### Exemplo 1: Site-to-Site VPN (strongSwan)

#### Topologia
```

Rede A (192.168.1.0/24) ←─── Gateway A (203.0.113.1) ←──────→ Gateway B (203.0.113.2) ───→ Rede B (192.168.2.0/24)

```
#### Gateway A (/etc/ipsec.conf)
```

config setup charondebug="ike 2, knl 2, cfg 2"

conn site-to-site type=tunnel authby=secret

```
# Local (Gateway A)
left=203.0.113.1
leftsubnet=192.168.1.0/24
leftid=@gatewayA

# Remote (Gateway B)
right=203.0.113.2
rightsubnet=192.168.2.0/24
rightid=@gatewayB

# Phase 1 (IKE)
ike=aes256-sha256-modp2048!
ikelifetime=28800s

# Phase 2 (ESP)
esp=aes256-sha256!
lifetime=3600s

# Options
keyexchange=ikev2
auto=start
dpdaction=restart
dpddelay=30s
```

```
#### Gateway A (/etc/ipsec.secrets)
```

@gatewayA @gatewayB : PSK "ChaveSecretaMuitoForte123!@#"

```
#### Gateway B (/etc/ipsec.conf)
```

config setup charondebug="ike 2, knl 2, cfg 2"

conn site-to-site type=tunnel authby=secret

```
# Local (Gateway B)
left=203.0.113.2
leftsubnet=192.168.2.0/24
leftid=@gatewayB

# Remote (Gateway A)
right=203.0.113.1
rightsubnet=192.168.1.0/24
rightid=@gatewayA

# Phase 1 (IKE)
ike=aes256-sha256-modp2048!
ikelifetime=28800s

# Phase 2 (ESP)
esp=aes256-sha256!
lifetime=3600s

# Options
keyexchange=ikev2
auto=start
dpdaction=restart
dpddelay=30s
```

```
#### Iniciar túnel
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-j21d5b6mz" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar IPSec</span><span>
</span>ipsec start
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar status</span><span>
</span>ipsec status
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver SAs ativas</span><span>
</span>ipsec statusall
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Logs</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/syslog </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> charon
</span></code></pre></div>

---

### Exemplo 2: VPN de Acesso Remoto (strongSwan)

#### Servidor (/etc/ipsec.conf)
```

config setup charondebug="ike 2, knl 2, cfg 2"

conn remote-access type=tunnel authby=secret

```
# Servidor
left=%any
leftsubnet=0.0.0.0/0
leftfirewall=yes

# Clientes
right=%any
rightsubnet=10.10.10.0/24
rightsourceip=10.10.10.10-10.10.10.100

# Phase 1
ike=aes256-sha256-modp2048!

# Phase 2
esp=aes256-sha256!

# Options
keyexchange=ikev2
auto=add
dpdaction=clear
```

```
#### Cliente (Windows/macOS/Linux)
```

Nome da conexão: Empresa VPN Servidor: vpn.empresa.com Tipo: IKEv2 Autenticação: PSK PSK: ChaveSecretaDoCliente123!

```
---

### Exemplo 3: pfSense (GUI)

#### Configurar Fase 1
```

VPN > IPsec > Tunnels > Add P1

General Information: Key Exchange version: IKEv2 Internet Protocol: IPv4 Interface: WAN Remote Gateway: 203.0.113.2

Phase 1 Proposal: Authentication Method: Mutual PSK My identifier: My IP address Peer identifier: Peer IP address Pre-Shared Key: ChaveSecretaForte123!

Encryption Algorithm: ☑ AES 256 bits Hash Algorithm: SHA256 DH Group: 14 (2048 bit) Lifetime: 28800 seconds

```
#### Configurar Fase 2
```

VPN > IPsec > Tunnels > Show Phase 2 Entries > Add P2

General Information: Mode: Tunnel IPv4 Local Network: 192.168.1.0/24 Remote Network: 192.168.2.0/24

Phase 2 Proposal: Protocol: ESP Encryption Algorithms: ☑ AES 256 bits Hash Algorithms: ☑ SHA256 PFS key group: 14 (2048 bit) Lifetime: 3600 seconds

```
---

## 🔍 Troubleshooting

### Comandos Úteis

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pcpokutel" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar status do IPSec</span><span>
</span>ipsec status
<!-- -->ipsec statusall
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar IPSec</span><span>
</span>ipsec restart
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver SAs (Security Associations)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> xfrm state
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> xfrm policy
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Capturar tráfego IPSec</span><span>
</span><span>tcpdump </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> esp
</span><span>tcpdump </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> udp port </span><span class="token" style="color:rgb(247, 140, 108)">500</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># IKE</span><span>
</span><span>tcpdump </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> eth0 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> udp port </span><span class="token" style="color:rgb(247, 140, 108)">4500</span><span> </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># NAT-T</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Logs (Linux)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/syslog </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> charon
</span><span>journalctl </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> strongswan </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span>
</span></code></pre></div>

---

### Problemas Comuns

#### 1. Fase 1 não completa
**Sintomas:**
```

no acceptable proposal found

```
**Causa:** Incompatibilidade de algoritmos

**Solução:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-5nzten0n7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar propostas em ambos os lados</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Garantir que pelo menos uma combinação seja igual:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># - Encryption (AES-256)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># - Hash (SHA-256)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># - DH Group (14)</span><span>
</span></code></pre></div>

---

#### 2. Fase 2 não completa
**Sintomas:**
```

no acceptable CHILD_SA proposal found

```
**Causa:** Incompatibilidade de algoritmos ESP ou subnets

**Solução:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-hecnqj6j5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># - Encryption ESP (AES-256)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># - Hash ESP (SHA-256)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># - Subnets locais e remotos corretos</span><span>
</span></code></pre></div>

---

#### 3. Túnel estabelece mas não passa tráfego
**Causa:** Firewall bloqueando ou rotas incorretas

**Solução:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-i6scaa9eq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar firewall</span><span>
</span><span>iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-L</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-n</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar rotas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> route show
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar rota se necessário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> route </span><span class="token" style="color:rgb(130, 170, 255)">add</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.2.0/24 via </span><span class="token" style="color:rgb(247, 140, 108)">203.0</span><span>.113.2
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar IP forwarding</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> /proc/sys/net/ipv4/ip_forward
</span></code></pre></div>

---

#### 4. NAT Traversal (NAT-T)
**Problema:** Um ou ambos os peers estão atrás de NAT

**Solução:**
```

# Habilitar NAT-T (UDP 4500)

# strongSwan habilita automaticamente

# pfSense

System > Advanced > Firewall & NAT ☑ Enable IPsec NAT Traversal

```
---

## 🛡️ Segurança e Boas Práticas

### ✅ Recomendações

#### 1. Algoritmos
```

✅ IKEv2 (não IKEv1) ✅ AES-256 (não 3DES) ✅ SHA-256+ (não SHA-1 ou MD5) ✅ DH Group 14+ (não DH1, DH2, DH5) ✅ Perfect Forward Secrecy (PFS)

```
---

#### 2. Autenticação
```

✅ Certificados (melhor escalabilidade) ✅ PSK forte (mínimo 20 caracteres aleatórios) ❌ PSK fraco (senha comum)

```
---

#### 3. Lifetimes
```

IKE SA: 8 horas (28800s) IPSec SA: 1 hora (3600s)

Rekey antes de expirar (80% do lifetime)

```
---

#### 4. DPD (Dead Peer Detection)
```

# Detectar peer morto rapidamente

dpdaction=restart dpddelay=30s dpdtimeout=120s

```
---

#### 5. Firewall
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-n60yle292" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir IKE (UDP 500)</span><span>
</span><span>iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> udp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">500</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir NAT-T (UDP 4500)</span><span>
</span><span>iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> udp </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dport</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">4500</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir ESP (protocolo 50)</span><span>
</span><span>iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> esp </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Permitir AH (protocolo 51) - se usado</span><span>
</span><span>iptables </span><span class="token parameter" style="color:rgb(214, 222, 235)">-A</span><span> INPUT </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> ah </span><span class="token parameter" style="color:rgb(214, 222, 235)">-j</span><span> ACCEPT
</span></code></pre></div>

---

## 📊 Comparação: IPSec vs Outras VPNs

| Característica | IPSec | OpenVPN | WireGuard |
|----------------|-------|---------|-----------|
| **Camada OSI** | 3 (Rede) | 4/5 (Transporte/Aplicação) | 3 (Rede) |
| **Complexidade** | Alta | Média | Baixa |
| **Performance** | Alta | Média | Muito Alta |
| **Compatibilidade** | Nativa (OS) | Requer cliente | Requer módulo kernel |
| **Firewall-friendly** | Não (ESP) | Sim (TCP/UDP) | Sim (UDP) |
| **Configuração** | Complexa | Simples | Muito Simples |
| **Uso corporativo** | Muito comum | Comum | Crescente |

---

## 🔗 Links Relacionados

- [[Fundamentos-Cripto]]
- [[VPN]]
- [[Defesa-em-Profundidade]]
- [[Network-Security]]

---

## 📚 Referências

- RFC 4301: Security Architecture for IP
- RFC 4302: IP Authentication Header (AH)
- RFC 4303: IP Encapsulating Security Payload (ESP)
- RFC 7296: Internet Key Exchange Protocol Version 2 (IKEv2)
- strongSwan: [strongswan.org](https://www.strongswan.org/)
- Libreswan: [libreswan.org](https://libreswan.org/)