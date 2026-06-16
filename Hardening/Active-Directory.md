
# 🏢 Active Directory (AD)

> **Tags:** #active-directory #windows #ldap #kerberos #domain #authentication #authorization

---

## 📌 Visão Geral

**Active Directory (AD)** é o serviço de **diretório** da Microsoft usado para gerenciar usuários, computadores e recursos em redes Windows.

🎯 **Objetivo:** Centralizar autenticação, autorização e gerenciamento de recursos em ambientes corporativos.

**Componentes principais:**
- **Domain Controllers (DC):** Servidores que hospedam o AD
- **Domain:** Limite administrativo
- **Forest:** Coleção de domains
- **Organizational Units (OU):** Containers para organizar objetos
- **Group Policy Objects (GPO):** Políticas de configuração

---

## 🏗️ Estrutura do Active Directory

### Estrutura Lógica

Forest (floresta.local) │ ├─ Domain (empresa.floresta.local) │ │ │ ├─ OU: Usuarios │ │ ├─ User: joao.silva │ │ └─ User: maria.santos │ │ │ ├─ OU: Computadores │ │ ├─ Computer: WKS001 │ │ └─ Computer: WKS002 │ │ │ └─ OU: Grupos │ ├─ Group: TI │ └─ Group: RH │ └─ Domain (filial.floresta.local)


---

### Estrutura Física
```

Site: Matriz (São Paulo) │ ├─ Domain Controller: DC01 └─ Domain Controller: DC02 (backup)

Site: Filial (Rio de Janeiro) │ └─ Domain Controller: DC03

```
---

## 🔑 Componentes Principais

### 1️⃣ Domain Controller (DC)

**Funções:**
- Armazena banco de dados do AD (NTDS.dit)
- Autentica usuários
- Replica dados entre DCs
- Aplica Group Policies

**Instalar AD DS:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ai07ivqqs" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar função AD DS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Install-WindowsFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name AD-Domain-Services </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>IncludeManagementTools
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Promover servidor a Domain Controller</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Install-ADDSForest</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DomainName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;empresa.local&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DomainNetbiosName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;EMPRESA&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ForestMode </span><span class="token" style="color:rgb(173, 219, 103)">&quot;WinThreshold&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>DomainMode </span><span class="token" style="color:rgb(173, 219, 103)">&quot;WinThreshold&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>InstallDns:</span><span class="token" style="color:rgb(255, 88, 116)">$true</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>SafeModeAdministratorPassword </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">ConvertTo-SecureString</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Senha@123&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>AsPlainText </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Force</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span></code></pre></div>

---

### 2️⃣ Objetos do AD

#### Users (Usuários)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vklqaamty" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar usuário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-ADUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;João Silva&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>GivenName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;João&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Surname </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Silva&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>SamAccountName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>UserPrincipalName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva@empresa.local&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;OU=Usuarios,DC=empresa,DC=local&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>AccountPassword </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(130, 170, 255)">ConvertTo-SecureString</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Senha@123&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>AsPlainText </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Force</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Enabled </span><span class="token" style="color:rgb(255, 88, 116)">$true</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar usuários</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-ADUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span class="token" style="color:rgb(127, 219, 202)">Filter</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Properties </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Modificar usuário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ADUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Department </span><span class="token" style="color:rgb(173, 219, 103)">&quot;TI&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Title </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Analista&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar usuário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Disable-ADAccount</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Deletar usuário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Remove-ADUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Confirm:</span><span class="token" style="color:rgb(255, 88, 116)">$false</span><span>
</span></code></pre></div>

---

#### Groups (Grupos)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-hgcin2t3b" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-ADGroup</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Equipe_TI&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>GroupScope Global `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>GroupCategory Security `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;OU=Grupos,DC=empresa,DC=local&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar membro ao grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Add-ADGroupMember</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Equipe_TI&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Members </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar membros do grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-ADGroupMember</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Equipe_TI&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Remover membro do grupo</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Remove-ADGroupMember</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Equipe_TI&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Members </span><span class="token" style="color:rgb(173, 219, 103)">&quot;joao.silva&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Confirm:</span><span class="token" style="color:rgb(255, 88, 116)">$false</span><span>
</span></code></pre></div>

**Tipos de grupos:**
- **Security:** Controle de acesso
- **Distribution:** Listas de e-mail

**Escopos:**
- **Domain Local:** Acesso a recursos no domínio local
- **Global:** Membros do mesmo domínio
- **Universal:** Membros de qualquer domínio na floresta

