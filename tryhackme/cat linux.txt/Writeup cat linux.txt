# TryHackMe: Linux Fundamentals Part 1 - Writeup

![TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/terminaled?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

## 📌 Visão Geral
Este repositório contém a documentação e resolução da sala **Linux Fundamentals Part 1** do TryHackMe. O objetivo desta análise é validar conhecimentos fundamentais de administração de sistemas Linux, focando em estrutura de diretórios, manipulação de arquivos e comandos essenciais via CLI.

---

## 🛠️ Tópicos Abordados
*   **Introdução ao Shell:** Interação com o terminal.
*   **Manipulação de Arquivos:** Comandos de navegação e leitura (`ls`, `cd`, `cat`).
*   **Estrutura do Sistema:** Entendimento do padrão FHS (Filesystem Hierarchy Standard).
*   **Pesquisa e Filtros:** Localização de arquivos e strings básicas.

---

## 🚀 Resolução das Tarefas

### Tarefa 1 ao 3: Introdução e Primeiros Passos
Nestas etapas iniciais, o foco é a conexão via SSH e a compreensão de como o terminal interpreta comandos. 
*   **Conexão:** `ssh <username>@<ip_address>`
*   **Comando `echo`:** Utilizado para imprimir texto ou variáveis no terminal.

### Tarefa 4: Interagindo com o Sistema de Arquivos
Exploração de diretórios e identificação de conteúdo.
*   `ls`: Listar arquivos (uso frequente de `-la` para arquivos ocultos e permissões).
*   `cd`: Navegação entre diretórios.
*   `cat`: Leitura de arquivos de texto.

> **Challenge:** Localizar arquivos específicos dentro da home do usuário.
> *   *Dica de Prática:* Sempre verifique o diretório atual com `pwd` antes de realizar navegações complexas.

### Tarefa 5: Buscando por Arquivos
Introdução aos comandos de busca.
*   `find`: Localização baseada em nome, tipo ou permissão.
*   `grep`: Filtragem de conteúdo dentro de arquivos.

### Tarefa 6: Conclusão e Próximos Passos
O módulo encerra a base necessária para avançar para permissões de arquivos e administração de rede (Parte 2).

---

## 🧠 Insights de Experiência
Apesar de serem comandos fundamentais, a eficiência no uso do terminal é o que diferencia um analista de infraestrutura. Durante o laboratório, foquei em:
1.  **Agilidade:** Uso extensivo de *Tab Completion* para navegação rápida.
2.  **Documentação:** Registro de logs de saída para futuras auditorias (prática comum em ambientes de produção).
3.  **Estética Funcional:** Utilização de aliases e prompts customizados para melhorar a legibilidade das saídas.

---

## 🔧 Ferramentas Utilizadas
*   **OS:** Kali Linux / ZorinOS
*   **Terminal:** Fish Shell / Warp
*   **Conectividade:** OpenVPN / SSH
