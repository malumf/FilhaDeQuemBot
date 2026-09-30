---
name: reducao-de-prompt
description: >
  Reduz prompts e arquivos SKILL.md para gastar menos tokens sem perder o comportamento.
  Use quando o usuário disser: "reduz esse prompt", "enxuga esse prompt", "economiza tokens",
  "deixa mais curto", "otimiza esse prompt", "comprime essa skill", "esse prompt está grande demais".
license: MIT
version: "1.0.0"
tags: ["meta", "prompt", "tokens", "otimizacao"]
---

# Redução de Prompt

Pega um prompt (ou uma skill inteira) e devolve uma versão mais curta que faz a mesma coisa.

## Quando usar

- O prompt ou a skill ficou grande e está caro ou lento de rodar
- O agente está ignorando partes do prompt por ele estar longo demais
- Antes de adicionar uma skill nova ao agente (para não inflar o contexto)

## Fluxo

### 1. Ler e mapear
Identifique no texto original:
- **Objetivo**: o que o prompt precisa produzir
- **Regras obrigatórias**: restrições, formato de saída, tom, avisos legais
- **Gatilhos** (em skills): as frases do campo `description`, que ativam a skill
- **Gordura**: tudo o que não muda o resultado

### 2. Cortar (nesta ordem)
1. Remover introduções, agradecimentos, "você é um especialista incrível em..."
2. Remover repetições (a mesma regra dita de duas formas)
3. Remover explicações do óbvio (o modelo já sabe fazer)
4. Trocar parágrafos por listas curtas e frases por verbos diretos
5. Juntar exemplos parecidos e manter só 1 por caso
6. Mover conteúdo longo e raramente usado para um arquivo em `references/` e deixar só um ponteiro

### 3. Nunca cortar
- Formato de saída exigido (campos, ordem, schema)
- Avisos obrigatórios (ex.: divulgação de afiliado / #publi)
- Regras de segurança e dados não confiáveis
- Frases-gatilho do `description` (cortar isso quebra a ativação da skill)
- Números, limites e nomes exatos que o prompt cita

### 4. Conferir
- Rode o prompt original e o reduzido com o mesmo pedido de teste
- Compare: mesma estrutura, mesmas regras respeitadas, qualidade equivalente
- Se algo se perdeu, devolva só aquele trecho

## Formato de saída

```
## Prompt reduzido
[texto]

## Economia
Antes: ~X palavras | Depois: ~Y palavras (-Z%)

## O que foi cortado
[lista curta]

## Risco
[algo que pode ter mudado de comportamento, ou "nenhum identificado"]
```

## Regras

- Meta padrão: cortar 30–50% sem mudar o comportamento. Se passar disso e perder regra, volte atrás.
- Nunca mude o sentido de uma regra para ela ficar mais curta.
- Se o usuário pedir "o mais curto possível", avise o que foi sacrificado.
- Em skills, mantenha o frontmatter (`name`, `description`) válido.
