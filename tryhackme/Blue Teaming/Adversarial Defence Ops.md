# TryHackMe: Adversarial Defence Ops - Writeup

![Blue Team Badge]([https://tryhackme-badges.s3.amazonaws.com/adversarial-defence-ops.png](https://tryhackme.com/Lucas.Zafalon/badges/adversarial-defence-ops?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91))

## 🛡️ Visão Geral
Este writeup detalha a resolução da sala **Adversarial Defence Ops**. O foco aqui é a transição da segurança passiva para a **Defesa Ativa**, utilizando inteligência de ameaças para detectar, analisar e mitigar táticas de adversários em ambientes corporativos.

---

## 🔬 Tópicos Analisados
*   **Mapeamento MITRE ATT&CK:** Identificação de táticas, técnicas e procedimentos (TTPs).
*   **Detecção de Movimentação Lateral:** Monitoramento de acessos não autorizados entre sistemas.
*   **Análise de Persistência:** Identificação de mecanismos que permitem ao atacante manter o acesso após o reboot.
*   **Resposta a Incidentes:** Metodologias para contenção e erradicação de ameaças.

---

## 🚀 Resumo da Operação

### 1. Perfil do Adversário
A análise começou com o entendimento do perfil do atacante. Utilizei o framework MITRE para correlacionar eventos isolados e identificar que estávamos lidando com uma tentativa de exfiltração de dados sensíveis.

### 2. Identificação de Técnicas (TTPs)
Durante o laboratório, foram identificadas e mitigadas as seguintes técnicas:
*   **Initial Access:** Através de spearphishing e exploração de serviços vulneráveis.
*   **Discovery:** Uso de comandos nativos do SO para mapear a rede interna.
*   **Collection:** Agrupamento de dados para futura exfiltração.

### 3. Implementação de Defesas
Diferente de uma abordagem reativa, a operação focou em:
*   **Hardening de Sistemas:** Fechamento de portas desnecessárias e ajuste de políticas de privilégio mínimo.
*   **Monitoramento de Logs (SIEM):** Criação de regras de correlação para identificar padrões anômalos de tráfego.

---

## 🧠 Insights de Defesa (Blue Team Perspective)
Como profissional de infraestrutura com foco em Cybersecurity, este laboratório reforçou pontos críticos:
1.  **Visibilidade é Tudo:** Não se defende o que não se vê. A configuração correta de logs (como o Rsyslog e ferramentas de SIEM) é a primeira linha de defesa.
2.  **Contexto sobre Alertas:** Um alerta isolado pode ser um falso positivo, mas uma sequência de técnicas mapeadas no MITRE indica um ataque real em curso.
3.  **Automação na Resposta:** Utilizar scripts para isolar máquinas comprometidas ou bloquear IPs maliciosos em tempo real é o que separa uma contenção bem-sucedida de um desastre.

---

## 🔧 Stack de Defesa Utilizada
*   **Análise:** MITRE ATT&CK Navigator.
*   **Monitoramento:** Análise de logs de eventos e tráfego de rede.
*   **Ambiente:** Lab controlado simulando uma infraestrutura corporativa mista.
