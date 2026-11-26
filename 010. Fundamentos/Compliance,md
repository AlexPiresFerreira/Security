# 📋 Compliance em Segurança da Informação

> **Tags:** #compliance #sgsi #nist #iso27001 #cobit #lgpd #auditoria #governanca #risco
> **Fonte:** Aulas I e II — Profa. Cristina Godoy Bernardo de Oliveira (MBA Cibersegurança USP ESALQ)
> **Datas:** 26/11 e 03/12/2026

---

## 📌 Conceito Central

Compliance em segurança da informação é a capacidade de **identificar obrigações, implementar controles verificáveis e demonstrar evidências** de que as regras estão sendo cumpridas.

> 💡 O trabalho começa pela identificação do **critério aplicável** (lei, contrato, política interna).

### Tripé fundamental

| Fonte | Exemplo de exigência | Evidência esperada |
|---|---|---|
| Lei/Regulação | LGPD art. 46 — medidas técnicas e administrativas | Avaliação de risco, controles e resultados de testes |
| Contrato | Acesso do prestador limitado à janela aprovada | Cláusula, chamado de autorização e horário de revogação |
| Política interna | Identidade nominal e MFA | Configuração do provedor de identidade e eventos de autenticação |

---

## 🏛️ Fundamentos

### Integridade

Dois níveis distintos e complementares:

- **Integridade da informação** → Proteção contra alteração ou destruição indevida. Rastrear identidade, horário e versão do registro.
- **Integridade organizacional** → Coerência entre compromissos declarados e decisões reais, inclusive quando o controle atrasa a entrega.

> ⚠️ Um log tecnicamente íntegro pode registrar um processo com **decisões omitidas**. A integridade técnica não garante a organizacional.

**Teste de consistência:** Reconciliar chamados, concessões no sistema e exceções registradas. Buscar eventos sem autorização correspondente.

---

### Governança vs. Gestão

| Nível | Papel | Responsabilidade |
|---|---|---|
| **Órgão de Governança** | Avalia exposições materiais, orienta e monitora | Decisão estratégica, tolerância a risco |
| **Gestão** | Aloca recursos, implementa controles, resolve desvios | Execução operacional |
| **Supervisão** | Recebe indicadores com denominador e evidência | Escalonamento e acompanhamento |

---

### Accountability (Prestação de Contas)

| Papel | Decisão ou atuação | Registro esperado |
|---|---|---|
| Dono do risco | Aceita risco residual dentro de sua alçada | Aceite identificado, prazo e condições |
| CISO / Equipe de segurança | Avalia salvaguardas e monitora risco técnico | Parecer, alertas e trilha de monitoramento |
| Jurídico / Encarregado | Analisa obrigações e dados pessoais | Parecer ou orientação |
| Operação | Executa controles | Logs de execução |
| Auditoria interna | Avalia com independência | Papéis de trabalho |

---

## 📐 Referenciais e Frameworks

### NIST CSF 2.0

**Arquitetura:** Core + Profiles + Tiers

- **Core** → Resultados organizados em funções, categorias e subcategorias
- **Profiles** → Resultados atuais (perfil atual) e desejados (perfil-alvo) para escopo definido
- **Tiers** → Caracterizam o rigor das práticas (Tier 1 Partial → Tier 4 Adaptive)

#### As 6 Funções

GOVERN → IDENTIFY → PROTECT → DETECT → RESPOND → RECOVER

**A função GOVERN** orienta todas as outras e possui 6 grupos:

| Grupo | Foco |
|---|---|
| **GV.OC** | Contexto organizacional — obrigações e dependências |
| **GV.RM** | Gestão de risco — apetite e tolerância |
| **GV.RR** | Papéis e responsabilidades — autoridade e recursos |
| **GV.PO** | Política — estabelece e atualiza |
| **GV.OV** | Supervisão — usa resultados para ajustes |
| **GV.SC** | Cadeia de suprimentos — riscos de terceiros |

#### Exemplo de Perfil Atual × Alvo

| Resultado | Evidência atual | Resultado-alvo | Teste de aceitação |
|---|---|---|---|
| GV.RR-02 | Alçadas dispersas em e-mails | Alçadas publicadas e comunicadas | Simular escalonamento fora de horário |
| GV.SC-07 | Riscos revistos só na contratação | Riscos acompanhados durante o contrato | Conferir revisão e tratamento por fornecedor |
| PR.AA-05 | Acesso persistente em parte da operação | Privilégio temporário com revisão | Reconciliar concessões, vigência e revogação |

#### Plano de 90 dias (exemplo)

