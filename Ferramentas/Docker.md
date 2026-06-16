
# 🐳 Docker

> **Tags:** #docker #containers #containerization #devops #isolation #microservices

---

## 📌 Visão Geral

**Docker** é uma plataforma de **containerização** que permite empacotar aplicações e suas dependências em **containers** isolados e portáteis.

🎯 **Objetivo:** Simplificar deploy, garantir consistência entre ambientes e isolar aplicações.

**Site oficial:** [docker.com](https://www.docker.com/)

---

## 🆚 Containers vs Máquinas Virtuais

| Característica | Containers | VMs |
|----------------|------------|-----|
| **Tamanho** | MB | GB |
| **Inicialização** | Segundos | Minutos |
| **Performance** | Nativa | Overhead |
| **Isolamento** | Processo | Hardware virtualizado |
| **Portabilidade** | Alta | Média |
| **Densidade** | Centenas por host | Dezenas por host |

**Diagrama:**

Containers: VMs: ┌──────────────────────┐ ┌──────────────────────┐ │ App A │ App B │ App C│ │ App A │ App B │ App C│ ├──────────────────────┤ ├──────────────────────┤ │ Docker Engine │ │ OS │ OS │ OS │ ├──────────────────────┤ ├──────────────────────┤ │ Host OS │ │ Hypervisor │ ├──────────────────────┤ ├──────────────────────┤ │ Hardware │ │ Hardware │ └──────────────────────┘ └──────────────────────┘


---

## 📥 Instalação

### Linux (Ubuntu/Debian)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-hpbi6blwm" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar repositórios</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> update
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar dependências</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> apt-transport-https ca-certificates </span><span class="token" style="color:rgb(130, 170, 255)">curl</span><span> software-properties-common
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar chave GPG do Docker</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">curl</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-fsSL</span><span> https://download.docker.com/linux/ubuntu/gpg </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> gpg </span><span class="token parameter" style="color:rgb(214, 222, 235)">--dearmor</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-o</span><span> /usr/share/keyrings/docker-archive-keyring.gpg
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar repositório</span><span>
</span><span></span><span class="token" style="color:rgb(255, 203, 139)">echo</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;deb [arch=</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(214, 222, 235)">dpkg --print-architecture</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span class="token" style="color:rgb(173, 219, 103)"> signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu </span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(214, 222, 235)">lsb_release </span><span class="token parameter" style="color:rgb(214, 222, 235)">-cs</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span class="token" style="color:rgb(173, 219, 103)"> stable&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">tee</span><span> /etc/apt/sources.list.d/docker.list </span><span class="token" style="color:rgb(127, 219, 202)">&gt;</span><span> /dev/null
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar Docker</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> update
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> docker-ce docker-ce-cli containerd.io
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar instalação</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--version</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar usuário ao grupo docker (evitar sudo)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">usermod</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-aG</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token environment" style="color:rgb(130, 170, 255)">$USER</span><span>
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Logout e login novamente</span><span>
</span></code></pre></div>

---

### Windows/macOS

**Download:** [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop/)

**Instalação:**
1. Baixar Docker Desktop
2. Instalar executável
3. Reiniciar sistema
4. Verificar: `docker --version`

---

## 🚀 Comandos Básicos

### Imagens

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-b6b0q2r3c" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar imagem no Docker Hub</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> search nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Baixar imagem</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar imagens locais</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> images
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover imagem</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> rmi nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover imagens não utilizadas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> image prune
</span></code></pre></div>

---

### Containers

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-yzg7j5tmb" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container (modo interativo)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> ubuntu /bin/bash
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container (modo daemon/background)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar com nome customizado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> meu-nginx nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar com mapeamento de porta</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">8080</span><span>:80 nginx
</span><span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Host:8080 → Container:80</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar containers em execução</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ps</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar todos os containers (incluindo parados)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">ps</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-a</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> stop meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar container parado</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> start meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> restart meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover container forçadamente</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover todos os containers parados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> container prune
</span></code></pre></div>

---

### Logs e Inspeção

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-cvwdvo0rn" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs do container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> logs meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs em tempo real (follow)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> logs </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inspecionar container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> inspect meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver processos do container</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">top</span><span> meu-nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver estatísticas de uso (CPU, RAM)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> stats
</span></code></pre></div>

---

### Executar Comandos em Container

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-rkks5qcvf" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar comando em container em execução</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">exec</span><span> meu-nginx </span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span> /etc
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Abrir shell interativo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">exec</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> meu-nginx /bin/bash
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar como root</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> </span><span class="token" style="color:rgb(255, 203, 139)">exec</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> root </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> meu-nginx /bin/bash
</span></code></pre></div>

---

## 🐳 Dockerfile

**Arquivo para criar imagens customizadas.**

### Exemplo Básico

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">dockerfile</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-yory95ay0" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-dockerfile" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Usar imagem base</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">FROM</span><span class="token instruction"> ubuntu:22.04</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Metadados</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">LABEL</span><span class="token instruction"> maintainer=</span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;seu@email.com&quot;</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">LABEL</span><span class="token instruction"> description=</span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;Minha aplicação&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Atualizar e instalar pacotes</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">RUN</span><span class="token instruction"> apt update &amp;&amp; apt install -y </span><span class="token instruction" style="color:rgb(127, 219, 202)">\</span><span class="token instruction">
</span><span class="token instruction">    nginx </span><span class="token instruction" style="color:rgb(127, 219, 202)">\</span><span class="token instruction">
</span><span class="token instruction">    curl </span><span class="token instruction" style="color:rgb(127, 219, 202)">\</span><span class="token instruction">
</span><span class="token instruction">    &amp;&amp; rm -rf /var/lib/apt/lists/*</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Copiar arquivos do host para container</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">COPY</span><span class="token instruction"> index.html /var/www/html/</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Definir diretório de trabalho</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">WORKDIR</span><span class="token instruction"> /var/www/html</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Expor porta</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">EXPOSE</span><span class="token instruction"> 80</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Comando padrão ao iniciar container</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">CMD</span><span class="token instruction"> [</span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;nginx&quot;</span><span class="token instruction">, </span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;-g&quot;</span><span class="token instruction">, </span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;daemon off;&quot;</span><span class="token instruction">]</span><span>
</span></code></pre></div>

---

### Construir Imagem

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-w0kwiu363" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Construir imagem</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> build </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> minha-imagem:1.0 </span><span class="token" style="color:rgb(255, 203, 139)">.</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Construir com nome e tag</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> build </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> usuario/minha-imagem:latest </span><span class="token" style="color:rgb(255, 203, 139)">.</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar imagens</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> images
</span></code></pre></div>

---

### Exemplo: Aplicação Python

**Dockerfile:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">dockerfile</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-pelt14sy9" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-dockerfile" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token instruction" style="color:rgb(127, 219, 202)">FROM</span><span class="token instruction"> python:3.11-slim</span><span>
</span>
<span></span><span class="token instruction" style="color:rgb(127, 219, 202)">WORKDIR</span><span class="token instruction"> /app</span><span>
</span>
<span></span><span class="token instruction" style="color:rgb(127, 219, 202)">COPY</span><span class="token instruction"> requirements.txt .</span><span>
</span><span></span><span class="token instruction" style="color:rgb(127, 219, 202)">RUN</span><span class="token instruction"> pip install --no-cache-dir -r requirements.txt</span><span>
</span>
<span></span><span class="token instruction" style="color:rgb(127, 219, 202)">COPY</span><span class="token instruction"> . .</span><span>
</span>
<span></span><span class="token instruction" style="color:rgb(127, 219, 202)">EXPOSE</span><span class="token instruction"> 5000</span><span>
</span>
<span></span><span class="token instruction" style="color:rgb(127, 219, 202)">CMD</span><span class="token instruction"> [</span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;python&quot;</span><span class="token instruction">, </span><span class="token instruction" style="color:rgb(173, 219, 103)">&quot;app.py&quot;</span><span class="token instruction">]</span><span>
</span></code></pre></div>

**requirements.txt:**
```

flask==3.0.0

```

**app.py:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">python</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-e6frd0zv3" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-python" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(127, 219, 202)">from</span><span> flask </span><span class="token" style="color:rgb(127, 219, 202)">import</span><span> Flask
</span>
<span>app </span><span class="token" style="color:rgb(127, 219, 202)">=</span><span> Flask</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>__name__</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span>
<span></span><span class="token decorator annotation" style="color:rgb(199, 146, 234)">@app</span><span class="token decorator annotation" style="color:rgb(199, 146, 234)">.</span><span class="token decorator annotation" style="color:rgb(199, 146, 234)">route</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;/&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">def</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">hello</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token" style="color:rgb(127, 219, 202)">return</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Hello from Docker!&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(127, 219, 202)">if</span><span> __name__ </span><span class="token" style="color:rgb(127, 219, 202)">==</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;__main__&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    app</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>run</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>host</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;0.0.0.0&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span> port</span><span class="token" style="color:rgb(127, 219, 202)">=</span><span class="token" style="color:rgb(247, 140, 108)">5000</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

**Construir e executar:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vg2l6zikv" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> build </span><span class="token parameter" style="color:rgb(214, 222, 235)">-t</span><span> minha-app-python </span><span class="token" style="color:rgb(255, 203, 139)">.</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">5000</span><span>:5000 </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> app minha-app-python
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Testar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">curl</span><span> http://localhost:5000
</span></code></pre></div>

---

## 🗂️ Volumes (Persistência de Dados)

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-gg48h6t42" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume create meu-volume
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar volumes</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume </span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container com volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> meu-volume:/data </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> container-com-volume ubuntu
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Volume bind (mapear diretório do host)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span> /home/user/dados:/data </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> container-bind ubuntu
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inspecionar volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume inspect meu-volume
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover volume</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> meu-volume
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover volumes não utilizados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> volume prune
</span></code></pre></div>

---

## 🌐 Redes Docker

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-v5u4mrky9" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar redes</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network </span><span class="token" style="color:rgb(130, 170, 255)">ls</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar rede</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network create minha-rede
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Executar container em rede específica</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--network</span><span> minha-rede </span><span class="token parameter" style="color:rgb(214, 222, 235)">--name</span><span> web nginx
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Conectar container a rede</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network connect minha-rede meu-container
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desconectar container de rede</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network disconnect minha-rede meu-container
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Inspecionar rede</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network inspect minha-rede
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover rede</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> network </span><span class="token" style="color:rgb(130, 170, 255)">rm</span><span> minha-rede
</span></code></pre></div>

---

## 🐙 Docker Compose

**Gerenciar múltiplos containers com um único arquivo YAML.**

### Instalação

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-r2kf9wc9k" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Linux</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">curl</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-L</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;https://github.com/docker/compose/releases/latest/download/docker-compose-</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">uname</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-s</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span class="token" style="color:rgb(173, 219, 103)">-</span><span class="token" style="color:rgb(214, 222, 235)">$(</span><span class="token" style="color:rgb(130, 170, 255)">uname</span><span class="token" style="color:rgb(214, 222, 235)"> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-m</span><span class="token" style="color:rgb(214, 222, 235)">)</span><span class="token" style="color:rgb(173, 219, 103)">&quot;</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-o</span><span> /usr/local/bin/docker-compose
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">chmod</span><span> +x /usr/local/bin/docker-compose
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">--version</span><span>
</span></code></pre></div>

---

### Exemplo: WordPress + MySQL

**docker-compose.yml:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-g2byg8xlq" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">version</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&#x27;3.8&#x27;</span><span>
</span>
<span></span><span class="token key" style="color:rgb(255, 203, 139)">services</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">db</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">image</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> mysql</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span class="token" style="color:rgb(247, 140, 108)">8.0</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">environment</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_ROOT_PASSWORD</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> senha_root
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_DATABASE</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wordpress
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_USER</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_user
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">MYSQL_PASSWORD</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_senha
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">volumes</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> db_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>/var/lib/mysql
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">networks</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> wp_network
</span>
<span>  </span><span class="token key" style="color:rgb(255, 203, 139)">wordpress</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">image</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wordpress</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>latest
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">depends_on</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> db
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">ports</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;8080:80&quot;</span><span>
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">environment</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_HOST</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> db</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span class="token" style="color:rgb(247, 140, 108)">3306</span><span>
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_USER</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_user
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_PASSWORD</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wp_senha
</span><span>      </span><span class="token key" style="color:rgb(255, 203, 139)">WORDPRESS_DB_NAME</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> wordpress
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">volumes</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> wp_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>/var/www/html
</span><span>    </span><span class="token key" style="color:rgb(255, 203, 139)">networks</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>      </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> wp_network
</span>
<span></span><span class="token key" style="color:rgb(255, 203, 139)">volumes</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">db_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">wp_data</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span>
<span></span><span class="token key" style="color:rgb(255, 203, 139)">networks</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token key" style="color:rgb(255, 203, 139)">wp_network</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span></code></pre></div>

**Comandos:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-j63l6mw4h" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Iniciar serviços</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> up </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Ver logs</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> logs </span><span class="token parameter" style="color:rgb(214, 222, 235)">-f</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar serviços</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> stop
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar e remover containers</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> down
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Parar e remover containers + volumes</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker-compose</span><span> down </span><span class="token parameter" style="color:rgb(214, 222, 235)">-v</span><span>
</span></code></pre></div>

---

## 🔒 Docker em Segurança da Informação

### 1️⃣ Labs de Vulnerabilidades

**DVWA (Damn Vulnerable Web Application):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-90sr42gek" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span>:80 vulnerables/web-dvwa
</span></code></pre></div>

**Metasploitable 3:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-r80tc1qao" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull tleemcjr/metasploitable2
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">21</span><span>:21 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">22</span><span>:22 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">80</span><span>:80 tleemcjr/metasploitable2
</span></code></pre></div>

---

### 2️⃣ Ferramentas de Pentest

**Kali Linux:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-i6tvzg3pc" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull kalilinux/kali-rolling
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> kalilinux/kali-rolling /bin/bash
</span></code></pre></div>

**OWASP ZAP:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ymvd4o3ac" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-u</span><span> zap </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">8080</span><span>:8080 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-i</span><span> owasp/zap2docker-stable zap-webswing.sh
</span></code></pre></div>

---

### 3️⃣ Análise de Malware (Sandbox)

**REMnux:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-tbt015eoy" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull remnux/remnux-distro
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-it</span><span> remnux/remnux-distro /bin/bash
</span></code></pre></div>

---

### 4️⃣ SIEM

**Wazuh:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-lvk4quaem" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> pull wazuh/wazuh
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">docker</span><span> run </span><span class="token parameter" style="color:rgb(214, 222, 235)">-d</span><span> </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1514</span><span>:1514 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">1515</span><span>:1515 </span><span class="token parameter" style="color:rgb(214, 222, 235)">-p</span><span> </span><span class="token" style="color:rgb(247, 140, 108)">55000</span><span>:55000 wazuh/wazuh
</span></code></pre></div>

---

## 🔗 Links Relacionados

- [[Virtualizacao]]
- [[Labs-CTF]]
- [[Kali-Linux]]
- [[DevOps]]

---

## 📚 Referências

- Docker Docs: [docs.docker.com](https://docs.docker.com/)
- Docker Hub: [hub.docker.com](https://hub.docker.com/)
- Docker Compose: [docs.docker.com/compose](https://docs.docker.com/compose/)