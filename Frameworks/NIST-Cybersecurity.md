
# 🏛️ NIST Cybersecurity Framework

> **Tags:** #nist #framework #cybersecurity #governanca #compliance #risk-management

---

## 📌 Visão Geral

O **NIST Cybersecurity Framework** (CSF) é um conjunto de diretrizes, melhores práticas e padrões desenvolvido pelo **National Institute of Standards and Technology (NIST)** dos Estados Unidos para ajudar organizações a gerenciar e reduzir riscos de segurança cibernética.

🎯 **Objetivo:** Fornecer uma abordagem flexível e baseada em riscos para melhorar a segurança cibernética.

**Site oficial:** [nist.gov/cyberframework](https://www.nist.gov/cyberframework)

---

## 🏗️ Estrutura do Framework

O NIST CSF é organizado em **5 Funções Principais** (Core Functions):

┌─────────────────────────────────────────────┐ 
│ 1. IDENTIFY (Identificar)                                           │ 
│ 2. PROTECT (Proteger)                                             │
│ 3. DETECT (Detectar)                                                │ 
│ 4. RESPOND (Responder)                                        │
│ 5. RECOVER (Recuperar)                                           │
└─────────────────────────────────────────────┘


---

## 1️⃣ IDENTIFY (Identificar)

### Descrição
Desenvolver compreensão organizacional para **gerenciar riscos** de segurança cibernética para sistemas, pessoas, ativos, dados e capacidades.

### Objetivos
- 🔍 Identificar ativos de alto valor
- 📊 Avaliar riscos
- 🏢 Entender contexto de negócio
- 👥 Identificar papéis e responsabilidades
- ⚖️ Compreender requisitos regulatórios

### Categorias

#### ID.AM - Asset Management (Gestão de Ativos)
**Atividades:**
- Inventário de hardware físico
- Inventário de software
- Mapeamento de fluxos de dados
- Classificação de ativos por criticidade

**Exemplo prático:**
```

Ativo: Servidor de banco de dados de clientes Classificação: CRÍTICO Valor: Alto (dados sensíveis) Localização: Data center principal Responsável: Equipe de TI

```
---

#### ID.BE - Business Environment (Ambiente de Negócio)
**Atividades:**
- Entender missão e objetivos da organização
- Identificar dependências críticas
- Mapear cadeia de suprimentos

---

#### ID.GV - Governance (Governança)
**Atividades:**
- Políticas de segurança
- Processos de gestão de risco
- Requisitos legais e regulatórios (LGPD, GDPR)

---

#### ID.RA - Risk Assessment (Avaliação de Riscos)
**Atividades:**
- Identificar ameaças e vulnerabilidades
- Avaliar probabilidade e impacto
- Priorizar riscos

**Metodologia:**
```

Risco = Ameaça × Vulnerabilidade × Impacto

Exemplo: Ameaça: Ransomware Vulnerabilidade: Patches desatualizados Impacto: Perda de dados críticos Risco: ALTO

```
---

#### ID.RM - Risk Management Strategy (Estratégia de Gestão de Riscos)
**Atividades:**
- Definir apetite de risco
- Estabelecer prioridades
- Determinar tolerância ao risco

---

#### ID.SC - Supply Chain Risk Management (Gestão de Riscos da Cadeia de Suprimentos)
**Atividades:**
- Avaliar fornecedores
- Contratos com cláusulas de segurança
- Monitoramento de terceiros

---

## 2️⃣ PROTECT (Proteger)

### Descrição
Desenvolver e implementar **salvaguardas apropriadas** para garantir a entrega de serviços críticos.

### Objetivos
- 🛡️ Proteger contra ameaças conhecidas
- 🔐 Implementar controles de segurança
- 🎓 Treinar funcionários
- 🔒 Proteger dados sensíveis

### Categorias

#### PR.AC - Identity Management and Access Control (Gestão de Identidade e Controle de Acesso)
**Controles:**
- **MFA (Multi-Factor Authentication)**
- **Least Privilege** (menor privilégio)
- **RBAC** (Role-Based Access Control)
- Revisão periódica de acessos
- Offboarding automático

**Exemplo de política:**
<div class="widget code-container remove-before-copy"><div class="code-header non-draggable"><span class="iaf s13 w700 code-language-placeholder">yaml</span><div class="code-copy-button"><span class="iaf s13 w500 code-copy-placeholder">Copiar</span><img class="code-copy-icon" src="data:image/svg+xml;utf8,%0A%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%3E%0A%20%20%3Cpath%20d%3D%22M10.8%208.63V11.57C10.8%2014.02%209.82%2015%207.37%2015H4.43C1.98%2015%201%2014.02%201%2011.57V8.63C1%206.18%201.98%205.2%204.43%205.2H7.37C9.82%205.2%2010.8%206.18%2010.8%208.63Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%20%20%3Cpath%20d%3D%22M15%204.42999V7.36999C15%209.81999%2014.02%2010.8%2011.57%2010.8H10.8V8.62999C10.8%206.17999%209.81995%205.19999%207.36995%205.19999H5.19995V4.42999C5.19995%201.97999%206.17995%200.999992%208.62995%200.999992H11.57C14.02%200.999992%2015%201.97999%2015%204.42999Z%22%20stroke%3D%22%23717C92%22%20stroke-width%3D%221.05%22%20stroke-linecap%3D%22round%22%20stroke-linejoin%3D%22round%22%2F%3E%0A%3C%2Fsvg%3E%0A" /></div></div><pre id="code-qy1569rl8" style="color:white;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;padding:8px;margin:8px;overflow:auto;background:#011627;width:calc(100% - 8px);border-radius:8px;box-shadow:0px 8px 18px 0px rgba(120, 120, 143, 0.10), 2px 2px 10px 0px rgba(255, 255, 255, 0.30) inset"><code class="language-yaml" style="white-space:pre;color:#d6deeb;font-family:Consolas, Monaco, &quot;Andale Mono&quot;, &quot;Ubuntu Mono&quot;, monospace;text-align:left;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;font-size:1em;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none"><span class="token key" style="color:rgb(255, 203, 139)">Usuário</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> joao.silva
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Função</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Analista de Suporte
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Permissões</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span>
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Ler tickets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> SIM
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Criar tickets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> SIM
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Deletar tickets</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> NÃO
</span><span>  </span><span class="token" style="color:rgb(199, 146, 234)">-</span><span> </span><span class="token key" style="color:rgb(255, 203, 139)">Acessar configurações</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> NÃO
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">MFA</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Obrigatório
</span><span></span><span class="token key" style="color:rgb(255, 203, 139)">Revisão de acesso</span><span class="token" style="color:rgb(199, 146, 234)">:</span><span> Trimestral
</span></code></pre></div>

---

#### PR.AT - Awareness and Training (Conscientização e Treinamento)
**Atividades:**
- Treinamento de segurança anual
- Simulações de phishing
- Campanhas de conscientização
- Treinamento específico por função

**Tópicos de treinamento:**
- Reconhecer phishing
- Proteção de credenciais
- Segurança de dispositivos móveis
- Trabalho remoto seguro
- Engenharia social

---

#### PR.DS - Data Security (Segurança de Dados)
**Controles:**
- **Criptografia em repouso** (BitLocker, LUKS)
- **Criptografia em trânsito** (TLS/SSL, VPN)
- **DLP** (Data Loss Prevention)
- **Classificação de dados**
- **Backup regular**

**Classificação de dados:**
```

PÚBLICO: Sem restrição INTERNO: Apenas funcionários CONFIDENCIAL: Acesso restrito + MFA SECRETO: Máxima proteção + auditoria

```
---

#### PR.IP - Information Protection Processes and Procedures (Processos de Proteção da Informação)
**Atividades:**
- Políticas de segurança documentadas
- Procedimentos de resposta a incidentes
- Gestão de configuração
- Gestão de vulnerabilidades

---

#### PR.MA - Maintenance (Manutenção)
**Atividades:**
- Patch management
- Manutenção preventiva
- Logs de manutenção
- Ferramentas autorizadas

---

#### PR.PT - Protective Technology (Tecnologia de Proteção)
**Controles:**
- **Firewall**
- **IDS/IPS**
- **Antivírus/EDR**
- **WAF** (Web Application Firewall)
- **Segmentação de rede**

---

## 3️⃣ DETECT (Detectar)

### Descrição
Desenvolver e implementar atividades apropriadas para **identificar a ocorrência** de um evento de segurança cibernética.

### Objetivos
- 👁️ Detectar ataques em tempo real
- 🔍 Monitorar anomalias
- 🚨 Gerar alertas
- 📊 Analisar eventos de segurança

### Categorias

#### DE.AE - Anomalies and Events (Anomalias e Eventos)
**Atividades:**
- Estabelecer baseline de rede
- Detectar desvios do comportamento normal
- Correlacionar eventos

**Ferramentas:**
- **SIEM** (Splunk, ELK, Wazuh)
- **Network behavior analysis**
- **User behavior analytics (UBA)**

---

#### DE.CM - Security Continuous Monitoring (Monitoramento Contínuo de Segurança)
**Atividades:**
- Monitoramento de rede 24/7
- Análise de logs
- Monitoramento de vulnerabilidades
- Monitoramento de ativos

**Logs críticos:**
```

- Autenticações (sucesso e falha)
- Mudanças de configuração
- Acesso a dados sensíveis
- Tráfego de rede anômalo
- Alertas de segurança

```
---

#### DE.DP - Detection Processes (Processos de Detecção)
**Atividades:**
- Definir papéis e responsabilidades
- Testar processos de detecção
- Comunicar detecções

---

## 4️⃣ RESPOND (Responder)

### Descrição
Desenvolver e implementar atividades apropriadas para **tomar ação** em relação a um incidente de segurança cibernética detectado.

### Objetivos
- 🚨 Responder rapidamente a incidentes
- 🛑 Conter ameaças
- 📋 Documentar incidentes
- 🔄 Melhorar processos

### Categorias

#### RS.RP - Response Planning (Planejamento de Resposta)
**Atividades:**
- Criar **Incident Response Plan**
- Definir equipe de resposta
- Estabelecer procedimentos
- Treinar equipe

**Estrutura de IR Plan:**
```

1. Preparação
2. Identificação
3. Contenção
4. Erradicação
5. Recuperação
6. Lições aprendidas

```
---

#### RS.CO - Communications (Comunicações)
**Atividades:**
- Comunicar incidente internamente
- Notificar stakeholders
- Comunicar com autoridades (quando necessário)
- Comunicar com mídia (se aplicável)

**Exemplo de comunicação:**
```

INCIDENTE: Ransomware detectado SEVERIDADE: CRÍTICA SISTEMAS AFETADOS: Servidor de arquivos AÇÕES TOMADAS: Isolamento do servidor STATUS: Em contenção PRÓXIMOS PASSOS: Restauração de backup

```
---

#### RS.AN - Analysis (Análise)
**Atividades:**
- Investigar causa raiz
- Analisar impacto
- Coletar evidências forenses
- Documentar timeline

---

#### RS.MI - Mitigation (Mitigação)
**Atividades:**
- Conter incidente
- Isolar sistemas afetados
- Aplicar patches emergenciais
- Bloquear IOCs

---

#### RS.IM - Improvements (Melhorias)
**Atividades:**
- Lições aprendidas
- Atualizar procedimentos
- Implementar melhorias
- Treinar equipe

---

## 5️⃣ RECOVER (Recuperar)

### Descrição
Desenvolver e implementar atividades apropriadas para manter planos de **resiliência** e **restaurar** capacidades ou serviços que foram prejudicados.

### Objetivos
- 🔄 Restaurar operações normais
- 💾 Recuperar dados
- 📈 Melhorar resiliência
- 📋 Comunicar recuperação

### Categorias

#### RC.RP - Recovery Planning (Planejamento de Recuperação)
**Atividades:**
- **Disaster Recovery Plan (DRP)**
- **Business Continuity Plan (BCP)**
- Testes de recuperação
- Backups regulares

**Estratégia 3-2-1:**
```

3 cópias dos dados 2 tipos de mídia diferentes 1 cópia offsite

```
---

#### RC.IM - Improvements (Melhorias)
**Atividades:**
- Incorporar lições aprendidas
- Atualizar planos
- Melhorar processos

---

#### RC.CO - Communications (Comunicações)
**Atividades:**
- Comunicar status de recuperação
- Atualizar stakeholders
- Documentar recuperação

---

## 📊 Implementation Tiers (Níveis de Implementação)

O NIST CSF define **4 níveis** de maturidade:

### Tier 1: Partial (Parcial)
- Processos ad-hoc
- Gestão de risco reativa
- Conscientização limitada

### Tier 2: Risk Informed (Informado por Risco)
- Processos aprovados mas não consistentes
- Gestão de risco em nível organizacional
- Conscientização crescente

### Tier 3: Repeatable (Repetível)
- Processos formalizados e documentados
- Gestão de risco integrada
- Treinamento regular

### Tier 4: Adaptive (Adaptativo)
- Processos continuamente melhorados
- Gestão de risco proativa
- Cultura de segurança forte

---

## 🎯 Profiles (Perfis)

**Current Profile:** Estado atual de segurança
**Target Profile:** Estado desejado de segurança
**Gap Analysis:** Diferença entre atual e desejado

**Exemplo:**
```

Função: PROTECT Categoria: PR.AC (Access Control)

Current Profile:

- MFA: 50% dos usuários
- Least Privilege: Parcialmente implementado
- Revisão de acesso: Anual

Target Profile:

- MFA: 100% dos usuários
- Least Privilege: Totalmente implementado
- Revisão de acesso: Trimestral

Gap:

- Implementar MFA para 50% restante
- Revisar e ajustar permissões
- Automatizar revisões trimestrais

```
---

## 🔗 Relação com Outros Frameworks

### ISO 27001
**NIST CSF** é mais flexível e focado em riscos
**ISO 27001** é mais prescritivo e focado em conformidade

### CIS Controls
**CIS Controls** fornece ações técnicas específicas
**NIST CSF** fornece estrutura de alto nível

### MITRE ATT&CK
**MITRE ATT&CK** detalha táticas e técnicas de atacantes
**NIST CSF** fornece funções de defesa

---

## 📚 Recursos e Documentos

### Documentos Oficiais
- **Framework Core:** [NIST CSF v1.1](https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.04162018.pdf)
- **Quick Start Guide:** [NIST CSF Quick Start](https://www.nist.gov/cyberframework/getting-started)

### Ferramentas
- **NIST CSF Assessment Tool**
- **Crosswalk entre frameworks**

---

## 🎯 Implementação Prática

### Passo 1: Priorizar e Escopo
- Definir escopo (toda organização ou área específica)
- Identificar ativos críticos
- Definir objetivos de negócio

### Passo 2: Orientar
- Identificar sistemas e ativos relacionados
- Identificar requisitos regulatórios
- Avaliar ameaças e vulnerabilidades

### Passo 3: Criar Current Profile
- Avaliar práticas atuais
- Mapear para categorias do framework
- Identificar gaps

### Passo 4: Conduzir Risk Assessment
- Analisar ambiente operacional
- Identificar ameaças
- Avaliar probabilidade e impacto

### Passo 5: Criar Target Profile
- Definir estado desejado
- Priorizar melhorias
- Considerar custo-benefício

### Passo 6: Determinar, Analisar e Priorizar Gaps
- Comparar Current vs Target
- Criar plano de ação
- Priorizar por risco e impacto

### Passo 7: Implementar Action Plan
- Executar melhorias
- Monitorar progresso
- Ajustar conforme necessário

---

## 🔗 Links Relacionados

- [[CIA-Triad]]
- [[Defesa-em-Profundidade]]
- [[Risco-e-Vulnerabilidades]]
- [[ISO-27001]]
- [[CIS-Controls]]

---

## 📚 Referências

- NIST Cybersecurity Framework: [nist.gov/cyberframework](https://www.nist.gov/cyberframework)
- NIST SP 800-53 (Security Controls)
- NIST SP 800-30 (Risk Assessment)