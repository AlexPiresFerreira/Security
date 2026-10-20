
> **Tags:** #criptografia #encryption #seguranca #confidencialidade #integridade #autenticacao

## Conceitos fundamentais

### O que é criptografia?

Criptografia é o uso de técnicas matemáticas para proteger informações. A **cifragem** transforma dados legíveis (*plaintext*) em dados cifrados (*ciphertext*); a **decifragem** recupera os dados usando uma chave apropriada.

A criptografia pode ajudar a fornecer:

- **Confidencialidade:** restringe a leitura dos dados a quem possui autorização e as chaves necessárias.
- **Integridade:** permite detectar alterações, quando combinada com mecanismos de autenticação.
- **Autenticidade:** ajuda a verificar a origem de uma mensagem ou identidade, conforme o mecanismo usado.
- **Não repúdio:** assinaturas digitais podem fornecer evidências de autoria, desde que a chave privada e sua associação à identidade sejam confiáveis. Isso não é garantido apenas pelo uso de criptografia.

> Criptografia, por si só, não garante que um sistema seja seguro. Gestão de chaves, implementação, configuração e validação de identidades também são essenciais.

## Terminologia básica

| Termo | Definição |
|---|---|
| **Plaintext** | Dados originais, antes da cifragem |
| **Ciphertext** | Dados cifrados |
| **Encryption / Cifragem** | Transformação de dados em ciphertext |
| **Decryption / Decifragem** | Recuperação dos dados a partir do ciphertext |
| **Key / Chave** | Valor usado pelo algoritmo para cifrar, decifrar ou autenticar |
| **Algorithm / Algoritmo** | Procedimento matemático, como AES ou RSA |
| **Cipher / Cifra** | Algoritmo ou construção criptográfica usada para proteger dados |

## Tipos de criptografia

### 1. Criptografia simétrica

Usa a mesma chave secreta — ou chaves facilmente derivadas entre si — para cifrar e decifrar dados.

```
Plaintext ──[cifragem com chave K]──> Ciphertext
Plaintext <──[decifragem com chave K]── Ciphertext
```

**Vantagens**
- Rápida e adequada para cifrar grandes volumes de dados.
- Menor custo computacional que a criptografia assimétrica.

**Desafios**
- A chave precisa ser compartilhada e protegida com segurança.
- Não fornece, por si só, não repúdio.

#### Algoritmos simétricos comuns

| Algoritmo | Observações |
|---|---|
| **AES** | Cifra de blocos com chaves de 128, 192 ou 256 bits. Amplamente usada. |
| **ChaCha20** | Cifra de fluxo moderna, normalmente combinada com Poly1305 para autenticação. |
| **DES** | Obsoleto; o tamanho efetivo da chave é insuficiente contra ataques de força bruta. |
| **3DES** | Depreciado e lento; evite em sistemas novos. |
| **Blowfish** | Algoritmo legado. Para novas aplicações, prefira construções modernas e bibliotecas atuais. |

#### Modos de operação

**ECB (Electronic Codebook) — não usar para dados comuns**

Blocos de plaintext iguais produzem blocos cifrados iguais, revelando padrões.

**CBC (Cipher Block Chaining) — legado; requer cuidados**

CBC precisa de um IV imprevisível e exclusivo para cada cifragem com a mesma chave, além de padding. **CBC não autentica os dados**: deve ser combinado corretamente com um MAC, usando uma construção segura. Uma implementação incorreta pode permitir ataques como *padding oracle*.

**GCM (Galois/Counter Mode) — opção comum de AEAD**

AES-GCM oferece confidencialidade e autenticação dos dados (AEAD). A reutilização de um nonce com a mesma chave é perigosa e pode comprometer a segurança.

**ChaCha20-Poly1305 — opção comum de AEAD**

Combina cifragem e autenticação. É usada, por exemplo, em alguns conjuntos criptográficos de TLS.

> Em aplicações novas, prefira uma biblioteca confiável e um modo AEAD, como AES-GCM ou ChaCha20-Poly1305. Não implemente padding, modos ou gerenciamento de nonce manualmente sem necessidade.

### Exemplo didático: AES-GCM em Python

Instalação da biblioteca PyCryptodome:

```
python -m pip install pycryptodome
```


from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes

# Chave de 256 bits gerada com fonte aleatória segura
key = get_random_bytes(32)

# GCM gera um nonce. Guarde-o junto ao ciphertext.
cipher = AES.new(key, AES.MODE_GCM)
ciphertext, tag = cipher.encrypt_and_digest(b"Mensagem secreta")