- **Dias 1–30** → Medir cobertura, definir alcance, alçada e fontes de autorização
- **Dias 31–60** → Ativar acesso temporário nos serviços de maior exposição; ensaiar fluxo de emergência
- **Dias 61–90** → Reexecutar teste, documentar lacunas e revisar perfil atual

---

### ISO/IEC 27001:2022 (SGSI)

**Arquitetura das cláusulas:**
Cláusulas 4–6: Contexto, Liderança e Planejamento Cláusulas 7–8: Suporte e Operação Cláusulas 9–10: Avaliação e Melhoria

#### Fluxo de Avaliação de Risco

1. **Identificação** → Descrever evento e consequências possíveis
2. **Análise** → Usar critérios de impacto e probabilidade; registrar premissas
3. **Avaliação** → Comparar com critérios de aceitação; atribuir dono do risco

#### SoA — Declaração de Aplicabilidade

Liga a **seleção de controles** ao **tratamento de riscos**. Deve conter:
- Justificativa de inclusão
- Estado de implementação
- Justificativas de **exclusão** de controles do Anexo A

**Exemplo aplicado a acessos privilegiados:**

| Controle | Justificativa | Estado | Evidência prevista |
|---|---|---|---|
| A.5.16 Gestão de identidades | Atribuir cada sessão a uma identidade | Implementado no serviço A | Inventário e logs de identidade |
| A.5.18 Direitos de acesso | Revisar concessões e revogar no encerramento | Parcial no serviço B | Relatório de revisão e eventos de revogação |
| A.8.2 Acessos privilegiados | Limitar privilégio e duração | Previsto no serviço C | Configuração PAM e teste de expiração |

#### Controles relevantes na ISO 27002

| Controle | Foco |
|---|---|
| 5.15 e 5.16 | Regras de acesso e ciclo de vida de identidades |
| 5.18 e 8.2 | Concessão, revisão, revogação de direitos privilegiados |
| 8.15 e 8.16 | Eventos registrados e atividades monitoradas |

#### Não conformidade → Ação corretiva
Correção (imediata) → Revogar acesso, revisar atividade no período ↓ Causa → Verificar se expiração falhou por configuração, integração ou processo ↓ Ação corretiva → Atuar na causa e testar recorrência em concessões novas

---

### ISO/IEC 27701:2025 (Privacidade — PIMS)

- Estrutura o **sistema de gestão de informações de privacidade**
- Delimita operações de tratamento e interfaces com o SGSI
- Mapeia atuação como **controladora ou operadora** em cada operação
- Vincula obrigações, instruções, registros, retenção e controles ao processo de tratamento

---

### COBIT 2019

**Modelo:** 40 objetivos em 5 domínios

| Domínio | Natureza | Foco |
|---|---|---|
| **EDM** | Governança | Avaliar, Direcionar e Monitorar |
| **APO** | Gestão | Alinhar, Planejar e Organizar |
| **BAI** | Gestão | Construir, Adquirir e Implementar |
| **DSS** | Gestão | Entregar, Servir e Suportar |
| **MEA** | Gestão | Monitorar, Avaliar e Analisar |

#### Objetivos-chave no contexto de compliance

| Objetivo | Função |
|---|---|
| **EDM03** | Governança avalia, orienta e monitora a gestão do risco |
| **APO12** | Gestão identifica, analisa, comunica e trata riscos |
| **APO13** | Organiza a gestão da segurança e o tratamento de riscos |
| **DSS05** | Opera serviços de segurança (eventos, revisões, ações) |
| **MEA03** | Identifica requisitos externos e avalia conformidade |
| **MEA04** | Planeja e executa atividades de assurance |

#### 7 Componentes do sistema de governança

1. Processos e estruturas
2. Políticas
3. Informação
4. Cultura
5. Pessoas
6. Tecnologia
7. *(Serviços, infraestrutura e aplicações)*

> ⚠️ Um objetivo pode falhar mesmo com um procedimento formal instituído se qualquer componente estiver ausente.

---

### Crosswalk entre frameworks

| Pergunta | NIST CSF 2.0 | ISO/IEC 27001/27002 | COBIT 2019 |
|---|---|---|---|
| Quem decide? | GV.RR e GV.RM | Cl. 5.3 e 6.1 | EDM03 e APO12 |
| Como tratar privilégios? | PR.AA-05 | A.5.18 e A.8.2 | APO13 e DSS05 |
| Como avaliar? | GV.OV | Cl. 9.1 e 9.2 | MEA03 (requisitos externos) |

---

## ⚖️ Legislação

### LGPD — Lei 13.709/2018

- **Art. 46** → Medidas técnicas e administrativas de segurança
- **Art. 48** → Comunicação de incidentes

### Resolução CD/ANPD nº 15/2024