---

#### Computers (Computadores)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wy0sxo8lb" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar computadores</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-ADComputer</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span class="token" style="color:rgb(127, 219, 202)">Filter</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Properties </span><span class="token" style="color:rgb(127, 219, 202)">*</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar objeto de computador</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-ADComputer</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;WKS001&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;OU=Computadores,DC=empresa,DC=local&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar computador</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Disable-ADAccount</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;WKS001$&quot;</span><span>
</span></code></pre></div>

---

#### Organizational Units (OUs)
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ymmlwnbj1" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar OU</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-ADOrganizationalUnit</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;TI&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;DC=empresa,DC=local&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar sub-OU</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-ADOrganizationalUnit</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Servidores&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;OU=TI,DC=empresa,DC=local&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Mover objeto para OU</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Move-ADObject</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;CN=joao.silva,CN=Users,DC=empresa,DC=local&quot;</span><span> `
</span><span>  </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>TargetPath </span><span class="token" style="color:rgb(173, 219, 103)">&quot;OU=TI,DC=empresa,DC=local&quot;</span><span>
</span></code></pre></div>

---

### 3️⃣ Group Policy Objects (GPO)

**Função:** Aplicar configurações centralizadas a usuários e computadores.

#### Criar GPO
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vtpr4fqpd" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Criar nova GPO</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-GPO</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Politica_Senha_Forte&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Vincular GPO a OU</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">New-GPLink</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Politica_Senha_Forte&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Target </span><span class="token" style="color:rgb(173, 219, 103)">&quot;OU=Usuarios,DC=empresa,DC=local&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar GPOs</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-GPO</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>All
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Backup de GPO</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Backup-GPO</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Politica_Senha_Forte&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:\GPO_Backup&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Restaurar GPO</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Restore-GPO</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Politica_Senha_Forte&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;C:\GPO_Backup&quot;</span><span>
</span></code></pre></div>

---

#### Exemplos de Políticas

##### Política de Senha
```

Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy

☑ Minimum password length: 14 characters ☑ Password must meet complexity requirements: Enabled ☑ Maximum password age: 90 days ☑ Enforce password history: 24 passwords

```
---

##### Política de Bloqueio de Conta
```

Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Account Lockout Policy

☑ Account lockout threshold: 5 invalid attempts ☑ Account lockout duration: 30 minutes ☑ Reset account lockout counter after: 30 minutes

```
---

##### Política de Firewall
```

Computer Configuration > Policies > Windows Settings > Security Settings > Windows Defender Firewall

☑ Domain Profile: Enabled ☑ Private Profile: Enabled ☑ Public Profile: Enabled

```
---

##### Política de Software (AppLocker)
```

Computer Configuration > Policies > Windows Settings > Security Settings > Application Control Policies > AppLocker

Criar regras:

- Permitir executáveis assinados pela Microsoft
- Bloquear executáveis em C:\Users*\Downloads*

```
---

## 🔐 Autenticação e Protocolos

### 1️⃣ Kerberos

**Protocolo padrão** de autenticação no AD.

#### Como Funciona
```

1. Cliente solicita TGT (Ticket Granting Ticket) ao KDC ├─ Envia hash da senha do usuário └─ KDC valida e retorna TGT (criptografado com krbtgt)
    
2. Cliente solicita TGS (Ticket Granting Service) para acessar recurso ├─ Envia TGT ao KDC └─ KDC retorna TGS (criptografado com chave do serviço)
    
3. Cliente apresenta TGS ao servidor do recurso └─ Servidor valida e concede acesso
    

```
**Portas:**
- **88/TCP e 88/UDP:** Kerberos

---

#### Comandos Kerberos

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vzcnctaxa" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar tickets Kerberos em cache</span><span>
</span>klist
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Purgar tickets</span><span>
</span>klist purge
<!-- -->
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Solicitar novo TGT</span><span>
</span><span>kinit usuario@EMPRESA</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>LOCAL
</span></code></pre></div>

---

### 2️⃣ LDAP (Lightweight Directory Access Protocol)

**Protocolo** para consultar e modificar o diretório AD.

**Portas:**
- **389/TCP:** LDAP
- **636/TCP:** LDAPS (LDAP sobre SSL/TLS)
- **3268/TCP:** Global Catalog
- **3269/TCP:** Global Catalog sobre SSL/TLS

