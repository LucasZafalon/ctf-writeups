
# 📝 MEU PRIMEIRO WRITEUP (OhSINT)

---

## OhSINT — TryHackMe

**Dificuldade:** Fácil
**Categoria:** OSINT
**Data:** 29/04/2026

---

## 🧠 Resumo

Desafio de OSINT baseado na análise de uma imagem contendo metadados sensíveis. Através da extração de informações EXIF e correlação com dados públicos, foi possível identificar o usuário, localização, redes utilizadas e informações pessoais expostas online.

---

## 🔍 Enumeração

### Análise inicial

O desafio fornece uma imagem como ponto de partida. A primeira etapa foi realizar análise manual e extração de metadados.

### Extração de metadados

Utilizei a ferramenta ExifTool:

Comando:

```
exiftool WindowsXP_1551719014755.jpg
```

### Informações relevantes encontradas:

* Autor: **OWoodflint**
* Coordenadas GPS: **54°17'41.27"N, 2°15'1.33"W**
* Indicação de localização no Reino Unido

---

## 🌐 Investigação OSINT

### Identificação do usuário

A partir do nome **OWoodflint**, foi realizada busca em fontes públicas, levando à identificação de perfis online e presença digital.

### Localização

As coordenadas foram analisadas via Google Maps, permitindo identificar a cidade do usuário.

---

### Descoberta de rede Wi-Fi

Em um dos perfis encontrados, o usuário divulgou:

* BSSID da rede
* Comentário indicando uso de Wi-Fi aberto

A partir disso, foi possível identificar o SSID da rede.

---

### Identificação de e-mail

Foi encontrado um blog pessoal hospedado em:

* WordPress

Neste site, foi possível localizar o e-mail pessoal do usuário.

---

### Informações pessoais (OSINT)

O blog continha informações adicionais como:

* Viagens realizadas
* Preferências pessoais

Essas informações foram utilizadas para correlação.

---

## 🔐 Descoberta da senha

A senha foi identificada através de análise de padrões de comportamento do usuário.

Foi observado que:

* O usuário reutiliza informações pessoais
* Referências a viagens e preferências estavam expostas publicamente

A partir disso, foi possível inferir a senha com base em contexto pessoal.

---

## 🚩 Respostas

* Avatar: Cat.
* Cidade: London.
* SSID: UnileverWiFi
* Email: OWoodflint@gmail.com
* Site: Github
* Férias: New York
* Senha: pennYDr0pper.!

---

## 🧠 Lições

Este desafio demonstra como pequenas exposições podem comprometer completamente a segurança de um usuário.

### Pontos críticos:

* Metadados (EXIF) podem revelar localização precisa
* Reutilização de username facilita correlação de identidade
* Divulgação de informações em redes sociais expõe ativos
* Senhas baseadas em informações pessoais são altamente vulneráveis

---

## 🛡️ Como um SOC detectaria isso

* Monitoramento de vazamento de credenciais em fontes abertas
* Correlação de identidade digital via ferramentas OSINT
* Alertas de login suspeito baseado em localização
* Análise de comportamento anômalo em autenticações

---

## 🔐 Mitigações

* Remover metadados de arquivos antes de publicar
* Utilizar senhas fortes e únicas
* Evitar exposição excessiva de informações pessoais
* Utilizar autenticação multifator (MFA)
