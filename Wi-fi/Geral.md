## 1. Sistemas usados em auditoria Wi‑Fi

- **Kali Linux**
- **Parrot Security OS**
- **BlackArch Linux**

### Ideia principal

- Essas distribuições concentram ferramentas de rede e segurança.
- O mais importante não é só a distro, mas o **suporte do driver/chipset** do adaptador Wi‑Fi.

---

## 2. Roteador x adaptador

- **Roteador**
    
    - É o ponto de acesso da rede.
    - Gerencia SSID, canal, autenticação e tráfego.
- **Adaptador Wi‑Fi**
    
    - É a interface do computador para se conectar e monitorar redes.
    - Para análise de segurança, idealmente precisa suportar:
    - **modo monitor**
    - **injeção de pacotes**
    - bandas **2.4 GHz** e **5 GHz**

### Exemplo citado

- **Alfa AWUS036ACHM**
    - Citado como adaptador usado em auditoria por sua compatibilidade.

---

## 3. dBm e dBi

- **dBm**
    
    - Mede **potência do sinal**.
    - Relacionado ao nível de transmissão/recepção.
- **dBi**
    
    - Mede o **ganho da antena**.
    - Quanto maior o ganho, maior a capacidade de ampliar alcance em certas condições.

### Observação importante

- O alcance real depende também de:
    - frequência
    - obstáculos
    - interferência
    - distância
    - clima
    - qualidade do chipset e da antena

---

## 4. Ferramentas de diagnóstico e reconhecimento

### Ferramentas citadas

- `ifconfig` / `ip`
- `iwconfig` / `iw`
- `iwlist`
- `lsusb`

### Para que servem

- **Identificar interfaces de rede**
- **Ver informações da placa Wi‑Fi**
- **Listar canais e frequências**
- **Verificar chipset**
- **Confirmar se a interface está ativa**

### Ideia prática

- Em auditoria, o primeiro passo costuma ser entender:
    - qual é a interface Wi‑Fi
    - qual chipset ela usa
    - quais canais e frequências ela suporta
    - se ela consegue entrar em modo monitor

---

## 5. Modo monitor

- É o modo em que a placa captura quadros 802.11 do ar.
- Diferente de um uso normal conectado à rede.
- É essencial para análise de tráfego e reconhecimento.

### Relacionado ao monitoramento

- Captura de beacon frames
- Observação de SSID, canal e BSSID
- Acompanhamento de tráfego ao redor

### Ferramentas associadas

- `tcpdump`
- `tshark`
- ferramentas de análise de pacotes

---

## 6. Técnicas de defesa ineficientes

### Esconder SSID

- **Não é proteção real**.
- A rede ainda pode ser detectada por tráfego e comportamento dos clientes.

### Filtro de MAC

- **Também não é uma defesa forte**.
- MAC pode ser copiado ou alterado em ambientes compatíveis.
- Serve mais como controle básico do que como segurança robusta.

### Resumo

- Essas medidas ajudam pouco contra um atacante real.
- Segurança de Wi‑Fi deve depender de:
    - criptografia forte
    - senha forte
    - desativação de recursos inseguros
    - boa configuração do roteador

---

## 7. Captive Portal

- É a tela que aparece antes do acesso total à internet.
- Muito usada em redes públicas ou controladas.

### Componentes comuns

- **IP**
- **DNS resolver**
- **rota padrão**
- **servidor web**

### Risco associado

- Pode ser usado de forma legítima, mas também pode ser **imitado em ataques de engenharia social**.
- Em testes autorizados, analisa-se se o portal realmente protege o acesso ou apenas redireciona a navegação.

---

## 8. Evil Twin e Evil Portal

### Evil Twin

- Rede falsa que tenta se passar por um ponto de acesso legítimo.
- Explora o fato de que dispositivos podem preferir:
    - sinal mais forte
    - nome conhecido
    - conexão automática

### Evil Portal

- Variante focada em reproduzir uma página de login/captive portal.
- Objetivo: induzir o usuário a interagir com uma página falsa.

### Defesa

- Desativar conexão automática com redes abertas
- Usar redes com autenticação forte
- Educar usuários para checar SSID e certificados
- Preferir WPA2‑Enterprise / WPA3 quando possível

---

## 9. Ataques de oportunidade

- São ataques que aproveitam características do ambiente.
- Exemplos conceituais:
    - redes com nomes comuns
    - dispositivos que se reconectam automaticamente
    - redes abertas ou mal configuradas
    - usuários que aceitam qualquer página de login

### Tema ligado

- **WarDriving**
    - reconhecimento de redes Wi‑Fi em deslocamento
    - usado para mapear SSID, posição e cobertura

---

## 10. MAC e OUI

- **MAC**
    
    - Endereço físico da interface.
- **OUI**
    
    - Prefixo que identifica o fabricante do equipamento.

### Uso

- Ajuda a identificar fabricante da placa ou roteador.
- Útil em inventário, diagnóstico e análise de segurança.

---

## 11. Ataques clássicos em Wi‑Fi

> Aqui o ponto importante é entender o **risco**, não operar o ataque.

### WPS

- O **WPS** facilita a conexão, mas historicamente foi alvo de muitas falhas.
- O problema principal é o **PIN de 8 dígitos** e a possibilidade de abuso em redes mal configuradas.

### WEP

- Criptografia antiga e **insegura**.
- Deve ser evitada totalmente.

### WPA/WPA2 PSK

- Mais seguro que WEP, mas depende de:
    - senha forte
    - configuração correta
    - captura de handshake em auditorias autorizadas
- Senhas fracas continuam sendo o grande problema.

### Defesa recomendada

- Desativar WPS
- Usar WPA2 forte ou WPA3
- Senhas longas e únicas
- Atualizar firmware do roteador

---

## 12. Reconhecimento e análise de WPA/WPS

### Ferramentas citadas no material

- Kismet
- Airodump-ng
- Bettercap
- Hcxdumptool

### Função geral

- Descobrir redes, canais, clientes e parâmetros de segurança.
- Em contexto autorizado, ajudam a validar:
    - se o WPS está ativo
    - se o WPA está configurado corretamente
    - se há clientes vulneráveis a reconexões indevidas

---

## 13. GREP no contexto de análise

- `grep` é útil para filtrar saídas de comandos e logs.

### Opções citadas

- `-v` → remove linhas que contêm o padrão
- `-i` → ignora maiúsculas/minúsculas
- `-A` → mostra linhas abaixo
- `-B` → mostra linhas acima

### Uso prático

- Filtragem de inventário de redes
- Busca em logs
- Extração de informações relevantes

---

## 14. Wordlists e referências

- **Wordlists**
    
    - listas de palavras usadas em testes de força bruta e validações autorizadas
    - muito comuns em auditoria de senhas e credenciais
- **Wireless Security Database**
    
    - base de consulta sobre equipamentos e segurança Wi‑Fi
- **OUI IEEE**
    
    - base para identificar fabricantes de MAC