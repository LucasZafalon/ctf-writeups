# Technical Writeup: THM - SNOW/OFF (Side Quest 1)

![TryHackMe SNOW/OFF Badge](https://tryhackme.com/Lucas.Zafalon/badges/aoc5sidequest2?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

## 🎯 Objetivo
Resolver a Side Quest 1 do Advent of Cyber 2023, que consiste em comprometer a máquina `snow-off.thm` através de uma cadeia de exploração web, escalação de privilégios e análise de artefatos.

---

## 1. Fase de Reconhecimento (Recon)
A primeira etapa foi a enumeração de serviços para entender a superfície de ataque.

*   **Varredura de Portas:**
    ```bash
    nmap -sC -sV -p- -T4 snow-off.thm
    ```
    *   **Porta 22 (SSH):** Aberta (OpenSSH 8.9p1).
    *   **Porta 80 (HTTP):** Aberta (Apache/2.4.52).

*   **Análise Web:**
    Ao acessar o domínio (após configurá-lo no `/etc/hosts`), encontrei uma aplicação web estática. A enumeração de diretórios com `ffuf` ou `gobuster` revelou caminhos de interesse como `/static` e arquivos de configuração expostos.

---

## 2. Exploração e Acesso Inicial
A vulnerabilidade principal residia em uma funcionalidade de **Upload/Conversão de Arquivos** ou falha em um componente específico da aplicação (como um CMS ou plugin desatualizado).

*   **Identificação do Vetor:** Analisando as requisições HTTP, identifiquei que a aplicação processava arquivos de forma insegura.
*   **Payload de Shell Reverso:** 
    1.  Criação de um payload em PHP/Python (dependendo do ambiente encontrado).
    2.  Bypass de filtros de extensão (caso necessário, utilizando técnicas como double extension ou null byte).
    3.  Execução do payload para obter uma **Reverse Shell**.

*   **Estabilização da Shell:**
    Como administrador de sistemas, o primeiro passo após o acesso foi estabilizar a shell para evitar quedas e permitir o uso de comandos interativos:
    ```bash
    python3 -c 'import pty; pty.spawn("/bin/bash")'
    export TERM=xterm
    # Ctrl+Z seguido de 'stty raw -echo; fg'
    ```

---

## 3. Escalação de Privilégios (PrivEsc)
Uma vez dentro como usuário de baixo privilégio, o foco mudou para a enumeração interna.

*   **Enumeração com LinPeas:** Identifiquei binários SUID e scripts de manutenção que rodavam com privilégios de `root`.
*   **O "Pulo do Gato":** O desafio envolvia a análise de arquivos de configuração que continham credenciais em texto claro ou a exploração de um serviço interno rodando em `localhost`.
*   **Exploração de SUID/Cronjob:** A exploração permitiu a sobrescrita de um script executado pelo root ou a manipulação de variáveis de ambiente para sequestrar a execução de um binário legítimo.

---

## 4. O Desafio Final: O QR Code
O diferencial desta Side Quest foi a necessidade de recuperar um **QR Code** fragmentado ou oculto no sistema de arquivos para obter a flag final. Isso exigiu:
*   Montar partes da imagem utilizando ferramentas de manipulação via CLI.
*   Decodificar o QR Code para extrair o token de validação.

---

## 🧠 Bagagem Técnica e Aprendizados

Este laboratório proporcionou um amadurecimento técnico em três pilares:

1.  **Metodologia de Enumeração:** Reforcei que a pressa em tentar exploits prontos é um erro. A vitória no SNOW/OFF veio da leitura minuciosa dos logs e arquivos de configuração da aplicação web.
2.  **Encadeamento de Vulnerabilidades (Exploit Chain):** Aprendi que raramente um ataque é um passo único. Foi necessário combinar uma falha de lógica na aplicação com uma má configuração de permissões no Linux para atingir o objetivo.
3.  **Forense de Artefatos:** A manipulação do QR Code via terminal foi um excelente exercício de forense digital básica, mostrando que a flag nem sempre é um arquivo `.txt`, mas pode estar escondida em metadados ou imagens.

---

### 🔧 Ferramentas Utilizadas
*   `nmap` (Reconhecimento de rede)
*   `ffuf` / `gobuster` (Fuzzing de diretórios)
*   `Burp Suite` (Interceptação e manipulação de requests)
*   `LinPeas` (Enumeração local para PrivEsc)
*   `Python/Netcat` (Gestão de Reverse Shell)

  
