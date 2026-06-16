
# 🔐 Fundamentos de Criptografia

> **Tags:** #criptografia #encryption #seguranca #confidencialidade #integridade #autenticacao

---

## 📌 Conceitos Fundamentais

### O que é Criptografia?

**Criptografia** é a ciência de **proteger informações** através da transformação de dados legíveis (plaintext) em formato ilegível (ciphertext), de forma que apenas partes autorizadas possam acessá-los.

🎯 **Objetivos da Criptografia:**
- 🔒 **Confidencialidade:** Apenas destinatários autorizados podem ler
- ✅ **Integridade:** Detectar modificações não autorizadas
- 🔑 **Autenticação:** Verificar identidade do remetente
- 🚫 **Não-repúdio:** Remetente não pode negar ter enviado

---

## 📚 Terminologia Básica

| Termo | Definição |
|-------|-----------|
| **Plaintext** | Texto original (legível) |
| **Ciphertext** | Texto cifrado (ilegível) |
| **Encryption** | Processo de cifrar (plaintext → ciphertext) |
| **Decryption** | Processo de decifrar (ciphertext → plaintext) |
| **Key** | Chave usada para cifrar/decifrar |
| **Algorithm** | Método matemático usado (AES, RSA, etc) |
| **Cipher** | Algoritmo de criptografia |

---

## 🔑 Tipos de Criptografia

### 1️⃣ Criptografia Simétrica (Chave Única)

**Conceito:** Mesma chave é usada para **cifrar e decifrar**.

┌─────────┐ Chave K ┌─────────┐ │ Plaintext│ ───────────→ │Ciphertext│ └─────────┘ Encryption └─────────┘ ↓ Chave K ↓ ┌─────────┐ ┌─────────┐ │ Plaintext│ ←─────────── │Ciphertext│ └─────────┘ Decryption └─────────┘

**Vantagens:**
- ✅ **Rápido** (ideal para grandes volumes)
- ✅ Menos processamento

**Desvantagens:**
- ❌ Distribuição segura da chave é desafiadora
- ❌ Não fornece não-repúdio

---

#### Algoritmos Simétricos Comuns

##### AES (Advanced Encryption Standard)
**Tamanhos de chave:** 128, 192, 256 bits

**Uso:** Padrão atual para criptografia simétrica

**Exemplo Python:**

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2sy414wb3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">from</span><span> Crypto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Cipher </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> AES
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> Crypto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Random </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> get_random_bytes
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> Crypto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Util</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Padding </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> pad</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> unpad
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar chave</span><span>
</span><span>key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> get_random_bytes</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">32</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 256 bits</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar cipher</span><span>
</span><span>cipher </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>new</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>key</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MODE_CBC</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Cifrar</span><span>
</span><span>plaintext </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;Mensagem secreta&quot;</span><span>
</span><span>ciphertext </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> cipher</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>encrypt</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>pad</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>plaintext</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>block_size</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Decifrar</span><span>
</span><span>decipher </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>new</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>key</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MODE_CBC</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> cipher</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>iv</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>decrypted </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> unpad</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>decipher</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>decrypt</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>ciphertext</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>block_size</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Original: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">plaintext</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Cifrado: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">ciphertext</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">.</span><span class="token string-interpolation interpolation" style="color:rgb(130, 170, 255)">hex</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">)</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Decifrado: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">decrypted</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

##### DES (Data Encryption Standard)
**Tamanho de chave:** 56 bits

**Status:** ❌ **OBSOLETO** (quebrado por força bruta)

**Substituto:** 3DES (Triple DES) ou AES

---

##### 3DES (Triple DES)
**Tamanho de chave:** 168 bits (3 × 56)

**Status:** ⚠️ **DEPRECADO** (lento, sendo substituído por AES)

---

##### Blowfish
**Tamanho de chave:** 32-448 bits

**Status:** ✅ Ainda usado, mas AES é preferível

---

##### ChaCha20
**Tamanho de chave:** 256 bits

**Status:** ✅ Moderno, rápido (usado em TLS 1.3)

**Uso:** Alternativa ao AES, especialmente em dispositivos móveis

---

#### Modos de Operação

