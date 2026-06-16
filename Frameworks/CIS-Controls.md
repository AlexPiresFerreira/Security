
# 🛡️ CIS Controls (Critical Security Controls)

> **Tags:** #cis #controls #security #best-practices #hardening #cybersecurity

---

## 📌 Visão Geral

Os **CIS Controls** (anteriormente conhecidos como SANS Top 20) são um conjunto de **ações prioritárias** para defesa cibernética, desenvolvidas pelo **Center for Internet Security (CIS)**.

🎯 **Objetivo:** Fornecer um conjunto prescritivo e priorizado de ações para proteger organizações contra as ameaças cibernéticas mais comuns.

**Site oficial:** [cisecurity.org/controls](https://www.cisecurity.org/controls/)

**Versão atual:** CIS Controls v8 (2021)

---

## 📊 Estrutura dos CIS Controls v8

### 18 Controles Organizados em 3 Grupos de Implementação

┌─────────────────────────────────────────┐ 
│ Implementation Group 1 (IG1)                         │
│ Controles essenciais básicos                            │
│ Para organizações pequenas                            │ ├─────────────────────────────────────────┤
│ Implementation Group 2 (IG2)                          │
│ Controles intermediários                                  │
│ Para organizações médias                                 │ ├─────────────────────────────────────────┤
│ Implementation Group 3 (IG3)                         │
│ Controles avançados                                        │
│ Para organizações grandes/críticas                  │ └─────────────────────────────────────────┘


---

## 🔵 Basic CIS Controls (Controles Básicos)

### 1️⃣ Inventory and Control of Enterprise Assets

**Objetivo:** Gerenciar ativamente todos os dispositivos de hardware conectados à rede.

**Por que é importante:**
- Não é possível proteger o que você não conhece
- Dispositivos não autorizados são vetores de ataque

**Ações:**

#### 1.1 - Estabelecer e Manter Inventário de Ativos
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-cvra1bbf8" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">Ativo</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Servidor Web Produção
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Tipo</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Servidor físico
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Localização</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Data Center Principal
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">IP</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> 192.168.10.50
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">SO</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Ubuntu 22.04 LTS
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Responsável</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Equipe de Infraestrutura
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Criticidade</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Alta
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Última atualização</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token datetime" style="color:rgb(247, 140, 108)">2025-12-31</span><span>
</span></code></pre></div>

**Ferramentas:**
- **Nmap:** Descoberta de rede
- **Asset Management:** ServiceNow, Lansweeper
- **CMDB:** Configuration Management Database

---

#### 1.2 - Endereçar Ativos Não Autorizados
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9imlapd3h" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Detectar dispositivos não autorizados</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">-sn</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.0/24 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-oG</span><span> - </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">grep</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Up&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> dispositivos_ativos.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Comparar com inventário autorizado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">comm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-13</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> inventario_autorizado.txt</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>         </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> dispositivos_ativos.txt</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> nao_autorizados.txt
</span></code></pre></div>

**Ação:** Isolar ou remover dispositivos não autorizados

---

### 2️⃣ Inventory and Control of Software Assets

**Objetivo:** Gerenciar ativamente todo o software instalado.

**Ações:**

#### 2.1 - Estabelecer Inventário de Software
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-j4petag6n" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux - Listar pacotes instalados</span><span>
</span><span>dpkg </span><span class="token parameter" style="color:rgb(214, 222, 235)">-l</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> software_inventory.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Debian/Ubuntu</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rpm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-qa</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> software_inventory.txt  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Red Hat/CentOS</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Windows - PowerShell</span><span>
</span><span>Get-WmiObject </span><span class="token parameter" style="color:rgb(214, 222, 235)">-Class</span><span> Win32_Product </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> Export-Csv software_inventory.csv
</span></code></pre></div>

---

#### 2.3 - Software Autorizado
**Implementar whitelist de software:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-rrqicrnot" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># AppLocker (Windows)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-AppLockerPolicy</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>RuleType Publisher </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>User Everyone `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>RuleNamePrefix </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Permitido&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:\Program Files\SoftwareAutorizado\*&quot;</span><span>
</span></code></pre></div>

---

#### 2.7 - Remover Software Não Autorizado
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-e7ltgl4mt" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Identificar software não autorizado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">comm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-13</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> software_autorizado.txt</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">\</span><span>
</span><span>         </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">sort</span><span> software_instalado.txt</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> software_nao_autorizado.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">while</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">read</span><span> software</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">do</span><span>
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> remove </span><span class="token parameter" style="color:rgb(214, 222, 235)">-y</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(214, 222, 235)">$software</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">done</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&lt;</span><span> software_nao_autorizado.txt
</span></code></pre></div>

---

### 3️⃣ Data Protection

**Objetivo:** Proteger dados sensíveis.

**Ações:**

#### 3.1 - Estabelecer e Manter Processo de Classificação de Dados
```

PÚBLICO: Sem restrição INTERNO: Apenas funcionários CONFIDENCIAL: Acesso restrito + MFA SECRETO: Máxima proteção + auditoria detalhada

```
---

#### 3.3 - Configurar Proteção de Dados em Trânsito
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">nginx</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-4ejdw0uwo" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-nginx" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Nginx - Forçar HTTPS</span><span>
</span><span></span><span class="token directive" style="color:rgb(127, 219, 202)">server</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">listen</span><span class="token directive"> </span><span class="token directive" style="color:rgb(247, 140, 108)">80</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">server_name</span><span class="token directive"> exemplo.com</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">return</span><span class="token directive"> </span><span class="token directive" style="color:rgb(247, 140, 108)">301</span><span class="token directive"> https://</span><span class="token directive" style="color:rgb(214, 222, 235)">$server_name</span><span class="token directive" style="color:rgb(214, 222, 235)">$request_uri</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span>
<span></span><span class="token directive" style="color:rgb(127, 219, 202)">server</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">listen</span><span class="token directive"> </span><span class="token directive" style="color:rgb(247, 140, 108)">443</span><span class="token directive"> ssl http2</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">server_name</span><span class="token directive"> exemplo.com</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">ssl_certificate</span><span class="token directive"> /etc/ssl/certs/exemplo.crt</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">ssl_certificate_key</span><span class="token directive"> /etc/ssl/private/exemplo.key</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># TLS 1.2 e 1.3 apenas</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">ssl_protocols</span><span class="token directive"> TLSv1.2 TLSv1.3</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span>    </span><span class="token directive" style="color:rgb(127, 219, 202)">ssl_ciphers</span><span class="token directive"> HIGH:!aNULL:!MD5</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

#### 3.4 - Implementar Criptografia de Dados em Repouso
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-llhw9ms62" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux - LUKS (disk encryption)</span><span>
</span>cryptsetup luksFormat /dev/sdb
<!-- -->cryptsetup luksOpen /dev/sdb encrypted_disk
<!-- -->mkfs.ext4 /dev/mapper/encrypted_disk
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Windows - BitLocker</span><span>
</span><span>Enable-BitLocker </span><span class="token parameter" style="color:rgb(214, 222, 235)">-MountPoint</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-EncryptionMethod</span><span> XtsAes256
</span></code></pre></div>

---

### 4️⃣ Secure Configuration of Enterprise Assets and Software

**Objetivo:** Configurar dispositivos e software de forma segura.

**Ações:**

#### 4.1 - Estabelecer e Manter Processo de Configuração Segura
**Usar CIS Benchmarks:**
- CIS Benchmark for Ubuntu Linux
- CIS Benchmark for Windows Server
- CIS Benchmark for Cisco IOS

**Download:** [cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks/)

---

#### 4.2 - Estabelecer e Manter Baseline de Configuração Segura
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-yovum93y3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar baseline</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 1. Instalar sistema limpo</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 2. Aplicar hardening</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 3. Documentar configurações</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># 4. Criar snapshot/imagem</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar compliance</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar CIS-CAT (CIS Configuration Assessment Tool)</span><span>
</span></code></pre></div>

---

#### 4.7 - Gerenciar Configurações Padrão de Contas
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-w0cmxmog2" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar contas padrão</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">usermod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-L</span><span> root  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux</span><span>
</span><span>Disable-LocalUser </span><span class="token parameter" style="color:rgb(214, 222, 235)">-Name</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Administrator&quot;</span><span>  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Windows</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Forçar mudança de senha no primeiro login</span><span>
</span><span>chage </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> usuario  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux</span><span>
</span></code></pre></div>

---

### 5️⃣ Account Management

**Objetivo:** Gerenciar o ciclo de vida de contas de usuário.

**Ações:**

#### 5.1 - Estabelecer e Manter Inventário de Contas
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">sql</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ohchfox0y" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-sql" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic">-- Listar todas as contas</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">SELECT</span><span> username</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> created_date</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> last_login</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> is_active
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">FROM</span><span> users
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">ORDER</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">BY</span><span> last_login </span><span class="token" style="color:rgb(127, 219, 202)">DESC</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span>
</span></code></pre></div>

---

#### 5.2 - Usar Autenticação Única (SSO)
**Implementar:**
- **SAML 2.0**
- **OAuth 2.0 / OpenID Connect**
- **LDAP/Active Directory**

**Benefícios:**
- ✅ Gerenciamento centralizado
- ✅ Melhor experiência do usuário
- ✅ Facilita auditoria

---

#### 5.3 - Desabilitar Contas Inativas
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-g1a3h626y" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Encontrar contas sem login há 90+ dias</span><span>
</span><span>lastlog </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">awk</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;$4 &gt; 90 {print $1}&#x27;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">usermod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-L</span><span> usuario_inativo
</span></code></pre></div>

---

#### 5.4 - Restringir Privilégios de Administrador
```

Princípio do Menor Privilégio:

- Usuários comuns: Sem privilégios administrativos
- Administradores: Contas separadas (admin-joao)
- Usar sudo/runas quando necessário

```
---

### 6️⃣ Access Control Management

**Objetivo:** Gerenciar acesso a ativos baseado em necessidade.

**Ações:**

#### 6.1 - Estabelecer Processo de Controle de Acesso
**Implementar RBAC (Role-Based Access Control):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-99ni170km" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">Função</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Analista de Suporte
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Permissões</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Ler tickets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> SIM
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Criar tickets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> SIM
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Deletar tickets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> NÃO
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Acessar logs</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> NÃO
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Modificar configurações</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> NÃO
</span></code></pre></div>

---

#### 6.2 - Estabelecer Processo de Revisão de Acesso
```

Frequência: Trimestral Responsável: Gestor de cada área Ações:

1. Revisar lista de acessos
2. Remover acessos desnecessários
3. Documentar justificativa para manter acessos
4. Aprovar formalmente

```
---

#### 6.5 - Requerer MFA

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-kk77hxl6u" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Exemplo Flask com MFA</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">from</span><span> flask </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> Flask</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> request
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> pyotp
</span>
<span>app </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> Flask</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>__name__</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token decorator annotation" style="color:rgb(199, 146, 234)">@app</span><span class="token decorator annotation" style="color:rgb(199, 146, 234)">.</span><span class="token decorator annotation" style="color:rgb(199, 146, 234)">route</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;/login&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> methods</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;POST&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">def</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">login</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    username </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> request</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>form</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;username&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span><span>    password </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> request</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>form</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;password&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span><span>    totp_code </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> request</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>form</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;totp&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar senha</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">not</span><span> verify_password</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>username</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> password</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>        </span><span class="token" style="color:rgb(127, 219, 202)">return</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Credenciais inválidas&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">401</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar TOTP</span><span>
</span><span>    user_secret </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> get_user_totp_secret</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>username</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    totp </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> pyotp</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>TOTP</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>user_secret</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">not</span><span> totp</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>verify</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>totp_code</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>        </span><span class="token" style="color:rgb(127, 219, 202)">return</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Código MFA inválido&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">401</span><span>
</span>
<span>    </span><span class="token" style="color:rgb(127, 219, 202)">return</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Login bem-sucedido&quot;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">200</span><span>
</span></code></pre></div>

---

### 7️⃣ Continuous Vulnerability Management

**Objetivo:** Desenvolver plano para avaliar e remediar vulnerabilidades continuamente.

**Ações:**

#### 7.1 - Estabelecer e Manter Processo de Gestão de Vulnerabilidades
```

1. Scan semanal de vulnerabilidades
2. Priorizar por CVSS score
3. Aplicar patches críticos em 48h
4. Aplicar patches altos em 7 dias
5. Aplicar patches médios em 30 dias
6. Re-scan para verificar correção

```
---

#### 7.2 - Estabelecer e Manter Processo de Remediação
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ed9cmvhox" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan com Nmap NSE</span><span>
</span><span>nmap </span><span class="token parameter" style="color:rgb(214, 222, 235)">--script</span><span> vuln </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.0/24 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-oX</span><span> vuln_scan.xml
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ou usar scanner dedicado</span><span>
</span><span>nessus_scan.sh </span><span class="token parameter" style="color:rgb(214, 222, 235)">--target</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">192.168</span><span>.1.0/24 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--output</span><span> report.html
</span></code></pre></div>

---

#### 7.3 - Realizar Testes de Penetração Automatizados
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-74ovd8cm7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Nuclei - Scanner de vulnerabilidades</span><span>
</span><span>nuclei </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> https://exemplo.com </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> cves/ </span><span class="token parameter" style="color:rgb(214, 222, 235)">-o</span><span> resultados.txt
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># OWASP ZAP - Scan automatizado</span><span>
</span>zap-cli quick-scan --self-contained https://exemplo.com
</code></pre></div>

---

### 8️⃣ Audit Log Management

**Objetivo:** Coletar, alertar, revisar e reter logs de auditoria.

**Ações:**

#### 8.2 - Coletar Logs de Auditoria
**O que logar:**
```

✅ Autenticações (sucesso e falha) ✅ Mudanças de configuração ✅ Acesso a dados sensíveis ✅ Criação/modificação/exclusão de contas ✅ Mudanças de privilégios ✅ Instalação de software ✅ Conexões de rede

```
---

#### 8.3 - Garantir Proteção Adequada de Logs
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-e8wjd50v0" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Logs imutáveis (append-only)</span><span>
</span>chattr +a /var/log/audit/audit.log
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Enviar para servidor centralizado (syslog)</span><span>
</span>*.* @@siem-server.empresa.com:514
</code></pre></div>

---

#### 8.5 - Coletar Logs Detalhados
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-uorye6ps7" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">import</span><span> logging
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Configurar logging detalhado</span><span>
</span><span>logging</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>basicConfig</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>
</span><span>    level</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span>logging</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>INFO</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    </span><span class="token" style="color:rgb(130, 170, 255)">format</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;%(asctime)s - %(name)s - %(levelname)s - %(message)s&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>    handlers</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(199, 146, 234)">[</span><span>
</span><span>        logging</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>FileHandler</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;/var/log/app/app.log&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>
</span><span>        logging</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>StreamHandler</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>    </span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Log de eventos</span><span>
</span><span>logging</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>info</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Login bem-sucedido: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">username</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)"> de </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">request</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">.</span><span class="token string-interpolation interpolation">remote_addr</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span>logging</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>warning</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">f&quot;Tentativa de acesso negado: </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">username</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)"> tentou acessar </span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">{</span><span class="token string-interpolation interpolation">resource</span><span class="token string-interpolation interpolation" style="color:rgb(199, 146, 234)">}</span><span class="token string-interpolation" style="color:rgb(173, 219, 103)">&quot;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