#### Consultas LDAP

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-vvln24e27" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar usuário</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-ADUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>LDAPFilter </span><span class="token" style="color:rgb(173, 219, 103)">&quot;(sAMAccountName=joao.silva)&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar por departamento</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-ADUser</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>LDAPFilter </span><span class="token" style="color:rgb(173, 219, 103)">&quot;(department=TI)&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Buscar grupos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-ADGroup</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>LDAPFilter </span><span class="token" style="color:rgb(173, 219, 103)">&quot;(name=Equipe_TI)&quot;</span><span>
</span></code></pre></div>

---

### 3️⃣ NTLM (NT LAN Manager)

**Protocolo legado** de autenticação (menos seguro que Kerberos).

**Quando é usado:**
- Autenticação por IP (sem DNS)
- Workgroups (sem domínio)
- Fallback quando Kerberos falha

**Vulnerabilidades:**
- Pass-the-Hash
- NTLM Relay

---

## 🛡️ Segurança do Active Directory

### 1️⃣ Hardening do Domain Controller

#### Atualizações
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-sa0908i8z" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Verificar atualizações</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-WindowsUpdate</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar atualizações</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Install-WindowsUpdate</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>AcceptAll </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>AutoReboot
</span></code></pre></div>

---

#### Desabilitar Protocolos Inseguros

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-e2ka4by2y" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar SMBv1</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Disable-WindowsOptionalFeature</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Online </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FeatureName SMB1Protocol
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar LLMNR</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SOFTWARE\Policies\Microsoft\Windows NT\DNSClient&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name EnableMulticast </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 0
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Desabilitar NetBIOS</span><span>
</span><span></span><span class="token" style="color:rgb(214, 222, 235)">$adapters</span><span> = </span><span class="token" style="color:rgb(130, 170, 255)">Get-WmiObject</span><span> Win32_NetworkAdapterConfiguration </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">Where-Object</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(214, 222, 235)">$_</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>IPEnabled </span><span class="token" style="color:rgb(127, 219, 202)">-eq</span><span> </span><span class="token" style="color:rgb(255, 88, 116)">$true</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span><span></span><span class="token" style="color:rgb(127, 219, 202)">foreach</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">(</span><span class="token" style="color:rgb(214, 222, 235)">$adapter</span><span> in </span><span class="token" style="color:rgb(214, 222, 235)">$adapters</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>
</span><span>    </span><span class="token" style="color:rgb(214, 222, 235)">$adapter</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>SetTcpipNetbios</span><span class="token" style="color:rgb(199, 146, 234)">(</span><span>2</span><span class="token" style="color:rgb(199, 146, 234)">)</span><span>
</span><span></span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

#### Auditoria Avançada

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-og6z062st" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar auditoria de logon</span><span>
</span><span>auditpol </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(130, 170, 255)">set</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>subcategory:</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Logon&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>success:enable </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>failure:enable
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar auditoria de mudanças em contas</span><span>
</span><span>auditpol </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(130, 170, 255)">set</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>subcategory:</span><span class="token" style="color:rgb(173, 219, 103)">&quot;User Account Management&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>success:enable </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>failure:enable
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar auditoria de mudanças em grupos</span><span>
</span><span>auditpol </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span class="token" style="color:rgb(130, 170, 255)">set</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>subcategory:</span><span class="token" style="color:rgb(173, 219, 103)">&quot;Security Group Management&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>success:enable </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>failure:enable
</span></code></pre></div>

---

### 2️⃣ Proteção de Credenciais

#### Protected Users Group
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wmmcsx1zx" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Adicionar usuários ao grupo Protected Users</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Add-ADGroupMember</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Protected Users&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Members </span><span class="token" style="color:rgb(173, 219, 103)">&quot;admin_joao&quot;</span><span>
</span></code></pre></div>

**Proteções:**
- Não pode usar NTLM
- Não pode usar DES ou RC4 em Kerberos
- Credenciais não são armazenadas em cache
- Não pode delegar credenciais

---

#### Credential Guard
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-l8bhlb4o9" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Habilitar Credential Guard</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-ItemProperty</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Path </span><span class="token" style="color:rgb(173, 219, 103)">&quot;HKLM:\SYSTEM\CurrentControlSet\Control\Lsa&quot;</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Name LsaCfgFlags </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Value 1
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Reiniciar</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Restart-Computer</span><span>
</span></code></pre></div>

---