##### ECB (Electronic Codebook) - ❌ NÃO USAR
**Problema:** Blocos idênticos geram ciphertext idêntico
```

Plaintext: AAAA BBBB AAAA Ciphertext: XXXX YYYY XXXX # Padrão visível!

```
---

##### CBC (Cipher Block Chaining) - ✅ Seguro
**Características:**
- Usa IV (Initialization Vector)
- Cada bloco depende do anterior
- Mais seguro que ECB

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7egg2a2al" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>cipher </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>new</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>key</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MODE_CBC</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>iv </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> cipher</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>iv  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Salvar IV para decifrar</span><span>
</span></code></pre></div>

---

##### GCM (Galois/Counter Mode) - ✅ Recomendado
**Características:**
- **AEAD** (Authenticated Encryption with Associated Data)
- Fornece confidencialidade + integridade
- Usado em TLS 1.3

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-z00lz6mw0" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>cipher </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>new</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>key</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> AES</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MODE_GCM</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>ciphertext</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> tag </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> cipher</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>encrypt_and_digest</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>plaintext</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

### 2️⃣ Criptografia Assimétrica (Chave Pública/Privada)

**Conceito:** Usa **par de chaves** - uma pública (compartilhada) e uma privada (secreta).
```

┌──────────────┐ ┌──────────────┐ │ Alice │ │ Bob │ │ │ │ │ │ Chave Pública│◄───────────────────│Chave Pública │ │ Chave Privada│ │Chave Privada │ └──────────────┘ └──────────────┘

Bob cifra com chave pública de Alice Alice decifra com sua chave privada

```
**Vantagens:**
- ✅ Não precisa compartilhar chave secreta
- ✅ Fornece não-repúdio (assinaturas digitais)
- ✅ Facilita distribuição de chaves

**Desvantagens:**
- ❌ **Lento** (1000x mais lento que simétrica)
- ❌ Mais processamento

---

#### Algoritmos Assimétricos Comuns

##### RSA (Rivest-Shamir-Adleman)
**Tamanhos de chave:** 1024, 2048, 4096 bits

**Uso:**
- Assinaturas digitais
- Troca de chaves
- Certificados SSL/TLS

**Exemplo Python:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-aqydbme5y" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">from</span><span> Crypto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>PublicKey </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> RSA
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> Crypto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Cipher </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> PKCS1_OAEP
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar par de chaves</span><span>
</span><span>key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> RSA</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>generate</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">2048</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>private_key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>export_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>public_key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>publickey</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>export_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Cifrar com chave pública</span><span>
</span><span>recipient_key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> RSA</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>import_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>public_key</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>cipher </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> PKCS1_OAEP</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>new</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>recipient_key</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>ciphertext </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> cipher</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>encrypt</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">b&quot;Mensagem secreta&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Decifrar com chave privada</span><span>
</span><span>private_key_obj </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> RSA</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>import_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>private_key</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>decipher </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> PKCS1_OAEP</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>new</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>private_key_obj</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>plaintext </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> decipher</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>decrypt</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>ciphertext</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

##### ECC (Elliptic Curve Cryptography)
**Tamanhos de chave:** 256, 384, 521 bits

**Vantagens:**
- ✅ Chaves menores com mesma segurança (256-bit ECC ≈ 3072-bit RSA)
- ✅ Mais rápido que RSA
- ✅ Menos uso de recursos

**Uso:**
- Bitcoin/Ethereum
- TLS 1.3
- SSH (Ed25519)

**Exemplo (Assinatura Digital):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4x3h6nayp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">from</span><span> cryptography</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hazmat</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>primitives</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>asymmetric </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> ec
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> cryptography</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hazmat</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>primitives </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> hashes
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar par de chaves</span><span>
</span><span>private_key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> ec</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>generate_private_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>ec</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SECP256R1</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>public_key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> private_key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>public_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Assinar</span><span>
</span><span>signature </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> private_key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>sign</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>    </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;Mensagem&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    ec</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>ECDSA</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SHA256</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">try</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    public_key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>verify</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>        signature</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>        </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;Mensagem&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>        ec</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>ECDSA</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SHA256</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    </span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Assinatura válida!&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">except</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Assinatura inválida!&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

##### Diffie-Hellman (DH)
**Uso:** **Troca de chaves** (não cifra dados diretamente)