### 9️⃣ Email and Web Browser Protections

**Objetivo:** Melhorar defesas e minimizar ataques via e-mail e navegadores.

**Ações:**

#### 9.2 - Garantir que Apenas Aplicações Aprovadas Sejam Instaladas
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-x3gk98tix" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># AppLocker - Bloquear instalação não autorizada</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-AppLockerPolicy</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>RuleType Publisher `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>User Everyone `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>RuleNamePrefix </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Bloqueado&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:\Users\*\Downloads\*&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Action Deny
</span></code></pre></div>

---

#### 9.3 - Implementar DMARC
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">dns</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7zj7wjjyq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-dns" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span>; DNS TXT record
</span>_dmarc.exemplo.com. IN TXT &quot;v=DMARC1; p=reject; rua=mailto:dmarc@exemplo.com&quot;
<!-- -->
<!-- -->; SPF
<!-- -->exemplo.com. IN TXT &quot;v=spf1 ip4:203.0.113.0/24 -all&quot;
<!-- -->
<!-- -->; DKIM
<!-- -->default._domainkey.exemplo.com. IN TXT &quot;v=DKIM1; k=rsa; p=MIGfMA0GCS...&quot;
</code></pre></div>

---

#### 9.7 - Implementar DNS Filtering
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-kpzrov1te" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar DNS seguro (Cloudflare, Quad9)</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># /etc/resolv.conf</span><span>
</span><span>nameserver </span><span class="token" style="color:rgb(247, 140, 108)">1.1</span><span>.1.2  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Cloudflare for Families (bloqueia malware)</span><span>
</span><span>nameserver </span><span class="token" style="color:rgb(247, 140, 108)">9.9</span><span>.9.9  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Quad9 (bloqueia malware)</span><span>
</span></code></pre></div>

