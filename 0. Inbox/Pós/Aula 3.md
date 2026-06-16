---
tags:
  - web
---

#### Livro

[[Acadi-ti MTIA - e-book Parte 03.pdf]]

[[Acadi-ti MTIA - Infografico Parte 03.pdf]]

#### Lab

- **PortSwiggeer:** https://portswigger.net/web-security/getting-started
	- **HTTP**
		-  https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-authentication-bypass
		-  https://portswigger.net/web-security/information-disclosure/lab-infoleak-via-backup-files
	- **XSS**
		- https://portswigger.net/web-security/all-labs#cross-site-scripting
		- https://portswigger.net/web-security/prototype-pollution
		- https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-dom-xss-via-client-side-prototype-pollution
		- https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-dom-xss-via-an-alternative-prototype-pollution-vector
		- https://portswigger.net/web-security/prototype-pollution/client-side/lab-prototype-pollution-client-side-prototype-pollution-via-flawed-sanitization
	- **MVC**
		- https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-without-strings
		- https://portswigger.net/web-security/cross-site-scripting/contexts/client-side-template-injection/lab-angular-sandbox-escape-and-csp
	- **SOP**
		-  https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack
		- https://portswigger.net/web-security/cors/lab-null-origin-whitelisted-attack
		-  https://portswigger.net/web-security/cors/lab-breaking-https-attack
		- https://portswigger.net/web-security/cors/lab-internal-network-pivot-attack
		-  https://portswigger.net/web-security/csrf/lab-no-defenses
		-  https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-validation-depends-on-request-method
		- https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-validation-depends-on-token-being-present
		- https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-not-tied-to-user-session
		- https://portswigger.net/web-security/csrf/bypassing-token-validation/lab-token-duplicated-in-cookie
		- https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references
		- https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids
		- https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect
	- **SQL**
		- https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data
		- https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns
		- https://portswigger.net/web-security/sql-injection/blind/lab-conditional-responses
		- https://github.com/petryx/Sqli_playground
	- **JSON WEB TOKEN(JWT)**
		- https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-unverified-signature
		- https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-weak-signing-key
		- https://portswigger.net/web-security/jwt/lab-jwt-authentication-bypass-via-kid-header-path-traversal
		- https://portswigger.net/web-security/jwt/algorithm-confusion/lab-jwt-authentication-bypass-via-algorithm-confusion
	- **Command Injection**
		- https://portswigger.net/web-security/os-command-injection/lab-simple
		- https://portswigger.net/web-security/os-command-injection/lab-blind-time-delays
		- https://portswigger.net/web-security/os-command-injection/lab-blind-output-redirection
	- **ffuf**
		- http://ffuf.me
		- https://github.com/carlosalbertotuma/laboratorio-fuzzing
