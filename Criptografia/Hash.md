
# 🔐 Hash e Funções de Hash Criptográfico

> **Tags:** #hash #criptografia #md5 #sha #integridade #checksum #rainbow-table

---

## 📌 Conceito

**Hash** é uma função matemática que transforma dados de **tamanho variável** em uma **saída de tamanho fixo** (digest/resumo). É um processo **unidirecional** - não é possível reverter o hash para obter os dados originais.

🎯 **Características de uma boa função hash:**
- ✅ **Determinística:** Mesma entrada sempre gera mesma saída
- ✅ **Rápida:** Cálculo eficiente
- ✅ **Efeito avalanche:** Pequena mudança na entrada altera completamente a saída
- ✅ **Resistente a colisões:** Difícil encontrar duas entradas com mesmo hash
- ✅ **Unidirecional:** Impossível reverter (pré-imagem)

---

## 🔢 Principais Algoritmos de Hash

### MD5 (Message Digest 5)
**Tamanho:** 128 bits (32 caracteres hexadecimais)

**Status:** ❌ **OBSOLETO** - Vulnerável a colisões

**Uso histórico:**
- Verificação de integridade de arquivos
- Checksums

**Exemplo:**

Entrada: "Hello World" MD5: b10a8db164e0754105b7a99be72e3fe5

**⚠️ Não usar para:**
- Senhas
- Assinaturas digitais
- Qualquer aplicação de segurança

---

### SHA-1 (Secure Hash Algorithm 1)
**Tamanho:** 160 bits (40 caracteres hexadecimais)

**Status:** ❌ **DEPRECADO** - Vulnerável a colisões (desde 2017)

**Exemplo:**
```

Entrada: "Hello World" SHA-1: 0a4d55a8d778e5022fab701977c5d840bbc486d0

```
---

### SHA-256 (SHA-2 Family)
**Tamanho:** 256 bits (64 caracteres hexadecimais)

**Status:** ✅ **SEGURO** (recomendado)

**Uso:**
- Blockchain (Bitcoin)
- Certificados digitais
- Assinaturas de software
- Verificação de integridade

**Exemplo:**
```

Entrada: "Hello World" SHA-256: a591a6d40bf420404a011733cfb7b190d62c65bf0bcda32b57b277d9ad9f146e

```
---

### SHA-512 (SHA-2 Family)
**Tamanho:** 512 bits (128 caracteres hexadecimais)

**Status:** ✅ **MUITO SEGURO**

**Uso:**
- Aplicações que exigem máxima segurança
- Armazenamento de senhas (com salt)

**Exemplo:**
```

Entrada: "Hello World" SHA-512: 2c74fd17edafd80e8447b0d46741ee243b7eb74dd2149a0ab1b9246fb30382f27e853d8585719e0e67cbda0daa8f51671064615d645ae27acb15bfb1447f459b

```
---

## 🛡️ Uso de Hash para Integridade

### Verificação de Arquivos

#### 🖥️ Windows

**PowerShell:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-h3pat8fbf" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">Get-FileHash</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\arquivo</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>zip </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Algorithm SHA256 </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Format-List</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Saída:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Algorithm : SHA256</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Hash      : A591A6D40BF420404A011733CFB7B190...</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Path      : C:\Users\...\arquivo.zip</span><span>
</span></code></pre></div>

**CMD (certutil):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">cmd</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-affjlnyqj" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-cmd" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>certutil -hashfile .\arquivo.zip SHA256
</span></code></pre></div>

---

#### 🐧 Linux

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-daorspcmp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SHA-256</span><span>
</span>sha256sum arquivo.zip
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># MD5</span><span>
</span>md5sum arquivo.zip
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># SHA-512</span><span>
</span>sha512sum arquivo.zip
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar integridade</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;hash_esperado  arquivo.zip&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> sha256sum </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span>
</span></code></pre></div>

---

### Exemplo Prático - Download Seguro

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pdgh5htne" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 1. Baixar arquivo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wget</span><span> https://exemplo.com/software.tar.gz
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 2. Baixar hash oficial</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wget</span><span> https://exemplo.com/software.tar.gz.sha256
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 3. Verificar</span><span>
</span><span>sha256sum </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> software.tar.gz.sha256
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Saída esperada:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># software.tar.gz: OK</span><span>
</span></code></pre></div>

---

## 🔓 Ataques a Hashes

### 1️⃣ Rainbow Tables

**Descrição:** Tabelas pré-computadas de hashes para senhas comuns.

**Como funciona:**
```

Senha: "password123" MD5: 482c811da5d5b4bc6d497ffa98491e38

Atacante consulta rainbow table: 482c811da5d5b4bc6d497ffa98491e38 → "password123"

```
**Tamanho:** Podem ter terabytes de dados

**Contramedida:** **Salt** (ver abaixo)

---

### 2️⃣ Brute Force

**Descrição:** Testar todas as combinações possíveis.

**Ferramentas:**
- **Hashcat:** GPU-accelerated
- **John the Ripper:** CPU-based

**Exemplo Hashcat:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0vmnth4y0" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Quebrar hash MD5</span><span>
</span><span>hashcat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">3</span><span> hash.txt ?a?a?a?a?a?a
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># -m 0: MD5</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># -a 3: Brute force</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># ?a: Todos os caracteres</span><span>
</span></code></pre></div>