---

### 🔟 Malware Defenses

**Objetivo:** Controlar instalação, propagação e execução de código malicioso.

**Ações:**

#### 10.1 - Implementar Antimalware
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-zanqtmd8x" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># ClamAV (Linux)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> clamav clamav-daemon
</span><span>freshclam  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar definições</span><span>
</span><span>clamscan </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> /home  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan recursivo</span><span>
</span></code></pre></div>

---

#### 10.2 - Configurar Atualizações Automáticas de Antimalware
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-l2bbnansn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualização automática (cron)</span><span>
</span><span></span><span class="token" style="color:rgb(247, 140, 108)">0</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">2</span><span> * * * /usr/bin/freshclam </span><span class="token parameter" style="color:rgb(214, 222, 235)">--quiet</span><span>
</span></code></pre></div>

---

#### 10.5 - Habilitar Proteções de Sistema Operacional
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-7mplf7urm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux - SELinux</span><span>
</span><span>setenforce </span><span class="token" style="color:rgb(247, 140, 108)">1</span><span>
</span><span>getenforce  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux - AppArmor</span><span>
</span><span>systemctl </span><span class="token" style="color:rgb(255, 203, 139)">enable</span><span> apparmor
</span>systemctl start apparmor
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Windows - Exploit Protection</span><span>
</span><span>Set-ProcessMitigation </span><span class="token parameter" style="color:rgb(214, 222, 235)">-System</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-Enable</span><span> DEP,SEHOP,ASLR
</span></code></pre></div>