#### LAPS (Local Administrator Password Solution)
**Função:** Gerenciar senhas de administrador local de forma única e rotativa.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-9rexpwqdk" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Instalar LAPS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Install-WindowsFeature</span><span> RSAT-AD-PowerShell
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Estender schema do AD</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Import-Module</span><span> AdmPwd</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span class="token" style="color:rgb(130, 170, 255)">PS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Update-AdmPwdADSchema</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Configurar permissões</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Set-AdmPwdComputerSelfPermission</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>OrgUnit </span><span class="token" style="color:rgb(173, 219, 103)">&quot;OU=Computadores,DC=empresa,DC=local&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Consultar senha LAPS</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-AdmPwdPassword</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>ComputerName </span><span class="token" style="color:rgb(173, 219, 103)">&quot;WKS001&quot;</span><span>
</span></code></pre></div>

---

### 3️⃣ Tiering Model (Modelo de Camadas)

**Conceito:** Segregar contas administrativas por níveis de privilégio.
```

Tier 0 (Crítico):

- Domain Controllers
- Contas Domain Admin
- Acesso apenas via Privileged Access Workstations (PAW)

Tier 1 (Servidores):

- Servidores de aplicação
- Contas de administração de servidores
- Não podem acessar Tier 0

Tier 2 (Workstations):

- Estações de trabalho
- Contas de usuários comuns
- Não podem acessar Tier 0 ou 1

```
---

### 4️⃣ Monitoramento e Detecção

#### Eventos Críticos do AD

| Event ID | Descrição |
|----------|-----------|
| **4624** | Logon bem-sucedido |
| **4625** | Falha de logon |
| **4720** | Conta de usuário criada |
| **4722** | Conta de usuário habilitada |
| **4723** | Tentativa de mudança de senha |
| **4724** | Tentativa de reset de senha |
| **4728** | Membro adicionado a grupo de segurança global |
| **4732** | Membro adicionado a grupo de segurança local |
| **4756** | Membro adicionado a grupo de segurança universal |

---