# Decifragem e verificação da autenticação
decipher = AES.new(key, AES.MODE_GCM, nonce=cipher.nonce)
plaintext = decipher.decrypt_and_verify(ciphertext, tag)

print(plaintext.decode("utf-8"))



O nonce e a tag não precisam ser secretos, mas devem ser preservados junto ao ciphertext. **Nunca reutilize o mesmo nonce com a mesma chave.** A chave precisa ser armazenada e compartilhada por um canal seguro.

### 2. Criptografia assimétrica

Usa um par de chaves relacionadas:

- **Chave pública:** pode ser compartilhada.
- **Chave privada:** deve permanecer protegida pelo proprietário.

Para confidencialidade, uma pessoa pode cifrar dados para o destinatário usando a **chave pública do destinatário**; o destinatário decifra usando sua **chave privada**. Para assinaturas digitais, o processo é diferente: o titular assina com a chave privada, e outras pessoas verificam com a chave pública correspondente.

**Vantagens**
- Facilita o estabelecimento de comunicações sem compartilhar previamente uma chave simétrica secreta.
- Permite assinaturas digitais.

**Desafios**
- Em geral, é mais lenta que a criptografia simétrica.
- É necessário confiar na associação entre a chave pública e a identidade alegada.

#### Algoritmos e mecanismos comuns

**RSA**
- Usado para assinaturas e, em alguns protocolos, para cifrar pequenas quantidades de dados.
- Em sistemas novos, use tamanhos e esquemas recomendados por padrões atuais; 2048 bits é um mínimo comum para muitas aplicações, enquanto requisitos de segurança maiores podem exigir chaves maiores.
- Para cifragem RSA, use esquemas modernos, como OAEP; para assinaturas, prefira PSS quando aplicável.
- RSA não é apropriado para cifrar diretamente grandes arquivos.

**ECC (criptografia de curvas elípticas)**
- Família de técnicas que oferece segurança comparável com chaves menores que RSA, dependendo do algoritmo e da curva.
- **ECDH** pode estabelecer um segredo compartilhado.
- **ECDSA** e **EdDSA** são algoritmos de assinatura; Ed25519 é uma variante de EdDSA usada em contextos como SSH.

**Diffie–Hellman (DH) e ECDH**
- São mecanismos de estabelecimento de chaves; não cifram diretamente os dados da aplicação.
- Sem autenticação das partes, podem ser vulneráveis a um ataque *man-in-the-middle*.
- O segredo compartilhado normalmente é processado por uma função de derivação de chaves (KDF) antes de ser usado.

### 3. Criptografia híbrida

Combina o estabelecimento de chaves assimétrico com a eficiência da criptografia simétrica:

1. As partes estabelecem ou negociam material de chave de sessão.
2. Uma chave simétrica é derivada ou obtida para a sessão.
3. Os dados são protegidos com uma cifra simétrica autenticada, como AES-GCM.
4. A identidade das partes e a negociação são autenticadas conforme o protocolo.

**Uso:** TLS, OpenPGP e outros protocolos seguros.

> TLS moderno não deve ser resumido como “cifrar uma chave AES com RSA”. TLS 1.3 usa mecanismos de troca de chaves como ECDHE e cifras autenticadas; a autenticação do servidor normalmente envolve certificados e assinaturas.

## Funções de hash criptográfico

Uma função de hash transforma uma entrada de tamanho arbitrário em uma saída de tamanho fixo, chamada **hash** ou **digest**. Hash não é cifragem: não há chave para decifrar o resultado.

Propriedades desejadas incluem:

- **Determinismo:** a mesma entrada produz a mesma saída.
- **Resistência à pré-imagem:** deve ser impraticável encontrar uma entrada que produza um hash escolhido.
- **Resistência à segunda pré-imagem:** deve ser impraticável encontrar outra entrada com o mesmo hash de uma entrada específica.
- **Resistência a colisões:** deve ser impraticável encontrar duas entradas distintas com o mesmo hash.
- **Efeito avalanche:** pequenas mudanças na entrada tendem a alterar bastante a saída.

| Algoritmo | Situação geral |
|---|---|
| **MD5** | Quebrado para usos que dependem de resistência a colisões. Não usar para segurança. |
| **SHA-1** | Depreciado para usos que dependem de resistência a colisões. |
| **SHA-256 / SHA-512** | Membros da família SHA-2; usados amplamente para integridade e outros fins. |
| **SHA-3** | Família de hash padronizada, com construção diferente de SHA-2. |
| **BLAKE2** | Família de hashes criptográficos eficiente. |

