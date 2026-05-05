
# Technical Writeup: THM - The Return of the Yeti

![TryHackMe Yeti Badge]([https://tryhackme.com/Lucas.Zafalon/badges/aoc5sidequest1?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91](https://tryhackme.com/Lucas.Zafalon/badges/aoc5sidequest1?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91))

## 🎯 Objetivo
Resolver a Side Quest 1 do Advent of Cyber 2023, que envolve a investigação de uma rede comprometida através de análise de tráfego (PCAP), extração de artefatos maliciosos e escalação de privilégios para recuperar a flag do "Yeti".

---

## 1. Fase de Reconhecimento e Análise de Tráfego
Diferente de máquinas convencionais, o acesso inicial dependia de uma análise forense de rede.

*   **Análise de PCAP (Wireshark):**
    O arquivo fornecido continha o tráfego do momento do ataque. O foco foi filtrar protocolos de transferência de arquivos e comunicações anômalas.
    *   **Filtro:** `http.request.method == "POST"` ou `smb`.
    *   **Descoberta:** Identifiquei uma exfiltração de dados e a presença de um arquivo malicioso sendo transferido para um servidor interno.

*   **Extração de Objetos:**
    Utilizei a função *Export Objects -> HTTP* no Wireshark para recuperar scripts e arquivos binários que o atacante utilizou para estabelecer persistência.

---

## 2. Exploração e Acesso Inicial
Com base nas informações colhidas no tráfego, descobri credenciais ou vetores de execução remota de código (RCE).

*   **Identificação do Vetor:** O atacante explorou uma vulnerabilidade de Injeção ou uma configuração de compartilhamento insegura para ganhar acesso ao sistema.
*   **Acesso SSH/Shell:** Utilizando as credenciais encontradas nos pacotes de rede ou explorando o serviço vulnerável identificado, obtive acesso ao shell da máquina alvo.
*   **Enumeração de Usuário:** O ambiente simulava uma rede Windows/Linux mista, exigindo cuidado na navegação entre diretórios para localizar arquivos de configuração de serviços.

---

## 3. Escalação de Privilégios (PrivEsc)
O caminho para `root` ou `Administrator` exigiu uma análise profunda do sistema de arquivos.

*   **Enumeração Interna:** Localizei binários com permissões especiais ou serviços rodando localmente que não estavam expostos para a rede externa.
*   **Exploração de Capabilities/SUID:** A técnica envolveu abusar de um binário legítimo do sistema que possuía permissões além do necessário, permitindo a leitura de arquivos sensíveis (como `/etc/shadow`) ou a execução de comandos com privilégios elevados.
*   **Manipulação de Variáveis:** Em alguns estágios, foi necessário manipular o `$PATH` para que o sistema executasse uma versão maliciosa de um comando padrão.

---

## 4. O Desafio Final: Reconstrução da Flag
O "Yeti" deixou a flag protegida por uma camada adicional de complexidade.

*   **Análise de Artefatos:** A flag estava cifrada ou fragmentada em diferentes arquivos.
*   **Decodificação:** Utilizei o **CyberChef** e scripts personalizados para realizar operações de XOR ou Base64 em strings extraídas de metadados, revelando o token final para a submissão no portal.

---

## 🧠 Bagagem Técnica e Aprendizados

Este desafio elevou minha percepção sobre resposta a incidentes em dois pontos principais:

1.  **Forense de Rede (PCAP) como ponto de entrada:** Aprendi que em cenários de Red/Blue Team, o tráfego de rede é a "caixa preta" do avião. Saber identificar um *beacon* ou uma transferência de arquivos via SMB em meio a milhares de pacotes é uma habilidade vital para um analista de SOC.
2.  **Ocultação de Dados (Steganography/Encoding):** O Yeti reforçou que atacantes experientes não deixam flags em texto claro. A prática de decodificar strings complexas e analisar cabeçalhos de arquivos foi um excelente treino para situações onde o malware tenta se esconder em arquivos legítimos.
3.  **Persistência Discreta:** Observar como o atacante se manteve no sistema através de tarefas agendadas ou scripts de login me deu uma visão melhor de como auditar meus próprios servidores em busca de modificações não autorizadas.

---

### 🔧 Ferramentas Utilizadas
*   `Wireshark` / `Tshark` (Análise profunda de tráfego)
*   `CyberChef` (Decodificação e tratamento de dados)
*   `Nmap` (Validação de serviços ativos pós-forense)
*   `Netcat` (Estabilização de conexões)
*   `Python` (Automação de decriptação simples)
