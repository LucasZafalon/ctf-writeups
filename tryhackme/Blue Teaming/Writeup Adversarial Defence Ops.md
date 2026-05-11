# Defending Adversarial Attacks - Writeup

Room: [TryHackMe Badge](https://tryhackme.com/Lucas.Zafalon/badges/adversarial-defence-ops?utm_campaign=social_share&utm_medium=social&utm_content=badge&utm_source=copy&sharerId=663e76ced6984cc4849c6b91)

A room **Defending Adversarial Attacks** da TryHackMe aborda técnicas de defesa contra ataques adversariais em modelos de Machine Learning e Inteligência Artificial.

O foco principal é entender:

* Como modelos de IA podem ser enganados
* Técnicas para endurecer modelos (hardening)
* Estratégias defensivas contra ataques FGSM, BIM e PGD
* Métodos de detecção de entradas adversariais
* Robustez em IA aplicada à segurança

Essa room é continuação da room:

* Detecting Adversarial Attacks


---

# Task 1 - Introduction

Nesta primeira task a room apresenta os objetivos do laboratório.

O conteúdo explica que:

* Modelos de IA são vulneráveis a manipulações
* Pequenas alterações em entradas podem causar classificações erradas
* Precisamos aplicar mecanismos defensivos para aumentar a robustez

Também é recomendado conhecimento básico em:

* Jupyter Notebook
* Conceitos básicos de IA/ML
* Ataques adversariais


## Resposta

```bash
No answer needed
```

---

# Task 2 - Defence Strategies for Adversarial Attacks

Nesta etapa aprendemos estratégias defensivas contra ataques adversariais.

---

# Gradient Hiding

Uma das técnicas apresentadas é:

```bash
Gradient Hiding
```

Essa técnica tenta esconder ou dificultar o acesso aos gradientes utilizados pelos ataques adversariais.

Ataques como:

* FGSM
* BIM
* PGD

Dependem de gradientes para gerar perturbações.

O Gradient Hiding reduz a eficiência principalmente de ataques mais simples.


---

## Pergunta

### Which gradient-based attack does gradient hiding defend against best?

## Resposta

```bash
FGSM
```


---

# FGSM (Fast Gradient Sign Method)

O FGSM é um dos ataques adversariais mais conhecidos.

Ele altera pixels da entrada usando os gradientes do modelo:

x_{adv}=x+\epsilon\cdot sign(\nabla_x J(\theta,x,y))

Onde:

* (x_{adv}) = imagem adversarial
* (\epsilon) = intensidade da perturbação
* (J) = função de perda
* (\nabla_x) = gradiente em relação à entrada

Pequenas alterações quase invisíveis podem fazer a IA errar completamente a classificação.


---

# Task 3 - Advanced Defence Techniques

Agora aprendemos técnicas mais avançadas de proteção contra ataques adversariais.

---

# NULL Labeling

Uma técnica apresentada é:

```bash
NULL Labeling
```

Essa abordagem adiciona um rótulo especial chamado:

```bash
NULL
```

Quando o modelo identifica uma entrada suspeita ou adversarial, ele pode rejeitá-la ao invés de classificá-la incorretamente.

---

## Pergunta

### Which label is added to a model to reject adversarial inputs?

## Resposta

```bash
NULL
```


---

# MagNet

Outra defesa importante apresentada é:

```bash
MagNet
```

O MagNet utiliza dois componentes principais:

* Detector
* Reformer

O objetivo é:

* Detectar entradas suspeitas
* Corrigir pequenas perturbações antes da classificação


---

# Detector

O:

```bash
Detector
```

Verifica se a entrada parece legítima ou anômala.

---

## Pergunta

### Which component in MagNet checks if an input looks normal?

## Resposta

```bash
Detector
```


---

# Reformer

O:

```bash
Reformer
```

Tenta reconstruir entradas levemente modificadas antes que cheguem ao classificador.

---

## Pergunta

### Which component in MagNet repairs slightly perturbed inputs?

## Resposta

```bash
reformer
```


---

# Técnicas Defensivas Aprendidas

Durante a room aprendemos:

* Gradient Hiding
* Defensive Distillation
* Feature Squeezing
* MagNet
* NULL Labeling
* Adversarial Training


---

# Task 4 - Pet Trouble

Nesta task prática trabalhamos com treinamento de modelos de Machine Learning.

Um dos conceitos abordados é:

```bash
Overfitting
```

---

# Overfitting

Overfitting ocorre quando:

* O modelo aprende demais os dados de treinamento
* Perde capacidade de generalização
* Fica menos eficiente em dados reais

Isso normalmente acontece quando:

* Existem muitas epochs
* Poucos dados
* Modelo excessivamente complexo


---

## Pergunta

### What can happen if you run too many epochs?

## Resposta

```bash
overfitting
```


---

# Conceitos Importantes

---

# Adversarial Attacks

Ataques adversariais consistem em:

* Alterações pequenas e intencionais
* Inputs manipulados
* Objetivo de enganar IA/ML

Esses ataques podem afetar:

* Reconhecimento facial
* Veículos autônomos
* Sistemas bancários
* Sistemas antifraude
* Diagnósticos médicos


---

# White-box vs Black-box

## White-box

O atacante possui:

* Arquitetura do modelo
* Gradientes
* Pesos
* Total conhecimento interno

## Black-box

O atacante possui apenas:

* Entradas
* Saídas
* Sem acesso interno ao modelo


---

# Técnicas de Defesa

| Técnica              | Objetivo                          |
| -------------------- | --------------------------------- |
| Gradient Hiding      | Esconder gradientes               |
| Feature Squeezing    | Reduzir ruído adversarial         |
| Adversarial Training | Treinar com exemplos adversariais |
| NULL Labeling        | Rejeitar entradas suspeitas       |
| MagNet               | Detectar e reparar entradas       |

---

# Fluxo da Room

```bash
Ataques adversariais
        ↓
Identificação das vulnerabilidades
        ↓
Aplicação de técnicas defensivas
        ↓
Hardening do modelo
        ↓
Maior robustez da IA
```

---

# Comandos e Ferramentas Utilizadas

## Jupyter Notebook

```bash
jupyter notebook
```

## Python

```python
import torch
import numpy as np
```

## Frameworks comuns

```bash
TensorFlow
PyTorch
```

---

# Importância na Cibersegurança

A segurança em IA/ML está se tornando extremamente importante devido ao crescimento do uso de IA em:

* SOCs
* SIEMs
* Detecção de fraudes
* EDR/XDR
* Monitoramento de ameaças
* Sistemas biométricos

Ataques adversariais podem comprometer completamente modelos defensivos.


---

# Conclusão

A room Defending Adversarial Attacks é uma excelente introdução à área de:

* AI Security
* ML Security
* Adversarial Machine Learning
* IA aplicada à Cibersegurança

Ela demonstra como:

* Modelos podem ser enganados
* Defesas podem ser implementadas
* Não existe proteção perfeita
* Segurança em IA exige múltiplas camadas defensivas

Além disso, a room reforça a importância crescente da segurança em IA conforme sistemas inteligentes passam a ser utilizados em ambientes críticos.

