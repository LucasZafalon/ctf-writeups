# Crack The Hash - Writeup

Room: [TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/hash-cracker?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **Crack The Hash** do TryHackMe é focada em identificação e quebra de hashes utilizando ferramentas como:

* Hashcat
* John The Ripper
* CrackStation
* Hash Identifier

Nesta room aprendemos:

* Identificar tipos de hash
* Utilizar wordlists
* Quebrar hashes com Hashcat
* Diferença entre hashes simples e salted hashes
* Modos do Hashcat


---

# Ferramentas Utilizadas

## Hashcat

Ferramenta extremamente utilizada para quebra de hashes.

Instalação:

```bash
sudo apt install hashcat
```

---

## Hash Identifier

Ferramenta para identificar o tipo do hash.

```bash
hashid <hash>
```

---

## CrackStation

Site utilizado para consultar hashes já quebrados em bases públicas.

[CrackStation](https://crackstation.net/)

---

# Task 1 - Level 1

Nesta etapa quebramos hashes simples utilizando:

* CrackStation
* Hashcat
* Hash Identifier

---

# Hash 1

## Hash

```bash
48bb6e862e54f2a795ffc4e541caed4d
```

Identificado como:

```bash
MD5
```

Comando:

```bash
hashcat -m 0 hash.txt rockyou.txt
```

## Resposta

```bash
easy
```


---

# Hash 2

## Hash

```bash
CBFDAC6008F9CAB4083784CBD1874F76618D2A97
```

Tipo:

```bash
SHA1
```

Comando:

```bash
hashcat -m 100 hash.txt rockyou.txt
```

## Resposta

```bash
password123
```


---

# Hash 3

## Hash

```bash
1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032
```

Tipo:

```bash
SHA256
```

Comando:

```bash
hashcat -m 1400 hash.txt rockyou.txt
```

## Resposta

```bash
letmein
```


---

# Hash 4

## Hash

```bash
$2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom
```

Tipo:

```bash
bcrypt
```

Comando:

```bash
hashcat -m 3200 hash.txt rockyou.txt
```

## Resposta

```bash
bleh
```


---

# Hash 5

## Hash

```bash
279412f945939ba78ce0758d3fd83daa
```

Tipo:

```bash
MD4
```

Comando:

```bash
hashcat -m 900 hash.txt rockyou.txt
```

## Resposta

```bash
Eternity22
```


---

# Task 2 - Level 2

Agora os hashes possuem maior dificuldade e alguns utilizam:

* Salt
* Algoritmos mais fortes
* Wordlists maiores

A própria room recomenda utilizar:

```bash
rockyou.txt
```

---

# Localizando a Wordlist

No Kali Linux:

```bash
/usr/share/wordlists/rockyou.txt
```

Caso esteja compactada:

```bash
sudo gzip -d /usr/share/wordlists/rockyou.txt.gz
```

---

# Hash 6

## Hash

```bash
F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85
```

Tipo:

```bash
SHA256
```

Comando:

```bash
hashcat -m 1400 hash.txt rockyou.txt
```

## Resposta

```bash
paule
```


---

# Hash 7

## Hash

```bash
1DFECA0C002AE40B8619ECF94819CC1B
```

Tipo:

```bash
NTLM
```

Comando:

```bash
hashcat -m 1000 hash.txt rockyou.txt
```

## Resposta

```bash
n63umy8lkf4i
```


---

# Hash 8

## Hash

```bash
$6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.
```

Tipo:

```bash
SHA512CRYPT
```

Comando:

```bash
hashcat -m 1800 hash.txt rockyou.txt
```

## Resposta

```bash
waka99
```


---

# Hash 9

## Hash

```bash
e5d8870e5bdd26602cab8dbe07a942c8669e56d6
```

Salt:

```bash
tryhackme
```

Tipo:

```bash
SHA1 + Salt
```

Formato do arquivo:

```bash
hash:salt
```

Exemplo:

```bash
e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme
```

Comando:

```bash
hashcat -m 120 hash.txt rockyou.txt
```

## Resposta

```bash
481616481616
```


---

# Identificando Hashes

Uma das partes mais importantes da room é aprender a identificar hashes.

Ferramentas úteis:

```bash
hashid
hash-identifier
haiti
```

Exemplo:

```bash
hashid 48bb6e862e54f2a795ffc4e541caed4d
```


---

# Modos do Hashcat Utilizados

| Algoritmo   | Mode |
| ----------- | ---- |
| MD5         | 0    |
| SHA1        | 100  |
| SHA256      | 1400 |
| bcrypt      | 3200 |
| NTLM        | 1000 |
| SHA512CRYPT | 1800 |

---

# Comandos Utilizados

## Quebrar MD5

```bash
hashcat -m 0 hash.txt rockyou.txt
```

## Quebrar SHA1

```bash
hashcat -m 100 hash.txt rockyou.txt
```

## Quebrar SHA256

```bash
hashcat -m 1400 hash.txt rockyou.txt
```

## Quebrar bcrypt

```bash
hashcat -m 3200 hash.txt rockyou.txt
```

## Quebrar NTLM

```bash
hashcat -m 1000 hash.txt rockyou.txt
```

---

# Dicas Importantes

## Se o Hashcat não funcionar

Verifique:

* Formato do hash
* Mode correto
* Wordlist
* Salt
* Espaços extras no arquivo

Muitos usuários relatam problemas de formatação ao utilizar Hashcat.

---

# Conceitos Aprendidos

## Hash != Criptografia

Hash:

* É unidirecional
* Não é feito para ser revertido
* Utilizado para armazenamento seguro

A quebra ocorre por:

* Wordlists
* Rainbow Tables
* Brute Force

---

## Salt

Salt adiciona dados extras ao hash:

```bash
hash(password + salt)
```

Isso dificulta ataques utilizando bases prontas.

---

# Fluxo da Room

```bash
Identificar hash
        ↓
Selecionar mode do Hashcat
        ↓
Escolher wordlist
        ↓
Executar ataque
        ↓
Encontrar senha
```

---

# Conclusão

A room Crack The Hash é excelente para aprender:

* Conceitos básicos de cracking
* Uso do Hashcat
* Tipos de hashes
* Wordlists
* Salted hashes

Ela também ajuda a entender:

* A importância de senhas fortes
* O impacto de hashes sem salt
* O perigo de reutilização de senhas

