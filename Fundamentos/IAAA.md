
# 🔐 IAAA (Identificação, Autenticação, Autorização, Auditoria)

> **Tags:** #seguranca #fundamentos #iaaa #autenticacao #autorizacao #auditoria

---

## 📌 Conceito

**IAAA** é um conjunto de processos usados para garantir a segurança de sistemas e dados, envolvendo quatro etapas principais que trabalham juntas para proteger recursos.

---

## 🆔 1. Identificação

### Definição
Processo de **declarar quem você é** no sistema.

### Exemplos
- Nome de usuário
- E-mail
- CPF
- ID de funcionário

---

## 🔑 2. Autenticação

### Definição
Processo de **provar que você é quem diz ser**.

### Fatores de Autenticação

#### 🧠 Algo que você SABE
- Senha
- PIN
- Resposta de segurança

#### 📱 Algo que você TEM
- Token físico (FIDO)
- Smartphone (SMS, App Authenticator)
- Cartão inteligente
- QR Code

#### 👤 Algo que você É
- Biometria (digital, facial, íris)
- Reconhecimento de voz
- Padrão de digitação

### MFA (Multi-Factor Authentication)
Combinação de **dois ou mais fatores** para aumentar segurança.

**Exemplo:**

Senha (algo que sei) + Token SMS (algo que tenho)

---

## 🛡️ 3. Autorização

### Definição
Processo de **definir o que você pode fazer** após autenticação.

### Técnicas
- **ACL (Access Control List)** - Lista de permissões por recurso
- **RBAC (Role-Based Access Control)** - Permissões baseadas em função
- **ABAC (Attribute-Based Access Control)** - Permissões baseadas em atributos
- **Princípio do Menor Privilégio** - Usuário tem apenas acessos essenciais

### Exemplo

Usuário: João Silva Função: Analista de Suporte Permissões: ✅ Ler tickets ✅ Responder tickets ❌ Deletar tickets ❌ Acessar configurações do sistema

---

## 📊 4. Auditoria

### Definição
Processo de **registrar e monitorar** todas as ações no sistema.

### Princípio: "No Logs, No Crime"

Toda ação deve responder:
- **Who** (Quem) - Qual usuário realizou a ação
- **What** (O quê) - Qual ação foi realizada
- **When** (Quando) - Data e hora exata
- **Where** (Onde) - Qual sistema/recurso foi acessado
- **Why** (Por quê) - Contexto da ação (quando aplicável)

### Ferramentas
- **SIEM** (Security Information and Event Management)
  - Splunk
  - Wazuh
  - ELK Stack
- **Logs de Sistema**
  - Windows Event Viewer
  - Syslog (Linux)
- **Audit Trails**
- **Dashboards de Monitoramento**

### Exemplo de Log

```

[2025-12-31 18:45:23] USER: joao.silva | ACTION: DELETE | RESOURCE: /config/firewall.conf | STATUS: DENIED | IP: 192.168.1.50

```

---

## 🔗 Links Relacionados
- [[CIA-Triad]]
- [[Controles-de-Acesso]]
- [[SIEM]]
- [[Zero-Trust]]

---

## 📚 Referências
- NIST SP 800-63 (Digital Identity Guidelines)
- ISO 27001