- **Art. 5º** → Definições
- **Art. 6º** → Critério de risco ou dano relevante aos titulares
- **Art. 9º** → Destinatários e prazo geral de **3 dias úteis** para comunicação

### Fluxo de decisão em incidente (LGPD)
Detecção técnica ↓ Confirmar: dados pessoais atingidos? Consequências? Cronologia? ↓ Avaliação jurídica: há risco ou dano relevante aos titulares? ↓ Se SIM → Comunicar ANPD e titulares no prazo aplicável ↓ Documentar toda a decisão e sua fundamentação

---

## 🔍 Auditoria

### Conceitos fundamentais

- **Pergunta de auditoria** → O que pretende concluir, sobre qual período e para quem
- **Escopo** → Período, sistemas, contas e tipos de registro
- **Critérios** → Política aprovada, cláusulas contratuais, requisitos do SGSI

### Três Linhas (IIA — 2020)
1ª Linha: Operação → Opera controles e corrige exceções 2ª Linha: Gestão de risco → Acompanha políticas, risco e conformidade 3ª Linha: Auditoria interna → Avalia com INDEPENDÊNCIA

> ⚠️ A auditoria deve avaliar a **competência, objetividade e qualidade** do trabalho da 2ª linha antes de usá-lo como evidência.

### Tipos de teste (NIST SP 800-53A)

| Método | O que faz |
|---|---|
| **Exame** | Analisa documentos, configurações e registros |
| **Entrevista** | Reconstrói o fluxo e investiga divergências com quem opera |
| **Teste** | Observa ou reexecuta comportamento sob condições definidas |

### Tipos de seleção

| Tipo | Quando usar |
|---|---|
| **Censo** | Regras determinísticas com campos e cobertura confiáveis |
| **Amostra direcionada** | Exceções raras, casos críticos, hipóteses específicas |
| **Amostra probabilística** | Inferência sobre a população — exige desenho adequado |

### Qualidade da evidência

- **Relevância** → A fonte mede a ocorrência do controle e cobre o período?
- **Confiabilidade** → Origem, acesso, integridade e possibilidade de adulteração
- **Suficiência** → Volume + cobertura + qualidade; identificar limitações materiais

### Papéis de trabalho reproduzíveis

Deve conter:
- **Identificação** → Teste, objetivo, período, responsável, fontes
- **Execução** → Filtros, transformações, amostra, exclusões, evidências
- **Conclusão** → Condição observada, limites da inferência, revisão e vínculo ao achado

---

## 🛠️ Ferramentas e Técnicas

### Mapa por camada

| Camada | Ferramenta / Fonte | Uso de auditoria |
|---|---|---|
| Governança | GRC, ITSM, repositório | Critérios, exceções, chamados e planos |
| Execução | IAM, PAM, SIEM, CMDB | Eventos, configuração e população |
| Análise | SQL, Power Query, Python, BI | Reconciliação, repetição e transparência |

### Ferramentas específicas

| Ferramenta | Uso principal |
|---|---|
| **ITSM** | Trilha de aprovação — comparar aprovação x concessão efetiva |
| **IAM** | Inventário de identidades, grupos, atribuições e expiração |
| **PAM** | Solicitação, sessão, privilégio liberado, aprovador e evidência de revogação |
| **SIEM** | Cobertura de eventos — verificar integração, fuso e retenção |
| **CMDB** | Denominador de ativos — reconciliar esperado vs. observado |
| **GRC** | Obrigação → controle → achado → ação corretiva |
| **SQL/Power Query** | Reconciliação com trilha reproduzível |

### Pontos críticos de qualidade de dados

- Reconciliar totais com o sistema de origem antes de análise
- Verificar **junções N:N** que podem inflar denominadores
- Tratar **fuso horário** em comparações temporais
- Classificar campos vazios em hipóteses distintas (omissão, falha de integração, chave alternativa)

---

## 📊 Dashboards e Monitoramento

### Tipos de indicadores

| Tipo | Exemplo | Mede |
|---|---|---|
| **KPI** | % de revisões concluídas no prazo | Desempenho da execução |
| **KRI** | Nº de privilégios ativos além da janela em serviços críticos | Exposição / sinal de risco |
| **KCI** | % de concessões com aprovação prévia confirmada | Funcionamento de um controle |

### Ficha técnica de indicador

| Campo | Definição |
|---|---|
| Numerador | Concessões avaliáveis com aprovação prévia |
| Denominador | Concessões avaliáveis do escopo e período (exibir também elegíveis e excluídas) |
| Limiar e ação | Se abaixo de 98% → abrir investigação; responsável em 1 dia útil |

### Armadilhas comuns

> ⚠️ **Taxa de conformidade ≠ cobertura**
> Se conformidade = 97% mas cobertura = 74%, o painel verde pode esconder exposição real.