> Hashes rápidos, como SHA-256, **não são adequados para armazenar senhas**. Para senhas, use uma função específica e deliberadamente custosa, como Argon2id; bcrypt, scrypt ou PBKDF2 podem ser opções conforme a plataforma e os requisitos.

### Exemplo: calcular hash de texto


pythonCopiarimport hashlib

texto = "Mensagem de exemplo".encode("utf-8")
digest = hashlib.sha256(texto).hexdigest()

print(digest)



### Uso: verificar integridade de arquivo


bashCopiarsha256sum arquivo.zip



Compare o resultado com um hash obtido por um canal confiável. Se o hash esperado vier da mesma fonte não confiável que forneceu o arquivo, a comparação não prova a autenticidade do arquivo.

### Armazenamento de senhas

Cada senha deve ser processada com uma função própria para senhas, que use salt e permita configurar o custo computacional. Não armazene senhas em texto puro nem use MD5 ou SHA-256 simples para esse fim.

Exemplo conceitual com `bcrypt`:


pythonCopiarimport bcrypt

senha = b"senha-de-exemplo"
hash_salvo = bcrypt.hashpw(senha, bcrypt.gensalt())

senha_valida = bcrypt.checkpw(senha, hash_salvo)
print(senha_valida)



Para sistemas novos, avalie **Argon2id** e siga as recomendações atuais da plataforma utilizada.

### HMAC

HMAC combina uma função de hash com uma chave secreta compartilhada. Pode fornecer **integridade e autenticação entre partes que compartilham a chave**. Não fornece não repúdio, pois qualquer parte que conhece a chave pode gerar um HMAC válido.


pythonCopiarimport hashlib
import hmac

mensagem = b"Dados importantes"
chave = b"substitua-por-uma-chave-aleatoria"

mac_enviado = hmac.new(chave, mensagem, hashlib.sha256).digest()

# No recebimento, calcule novamente sobre a mensagem recebida.
mac_recebido = hmac.new(chave, mensagem, hashlib.sha256).digest()

if hmac.compare_digest(mac_enviado, mac_recebido):
    print("HMAC válido")
else:
    print("HMAC inválido")



Em uma aplicação real, receba a mensagem e o HMAC pelo protocolo, proteja a chave e valide também o contexto da mensagem.

## Assinaturas digitais

Uma assinatura digital ajuda a verificar que os dados foram assinados por alguém que controla a chave privada correspondente e que os dados não foram alterados desde a assinatura. A associação da chave pública à identidade precisa ser validada separadamente, por exemplo, por certificados ou outro mecanismo confiável.

Em termos gerais:

1. O remetente cria uma assinatura usando a chave privada e um algoritmo de assinatura.
2. Envia a mensagem e a assinatura.
3. O destinatário verifica a assinatura usando a chave pública do remetente.
4. A verificação bem-sucedida indica que a assinatura corresponde à mensagem e à chave pública usada.

> Assinatura digital **não é simplesmente “cifrar o hash com a chave privada”**. Use APIs e esquemas de assinatura padronizados, como RSA-PSS, ECDSA ou EdDSA, conforme o contexto.

## Gestão de chaves

### Geração
- Use um gerador de números aleatórios criptograficamente seguro (CSPRNG).
- Use bibliotecas confiáveis para gerar chaves; não escolha chaves “na mão”.
- Escolha o algoritmo e o tamanho de chave conforme padrões atuais e requisitos do sistema.

### Armazenamento e acesso
- Restrinja o acesso às chaves e registre seu uso quando apropriado.
- Considere HSMs, KMSs ou cofres de segredos conforme o risco e o ambiente.
- Não coloque chaves em código-fonte, imagens de contêiner, logs ou repositórios Git.
- Proteja backups e planeje recuperação, revogação e resposta a comprometimento.

### Rotação e ciclo de vida
- Defina rotação conforme risco, política, requisitos legais, tipo de chave e capacidade de recriptografar ou migrar dados.
- Revogue ou substitua chaves comprometidas imediatamente, conforme o plano de resposta.
- Não existe um intervalo universal — por exemplo, “anual” — que seja correto para todas as chaves.

### Destruição
Apagar uma variável em Python não garante que o conteúdo tenha sido removido da memória. Sobrescrever memória diretamente também não é uma garantia geral, devido a cópias, gerenciamento de memória, swap, snapshots e características do hardware.

