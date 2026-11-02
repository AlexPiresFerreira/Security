262


![[Pasted image 20261101181021.png]]

- apt inmstall bat 
	- batcat
	- https://github.com/sharkdp/bat
		

inotify-tools

![[Pasted image 20261101183917.png]]
![[Pasted image 20261101184046.png]]

![[Pasted image 20261101184523.png]]

![[Pasted image 20261101184740.png]]

speechify.com
elevenlabs.io
veed.io

submarinecablemap.com

### DNS
- root-servers.org
- Arquivo de configuração: cat /etc/resolv.conf
- Verificação de IP: host <URL> | nslookup <URL> | dig +short <URL>
- CDN (rede de distribuição de conteúdo)
	- https://www.cloudflare.com/pt-br/learning/cdn/what-is-a-cdn/
- apelido (CNAME)
- Endereço IP(A)

### IP/TCP

SYN("alô") --> SYN-ACK("alo, pode falar") --> ACK("combinado")
hostname -I
nc -zv <URL> <Porta>
ip router
ip neighbor
whois
mtr -u -r -c 5
getent hosts <nome>

https://stackoverflow.com
[https://guilhermeonrails.github.io/aula-3-html/](https://guilhermeonrails.github.io/aula-3-html/)

### robots.txt

- curl http://target.local/robots.txt
	- information disclosure
- dirb <URL>
	- /usr/share/dirb/wordlist/common.txt
- gobuster dir -u <URL> -w /usr/share/dirb/wordlist/common.txt
- grep -oP 'href="\K[^"]+'
- curl -O <URL> 

### Markdown 
- glow <arquivo>

### Credencial

- Criptografia
- Políticas
- Monitoramento

curl -s -X POST <URL> -d <"username=user&password=senha">
- http verbos
- bcrypt-generator.com

### SQL Injection

- admin' -- | 1
- ' or '1' = '1' --
![[Pasted image 20261102145410.png]]

### Cross-Site script

# DevSecOps

Semgrep


### Aula 3
https://guilhermeonrails.github.io/aula-3-html/

https://marianabsctba.github.io/Linux_Cheat_Sheet/
https://usehatch.dev/p/ddgOWW5LITp7obdy
https://docs.docker.com/get-started/get-docker/


