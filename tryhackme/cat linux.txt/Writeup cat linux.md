# Linux Fundamentals Part 1 - Writeup

Room: ![TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/terminaled?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)


Este writeup aborda os conceitos básicos de Linux apresentados na room **Linux Fundamentals Part 1**.
O objetivo é introduzir comandos essenciais, navegação no sistema de arquivos e operadores básicos utilizados no terminal Linux. 

---

# Task 1 - Introduction

A primeira task apenas apresenta a room e explica que o Linux é um dos sistemas operacionais mais utilizados no mundo, principalmente em servidores, infraestrutura e cibersegurança.

## Resposta

```bash
No answer needed
```

---

# Task 2 - A Bit of Background on Linux

Nesta etapa aprendemos um pouco sobre a história do Linux e onde ele é utilizado.

O Linux é amplamente usado em:

* Servidores
* Android
* Supercomputadores
* Infraestrutura corporativa
* Ferramentas de segurança ofensiva e defensiva

A pergunta pede o ano da primeira versão do Linux.

## Pergunta

### What year was the first release of a Linux operating system?

## Resposta

```bash
1991
```

---

# Task 3 - Interacting With Your First Linux Machine

Aqui iniciamos a máquina Linux disponibilizada pelo TryHackMe através do navegador.

O objetivo é apenas acessar a máquina e abrir o terminal interativo. 

## Resposta

```bash
No answer needed
```

---

# Task 4 - Running Your First Few Commands

Nesta task executamos os primeiros comandos básicos do Linux.

## Comando `echo`

O comando `echo` serve para imprimir texto no terminal.

Exemplo:

```bash
echo Tux
```

## Pergunta

### If we wanted to output the text “TryHackMe”, what would our command be?

## Resposta

```bash
echo TryHackMe
```

---

## Comando `whoami`

O comando `whoami` mostra qual usuário está atualmente logado no sistema.

Exemplo:

```bash
whoami
```

## Pergunta

### What is the username of who you're logged in as on your deployed Linux machine?

## Resposta

```bash
tryhackme
```


---

# Task 5 - Interacting With the Filesystem

Agora começamos a navegar pelo sistema de arquivos Linux.

---

## Comando `ls`

Lista arquivos e diretórios.

Exemplo:

```bash
ls
```

---

## Comando `cd`

Utilizado para mudar de diretório.

Exemplo:

```bash
cd folder4
```

---

## Comando `cat`

Exibe o conteúdo de arquivos.

Exemplo:

```bash
cat note.txt
```

---

## Comando `pwd`

Mostra o caminho completo do diretório atual.

Exemplo:

```bash
pwd
```


---

## Pergunta

### On the Linux machine that you deploy, how many folders are there?

## Resposta

```bash
4
```

---

## Pergunta

### Which directory contains a file?

Após navegar entre os diretórios utilizando `cd` e `ls`, identificamos o arquivo dentro de:

## Resposta

```bash
folder4
```

---

## Pergunta

### What is the contents of this file?

Utilizando:

```bash
cat note.txt
```

## Resposta

```bash
Hello World
```

---

## Pergunta

### Use the cd command to navigate to this file and find out the new current working directory. What is the path?

Após entrar no diretório e utilizar `pwd`:

```bash
pwd
```

## Resposta

```bash
/home/tryhackme/folder4
```


---

# Task 6 - Searching for Files

Nesta etapa aprendemos a localizar arquivos utilizando o comando `find`.

## Comando `find`

Exemplo:

```bash
find -name passwords.txt
```

Também podemos procurar arquivos em todo o sistema:

```bash
find / -type f -name access.log 2>/dev/null
```

O `2>/dev/null` serve para ocultar mensagens de erro de permissões.

---

## Pergunta

### Use grep on “access.log” to find the flag that has a prefix of “THM”

Comando utilizado:

```bash
grep "THM" access.log
```

## Resposta

```bash
THM{ACCESS}
```

---

# Task 7 - An Introduction to Shell Operators

Aqui aprendemos alguns operadores importantes do terminal Linux.

---

## Operador `&`

Executa comandos em background.

Exemplo:

```bash
command &
```

---

## Operador `&&`

Executa o segundo comando apenas se o primeiro funcionar corretamente.

Exemplo:

```bash
command1 && command2
```

---

## Operador `>`

Redireciona a saída sobrescrevendo um arquivo.

Exemplo:

```bash
echo hello > file.txt
```

---

## Operador `>>`

Adiciona conteúdo ao arquivo sem sobrescrever.

Exemplo:

```bash
echo world >> file.txt
```


---

# Task 8 - Conclusions & Summaries

Nesta task a room faz um resumo do que foi aprendido:

* Navegação em Linux
* Manipulação de arquivos
* Busca de arquivos
* Uso de operadores shell
* Comandos básicos do terminal

## Resposta

```bash
No answer needed
```

---

# Task 9 - Linux Fundamentals Part 2

A última task apenas direciona para a continuação da trilha Linux Fundamentals.

## Resposta

```bash
No answer needed
```

---

# Conclusão

A room Linux Fundamentals Part 1 é uma excelente introdução ao Linux, principalmente para quem deseja seguir carreira em:

* Cibersegurança
* Pentest
* SOC
* Infraestrutura
* Administração de sistemas


Além disso, a room ensina conceitos fundamentais sobre navegação no terminal e manipulação de arquivos Linux, conhecimentos essenciais para qualquer profissional de segurança da informação. 