Para dados cifrados, a destruição controlada das chaves pode ser parte de uma estratégia de descarte, desde que todas as cópias da chave e dos dados sejam consideradas. Use os recursos e procedimentos apropriados à plataforma.

## Protocolos criptográficos

### TLS

TLS protege comunicações entre aplicações, como conexões HTTPS. A segurança depende de versões, algoritmos, configuração e validação correta de certificados.

| Protocolo | Orientação geral |
|---|---|
| **SSL 2.0 / SSL 3.0** | Inseguros; desabilitar |
| **TLS 1.0 / TLS 1.1** | Legados e depreciados; desabilitar quando possível |
| **TLS 1.2** | Pode ser seguro com configuração e conjuntos criptográficos adequados |
| **TLS 1.3** | Versão moderna; preferir quando suportada |

O handshake negocia parâmetros criptográficos e estabelece chaves de sessão. A validação do certificado e do nome do servidor é essencial para reduzir o risco de ataques *man-in-the-middle*.

### SSH

SSH protege sessões remotas e pode autenticar usuários por senha ou por chave pública. Chaves públicas não são secretas; proteja a chave privada, use uma frase-senha quando apropriado e valide a identidade do servidor.


bashCopiar# Gerar uma chave Ed25519
ssh-keygen -t ed25519 -C "seu-email"



### OpenPGP / GPG

OpenPGP pode ser usado para cifrar e assinar arquivos ou mensagens. Verifique cuidadosamente a identidade e a impressão digital (*fingerprint*) da chave pública do destinatário antes de confiar nela.


bashCopiar# Gerar um par de chaves
gpg --full-generate-key

# Cifrar para um destinatário
gpg --encrypt --recipient destinatario@example.com arquivo.txt

# Decifrar
gpg --output arquivo.txt --decrypt arquivo.txt.gpg

# Criar assinatura separada
gpg --armor --detach-sign arquivo.txt

# Verificar assinatura
gpg --verify arquivo.txt.asc arquivo.txt



## Ataques e defesas: visão geral

| Ameaça | Medidas relevantes |
|---|---|
| **Força bruta contra chaves** | Use algoritmos e tamanhos de chave recomendados; proteja credenciais e limite tentativas quando aplicável. |
| **Ataques a senhas** | Use senhas fortes, MFA e armazenamento com funções próprias para senhas, salt e custo adequado. |
| **Rainbow tables** | Use hashes de senha com salt; prefira funções lentas e especializadas. |
| **Man-in-the-middle** | Autentique as partes, valide certificados e configure corretamente os protocolos. |
| **Padding oracle** | Prefira AEAD; não exponha diferenças de erro ou comportamento de decifragem. |
| **Ataques de timing** | Use bibliotecas criptográficas confiáveis e comparações de tempo constante para segredos. |
| **Reutilização de nonce** | Siga as exigências do modo de operação; em AES-GCM, não reutilize nonce com a mesma chave. |
| **Comprometimento de chave** | Restrinja acesso, monitore uso, planeje rotação, revogação e resposta a incidentes. |

## Boas práticas

### Faça
- Use bibliotecas criptográficas reconhecidas e atualizadas.
- Prefira modos autenticados, como AES-GCM ou ChaCha20-Poly1305, quando aplicável.
- Valide certificados e a identidade do interlocutor.
- Separe chaves por finalidade e proteja seu ciclo de vida.
- Use funções próprias para armazenamento de senhas.
- Consulte padrões e orientações atuais para escolher algoritmos e parâmetros.

### Evite
- Criar seu próprio algoritmo ou protocolo criptográfico.
- Usar ECB para cifrar dados de aplicações.
- Reutilizar nonces quando o modo exige unicidade.
- Tratar hash simples como mecanismo de armazenamento de senhas.
- Colocar chaves secretas no código, em logs ou em repositórios.
- Tratar CBC sem autenticação como proteção completa.
- Presumir que criptografia, sozinha, garante autenticidade ou não repúdio.

## Links relacionados

- [[Hash]]
- [[IPSec]]
- [[PKI-Certificados]]
- [[013.1 - Esteganografia]]

> Confira se os nomes das notas vinculadas correspondem aos arquivos existentes no seu vault.

## Referências

- NIST — padrões e publicações de criptografia
- PyCryptodome — documentação da biblioteca
- Python Cryptographic Authority — documentação da biblioteca `cryptography`
- OpenSSL — documentação do projeto
- libsodium — documentação da biblioteca
```