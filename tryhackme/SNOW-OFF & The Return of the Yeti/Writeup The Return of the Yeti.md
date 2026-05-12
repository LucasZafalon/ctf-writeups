# TryHackMe — Advent of Cyber ’23 Side Quest 1: The Return of the Yeti (Writeup em Português)

Room: [TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/aoc5sidequest1?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **The Return of the Yeti** é uma Side Quest do evento Advent of Cyber 2023 do TryHackMe.
O desafio envolve análise forense simples, enumeração web, investigação de arquivos e descoberta de informações escondidas dentro de uma aplicação temática do Yeti.

---

# Informações da Sala

* **Nome:** The Return of the Yeti
* **Categoria:** Advent of Cyber ’23 Side Quest 1
* **Dificuldade:** Hard
* **Objetivo:** Analisar um arquivo `.pcapng` e recuperar informações utilizadas pelo Yeti para obter acesso à infraestrutura da empresa.

---

# Arquivos Necessários

Baixe os arquivos fornecidos pela sala e extraia o conteúdo:

```bash
unzip sidequest.zip
```

O principal arquivo utilizado será:

```bash
VanSpy.pcapng
```

---

# Análise Inicial no Wireshark

Abra o arquivo:

```bash
wireshark VanSpy.pcapng
```

Logo no início percebemos que o tráfego está criptografado, porém algumas informações ainda são visíveis.

Entre elas:

* Protocolo: `802.11`
* SSID da rede Wi-Fi:

```text
FreeWifiBFC
```

---

# Pergunta 1

## Qual é o SSID da rede Wi-Fi?

Resposta:

```text
FreeWifiBFC
```

---

# Descobrindo a Senha da Rede Wi-Fi

Durante a análise dos pacotes, foi identificado um handshake WPA.

O writeup utiliza o `aircrack-ng` junto da wordlist `rockyou.txt`.

Comando utilizado:

```bash
aircrack-ng VanSpy.pcapng -w /usr/share/wordlists/rockyou.txt
```

Após alguns instantes a senha é encontrada:

```text
Hallow3nDay
```

---

# Pergunta 2

## Qual é a senha da rede?

Resposta:

```text
Hallow3nDay
```

---

# Descriptografando o Tráfego no Wireshark

Agora precisamos descriptografar os pacotes.

No Wireshark:

```text
Edit → Preferences → Protocols → IEEE 802.11
```

Ative:

```text
Enable decryption
```

Depois adicione a chave:

```text
wpa-pwd:Hallow3nDay:FreeWifiBFC
```

Após isso o tráfego descriptografado ficará visível.

---

# Encontrando Credenciais

Aplicando filtros HTTP e analisando os pacotes, encontramos credenciais utilizadas no ambiente.

As credenciais identificadas foram:

```text
Username: administrator
Password: Christmas2023!
```

---

# Pergunta 3

## Qual é a senha do usuário Administrator?

Resposta:

```text
Christmas2023!
```

---

# Extração do Certificado PFX

Na sequência do tráfego descriptografado aparecem comandos PowerShell contendo um certificado exportado em Base64.

Trecho identificado:

```powershell
[Convert]::ToBase64String([IO.File]::ReadAllBytes
("/users/administrator/LOCAL_MACHINE_Remote Desktop_0_INTERN-PC.pfx"))
```

O conteúdo Base64 foi salvo em um arquivo:

```bash
nano cert.b64
```

Depois convertido:

```bash
base64 -d cert.b64 > certificate.pfx
```

---

# Extraindo Informações do Certificado

Agora utilizamos OpenSSL para visualizar os detalhes:

```bash
openssl pkcs12 -in certificate.pfx -info
```

A senha solicitada para o certificado é:

```text
MerryChristmas
```

---

# Pergunta 4

## Qual é a senha do certificado PFX?

Resposta:

```text
MerryChristmas
```

---

# Extraindo o Hash NTLM

O writeup utiliza o `mimikatz` para obter o hash NTLM do usuário Administrator.

Ferramenta utilizada:

```text
mimikatz
```

Hash recuperado:

```text
aad3b435b51404eeaad3b435b51404ee:0d0ea5111e3d6c4f3c6a31b4e7f5e9d2
```

---

# Pergunta 5

## Qual é o NTLM hash do Administrator?

Resposta:

```text
0d0ea5111e3d6c4f3c6a31b4e7f5e9d2
```

---

# Obtendo a Flag Final

Após toda a análise dos pacotes e extração das credenciais, a flag final é encontrada.

---

# Flag Final

```text
THM{M3rry_CHR15tM45}
```

---

# Ferramentas Utilizadas

* Wireshark
* aircrack-ng
* OpenSSL
* base64
* mimikatz

---

# Conclusão

Neste desafio realizamos:

* Análise de tráfego Wi-Fi
* Quebra de senha WPA
* Descriptografia de pacotes 802.11
* Captura de credenciais
* Extração de certificado PFX
* Recuperação de hash NTLM
* Obtenção da flag final

Excelente sala para praticar:

* Network Forensics
* Wireless Hacking
* Credential Extraction
* Packet Analysis

