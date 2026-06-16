
# ⚠️ Risco e Vulnerabilidades

> **Tags:** #risco #vulnerabilidades #gestao-risco #analise-risco #threat #vulnerability #impact

---

## 📌 Conceitos Fundamentais

### 🎯 Ativo (Asset)
**Definição:** Qualquer coisa de **valor** para a organização.

**Exemplos:**
- 💾 **Dados:** Informações de clientes, propriedade intelectual
- 💻 **Hardware:** Servidores, laptops, switches
- 📱 **Software:** Aplicações, sistemas operacionais
- 👥 **Pessoas:** Funcionários, conhecimento
- 🏢 **Instalações:** Data centers, escritórios
- 🔑 **Reputação:** Marca, confiança do cliente

---

### 🐛 Vulnerabilidade (Vulnerability)
**Definição:** **Fraqueza** ou **falha** em um sistema que pode ser explorada.

**Tipos:**

#### 🔧 Técnicas
- Software desatualizado
- Configuração incorreta
- Falhas de código (buffer overflow, SQL injection)
- Senhas fracas
- Falta de criptografia

#### 👥 Humanas
- Falta de treinamento
- Engenharia social
- Negligência
- Insider threat

#### 🏢 Físicas
- Falta de controle de acesso
- Ausência de CCTV
- Equipamentos não protegidos

#### 🔄 Processuais
- Falta de políticas
- Procedimentos inadequados
- Ausência de auditoria

**Exemplos:**

- CVE-2021-44228 (Log4Shell): RCE no Apache Log4j CVE-2017-0144 (EternalBlue): RCE no SMBv1 do Windows Senha padrão: admin/admin Porto 22 (SSH) exposto na internet


---

### 🎭 Ameaça (Threat)
**Definição:** **Potencial** causa de incidente indesejado que pode causar dano.

**Tipos:**

#### 🌐 Cibernéticas
- Malware
- Ransomware
- Phishing
- DDoS
- APTs

#### 🌍 Naturais
- Terremotos
- Enchentes
- Incêndios
- Tempestades

#### 👥 Humanas
- Erro humano
- Sabotagem
- Espionagem
- Insider threat

#### 🔧 Técnicas
- Falha de hardware
- Falha de software
- Queda de energia
- Falha de rede

---

### 💥 Risco (Risk)
**Definição:** **Probabilidade** de uma ameaça explorar uma vulnerabilidade e causar **impacto**.

**Fórmula:**
```

Risco = Ameaça × Vulnerabilidade × Impacto

```
**Ou simplificado:**
```

Risco = Probabilidade × Impacto

```
**Exemplo:**
```

Ameaça: Ransomware Vulnerabilidade: Servidor Windows desatualizado (EternalBlue) Impacto: Perda de dados críticos, parada de operação

Risco = ALTO

```
---

### 💔 Impacto (Impact)
**Definição:** **Consequência** negativa se o risco se materializar.

**Dimensões:**

#### 💰 Financeiro
- Perda de receita
- Multas regulatórias
- Custos de recuperação
- Processos judiciais

#### 🏢 Operacional
- Parada de serviços
- Perda de produtividade
- Interrupção de processos

#### 🎭 Reputacional
- Perda de confiança
- Dano à marca
- Perda de clientes

#### ⚖️ Legal/Regulatório
- Multas (LGPD, GDPR)
- Processos
- Perda de licenças

---

## 📊 Gestão de Riscos

### Processo de Gestão de Riscos
```

┌──────────────────┐ │ 1. Identificação │ ├──────────────────┤ │ 2. Análise │ ├──────────────────┤ │ 3. Avaliação │ ├──────────────────┤ │ 4. Tratamento │ ├──────────────────┤ │ 5. Monitoramento │ └──────────────────┘

```
---

### 1️⃣ Identificação de Riscos

**Métodos:**
- Brainstorming
- Entrevistas
- Análise de documentos
- Histórico de incidentes
- Threat modeling

**Ferramentas:**
- Risk register (planilha de riscos)
- SWOT analysis
- Threat intelligence feeds

**Exemplo de Risk Register:**

