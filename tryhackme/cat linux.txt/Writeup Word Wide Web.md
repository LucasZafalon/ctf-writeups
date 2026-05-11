# World Wide Web - Writeup

Room: [TryHackMe -Badge](https://tryhackme.com/Lucas.Zafalon/badges/world-wide-web?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **Putting It All Together** do TryHackMe reúne diversos conceitos fundamentais sobre aplicações web e infraestrutura utilizados ao navegar na internet.

Nesta room aprendemos:

* Funcionamento de websites
* DNS
* Load Balancers
* CDN
* WAF
* Web Servers
* Conteúdo estático e dinâmico
* Linguagens backend
* Componentes da infraestrutura web

Ela funciona como um resumo prático do módulo inicial de Web Fundamentals.

---

# Task 1 - Putting It All Together

A primeira task faz um resumo do fluxo completo de funcionamento da web.

Quando acessamos um site:

1. O DNS resolve o domínio para um IP
2. O navegador estabelece conexão TCP/IP
3. O servidor responde utilizando HTTP/HTTPS
4. O navegador renderiza:

   * HTML
   * CSS
   * JavaScript
   * Imagens
   * Outros recursos


---

## Pergunta

### I've read the previous tasks

## Resposta

```bash
No answer needed
```

---

# Task 2 - Other Components

Nesta etapa aprendemos componentes importantes da infraestrutura web moderna.

---

# Load Balancer

O:

```bash
Load Balancer
```

Distribui tráfego entre múltiplos servidores.

Objetivos:

* Alta disponibilidade
* Escalabilidade
* Balanceamento de carga
* Redundância

Sem Load Balancer:

* Um único servidor pode sobrecarregar

Com Load Balancer:

* O tráfego é dividido entre vários servidores


---

# CDN (Content Delivery Network)

Uma:

```bash
CDN
```

Armazena conteúdo em servidores distribuídos geograficamente.

Benefícios:

* Menor latência
* Melhor performance
* Menor carga no servidor principal
* Proteção contra DDoS

Exemplos:

* Cloudflare
* Akamai
* Fastly

---

# Databases

Os bancos de dados armazenam:

* Usuários
* Senhas
* Posts
* Produtos
* Sessões
* Informações da aplicação

Exemplos:

```bash
MySQL
PostgreSQL
MongoDB
MariaDB
```

---

# WAF (Web Application Firewall)

O:

```bash
WAF
```

Filtra requisições maliciosas antes que elas cheguem à aplicação.

Ele ajuda a bloquear:

* SQL Injection
* XSS
* Path Traversal
* Bots
* Explorações automatizadas


---

## Pergunta

### What does WAF stand for?

## Resposta

```bash
Web Application Firewall
```

---

## Pergunta

### What type of server caches static content to save bandwidth?

## Resposta

```bash
CDN
```

---

## Pergunta

### What allows servers to handle more traffic by spreading load?

## Resposta

```bash
Load Balancer
```

---

# Task 3 - How Web Servers Work

Agora aprendemos como servidores web funcionam.

---

# Web Server

Um:

```bash
Web Server
```

É responsável por:

* Receber requisições HTTP
* Processar respostas
* Servir conteúdo aos clientes

Exemplos:

```bash
Apache
Nginx
IIS
```

---

# Virtual Hosts

Virtual Hosts permitem:

* Hospedar múltiplos sites
* Utilizar o mesmo servidor/IP
* Separar domínios diferentes

Exemplo:

```bash
site1.com
site2.com
```

Ambos podem utilizar o mesmo servidor físico.

---

# Conteúdo Estático

Conteúdo estático:

* Não muda dinamicamente
* Mesmo conteúdo para todos

Exemplos:

```bash
HTML
CSS
Imagens
JS
```

---

# Conteúdo Dinâmico

Conteúdo dinâmico:

* Gerado em tempo real
* Depende do usuário ou banco de dados

Exemplos:

* Painéis
* Login
* Feed de redes sociais
* Carrinhos de compra

---

# Backend Languages

Linguagens backend processam:

* Lógica da aplicação
* Banco de dados
* Sessões
* Autenticação

Exemplos:

```bash
PHP
Python
NodeJS
Java
```


---

## Pergunta

### What does web servers host?

## Resposta

```bash
websites
```

---

## Pergunta

### What server-side language is used to make pages dynamic?

## Resposta

```bash
PHP
```

---

## Pergunta

### What type of content cannot interact with databases?

## Resposta

```bash
Static
```

---

# Task 4 - Quiz

A última etapa reúne os conceitos aprendidos durante a room.

A questão final normalmente envolve:

* Infraestrutura web
* Fluxo de websites
* Componentes da arquitetura

---

## Pergunta

### What code is used for a successful HTTP response?

## Resposta

```bash
200
```

---

# Conceitos Importantes

---

# Fluxo da Web

```bash
Usuário
   ↓
DNS
   ↓
Load Balancer
   ↓
WAF
   ↓
Web Server
   ↓
Aplicação
   ↓
Banco de Dados
```

---

# HTTP Status Codes

| Código | Significado           |
| ------ | --------------------- |
| 200    | OK                    |
| 301    | Redirect              |
| 403    | Forbidden             |
| 404    | Not Found             |
| 500    | Internal Server Error |

---

# DNS

DNS converte:

```bash
google.com
```

Em:

```bash
142.250.x.x
```

Sem DNS precisaríamos decorar IPs.

---

# Diferença entre Front-end e Back-end

| Front-end  | Back-end       |
| ---------- | -------------- |
| HTML       | PHP            |
| CSS        | Python         |
| JavaScript | NodeJS         |
| Interface  | Banco de Dados |

---

# Conceitos de Segurança

A room também introduz:

* Segurança em aplicações web
* Firewalls
* Infraestrutura segura
* Camadas defensivas

Esses conceitos são extremamente importantes para:

* Pentest
* Bug Bounty
* Web Hacking
* DevSecOps
* Blue Team

---

# Ferramentas Relacionadas

Durante estudos web normalmente utilizamos:

```bash
Burp Suite
Nmap
Gobuster
Nikto
ffuf
curl
```

---

# Comandos Úteis

## Testar HTTP

```bash
curl http://site.com
```

## Ver headers

```bash
curl -I http://site.com
```

## Resolver DNS

```bash
nslookup google.com
```

## Enumerar diretórios

```bash
gobuster dir -u http://site.com -w wordlist.txt
```

---

# Fluxo da Room

```bash
Cliente
    ↓
DNS resolve domínio
    ↓
HTTP Request
    ↓
Load Balancer
    ↓
WAF
    ↓
Web Server
    ↓
Backend
    ↓
Database
    ↓
HTTP Response
```

---

# Conclusão

A room World Wide Web / Putting It All Together é excelente para criar uma base sólida sobre:

* Funcionamento da internet
* Infraestrutura web
* Componentes de aplicações
* HTTP
* Segurança web

Ela ajuda bastante quem deseja seguir áreas como:

* Pentest Web
* Bug Bounty
* DevOps
* Cloud
* Engenharia de Segurança
* Desenvolvimento Web Seguro

Além disso, entender essa arquitetura é essencial antes de começar estudos avançados em exploração web e segurança ofensiva. ([Electronics Reference][1])