> ⚠️ **Campo vazio ≠ desvio confirmado**
> Hipóteses: (1) omissão de registro, (2) falha de integração, (3) chave alternativa.

### Como auditar o próprio dashboard

- **Origem** → Reconciliar totais com sistemas de origem
- **Cálculo** → Reexecutar indicador com dados brutos; testar nulos e fronteiras de data
- **Publicação** → Validar filtros, permissões e histórico de mudança da regra

---

## 🏥 Caso Prático — Acesso Privilegiado de Terceiros

> *Cenário didático fictício que percorre toda a disciplina*

**Situação:** Prestador de suporte hospitalar precisa de acesso privilegiado por 48h no fim de semana.

**Regras aplicáveis:**
- Aprovação prévia nominal
- MFA obrigatório
- Expiração automática em 48h
- Trilha de sessão registrada

**Classificação dos registros de teste:**

| ID | Aprovação | Revogação | Classificação |
|---|---|---|---|
| A | Prévia | 21h | ✅ Atende |
| B | Posterior | 30h | ❌ Desvio (aprovação) |
| C | Prévia | 60h | ❌ Desvio (prazo) |
| D | Prévia | 32h | ❌ Desvio (prazo) |
| E | Sem horário no extrato | 17h | ⚠️ Inconclusivo |
| F | Prévia | Evento ausente | ⚠️ Inconclusivo |

**Resultado:**
2 Atendem | 2 Desvios | 2 Inconclusivos

**Redação de achado:**

> "A política exige aprovação prévia e expiração em 48h. Em 430 registros avaliáveis (de 480 totais), 24 apresentaram desvios confirmados (5,6%). Para 50 concessões, a evidência é insuficiente para concluir. Recomenda-se: corrigir bloqueio e expiração automática, recuperar evidência dos 50 inconclusivos e atribuir responsável, prazo e reteste."

---

## 🔄 Programa de Compliance — Estrutura

### Política × Padrão × Procedimento

| Nível | Conteúdo |
|---|---|
| **Política** | Princípios, alcance, autoridade de aprovação e tratamento de exceções |
| **Padrão** | Requisitos verificáveis: MFA, identidade individual, prazo máximo |
| **Procedimento** | Passos, sistema de registro, responsável, contingência e evidência de encerramento |

### Ciclo do programa
Estabelecer → Operar → Supervisionar ↓ ↓ ↓ Escopo, Matriz de Revisar mudanças, critérios, obrigações, indicadores e achados patrocinador exceções, com responsáveis trilhas e datas

### Gestão de mudanças normativas

1. **Captura** → Monitorar fonte oficial; documentar entidade afetada, vigência e interpretação
2. **Impacto** → Identificar processos, contratos, controles e evidências que precisam mudar
3. **Validação** → Testar implementação, tratar lacunas e reportar risco residual ao dono competente

---

## 🔗 Links Relacionados

- [[CIA-Triad]]
- [[IAAA]]
- [[Risco-e-Vulnerabilidades]]
- [[Defesa-em-Profundidade]]
- [[CIS-Controls]]
- [[NISTCybersecurity]]
- [[Fundamentos-Cripto]]
- [[IPSec]]

---

## 📚 Referências

- NIST SP 800-12 Rev. 1 — An Introduction to Information Security
- NIST CSWP 29 (2024) — NIST Cybersecurity Framework (CSF) 2.0
- NIST SP 800-53 Rev. 5 — Security and Privacy Controls
- NIST SP 800-53A Rev. 5 — Assessing Security and Privacy Controls
- ISO/IEC 27001:2022 — Information Security Management Systems
- ISO/IEC 27002:2022 — Information Security Controls
- ISO/IEC 27701:2025 — Privacy Information Management
- ISACA — COBIT 2019 Framework
- IIA — Three Lines Model (2020)
- BRASIL — Lei nº 13.709/2018 (LGPD)
- ANPD — Resolução CD/ANPD nº 15/2024
- CaseWare IDEA — Complete Guide to Auditing with Data Analytics Tools (2019)
- IRS Criminal Investigation — Cybersecurity Dashboard on a Shoestring Budget (2017)
✅ O que foi incluído
Este resumo cobre as duas aulas completas:

Aula I	Aula II
Fundamentos e ética	Auditoria (programa, procedimentos, evidências)
Governança vs. Gestão	Ferramentas (ITSM, IAM, PAM, SIEM, SQL)
NIST CSF 2.0	Dashboards e indicadores (KPI, KRI, KCI)
ISO 27001/27002/27701	Monitoramento contínuo
COBIT 2019	Caso integrado completo
LGPD e ANPD	Comunicação de incidentes

Exportar

Copiar

