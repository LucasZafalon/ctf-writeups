# HTTP in Detail (Webbed) - Writeup

Room: [TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/web-fund?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **HTTP in Detail** do TryHackMe faz parte da trilha **Webbed** e ensina os fundamentos do protocolo HTTP, principal tecnologia utilizada na comunicação entre navegadores e servidores web.

Nesta room aprendemos:

* HTTP e HTTPS
* Requests e Responses
* Métodos HTTP
* Status Codes
* Headers
* Cookies
* Como funcionam requisições web

Ela é extremamente importante para quem deseja estudar:

* Pentest Web
* Bug Bounty
* Desenvolvimento Web
* APIs
* Segurança de Aplicações


---

# Task 1 - What is HTTP(S)?

Nesta primeira task aprendemos o básico sobre:

* HTTP
* HTTPS

---

# HTTP

HTTP significa:

```bash
HyperText Transfer Protocol
```

É o protocolo responsável pela comunicação entre:

* Navegador
* Servidor Web

Sempre que acessamos um site, estamos utilizando HTTP ou HTTPS.

---

# HTTPS

HTTPS é a versão segura do HTTP.

Ele utiliza:

```bash
TLS/SSL
```

Para criptografar os dados transmitidos.

Isso impede:

* Interceptação de dados
* Roubo de credenciais
* Ataques Man-in-the-Middle


---

## Pergunta

### What does HTTP stand for?

## Resposta

```bash
HyperText Transfer Protocol
```

---

## Pergunta

### What does the S in HTTPS stand for?

## Resposta

```bash
Secure
```

---

## Pergunta

### On the mock webpage on the right there is an issue, once you've found it, click on it. What is the challenge flag?

## Resposta

```bash
THM{INVALID_HTTP_CERT}
```


---

# Task 2 - Requests And Responses

Nesta etapa aprendemos como navegadores e servidores se comunicam.

---

# HTTP Request

Uma requisição HTTP possui:

```http
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Firefox
```

---

# Estrutura de uma URL

Uma URL possui:

* Scheme
* Host
* Porta
* Path
* Query String
* Fragment

Exemplo:

```bash
http://user:password@tryhackme.com:80/view-room?id=1#task3
```

---

# Componentes da URL

| Parte         | Função    |
| ------------- | --------- |
| http          | Protocolo |
| tryhackme.com | Host      |
| 80            | Porta     |
| /view-room    | Caminho   |
| id=1          | Query     |
| #task3        | Fragment  |


---

## Pergunta

### What HTTP protocol is being used in the above example?

## Resposta

```bash
HTTP/1.1
```

---

## Pergunta

### What response header tells the browser how much data to expect?

## Resposta

```bash
Content-Length
```


---

# Task 3 - HTTP Methods

Métodos HTTP definem qual ação queremos executar.

---

# GET

Utilizado para:

```bash
Buscar informações
```

Exemplo:

```http
GET /news HTTP/1.1
```

---

# POST

Utilizado para:

```bash
Enviar dados
```

Exemplo:

* Login
* Cadastro
* Formulários

---

# PUT

Utilizado para:

```bash
Atualizar informações
```

---

# DELETE

Utilizado para:

```bash
Remover dados
```


---

## Pergunta

### What method would be used to create a new user account?

## Resposta

```bash
POST
```

---

## Pergunta

### What method would be used to update your email address?

## Resposta

```bash
PUT
```

---

## Pergunta

### What method would be used to remove a picture you've uploaded to your account?

## Resposta

```bash
DELETE
```

---

## Pergunta

### What method would be used to view a news article?

## Resposta

```bash
GET
```

---

# Task 4 - HTTP Status Codes

Status Codes indicam o resultado de uma requisição HTTP.

---

# Categorias

| Range   | Tipo             |
| ------- | ---------------- |
| 100-199 | Informativo      |
| 200-299 | Sucesso          |
| 300-399 | Redirecionamento |
| 400-499 | Erro do Cliente  |
| 500-599 | Erro do Servidor |

---

# Principais Status Codes

| Código | Significado           |
| ------ | --------------------- |
| 200    | OK                    |
| 201    | Created               |
| 301    | Redirect              |
| 401    | Unauthorized          |
| 403    | Forbidden             |
| 404    | Not Found             |
| 500    | Internal Server Error |


---

## Pergunta

### What response code might you receive if you've created a new user or blog post article?

## Resposta

```bash
201
```

---

## Pergunta

### What response code might you receive if you've tried to access a page that doesn't exist?

## Resposta

```bash
404
```

---

## Pergunta

### What response code might you receive if the web server cannot access its database and the application crashes?

## Resposta

```bash
500
```

---

## Pergunta

### What response code might you receive if you try to edit your profile without logging in first?

## Resposta

```bash
401
```

---

# Task 5 - Headers

Headers carregam informações extras durante requisições HTTP.

---

# Request Headers

Headers enviados pelo cliente.

Exemplo:

```http
User-Agent: Firefox
Host: tryhackme.com
Referer: https://google.com
```

---

# Response Headers

Headers enviados pelo servidor.

Exemplo:

```http
Content-Type: text/html
Set-Cookie: session=abc123
```

---

# Headers Importantes

| Header       | Função              |
| ------------ | ------------------- |
| Host         | Define o host       |
| User-Agent   | Navegador utilizado |
| Content-Type | Tipo do conteúdo    |
| Set-Cookie   | Define cookies      |
| Referer      | Página anterior     |


---

## Pergunta

### What header tells the web server what browser is being used?

## Resposta

```bash
User-Agent
```

---

## Pergunta

### What header tells the browser what type of data is being returned?

## Resposta

```bash
Content-Type
```

---

## Pergunta

### What header tells the web server which website is being requested?

## Resposta

```bash
Host
```

---

# Task 6 - Cookies

Cookies armazenam pequenas informações no navegador.

Eles ajudam em:

* Sessões
* Login
* Preferências
* Rastreamento

---

# Funcionamento

Servidor envia:

```http
Set-Cookie: session=abc123
```

O navegador salva o cookie e envia novamente nas próximas requisições.

---

# Exemplos de uso

* Permanecer logado
* Carrinho de compras
* Sessões autenticadas


---

## Pergunta

### Which header is used to save cookies to your computer?

## Resposta

```bash
Set-Cookie
```

---

# Task 7 - Making Requests

Nesta task utilizamos um simulador HTTP para criar requisições manualmente.

---

## Pergunta

### Make a GET request to /room page

## Resposta

```bash
THM{YOU'RE_IN_THE_ROOM}
```

---

## Pergunta

### Make a GET request to /blog page and set the id parameter to 1

## Resposta

```bash
THM{YOU_FOUND_THE_BLOG}
```

---

## Pergunta

### Make a DELETE request to /user/1 page

## Resposta

```bash
THM{USER_IS_DELETED}
```

---

## Pergunta

### Make a PUT request to /user/2 page with the username parameter set to admin

## Resposta

```bash
THM{USER_HAS_UPDATED}
```

---

## Pergunta

### Make a POST request to /login page with the username of thm and a password of letmein

## Resposta

```bash
THM{HTTP_REQUEST_MASTER}
```


---

# Ferramentas Relacionadas

Durante testes web utilizamos bastante:

```bash
curl
Burp Suite
Postman
ffuf
Gobuster
Nikto
```

---

# Comandos Úteis

## Fazer requisição GET

```bash
curl http://site.com
```

## Ver headers

```bash
curl -I http://site.com
```

## Fazer POST

```bash
curl -X POST http://site.com
```

## Adicionar header

```bash
curl -H "User-Agent: Firefox"
```

---

# Fluxo HTTP

```bash
Browser
   ↓
HTTP Request
   ↓
Web Server
   ↓
HTTP Response
   ↓
Browser Renderiza
```

---

# Conceitos Importantes

## HTTP é Stateless

HTTP não lembra requisições anteriores.

Por isso usamos:

```bash
Cookies
Sessions
Tokens
```

---

# HTTPS e Segurança

HTTPS protege:

* Credenciais
* Sessões
* Dados sensíveis

Sem HTTPS:

* Dados podem ser interceptados
* Cookies podem ser roubados
* Sessões podem ser sequestradas


---

# Importância no Pentest

Entender HTTP é essencial para:

* Web Hacking
* Bug Bounty
* APIs
* Burp Suite
* Exploração Web

Grande parte das vulnerabilidades web envolve:

* Requests
* Headers
* Cookies
* Métodos HTTP
* Sessões

---

# Conclusão

A room HTTP in Detail é uma das bases mais importantes para qualquer pessoa estudando:

* Segurança Web
* Pentest
* Desenvolvimento Web
* APIs
* Bug Bounty

Ela ensina o funcionamento interno do protocolo HTTP e ajuda bastante a entender como aplicações web realmente funcionam.