|ID|Risco|Ameaça|Vulnerabilidade|Ativo|Prob|Impacto|
|---|---|---|---|---|---|---|
|R1|Ransomware|Malware|Patches atrasados|Servidor|Alta|Alto|
|R2|Phishing|Email malicioso|Falta de treino|Usuários|Média|Médio|
|```|||||||


---

### 2️⃣ Análise de Riscos

#### Análise Qualitativa
**Descrição:** Avaliação **subjetiva** usando escalas.

**Escalas:**

**Probabilidade:**
- **Muito Baixa:** < 10%
- **Baixa:** 10-30%
- **Média:** 30-50%
- **Alta:** 50-70%
- **Muito Alta:** > 70%

**Impacto:**
- **Muito Baixo:** < R$ 10k
- **Baixo:** R$ 10k - 50k
- **Médio:** R$ 50k - 200k
- **Alto:** R$ 200k - 1M
- **Muito Alto:** > R$ 1M

---

#### Análise Quantitativa
**Descrição:** Avaliação **numérica** em valores monetários.

**Métricas:**

##### ALE (Annual Loss Expectancy)
```

ALE = SLE × ARO

SLE (Single Loss Expectancy): Perda por incidente ARO (Annual Rate of Occurrence): Frequência anual

```
**Exemplo:**
```

Ativo: Servidor de banco de dados Valor do ativo: R$ 500.000 Perda estimada por incidente (SLE): R$ 200.000 Probabilidade anual (ARO): 0,3 (30% ao ano)

ALE = R$ 200.000 × 0,3 = R$ 60.000/ano

```
---

### 3️⃣ Avaliação de Riscos

#### Matriz de Risco (Risk Matrix)


```
    IMPACTO
                                       │ Baixo │ Médio │ Alto │
────────┼───────┼───────┼──────┤ Alta  │   🟡  │  🟠  │  🔴  │ ────────┼───────┼───────┼──────┤ Média │   🟢  │  🟡  │  🟠  │ ────────┼───────┼───────┼──────┤ Baixa │   🟢  │  🟢  │  🟡  │ ────────┴───────┴───────┴──────┘

🟢 Baixo: Aceitar 🟡 Médio: Monitorar 🟠 Alto: Mitigar 🔴 Crítico: Mitigar urgentemente

```
---

#### Apetite de Risco (Risk Appetite)
**Definição:** Nível de risco que a organização está **disposta a aceitar**.

**Exemplo:**
```

Empresa de tecnologia startup: Alto apetite (inovação rápida) Banco: Baixo apetite (conformidade rigorosa)

```
---

### 4️⃣ Tratamento de Riscos

#### Opções de Tratamento

##### 🛡️ Mitigar (Reduce)
**Descrição:** Implementar controles para **reduzir** probabilidade ou impacto.

**Exemplo:**
```

Risco: Ransomware Mitigação:

- Instalar patches
- Implementar EDR
- Treinar usuários
- Backups regulares

```
**Custo vs Benefício:**
```

Se ALE = R$ 60.000/ano E controle custa R$ 20.000/ano E reduz risco em 80%

Benefício = R$ 60.000 × 0,8 = R$ 48.000 Custo = R$ 20.000 ROI = R$ 48.000 - R$ 20.000 = R$ 28.000 ✅ Vale a pena!

```
---

##### 🔄 Transferir (Transfer)
**Descrição:** Transferir o risco para **terceiros** (seguro, outsourcing).

**Exemplo:**
```

Risco: Perda de dados por incêndio Transferência: Contratar seguro cibernético

```
**Considerações:**
- Custo do seguro vs ALE
- Cobertura (o que está incluído?)
- Franquia

---

##### ✅ Aceitar (Accept)
**Descrição:** **Aceitar** o risco quando custo de mitigação > impacto.

**Exemplo:**
```

Risco: Ataque DDoS a blog pessoal ALE: R$ 100/ano Custo de mitigação (CDN): R$ 500/ano Decisão: Aceitar o risco ✅

```
**Requisitos:**
- Aprovação formal da gerência
- Documentação da decisão
- Revisão periódica

---

##### 🚫 Evitar (Avoid)
**Descrição:** **Eliminar** a atividade que gera o risco.

**Exemplo:**
```

