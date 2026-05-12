# Advent of Cyber ’23 - Side Quest Writeup

Room: [TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/aoc5sidequest2?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **Advent of Cyber ’23 Side Quest** do TryHackMe é uma missão especial baseada em investigação, enumeração e exploração de arquivos escondidos relacionados ao universo do Advent of Cyber 2023.

Nesta room trabalhamos:

* Enumeração web
* Descoberta de arquivos ocultos
* Análise de código
* Investigação de endpoints
* Decodificação
* Coleta de flags

A room possui uma pegada de investigação narrativa, exigindo atenção aos detalhes e análise manual.

---

# Task 1 - Start The Side Quest

Ao iniciar a room recebemos acesso a uma aplicação web temática do Advent of Cyber.

O primeiro passo é realizar reconhecimento inicial:

* Navegação manual
* Análise de source code
* Enumeração de diretórios
* Identificação de endpoints escondidos

---

# Reconhecimento Inicial

Ferramentas utilizadas:

```bash
Gobuster
ffuf
curl
Burp Suite
```

---

# Enumeração de Diretórios

Utilizamos:

```bash
gobuster dir -u http://<IP> -w /usr/share/wordlists/dirb/common.txt
```

Durante a enumeração encontramos diretórios importantes relacionados à side quest.


---

# Análise do Código-Fonte

Visualizando o source code:

```bash
CTRL + U
```

Ou:

```bash
view-source:http://<IP>
```

Encontramos comentários e referências escondidas utilizadas como pistas.

---

# Investigando Arquivos

Durante a exploração identificamos arquivos ocultos contendo:

* Mensagens codificadas
* Pistas
* Endpoints internos
* Informações relacionadas ao enredo

Ferramentas úteis:

```bash
curl
wget
strings
file
```

---

# Decodificação

Parte da room exige decodificar conteúdos encontrados.

Exemplos comuns:

* Base64
* Hex
* ROT13

---

## Base64

Exemplo:

```bash
echo "VEhNe0ZMQUd9" | base64 -d
```

Saída:

```bash
THM{FLAG}
```

---

# Enumeração Avançada

Também utilizamos fuzzing para encontrar rotas escondidas:

```bash
ffuf -u http://<IP>/FUZZ -w /usr/share/wordlists/dirb/common.txt
```

Isso permitiu descobrir:

* Arquivos administrativos
* APIs ocultas
* Páginas não indexadas


---

# Investigação Narrativa

A Side Quest mistura:

* Storytelling
* Enumeração técnica
* Desafios investigativos

Por isso é importante:

* Ler mensagens cuidadosamente
* Correlacionar pistas
* Analisar arquivos encontrados
* Explorar comportamentos da aplicação

---

# Ferramentas Utilizadas

## Gobuster

```bash
gobuster dir -u http://<IP> -w common.txt
```

---

## ffuf

```bash
ffuf -u http://<IP>/FUZZ -w common.txt
```

---

## curl

```bash
curl http://<IP>
```

---

## strings

```bash
strings arquivo.txt
```

---

## file

```bash
file arquivo.bin
```

---

# Técnicas Aprendidas

Durante a room trabalhamos:

* Web Enumeration
* OSINT leve
* Source Code Review
* Fuzzing
* Decoding
* Investigação Web
* Reconhecimento Manual

---

# Conceitos Importantes

---

# Fuzzing

Fuzzing consiste em:

* Automatizar descoberta de conteúdo
* Encontrar endpoints ocultos
* Descobrir arquivos esquecidos

Ferramentas comuns:

```bash
Gobuster
ffuf
Dirsearch
Feroxbuster
```

---

# Source Code Review

Muitas aplicações deixam:

* Comentários
* Credenciais
* Endpoints
* Chaves
* TODOs

Escondidos no código-fonte.

Sempre analise:

```bash
CTRL + U
```

---

# Encoding vs Encryption

## Encoding

Transforma formato dos dados:

```bash
Base64
Hex
URL Encode
```

## Encryption

Protege dados utilizando:

* Chaves
* Algoritmos criptográficos

---

# Fluxo da Room

```bash
Reconhecimento
      ↓
Enumeração
      ↓
Descoberta de endpoints
      ↓
Análise de arquivos
      ↓
Decodificação
      ↓
Flags
```

---

# Comandos Utilizados

## Enumeração

```bash
gobuster dir -u http://<IP> -w common.txt
```

## Fuzzing

```bash
ffuf -u http://<IP>/FUZZ -w common.txt
```

## Visualizar source code

```bash
CTRL + U
```

## Decodificar Base64

```bash
echo "<base64>" | base64 -d
```

## Identificar arquivo

```bash
file arquivo
```

---

# Dicas Importantes

Durante desafios web:

* Sempre analise headers
* Verifique source code
* Procure arquivos ocultos
* Teste encoding
* Faça enumeração manual e automatizada
* Observe mensagens da aplicação

---

# Conceitos Relacionados à Cibersegurança

A room ajuda bastante em:

* Pentest Web
* Bug Bounty
* CTFs
* Reconhecimento Web
* Investigação de aplicações

Muitos conceitos utilizados em CTFs aparecem também em ambientes reais.

---

# Conclusão

A Advent of Cyber ’23 Side Quest é uma room muito interessante para praticar:

* Enumeração
* Investigação web
* Descoberta de conteúdo oculto
* Fuzzing
* Decodificação

Ela mistura narrativa com desafios técnicos e reforça a importância da observação durante testes de segurança.

Além disso, demonstra como pequenas pistas podem levar à descoberta de informações críticas dentro de aplicações web.