**Como funciona:**
```

Alice e Bob querem compartilhar segredo sem transmiti-lo

1. Alice e Bob concordam em números públicos (p, g)
2. Alice escolhe número secreto a, calcula A = g^a mod p
3. Bob escolhe número secreto b, calcula B = g^b mod p
4. Alice envia A para Bob (público)
5. Bob envia B para Alice (público)
6. Alice calcula s = B^a mod p
7. Bob calcula s = A^b mod p
8. Ambos chegam ao mesmo segredo s!

```
**Exemplo Python:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-89e8dkko4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">from</span><span> cryptography</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hazmat</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>primitives</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>asymmetric </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> dh
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> cryptography</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hazmat</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>primitives</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>kdf</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hkdf </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> HKDF
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> cryptography</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hazmat</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>primitives </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> hashes
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar parâmetros</span><span>
</span><span>parameters </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> dh</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>generate_parameters</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>generator</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">2</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> key_size</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">2048</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alice</span><span>
</span><span>alice_private </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> parameters</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>generate_private_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>alice_public </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> alice_private</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>public_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bob</span><span>
</span><span>bob_private </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> parameters</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>generate_private_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>bob_public </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> bob_private</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>public_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alice deriva chave compartilhada</span><span>
</span><span>alice_shared </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> alice_private</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>exchange</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>bob_public</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bob deriva chave compartilhada</span><span>
</span><span>bob_shared </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> bob_private</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>exchange</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>alice_public</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># alice_shared == bob_shared ✅</span><span>
</span></code></pre></div>

---

### 3️⃣ Criptografia Híbrida

**Conceito:** Combina **simétrica** (velocidade) com **assimétrica** (segurança de distribuição).

**Como funciona:**
```

1. Gerar chave simétrica aleatória (session key)
2. Cifrar dados com chave simétrica (AES)
3. Cifrar chave simétrica com chave pública do destinatário (RSA)
4. Enviar: ciphertext + chave simétrica cifrada
5. Destinatário decifra chave simétrica com chave privada
6. Destinatário decifra dados com chave simétrica

```
**Uso:** TLS/SSL, PGP, S/MIME

---

## 🔏 Funções de Hash Criptográfico

**Conceito:** Função **unidirecional** que gera **fingerprint** de tamanho fixo.

**Características:**
- ✅ Determinística (mesma entrada = mesma saída)
- ✅ Rápida de calcular
- ✅ Impossível reverter (unidirecional)
- ✅ Resistente a colisões
- ✅ Efeito avalanche (pequena mudança = hash completamente diferente)

### Algoritmos de Hash

| Algoritmo | Tamanho | Status | Uso |
|-----------|---------|--------|-----|
| **MD5** | 128 bits | ❌ QUEBRADO | Não usar |
| **SHA-1** | 160 bits | ❌ DEPRECADO | Não usar |
| **SHA-256** | 256 bits | ✅ SEGURO | Recomendado |
| **SHA-512** | 512 bits | ✅ SEGURO | Recomendado |
| **SHA-3** | Variável | ✅ SEGURO | Moderno |
| **BLAKE2** | Variável | ✅ SEGURO | Rápido |

**Exemplo:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-cf2tk2375" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> hashlib
</span>
<span>texto </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Mensagem secreta&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># MD5 (não usar!)</span><span>
</span><span>md5 </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> hashlib</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>md5</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>texto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>encode</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hexdigest</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;MD5: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">md5</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SHA-256 (recomendado)</span><span>
</span><span>sha256 </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> hashlib</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>sha256</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>texto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>encode</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hexdigest</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;SHA-256: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">sha256</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SHA-512</span><span>
</span><span>sha512 </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> hashlib</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>sha512</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>texto</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>encode</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hexdigest</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;SHA-512: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">sha512</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

### Uso de Hashes

#### 1. Verificação de Integridade
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-diedsazu7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Calcular hash de arquivo</span><span>
</span>sha256sum arquivo.zip
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># a591a6d40bf420404a011733cfb7b190...</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;a591a6d40bf420404a011733cfb7b190...  arquivo.zip&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> sha256sum </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># arquivo.zip: OK</span><span>
</span></code></pre></div>