---

### 3️⃣ Dictionary Attack

**Descrição:** Testar senhas de uma wordlist.

**Wordlists famosas:**
- **rockyou.txt:** 14 milhões de senhas
- **SecLists:** Coleção de wordlists

**Exemplo:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-u8ecmdwg8" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># John the Ripper</span><span>
</span><span>john </span><span class="token parameter" style="color:rgb(214, 222, 235)">--wordlist</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>rockyou.txt hashes.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Hashcat</span><span>
</span><span>hashcat </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> hash.txt rockyou.txt
</span></code></pre></div>

---

## 🧂 Salt (Sal Criptográfico)

### Conceito

**Salt** é um valor **aleatório** adicionado à senha **antes** de fazer o hash.

**Sem salt:**
```

Usuário A: senha "123456" → MD5: e10adc3949ba59abbe56e057f20f883e Usuário B: senha "123456" → MD5: e10adc3949ba59abbe56e057f20f883e

```
❌ **Problema:** Hashes iguais! Rainbow table funciona.

**Com salt:**
```

Usuário A: senha "123456" + salt "x8Kf2p" → SHA256: a7d3f2… Usuário B: senha "123456" + salt "9mLq1z" → SHA256: b2e4c8…

```
✅ **Solução:** Hashes diferentes! Rainbow table inútil.

---

### Implementação

#### Python (bcrypt)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-gmillkmpm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> bcrypt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Gerar salt e hash</span><span>
</span><span>senha </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">b&quot;minha_senha_secreta&quot;</span><span>
</span><span>salt </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> bcrypt</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>gensalt</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">hash</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> bcrypt</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>hashpw</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>senha</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> salt</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Salt: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">salt</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Hash: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation" style="color:rgb(130, 170, 255)">hash</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar senha</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> bcrypt</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>checkpw</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>senha</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">hash</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">print</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Senha correta!&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

## 🔐 Bcrypt

**Descrição:** Algoritmo de hash **especialmente projetado** para senhas.

**Características:**
- ✅ Inclui **salt automático**
- ✅ **Adaptativo:** Pode aumentar o custo computacional
- ✅ Resistente a ataques de força bruta

**Formato:**
```

$2b$12$R9h/cIPz0gi.URNNX3kh2OPST9/PgBkqquzi.Ss7KIUgO2t0jWMUW │ │ │ │ │ │ │ └─ Hash (31 chars) │ │ └─ Salt (22 chars) │ └─ Cost factor (2^12 = 4096 rounds) └─ Algoritmo (bcrypt)

```
---

## 🛠️ Ferramentas de Hash

### HashCalc
**Plataforma:** Windows

**Descrição:** GUI para calcular hashes de arquivos.

**Download:** [slavasoft.com/hashcalc](http://www.slavasoft.com/hashcalc/)

---

### VirusTotal
**Site:** [virustotal.com](https://www.virustotal.com/gui/home/upload)

**Uso:**
1. Fazer upload do arquivo
2. VirusTotal calcula hashes automaticamente
3. Verifica se o hash é conhecido (malware)

---

### Online Hash Crackers

**Sites:**
- [crackstation.net](https://crackstation.net/)
- [hashes.com](https://hashes.com/)
- [md5decrypt.net](https://md5decrypt.net/)

⚠️ **Atenção:** Nunca use hashes de senhas reais nesses sites!

---

## 🎯 Casos de Uso

### 1️⃣ Verificação de Integridade
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1l2lcvpqj" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar checksum de backup</span><span>
</span><span>sha256sum backup.tar.gz </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> backup.sha256
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar após restauração</span><span>
</span><span>sha256sum </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> backup.sha256
</span></code></pre></div>

---

### 2️⃣ Assinatura Digital
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pgjyid82z" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Assinar documento</span><span>
</span><span>openssl dgst </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sha256</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sign</span><span> private.key </span><span class="token parameter" style="color:rgb(214, 222, 235)">-out</span><span> documento.sig documento.pdf
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar assinatura</span><span>
</span><span>openssl dgst </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sha256</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-verify</span><span> public.key </span><span class="token parameter" style="color:rgb(214, 222, 235)">-signature</span><span> documento.sig documento.pdf
</span></code></pre></div>

---

### 3️⃣ Blockchain
```

Bloco anterior: Hash A Transações: … Nonce: 12345 Hash do bloco: SHA256(A + transações + nonce)

```
---

### 4️⃣ Git (Controle de Versão)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vf5cia5lo" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Git usa SHA-1 para identificar commits</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">git</span><span> log </span><span class="token parameter" style="color:rgb(214, 222, 235)">--oneline</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Saída:</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># a7f3e2b Fix bug in login</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># b2c4d8f Add new feature</span><span>
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[Criptografia]]
- [[PKI-Certificados]]
- [[IPSec]]
- [[Esteganografia]]

---

## 📚 Referências

- NIST - Secure Hash Standard (FIPS 180-4)
- [SHA-256 Online Calculator](https://emn178.github.io/online-tools/sha256.html)
- [Bcrypt Calculator](https://bcrypt-generator.com/)