Risco: Vazamento de dados em cloud pública Evitar: Não usar cloud pública, manter tudo on-premises

```
**Considerações:**
- Pode limitar oportunidades de negócio
- Nem sempre é viável

---

### 5️⃣ Monitoramento e Revisão

**Atividades:**
- Revisão periódica do risk register (trimestral)
- Monitoramento de KRIs (Key Risk Indicators)
- Atualização após incidentes
- Revisão após mudanças significativas

**KRIs Exemplo:**
```

- Número de tentativas de phishing/mês
- Tempo médio para aplicar patches críticos
- Número de vulnerabilidades críticas abertas
- Uptime de sistemas críticos

```
---

## 🎯 Frameworks de Gestão de Riscos

### ISO 31000
**Descrição:** Padrão internacional para gestão de riscos.

**Princípios:**
- Integrado
- Estruturado
- Customizado
- Inclusivo
- Dinâmico
- Baseado em informação
- Considera fatores humanos e culturais
- Melhoria contínua

---

### NIST RMF (Risk Management Framework)
**Descrição:** Framework do NIST para gestão de riscos de segurança.

**Etapas:**
```

1. Categorize (classificar sistemas)
2. Select (selecionar controles)
3. Implement (implementar controles)
4. Assess (avaliar eficácia)
5. Authorize (autorizar operação)
6. Monitor (monitorar continuamente)

```
---

### FAIR (Factor Analysis of Information Risk)
**Descrição:** Modelo quantitativo para análise de risco cibernético.

**Componentes:**
```

Risk = Loss Event Frequency × Loss Magnitude

LEF = Threat Event Frequency × Vulnerability LM = Primary Loss + Secondary Loss

```
---

## 🛠️ Ferramentas de Gestão de Riscos

### GRC Platforms
- **ServiceNow GRC**
- **RSA Archer**
- **MetricStream**
- **LogicGate**

### Vulnerability Management
- **Tenable Nessus**
- **Qualys**
- **Rapid7 InsightVM**
- **OpenVAS**

### Threat Intelligence
- **MISP**
- **ThreatConnect**
- **Anomali**

---

## 📋 Exemplo Prático - Análise de Risco

### Cenário: E-commerce

#### Ativo
```

Sistema de pagamento online Valor: R$ 5.000.000 (receita anual)

```
#### Ameaça
```

Ataque de SQL Injection

```
#### Vulnerabilidade
```

Aplicação web sem input validation Última atualização: 2 anos atrás

```
#### Análise Quantitativa
```

SLE (perda por incidente):

- Parada do sistema: R$ 50.000
- Multa LGPD: R$ 500.000
- Dano reputacional: R$ 200.000 Total SLE: R$ 750.000

ARO (frequência anual): 0,4 (40% de chance)

ALE = R$ 750.000 × 0,4 = R$ 300.000/ano

```
#### Tratamento
```

Opção 1: Mitigar

- Contratar pentesting: R$ 30.000
    
- Implementar WAF: R$ 50.000/ano
    
- Refatorar código: R$ 100.000 Total: R$ 180.000 Redução de risco: 90%
    
    Novo ALE = R$ 300.000 × 0,1 = R$ 30.000 Benefício = R$ 300.000 - R$ 30.000 - R$ 180.000 = R$ 90.000 ✅
    

Opção 2: Transferir

- Seguro cibernético: R$ 80.000/ano Cobertura: até R$ 1.000.000

Decisão: Mitigar (Opção 1) - Melhor ROI

```
---

## 🔗 Links Relacionados

- [[CIA-Triad]]
- [[Defesa-em-Profundidade]]
- [[CWE-CVE]]
- [[NIST-Cybersecurity]]
- [[ISO-27001]]

---

## 📚 Referências

- ISO 31000 (Risk Management)
- NIST SP 800-30 (Guide for Conducting Risk Assessments)
- NIST RMF (Risk Management Framework)
- FAIR (Factor Analysis of Information Risk)
- ISO 27005 (Information Security Risk Management)