---

## 🟡 Foundational CIS Controls (11-16)

### 1️⃣1️⃣ Data Recovery

**Objetivo:** Estabelecer e manter processos de backup e recuperação.

**Ações:**

#### 11.1 - Estabelecer e Manter Processo de Backup
**Estratégia 3-2-1:**
```

3 cópias dos dados 2 tipos de mídia diferentes 1 cópia offsite

```
---

#### 11.3 - Proteger Backups
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-tz8wuxxzk" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criptografar backups</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tar</span><span> czf - /dados </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> gpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">-c</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> backup_</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">date</span><span class="token" style="color:rgb(214, 222, 235)"> +%Y%m%d</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span>.tar.gz.gpg
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Armazenar em local seguro (offsite)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">rsync</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-avz</span><span> backup_*.tar.gz.gpg usuario@backup-remoto:/backups/
</span></code></pre></div>

---

#### 11.4 - Testar Recuperação de Dados
```

Frequência: Mensal Procedimento:

1. Selecionar backup aleatório
2. Restaurar em ambiente de teste
3. Verificar integridade dos dados
4. Documentar tempo de recuperação (RTO)
5. Documentar ponto de recuperação (RPO)

```
---

### 1️⃣2️⃣ Network Infrastructure Management

**Objetivo:** Estabelecer, implementar e gerenciar infraestrutura de rede de forma segura.