---

#### 2. Armazenamento de Senhas (com Salt)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-2eb4zr79j" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> bcrypt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Hash de senha (com salt automático)</span><span>
</span><span>senha </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;senha123&quot;</span><span>
</span><span>hashed </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> bcrypt</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hashpw</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>senha</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> bcrypt</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>gensalt</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar senha</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> bcrypt</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>checkpw</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>senha</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> hashed</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Senha correta!&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

#### 3. HMAC (Hash-based Message Authentication Code)
**Uso:** Verificar integridade + autenticidade

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wq4rtvkqw" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> hmac
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> hashlib
</span>
<span>mensagem </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;Dados importantes&quot;</span><span>
</span><span>chave </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;chave_secreta&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar HMAC</span><span>
</span><span>mac </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> hmac</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>new</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>chave</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> mensagem</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> hashlib</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>sha256</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hexdigest</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar HMAC</span><span>
</span><span>mac_recebido </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;...&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> hmac</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>compare_digest</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>mac</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> mac_recebido</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Mensagem autêntica e íntegra!&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

## 🔐 Assinaturas Digitais

**Conceito:** Garantir **autenticidade** e **integridade** de mensagem.

**Como funciona:**
```

1. Alice calcula hash da mensagem
2. Alice cifra hash com sua chave privada (assinatura)
3. Alice envia: mensagem + assinatura
4. Bob calcula hash da mensagem recebida
5. Bob decifra assinatura com chave pública de Alice
6. Bob compara os hashes
    - Iguais = mensagem autêntica e íntegra ✅
    - Diferentes = mensagem alterada ou falsa ❌

```
**Exemplo:**

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-fipmlqecd" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">from</span><span> cryptography</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hazmat</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>primitives</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>asymmetric </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> rsa</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> padding
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> cryptography</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hazmat</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>primitives </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> hashes
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alice gera par de chaves</span><span>
</span><span>private_key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> rsa</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>generate_private_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>public_exponent</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">65537</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> key_size</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">2048</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>public_key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> private_key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>public_key</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Alice assina mensagem</span><span>
</span><span>mensagem </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;Contrato importante&quot;</span><span>
</span><span>assinatura </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> private_key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>sign</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>    mensagem</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    padding</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>PSS</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>        mgf</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>padding</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MGF1</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SHA256</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>        salt_length</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>padding</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>PSS</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MAX_LENGTH
</span><span>    </span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SHA256</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Bob verifica assinatura</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">try</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    public_key</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>verify</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>        assinatura</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>        mensagem</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>        padding</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>PSS</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>            mgf</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>padding</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MGF1</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SHA256</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>            salt_length</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>padding</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>PSS</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>MAX_LENGTH
</span><span>        </span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>        hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SHA256</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    </span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Assinatura válida! ✅&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">except</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Assinatura inválida! ❌&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

## 🔑 Gestão de Chaves

### Princípios

#### 1. Geração de Chaves
- ✅ Usar geradores de números aleatórios criptograficamente seguros (CSPRNG)
- ✅ Tamanho adequado (AES-256, RSA-2048+)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-zr5ykwmrl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> secrets
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar chave aleatória</span><span>
</span><span>key </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> secrets</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>token_bytes</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(247, 140, 108)">32</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 256 bits</span><span>
</span></code></pre></div>

---

#### 2. Armazenamento de Chaves
- ✅ **Hardware Security Module (HSM)**
- ✅ **Key Management Service (KMS)** - AWS KMS, Azure Key Vault
- ✅ **Vaults** - HashiCorp Vault
- ❌ **NUNCA** hardcoded no código
- ❌ **NUNCA** em repositórios Git

---

#### 3. Rotação de Chaves
```

Frequência recomendada:

- Chaves simétricas: Anual
- Certificados SSL: Anual
- Chaves de API: Trimestral
- Senhas: 90 dias

```
---

#### 4. Destruição de Chaves
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4szt7kwxa" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Sobrescrever memória antes de deletar</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> ctypes
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">def</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">secure_delete</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>data</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Sobrescrever com zeros</span><span>
</span><span>    ctypes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>memset</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">id</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>data</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">len</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>data</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">del</span><span> data
</span></code></pre></div>