- [**extremehacking** 
	- XSS Playgrounf (5 Flags)
	- Escape(1 Flag)
#### Site
- Para ver depois: 
	- https://webhook.site/#!/view/9d99dfe3-5d79-4c68-a075-0bb202ee344a

#### Tools

- **Burp Suite**
	- PC(SSL) -->  PROXY(Burp)(SSL) --> REDE ---> Rorteador --> Internet --> web
	- Instalação: 
		- sudo apt install burpsuite
	- Funções:
		- Repeater(CTRL+R)
			- Modificar e reenviar requisições HTTP de forma iterativa
		- Comparer
			- Comparar as diferenças nas respostas de duas requisições HTTP
		- Intruder(CTRL+i)
			- Ataque de brute force, teste de carga e variações de parâmetros
		- Decoder
			- Decodificador de payloads(Base64, URL encoding)
- **FoxyProxy**
	- Extensão para navegadores web
	- Alterando a configuração de proxy
	- Instalação: 
		- Loja de complementos do navegador
- **Gobuster**
	- Brute force
	- Descoberta de diretórios e arquivos em servidores WEB
	- Intalação: 
		- sudo napt install gobuster
- **ffuf**
	- Brute force
	- Varredura de subdomínios
	- Instalação: 
		- sudo apt install ffuf
	- Saiba Mais: 
		- Site: https://github.com/ffuf/ffuf
		- Documentos:  https://github.com/ffuf/ffuf/wiki
	- ffuf com Burp 
		- Criar uma variavel: export http_proxy=http://127.0.0.1:8080
		- executar ffuf: ffuf -w /usr/share/seclists/Discovery/Web-content/common.txt -u http://ffuf.me/cd/basic/FUZZ
- **Wordlists**
	- Brute force
	- Palavras ou senhas potenciais
	- Diretório: 
		- /usr/share/seclists/
	- Site: 
		- https://github.com/danielmiessler/SecLists
	- Instalação: 
		- sudo apt -y install seclists

 #### URI (Uniform Resource Identifier)
 - Endereço único que pode ser usado para localizar e acessar o recurso na rede
 
![[Pasted image 20250913100212.png]]
![[Pasted image 20250913100437.png]]


	- Schena(Esquema)
		- Protocolo: http & https
	-  Host
		- nome do domínio ou IP
	- Port
		- Identificação da porta de serviço 

- URL (Uniform Resource Identifier)
	- Especifica recursos e local
	- http://, ftp://, mailto://
- URN (Uniform Resource Name)
	- Especifica o nome do recurso
		- urn:isbn:0-486-27557-4, urn:tdm:aws:action:camera/capture
- Saiba mais
	- https://danielmiessler.com/study/difference-between-uri-url
#### HTTP
- Cliente-Servidor
- http
	- Stateless
- http1.1
	- Host Header
	- Métodos: PUT, PATCH, DELETE, CONNECT, TRACE e OPTIONS
	- Sequencial (várias conexões para buscar os recursos)
- http2.0
	- Multiplexação
	- Priorização de requisiçoes
	- Reset da conexão
	- Server Push

![[Pasted image 20250927175600.png]]
	- Saiba mais: 
		- [Entenda as diferenças entre HTTP/2 e HTTP/1.1 | Neomind](https://www.neomind.com.br/blog/diferencas-entre-http1-1-e-http2/)
- http3.0 (QUIC)
	- Status: Draft
	- Baseado em UDP
	- QUIC (Quick UDP Internet Connections)
		- Protocolo Camada de transporte
		- Multiplexação Nativa
		- Criptografia integrada
	- Instruções:
	   1. Execute o ffuf para achar o diretório de backup;
	   2. Acesse o diretório, encontre a senha do admin;
	   3. Realize a submissão da senha;
	   4. documente o precesso com print da ações tomadas.

![[Pasted image 20250920103253.png]]
	- Saiba mais: 
		- [The Road to QUIC](https://blog.cloudflare.com/the-road-to-quic/)
HTTP Methods
	- OPTIONS
		- Retorna a lista de métodos suportados pela URI
		- ![[Pasted image 20250920110048.png]]
	- HEAD
		- Retorna os HTTP Headers suportados
	- GET
		- Retorna dados do servidor, através da URI
			- Limitação caracteres URL
			- Registra no log servidor
		- API Rest - Listar os recursos
		- ![[Pasted image 20250920110120.png]]
	- POST (Envia dados)
		- Envia dados para o servidor para modificar um recurso
		- Os dados são enviado no Body
		- Sem restrição de tamanho
		- API Rest (Inseriri dados no BD)
	- ![[Pasted image 20250920110315.png]]
	- PUT (Upgrade)
		- Envia dados para o servidor para modificar um recurso
		- Os dados são enviado no Body
		- Sem restrição de tamanho
		- API Rest (Atualizar um recurso)
		- É informado todos os parâmetros para upgrade
	- PATCH
		- Similar ao PUT, porém somente é informado as parâmetros que serão modificado
	-  DELETE
		- Processo oara deletar algum dados (API REST), geralmente um recurso no banco de dados
	- CONNECT
	- TRACE
		- Método utilizado para realizar diagnóticos. 
		- Quando habilitado retorna um eco da requisição. 
		- Quando existe um proxy reverso pode retornar os http headers com cookies ou Headers de Autenticação
	- HTTP Error Codes
		- [http-status-codes-cheat-sheet](https://javaconceptoftheday.com/http-status-codes-cheat-sheet/)
#### Cross Site Scripting(XSS)  
- É um ataque que visa comprometer o cliente (Browser) front-end. Não afetando diretamente o servidor
- Conseguir acesso aos dados do usuário
- Injetar códigos Javascript na aplicação web
- Tipos XSS
	- Reflected XSS:
		- Através da manipulaçao de URL
	- Stored XSS(Persistent XSS):
		- Através da inserção de scripts no banco de dados
		- Saiba mais: 
			- [How I hacked Facebook and received a $3,500 USD Bug Bounty - Blog Detectify](https://blog.detectify.com/industry-insights/how-i-hacked-facebook-and-received-a-3500-usd-facebook-bug-bounty/)
	- DOM-based XSS: Quando a aplicação processa dados de modo inseguro
		- DOM (Document Object Model)
			- É uma interface de programação que representa a estrutura de uma pági na web como um conjunto de objetos que podem ser manipulados programaticamente
		- Saiba mais: 
			- [Introduction to the DOM - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
	- XSS Polyglot
		- É um payload que combina diferentes técnicas de injeção de código em um único script. Ele é projetado para ser interpretado de várias maneiras pelos navegadores, servidores e ferramentas de se gurança, o que o torna uma ferramenta poderosa para identifi car vulnerabilidades de XSS em uma aplicação web
		- Exemplo: 
			- jaVasCript:/*-/*`/*\`/*’/*”/**/(/**/oNcliCk=alert())//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</ scRipt/-- !>\x3csVg/<sVg/oNloAd=alert()//>\x3e
			- Saiba mais: 
				- [Relatórios HackerOne](https://github.com/reddelexc/hackerone-reports/blob/master/tops_by_bug_type/TOPXSS.md)
				- [XSS Payloads](https://github.com/payloadbox/xss-payload-list)
		- XSS Golden Rule
			1. Comerce com tags html; 
			2. Verifique onde o payload foi inserido no código fonte pa página; 
			3. Se quebrou? Conserte!; 
			4. Avalie todas as funçoes que estão carregadas na página web; 
			5. Portanto, é possível realizar chamadas e API para o backend, além das demais funções JavaScript; 
			6. Por fim, XSS pode não esta sozinho e ter um SQLi. 
- LAB 
	- [All labs | Web Security Academy](https://portswigger.net/web-security/all-labs#cross-site-scripting)
#### Prototype Pollution 
- Javascript
- Exemplo
	- // Suponha que a aplicação tenha o seguinte código:
	  let user = { name: ‘Alice’ };
	- // Um atacante pode explorar a Prototype Pollution para 
	 modificar o objeto ‘user’:
	 Object.prototype.isAdmin = true;
	- // Agora, o objeto ‘user’ terá uma propriedade ‘isAdmin’ 
	 adicionada automaticamente:
	 console.log(user.isAdmin); // true
- Proteção
	- Filtragem e validação de entrada 
	- Utilize Object.freeze()
	- Evite Extensões de Protótipos Globais
	- Sanitização de saída
	- Uso de CSP(Content Security Policy)
	- Atualização e patches
	- Auditoria de Código:
	- Treinamento de segurança
- Protótipos
	- __proto__
- Injection JSON(JavaScript Object Notation)
	- JSON.parse()
#### Server-Side JavaScript Injection
- Os invasores exploram vulnerabilidades na aplicação que permitem a inserção de código JavaScript no servidor.
- Mitigação
	- Validação e Sanitização de entradas
	- Principio do menor privilégio
	- Monitoramento de logs e auditorias de segurança
#### MVC (Model View Controller)

- Arquitetura
	![[Pasted image 20250920145741.png]]

- Camada 
	- Model - Dados
	- View - Boa aparência
	- Controller - Funções da aplicação
	- ![[Pasted image 20250920145958.png]]
- Frameworks JS (Client Side)
	- ![[Pasted image 20250920150113.png]]
	- VueJS
		- ![[Pasted image 20250920151029.png]]
	- AngularJS
		- ![[Pasted image 20250920151412.png]]
	- Site 
		- https://code.google.com/archive/p/mustache-security/
- Attaque
	- Client Side Template Injection (CSTI)
		- Roubo de informações confidencias 
		- Ataques de redirecionamento e phishing
		- Comprometimento da integridade do conteúdo
		- Mitigação 
			- Validação de entrada
			- Sanitização de dados
			- Utilize CSP(Content Security Policy)
			- Atualização de fremeworks e bibliotecas
		- ![[Pasted image 20250920150449.png]]
		- Web 4 - SPA (Sing Page Application)
		- ![[Pasted image 20250920151730.png]]

- SOP (SAME ORIGIN POLICY)
	- Origin
		- protocolo, host, porta
			- ![[Pasted image 20250920151859.png]]
	- CORS (Cross-Origin Resource Sharing)
	- SameSite
		- Strict
		- LAX
		- Nome
		- https://web.dev/samesite-cookies-explained/
	- CSRF (Cross Site Request Forgery)
		- ![[Pasted image 20250920154107.png]]
	Broken Access Control 
	- IDOR
		- ![[Pasted image 20250920154538.png]]
		- ![[Pasted image 20250920154944.png]]
	- UUID - Universally Unique Identifier
		- ![[Pasted image 20250920154830.png]]
#### SQL 
- DDL
	- ![[Pasted image 20250923192511.png]]
- DLQ
	- ![[Pasted image 20250923192542.png]]
- DML
	- ![[Pasted image 20250923192602.png]]
	- 
- SQL Injection
	- ![[Pasted image 20250923192656.png]]
	- ![[Pasted image 20250923192745.png]]
	- ![[Pasted image 20250923192837.png]]
	- ![[Pasted image 20250923192903.png]]
	- ![[Pasted image 20250923193041.png]]
	- 
	- Payloads
		- ![[Pasted image 20250923193226.png]]
		- ![[Pasted image 20250923193405.png]]
		- 
	- Blind Ataques
		- ![[Pasted image 20250923193613.png]]
		- 
	- Correção 
		- ![[Pasted image 20250923195110.png]]
		- ![[Pasted image 20250923195132.png]]
		- ![[Pasted image 20250923195149.png]]
		- ![[Pasted image 20250923195307.png]]
		- Aula 107
- Server Side Request Forgery
	- ![[Pasted image 20250923200113.png]]
	- ![[Pasted image 20250923200326.png]]
	- ![[Pasted image 20250923200341.png]]
	- ![[Pasted image 20250923200412.png]]
	- ![[Pasted image 20250923200423.png]]
	- ![[Pasted image 20250923200455.png]]
	- LAB 
		- Aula 110
- PHP Type Juggling
	- ![[Pasted image 20250923201628.png]]
	- ![[Pasted image 20250923201809.png]]
- JSON WEB TOKEN(JWT)
	- ![[Pasted image 20250923201933.png]]
	- RFC 7519
	- Header
		- ![[Pasted image 20250923202128.png]]
		- ![[Pasted image 20250923202142.png]]
	- Payload
		- ![[Pasted image 20250923202223.png]]
		- ![[Pasted image 20250923202231.png]]
	- Signature
		- ![[Pasted image 20250923202302.png]]
		- ![[Pasted image 20250923202403.png]]
		- ![[Pasted image 20250923202503.png]]
		- ![[Pasted image 20250923202811.png]]
		- ![[Pasted image 20250923202835.png]]
		- ![[Pasted image 20250923202852.png]]
		- ![[Pasted image 20250923202949.png]]
		- ![[Pasted image 20250923203007.png]]
		- ![[Pasted image 20250923203033.png]]
- PHP WRAPPERS
	- ![[Pasted image 20250923203414.png]]
	- ![[Pasted image 20250923203458.png]]
	- ![[Pasted image 20250923203524.png]]
	- ![[Pasted image 20250923203549.png]]
- XML
	- ![[Pasted image 20250923204343.png]]
	- ![[Pasted image 20250923204355.png]]
	- ![[Pasted image 20250923204403.png]]
	- ![[Pasted image 20250923204422.png]]
	- ![[Pasted image 20250923204512.png]]
	- ![[Pasted image 20250923204521.png]]
	- ![[Pasted image 20250923204600.png]]
	- ![[Pasted image 20250923204636.png]]
	- ![[Pasted image 20250923204706.png]]
	- ![[Pasted image 20250923204830.png]]
	- ![[Pasted image 20250923204848.png]]

- Command Injection 
	- ![[Pasted image 20250923205248.png]]
	- ![[Pasted image 20250923205300.png]]
	- ![[Pasted image 20250923205345.png]]
	- ![[Pasted image 20250923205410.png]]
	- ![[Pasted image 20250923205457.png]]
	- 
	- ![[Pasted image 20250923205528.png]]
	- ![[Pasted image 20250923205703.png]]
- 27/09/2025
	- Python Request
		- ![[Pasted image 20250927091240.png]]