**Ações:**

#### 12.1 - Garantir Segurança de Dispositivos de Rede
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1bqsddsap" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Cisco IOS - Hardening básico</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">enable</span><span> secret </span><span class="token" style="color:rgb(247, 140, 108)">5</span><span> </span><span class="token" style="color:rgb(214, 222, 235)">$1</span><span class="token" style="color:rgb(214, 222, 235)">$mERr</span><span class="token" style="color:rgb(214, 222, 235)">$hx5rVt7rPNoS4wqbXKX7m0</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">service</span><span> password-encryption
</span><span>no </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> http server
</span><span>no </span><span class="token" style="color:rgb(130, 170, 255)">ip</span><span> http secure-server
</span>banner login ^C
<!-- -->ACESSO AUTORIZADO APENAS
<!-- -->Todas as atividades são monitoradas
<!-- -->^C
</code></pre></div>

---

#### 12.4 - Estabelecer e Manter Arquitetura de Rede
**Segmentação:**
```

VLAN 10: Servidores (192.168.10.0/24) VLAN 20: Workstations (192.168.20.0/24) VLAN 30: Convidados (192.168.30.0/24) VLAN 40: IoT (192.168.40.0/24) VLAN 50: Gerência (192.168.50.0/24) DMZ: Servidores públicos (203.0.113.0/24)

```
---