---

## 🌐 Protocolos Criptográficos

### TLS/SSL (Transport Layer Security)

**Versões:**
- SSL 2.0 - ❌ INSEGURO
- SSL 3.0 - ❌ INSEGURO (POODLE)
- TLS 1.0 - ❌ DEPRECADO
- TLS 1.1 - ❌ DEPRECADO
- TLS 1.2 - ✅ SEGURO
- TLS 1.3 - ✅ RECOMENDADO

**Handshake TLS 1.3:**
```

Cliente Servidor │ │ ├──ClientHello──────────────────>│ │ (cipher suites, key share) │ │ │ │<─────ServerHello────────────────┤ │ (cipher, key share, cert) │ │ │ ├──[Encrypted]──────────────────>│ │ │ │<─────[Encrypted]────────────────┤

```
---

### SSH (Secure Shell)

**Autenticação:**
- Senha (menos seguro)
- Chave pública (recomendado)

**Gerar par de chaves:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4ooa5jrtx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ed25519 (recomendado)</span><span>
</span><span>ssh-keygen </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> ed25519 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-C</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;seu@email.com&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># RSA (alternativa)</span><span>
</span><span>ssh-keygen </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> rsa </span><span class="token parameter" style="color:rgb(214, 222, 235)">-b</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">4096</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-C</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;seu@email.com&quot;</span><span>
</span></code></pre></div>

---

### PGP/GPG (Pretty Good Privacy)

**Uso:**
- Criptografia de e-mails
- Assinatura de arquivos
- Criptografia de arquivos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-o5a5l3pja" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar par de chaves</span><span>
</span>gpg --full-generate-key
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Cifrar arquivo</span><span>
</span><span>gpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">-e</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> destinatario@email.com arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Decifrar</span><span>
</span><span>gpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> arquivo.txt.gpg </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Assinar</span><span>
</span><span>gpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">--sign</span><span> arquivo.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar assinatura</span><span>
</span><span>gpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">--verify</span><span> arquivo.txt.sig
</span></code></pre></div>

---

## ⚠️ Ataques Criptográficos

### 1. Brute Force
**Defesa:** Chaves longas (AES-256, RSA-2048+)

### 2. Rainbow Tables
**Defesa:** Salt em hashes de senha

### 3. Man-in-the-Middle (MITM)
**Defesa:** Certificados digitais, pinning

### 4. Padding Oracle
**Defesa:** Usar AEAD (GCM), não CBC sem MAC

### 5. Timing Attacks
**Defesa:** Comparação de tempo constante

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-bnz89hfbk" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> hmac
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># ❌ Vulnerável a timing attack</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> hash1 </span><span class="token" style="color:rgb(127, 219, 202)">==</span><span> hash2</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">pass</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># ✅ Seguro (tempo constante)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> hmac</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>compare_digest</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>hash1</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> hash2</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">pass</span><span>
</span></code></pre></div>

---

## 🎯 Boas Práticas

### ✅ DO (Faça)
- Usar bibliotecas estabelecidas (OpenSSL, libsodium, cryptography)
- Manter bibliotecas atualizadas
- Usar algoritmos modernos (AES-256, RSA-2048+, SHA-256+)
- Usar salt em hashes de senha
- Usar AEAD quando possível (GCM)
- Validar certificados SSL/TLS
- Implementar rotação de chaves

### ❌ DON'T (Não Faça)
- **NUNCA** criar seu próprio algoritmo criptográfico
- **NUNCA** usar MD5 ou SHA-1 para segurança
- **NUNCA** reutilizar IVs/nonces
- **NUNCA** hardcoded chaves no código
- **NUNCA** usar ECB mode
- **NUNCA** armazenar senhas em plaintext

---

## 🔗 Links Relacionados

- [[Hash]]
- [[IPSec]]
- [[PKI-Certificados]]
- [[Esteganografia]]

---

## 📚 Referências

- NIST Cryptographic Standards: [csrc.nist.gov](https://csrc.nist.gov/)
- Cryptography.io: [cryptography.io](https://cryptography.io/)
- OpenSSL: [openssl.org](https://www.openssl.org/)
- Libsodium: [libsodium.org](https://libsodium.org/)