#### Monitorar com PowerShell

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-5pm9r64zr" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Monitorar criação de usuários</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-WinEvent</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FilterHashtable @</span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>LogName=</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;Security&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> ID=4720</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>MaxEvents 10
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Monitorar falhas de logon</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-WinEvent</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FilterHashtable @</span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>LogName=</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;Security&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> ID=4625</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>MaxEvents 50
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Monitorar mudanças em grupos privilegiados</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-WinEvent</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>FilterHashtable @</span><span class="token" style="color:rgb(199, 146, 234)">{</span><span>LogName=</span><span class="token" style="color:rgb(173, 219, 103)">&#x27;Security&#x27;</span><span class="token" style="color:rgb(199, 146, 234)">;</span><span> ID=4728</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>4732</span><span class="token" style="color:rgb(199, 146, 234)">,</span><span>4756</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">|</span><span> 
</span><span>  </span><span class="token" style="color:rgb(130, 170, 255)">Where-Object</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">{</span><span class="token" style="color:rgb(214, 222, 235)">$_</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>Message </span><span class="token" style="color:rgb(127, 219, 202)">-match</span><span> </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Domain Admins|Enterprise Admins&quot;</span><span class="token" style="color:rgb(199, 146, 234)">}</span><span>
</span></code></pre></div>

---

## ⚔️ Ataques Comuns ao AD

### 1️⃣ Pass-the-Hash (PtH)

**Descrição:** Usar hash NTLM capturado para autenticar sem conhecer a senha.

**Ferramenta:** Mimikatz
```

mimikatz # sekurlsa::pth /user:Administrator /domain:empresa.local /ntlm:hash_aqui

```
**Mitigação:**
- Credential Guard
- Protected Users Group
- Limitar uso de contas locais para acesso remoto

---

### 2️⃣ Kerberoasting

**Descrição:** Solicitar TGS para contas de serviço e quebrar offline.

**Ferramenta:** Rubeus
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-i7vu5cesg" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\Rubeus</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>exe kerberoast </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>outfile:hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>txt
</span></code></pre></div>

**Mitigação:**
- Senhas fortes para contas de serviço (25+ caracteres)
- Usar Managed Service Accounts (MSA/gMSA)
- Monitorar Event ID 4769 (TGS solicitado)

---

### 3️⃣ AS-REP Roasting

**Descrição:** Atacar contas com "Do not require Kerberos preauthentication" habilitado.

**Ferramenta:** Rubeus
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-dp8yobey2" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\Rubeus</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>exe asreproast </span><span class="token" style="color:rgb(127, 219, 202)">/</span><span>outfile:hashes</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>txt
</span></code></pre></div>

**Mitigação:**
- Não habilitar "Do not require Kerberos preauthentication"
- Senhas fortes

---

### 4️⃣ Golden Ticket

**Descrição:** Forjar TGT usando hash da conta krbtgt.

**Ferramenta:** Mimikatz
```

mimikatz # kerberos::golden /user:Administrator /domain:empresa.local /sid:S-1-5-21-… /krbtgt:hash_aqui

```
**Mitigação:**
- Proteger Domain Controllers
- Rotacionar senha krbtgt regularmente (2x)
- Monitorar Event ID 4768 (TGT solicitado)

---

### 5️⃣ DCSync

**Descrição:** Simular Domain Controller para replicar credenciais.

**Ferramenta:** Mimikatz
```

mimikatz # lsadump::dcsync /domain:empresa.local /user:Administrator

```
**Mitigação:**
- Limitar permissões de replicação
- Monitorar Event ID 4662 (operação em objeto AD)

---

### 6️⃣ Zerologon (CVE-2020-1472)

**Descrição:** Explorar falha no Netlogon para zerar senha do DC.

**Mitigação:**
- Aplicar patch MS-NRPC (KB4571723)
- Habilitar modo de imposição

---

## 🔍 Ferramentas de Enumeração

### BloodHound

**Descrição:** Mapeamento visual de caminhos de ataque no AD.

**Instalação:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">bash</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-wyzsvdwkk" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-bash" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Neo4j (banco de dados)</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">sudo</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">apt</span><span> </span><span class="token" style="color:rgb(130, 170, 255)">install</span><span> neo4j
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># BloodHound</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">wget</span><span> https://github.com/BloodHoundAD/BloodHound/releases/latest/download/BloodHound-linux-x64.zip
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">unzip</span><span> BloodHound-linux-x64.zip
</span></code></pre></div>

**Coletar dados (SharpHound):**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-ojiwi402r" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\SharpHound</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>exe </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>c All
</span></code></pre></div>

**Analisar:**
```

1. Iniciar Neo4j
2. Abrir BloodHound
3. Importar ZIP gerado pelo SharpHound
4. Executar queries:
    - Find Shortest Paths to Domain Admins
    - Find Principals with DCSync Rights

```
---

### PowerView

**Descrição:** Ferramenta PowerShell para enumeração de AD.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-3tsxwn63c" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Importar PowerView</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Import-Module</span><span> </span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\PowerView</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>ps1
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar usuários</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-DomainUser</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar grupos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-DomainGroup</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Listar Domain Admins</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-DomainGroupMember</span><span> </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>Identity </span><span class="token" style="color:rgb(173, 219, 103)">&quot;Domain Admins&quot;</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Encontrar compartilhamentos</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Find-DomainShare</span><span>
</span>
<span></span><span class="token" style="color:rgb(99, 119, 119);font-style:italic"># Encontrar GPPs com senhas</span><span>
</span><span></span><span class="token" style="color:rgb(130, 170, 255)">Get-DomainGPPPassword</span><span>
</span></code></pre></div>

---

### ADRecon

**Descrição:** Ferramenta de auditoria de AD.

<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">powershell</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-k1wd2e3nl" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-powershell" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token" style="color:rgb(199, 146, 234)">.</span><span>\ADRecon</span><span class="token" style="color:rgb(199, 146, 234)">.</span><span>ps1 </span><span class="token" style="color:rgb(127, 219, 202)">-</span><span>OutputDir C:\ADRecon_Report
</span></code></pre></div>

**Gera relatório HTML com:**
- Usuários e grupos
- Computadores
- GPOs
- ACLs
- Trusts

---

## 🔗 Links Relacionados

- [[Windows-Hardening]]
- [[Kerberos]]
- [[LDAP]]
- [[Group-Policy]]
- [[Mimikatz]]

---

## 📚 Referências

- Microsoft AD Documentation: [docs.microsoft.com/active-directory](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/)
- BloodHound: [bloodhound.readthedocs.io](https://bloodhound.readthedocs.io/)
- PowerView: [github.com/PowerShellMafia/PowerSploit](https://github.com/PowerShellMafia/PowerSploit)
- LAPS: [microsoft.com/laps](https://www.microsoft.com/en-us/download/details.aspx?id=46899)