#### 12.8 - Estabelecer e Manter Sistemas de Detecção de Intrusão
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-1hhfjp7ih" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Suricata</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> suricata
</span><span>suricata-update  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar regras</span><span>
</span>systemctl start suricata
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar alertas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">tail</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> /var/log/suricata/fast.log
</span></code></pre></div>

---

### 1️⃣3️⃣ Network Monitoring and Defense

**Objetivo:** Operar processos e ferramentas para estabelecer e manter defesas de rede abrangentes.

**Ações:**

#### 13.1 - Centralizar Coleta de Logs de Segurança
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-a68m01qsw" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Rsyslog - Enviar para SIEM</span><span>
</span>*.* @@siem.empresa.com:514
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Logstash (ELK Stack)</span><span>
</span><span>input </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>  syslog </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    port </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">514</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span>
<span>output </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>  elasticsearch </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    hosts </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">[</span><span class="token" style="color:rgb(173, 219, 103)">&quot;localhost:9200&quot;</span><span class="token" style="color:rgb(199, 146, 234)">]</span><span>
</span><span>    index </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;logs-%{+YYYY.MM.dd}&quot;</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

#### 13.3 - Implementar Monitoramento de Tráfego de Rede
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-yd7nm0let" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Zeek (Bro)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> zeek
</span><span>zeek </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> eth0 </span><span class="token" style="color:rgb(255, 203, 139)">local</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Analisar logs</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">cat</span><span> /opt/zeek/logs/current/conn.log
</span></code></pre></div>

---

### 1️⃣4️⃣ Security Awareness and Skills Training

**Objetivo:** Estabelecer e manter programa de treinamento de segurança.

**Ações:**

#### 14.1 - Estabelecer e Manter Programa de Conscientização
```

Treinamento anual obrigatório:

- Reconhecer phishing
- Proteção de credenciais
- Segurança física
- Uso seguro de dispositivos móveis
- Trabalho remoto

Simulações trimestrais:

- Phishing simulado
- Testes de engenharia social

```
---

#### 14.4 - Estabelecer e Manter Programa de Treinamento Específico por Função
```

Desenvolvedores:

- Secure coding (OWASP Top 10)
- Code review
- SAST/DAST

Administradores:

- Hardening de sistemas
- Patch management
- Incident response

Usuários finais:

- Phishing awareness
- Proteção de dados
- Políticas de segurança

```
---

### 1️⃣5️⃣ Service Provider Management

**Objetivo:** Desenvolver processo para avaliar provedores de serviço.

**Ações:**

#### 15.1 - Estabelecer e Manter Inventário de Provedores
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-3burq8xt9" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">Provedor</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> AWS
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Serviço</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Cloud hosting
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Criticidade</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Alta
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Dados processados</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Confidenciais
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Contrato</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Até 2026</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span>12</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span class="token" style="color:rgb(247, 140, 108)">31</span><span>
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Certificações</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> ISO 27001</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> SOC 2
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Última auditoria</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token datetime" style="color:rgb(247, 140, 108)">2025-06-15</span><span>
</span></code></pre></div>

---

#### 15.2 - Estabelecer e Manter Processo de Avaliação de Provedores
```

Critérios de avaliação: ✅ Certificações de segurança (ISO 27001, SOC 2) ✅ Políticas de segurança documentadas ✅ Incident response plan ✅ Backup e disaster recovery ✅ Cláusulas de segurança em contrato ✅ Right to audit

```
---

### 1️⃣6️⃣ Application Software Security

**Objetivo:** Gerenciar segurança do ciclo de vida de software desenvolvido internamente.

**Ações:**

#### 16.1 - Estabelecer e Manter Processo de Desenvolvimento Seguro
```

SDL (Security Development Lifecycle):

1. Treinamento em secure coding
2. Definir requisitos de segurança
3. Threat modeling
4. Secure coding
5. Code review
6. SAST (Static Analysis)
7. DAST (Dynamic Analysis)
8. Penetration testing
9. Incident response plan

```
---

#### 16.6 - Estabelecer e Manter Processo de Gestão de Vulnerabilidades de Software
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-0ze03w4nv" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan de dependências (Python)</span><span>
</span><span>pip </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> safety
</span>safety check
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan de dependências (Node.js)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">npm</span><span> audit
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Scan de código (SAST)</span><span>
</span><span>bandit </span><span class="token parameter" style="color:rgb(214, 222, 235)">-r</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">.</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> json </span><span class="token parameter" style="color:rgb(214, 222, 235)">-o</span><span> report.json  </span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Python</span><span>
</span></code></pre></div>

