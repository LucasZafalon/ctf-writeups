# OhSINT - Writeup

Room: ![TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/ohsint?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **OhSINT** do TryHackMe é uma introdução prática ao mundo de **OSINT (Open Source Intelligence)**, onde utilizamos apenas informações públicas para investigar um alvo.

Nesta room aprendemos:

* Extração de metadados
* Investigação em redes sociais
* Enumeração em GitHub
* Pesquisa de Wi-Fi/BSSID
* Análise de código-fonte
* Correlação de informações públicas


---

# Task 1 - OhSINT

Ao iniciar a room, recebemos apenas uma imagem:

```bash
WindowsXP.jpg
```

O desafio consiste em utilizar técnicas de OSINT para responder todas as perguntas utilizando somente informações públicas.

---

# Análise Inicial da Imagem

A primeira etapa é analisar a imagem recebida.

Podemos visualizar a imagem com:

```bash
xdg-open WindowsXP.jpg
```

A imagem é o clássico wallpaper do Windows XP.

---

# Verificando Metadados

Utilizamos o `exiftool` para extrair metadados da imagem:

```bash
exiftool WindowsXP.jpg
```

Nos metadados encontramos:

```bash
Copyright : OWoodflint
```

Esse nome será o ponto inicial da investigação.


---

# Pesquisando o Usuário

Ao pesquisar por:

```bash
OWoodflint
```

Encontramos:

* Perfil no Twitter/X
* GitHub
* Blog WordPress

---

# Pergunta 1

## What is this user's avatar of?

Ao acessar o perfil do usuário no Twitter/X, observamos que o avatar é um gato.

## Resposta

```bash
cat
```


---

# Pergunta 2

## What city is this person in?

No GitHub do usuário encontramos informações indicando que ele mora em:

## Resposta

```bash
London
```

Também é possível descobrir utilizando o BSSID encontrado no Twitter e consultando no WiGLE.


---

# Pergunta 3

## What is the SSID of the WAP he connected to?

No Twitter/X encontramos o seguinte BSSID:

```bash
B4:5D:50:AA:86:41
```

Com ele, acessamos o site:

```bash
wigle.net
```

Pesquisando o BSSID, encontramos o nome da rede Wi-Fi.

## Resposta

```bash
UnileverWiFi
```


---

# Pergunta 4

## What is his personal email address?

No GitHub do usuário encontramos o email pessoal:

## Resposta

```bash
OWoodflint@gmail.com
```


---

# Pergunta 5

## What site did you find his email address on?

O email foi encontrado no GitHub.

## Resposta

```bash
Github
```


---

# Pergunta 6

## Where has he gone on holiday?

No blog WordPress do usuário encontramos uma postagem falando sobre férias em:

## Resposta

```bash
New York
```


---

# Pergunta 7

## What is the person's password?

A última questão exige análise mais detalhada.

Após verificar:

* Twitter
* GitHub
* Blog

A senha é encontrada no código-fonte da página WordPress.

Podemos visualizar o source code utilizando:

```bash
CTRL + U
```

Ou:

```bash
view-source:<URL>
```

No código-fonte encontramos:

## Resposta

```bash
pennYDr0pper.!
```


---

# Ferramentas Utilizadas

Durante a room utilizamos:

* Google Dorking
* Exiftool
* GitHub
* Twitter/X
* WordPress
* WiGLE
* Análise de código-fonte

---

# Comandos Utilizados

## Exibir imagem

```bash
xdg-open WindowsXP.jpg
```

## Extrair metadados

```bash
exiftool WindowsXP.jpg
```

## Ver código-fonte

```bash
CTRL + U
```

---

# Conceitos Aprendidos

## OSINT

OSINT significa:

```bash
Open Source Intelligence
```

Consiste em coletar informações públicas disponíveis na internet para investigação.

---

## EXIF Metadata

Metadados EXIF podem conter:

* Autor
* Modelo da câmera
* GPS
* Data
* Software utilizado

Por isso, sempre é importante analisar arquivos enviados por usuários.

---

# Dicas Importantes

Durante desafios OSINT:

* Analise metadados
* Pesquise usernames
* Verifique redes sociais
* Analise código-fonte
* Correlacione informações
* Use Google Dorks
* Consulte bancos de dados públicos

---

# Fluxo da Investigação

```bash
Imagem
   ↓
Metadados (Exiftool)
   ↓
Username encontrado
   ↓
Twitter/GitHub/Blog
   ↓
Correlação de informações
   ↓
Respostas
```

---

# Conclusão

A room OhSINT é uma excelente introdução ao mundo de:

* OSINT
* Reconhecimento passivo
* Investigação digital
* Correlação de dados públicos

Ela demonstra como pequenas informações públicas podem ser correlacionadas para revelar dados sensíveis de um alvo.

Além disso, mostra a importância de:

* Higiene digital
* Privacidade online
* Cuidados com exposição pública
* Segurança em redes sociais