---

## 🔴 Organizational CIS Controls (17-18)

### 1️⃣7️⃣ Incident Response Management

**Objetivo:** Estabelecer processo para desenvolver e manter plano de resposta a incidentes.

**Ações:**

#### 17.1 - Designar Pessoal para Gerenciar Resposta a Incidentes
```

Equipe de IR:

- Incident Response Manager
- Analistas de segurança
- Administradores de sistemas
- Especialistas forenses
- Comunicação/PR
- Jurídico

```
---

#### 17.3 - Estabelecer e Manter Processo de Gerenciamento de Contato
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-g3a78d9qn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">Contatos de emergência</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">CISO</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> +55 11 99999</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span class="token" style="color:rgb(247, 140, 108)">0001</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Gerente de TI</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> +55 11 99999</span><span class="token" style="color:rgb(199, 146, 234)">-</span><span class="token" style="color:rgb(247, 140, 108)">0002</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Fornecedor de segurança</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> support@vendor.com
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">CERT.br</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> cert@cert.br
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Polícia Federal</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">194</span><span>
</span></code></pre></div>

---

#### 17.9 - Estabelecer e Manter Processo de Gestão de Incidentes de Segurança
```

Fases:

1. Preparação
2. Identificação
3. Contenção
4. Erradicação
5. Recuperação
6. Lições aprendidas

```
---

### 1️⃣8️⃣ Penetration Testing

**Objetivo:** Testar eficácia de defesas através de testes controlados.

**Ações:**

#### 18.1 - Estabelecer e Manter Programa de Penetration Testing
```

Frequência: Anual (mínimo) Escopo:

- Rede externa
- Rede interna
- Aplicações web
- Aplicações móveis
- Wireless
- Social engineering

Metodologia:

- PTES (Penetration Testing Execution Standard)
- OWASP Testing Guide

```
---

#### 18.3 - Remediar Vulnerabilidades de Penetration Testing
```

Priorização: CRÍTICO: 48 horas ALTO: 7 dias MÉDIO: 30 dias BAIXO: 90 dias

Re-teste: Após remediação, executar re-teste para confirmar correção

```
---

## 🎯 Implementation Groups (Grupos de Implementação)

### IG1 - Basic Cyber Hygiene
**Para:** Pequenas empresas, recursos limitados

**Controles:** 1-6 (56 safeguards)

**Foco:**
- Inventário de ativos
- Configurações seguras
- Controle de acesso
- Vulnerabilidades críticas

---

### IG2 - Intermediate Cyber Hygiene
**Para:** Empresas médias, mais recursos

**Controles:** 1-16 (74 safeguards adicionais)

**Adiciona:**
- Gestão de vulnerabilidades completa
- Monitoramento de rede
- Treinamento de segurança
- Gestão de provedores

---

### IG3 - Advanced Cyber Hygiene
**Para:** Grandes empresas, infraestrutura crítica

**Controles:** 1-18 (23 safeguards adicionais)

**Adiciona:**
- Incident response avançado
- Penetration testing
- Red team exercises

---

## 🔗 Mapeamento com Outros Frameworks

### CIS Controls → NIST CSF
```

CIS 1-2 (Asset Management) → NIST Identify CIS 3-10 (Proteção) → NIST Protect CIS 8, 13 (Monitoramento) → NIST Detect CIS 17 (Incident Response) → NIST Respond CIS 11 (Backup) → NIST Recover

```
### CIS Controls → MITRE ATT&CK
```

CIS 7 (Vulnerability Management) → Mitigação de Initial Access CIS 10 (Malware Defenses) → Mitigação de Execution CIS 12-13 (Network) → Mitigação de Lateral Movement

```
---

## 🔗 Links Relacionados

- [[NIST-Cybersecurity]]
- [[Defesa-em-Profundidade]]
- [[MITRE-ATT&CK]]
- [[OWASP-Top-10]]

---

## 📚 Referências

- CIS Controls v8: [cisecurity.org/controls/v8](https://www.cisecurity.org/controls/v8/)
- CIS Benchmarks: [cisecurity.org/cis-benchmarks](https://www.cisecurity.org/cis-benchmarks/)
- CIS-CAT (Assessment Tool): [cisecurity.org/cybersecurity-tools/cis-cat-pro](https://www.cisecurity.org/cybersecurity-tools/cis-cat-pro/)
