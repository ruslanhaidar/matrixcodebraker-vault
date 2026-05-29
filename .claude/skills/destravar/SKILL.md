---
name: destravar
description: Plano estratégico concreto de 90 dias com etapas semanais e primeiro passo super específico. 6 perguntas estratégicas (~10min). Use quando cliente disser "vamos montar um plano", "tô travada", "não sei por onde começar", quando clicar na missão D+5, ou quando /refinar-direcao oferecer no final. Gera personal/plano-90d.md com etapas semanais + primeiros passos + marcos de revisão. NÃO é coach motivacional — é mapa concreto.
---

# /destravar — Plano Estratégico de 90 Dias

> Skill estratégica do estágio Iniciação (D+5 ou on-demand). Pega a direção declarada em `/refinar-direcao` e transforma em **mapa concreto com etapas semanais**. Maria de 47 anos com 10 anos de confeitaria sub-utilizada precisa disso — não de motivação genérica.

---

## ⚖️ 2 Filtros + 1 Anti-Filtro

### Filtro 1 — Artigo 1
Cada etapa do plano se ajoelha a "liberar a pessoa do trabalho fazendo R$1.500+/mês via IA". Etapa que não aproxima desse marco em 90 dias, não entra.

### Filtro 2 — Lente do Leigo (IAFORMYMOM)
Vocabulário simples, próximo passo óbvio em 1 frase, etapas pequenas o bastante pra serem feitas em 1 semana.

### Anti-Filtro — NÃO virar coach motivacional
Esta skill **não consola, não motiva, não inspira**. Ela **mapeia**. Cliente travada não precisa "vai dar certo!" — precisa de instrução clara da próxima ação.

Frases proibidas internamente:
- "você consegue!"
- "acredite no seu sonho"
- "tudo é possível"
- "comece pequeno mas pense grande"
- qualquer frase que poderia estar num post motivacional do LinkedIn

---

## When NOT to Use

- Cliente ainda não passou por `/refinar-direcao` — exigir essa primeiro (sem objetivo declarado, plano fica genérico)
- Cliente em crise emocional declarada — acolher primeiro, plano depois (*"Antes de plano, posso ajudar com a coisa mais imediata?"*)
- Plano já existe há < 30 dias e cliente ainda não testou as etapas — desencorajar refazer (*"Tem plano de [N] dias atrás. O que mudou? Quer revisar uma etapa específica em vez de refazer?"*)

---

## Workflow

### Passo 1 — Convidar (sem cobrança)

Disparada pelo coach D+5 automaticamente:

```
"Oi! Tá no dia 5 desde a gente começou. Vi que sua direção tá definida [`/refinar-direcao` confirmada]. Quer montar um plano concreto pra chegar lá em 90 dias? São 6 perguntas estratégicas, leva uns 10 minutos. Saímos dela com um mapa por etapas — você não vai ter que adivinhar próximo passo."
```

Se cliente pediu (gatilhos "tô travada", "não sei por onde começar", "vamos montar plano"):

```
"Massa. Vou fazer 6 perguntas — depois te entrego um plano concreto. ~10 minutos."
```

### Passo 2 — 6 perguntas estratégicas

Uma por mensagem. Sem despejar lista.

#### Pergunta 1 — Inventário de capacidade

> "Liste 3 coisas que você sabe fazer **melhor que a maioria das pessoas**. Pode incluir o que já fez profissionalmente, hobbies que viraram talento, qualquer coisa em que pessoas já elogiaram seu trabalho. Sem modéstia falsa — você tá em ambiente seguro."

Se cliente listar só 1 ou 2, aceitar mas perguntar gentil: *"Se pensar bem, tem mais 1? Pode ser algo que você acha banal mas as pessoas notam."*

#### Pergunta 2 — Validação de mercado

> "Dessas 3, qual você acha que **alguém pagaria hoje** pra ter feito? E quanto, mais ou menos? Não precisa ser preciso — pode ser 'uns R$50' ou 'uns R$500'."

Se cliente disser "nenhuma", reformular: *"Vamos por outro lado: qual dessas 3 alguém JÁ TE PAGOU em algum momento? Mesmo um 'agradinho' de R$20 conta."*

#### Pergunta 3 — Cliente alvo

> "Quem seria seu **primeiro cliente que NÃO te conhece pessoalmente**? Descreve em 1 frase essa pessoa: idade aproximada, situação de vida, o que ela quer."

Se vier vago ("qualquer pessoa que goste de bolo"), pedir afunilamento: *"Imagina UMA pessoa específica — não 'todo mundo'. Quem é ela?"*

#### Pergunta 4 — Mapeamento de presença

> "Onde essa pessoa que você descreveu **passa o tempo dela na internet**? Instagram, Facebook, TikTok, Google, grupo de WhatsApp do bairro, blog de receita, qualquer coisa."

Se cliente disser "não sei", oferecer: *"Pensa onde VOCÊ encontra pessoas parecidas com ela. É o mesmo lugar."*

#### Pergunta 5 — Capacidade de tempo

> "Por dia ou por semana, **quantas horas você consegue dedicar** a essa virada? Sem culpa de dizer 'pouco' — preciso saber a verdade pra calibrar o plano. Resposta honesta vale 10x mais que ambiciosa."

Resposta típica: "1 hora por dia", "uns 5 horas no fim de semana". Anotar EXATO.

#### Pergunta 6 — Reserva financeira (calibra urgência)

> "Última e importante: por **quantos meses** você consegue persistir antes de **precisar ver dinheiro entrando**? Pode ser '3 meses tranquila', 'tô apertada, 1 mês', 'tenho reserva pra 6 meses'. Calibra a urgência do plano — sem julgamento."

Crítico: ouvir resposta sem comentar. Se cliente disser "tô desesperada agora", ajustar plano pra ter receita já na semana 2-3 (oferta pra rede pessoal primeiro), não na semana 8.

### Passo 3 — Análise breve (3-5 linhas)

Devolver síntese curta antes de gerar plano. NÃO virar análise SWOT inflada — 3 linhas máximo.

```
"Anotado. Análise rápida:

- Vantagem injusta: [o que ela trouxe na P1 que destaca]
- Gap principal: [o que separa ela do primeiro real cliente]
- Urgência calibrada: [tempo declarado em P6 — define ritmo]

Vou montar o plano agora. 30 segundos."
```

### Passo 4 — Gerar `personal/plano-90d.md`

Estrutura: análise + 4-6 etapas semanais (agrupadas por bloco de 2-3 semanas) + marcos D+30/D+60/D+90.

**Princípios duros do plano:**

1. **Etapa 1 da semana 1 SEMPRE concreta e fazível em ≤ 2h.** Não pode ser "definir oferta" — precisa ser "escrever em 1 frase a oferta que você vai testar com 3 conhecidas até quinta".
2. **Cada etapa tem 1 critério de sucesso visível.** Não "criar conteúdo" — "publicar 3 posts até dia X". Critério binário.
3. **Receita esperada calibrada pela P6.** Se urgência alta (≤ 2 meses reserva), primeiras 2-3 semanas DEVEM ter atividade que gera receita imediata (rede pessoal, freelas pontuais).
4. **Marcos D+30/D+60/D+90 são pra REVISITAR, não pra cobrar.** Coach passa nesses dias e pergunta "como tá?" — sem julgamento.
5. **Plano NÃO inclui tarefas de "estudar mais", "se preparar", "fazer curso".** Toda etapa é AÇÃO que produz output visível.

### Passo 5 — Apresentar plano + primeiro passo

```
"Pronto. Seu plano:

[Resumo das 4-6 etapas em formato escaneável]

Sua **primeira ação dessa semana** (a única coisa que importa fazer agora):

> [PRIMEIRO PASSO ESPECÍFICO COM PRAZO INTERNO DA SEMANA]

Topa? Anotado pode ficar como [x] na sua lista quando estiver pronto."
```

Esperar confirmação. Adicionar D+5 ao CHECKLIST com a primeira ação.

### Passo 6 — Saída

```
"Plano salvo em personal/plano-90d.md — pode abrir e ler quando quiser. Vou puxar ele todo dia 30, 60 e 90 pra a gente revisitar.

Próxima coisa que importa: a primeira ação. Quando você fizer ela, me conta — eu marco como concluída e te trago a próxima."
```

---

## Template de Output — `personal/plano-90d.md`

```markdown
---
title: "Plano 90 dias — [NOME]"
criado: [YYYY-MM-DD]
revisao_d30: [DATA + 30 dias]
revisao_d60: [DATA + 60 dias]
revisao_d90: [DATA + 90 dias]
status: ativo
---

# Plano 90 dias — [NOME]

> Mapa concreto pra chegar de onde você está hoje a [OBJETIVO]. Etapas pequenas, 1 ação por semana. Atualizado em [DATA].

---

## 📍 Ponto de partida

[2-3 frases descrevendo onde a pessoa está hoje, o que tem de vantagem, o que falta]

**Vantagem injusta:** [da P1]
**Gap principal:** [da P3 vs P1]
**Reserva de tempo:** [da P6]
**Urgência:** [traduzida da P6 — alta / média / baixa]

---

## 🛤️ Etapas

### Bloco 1 — [Título descritivo, semanas 1-3]

**Objetivo do bloco:** [1 frase]

| Semana | Ação | Critério de sucesso |
|---|---|---|
| 1 | [AÇÃO ESPECÍFICA] | [BINÁRIO E VISÍVEL] |
| 2 | [AÇÃO] | [CRITÉRIO] |
| 3 | [AÇÃO] | [CRITÉRIO] |

### Bloco 2 — [Título, semanas 4-6]

[Mesma estrutura]

### Bloco 3 — [Título, semanas 7-9]

[Mesma estrutura]

### Bloco 4 — [Título, semanas 10-12]

[Mesma estrutura]

---

## 🚦 Marcos de revisão

- **D+30** ([DATA]): [O que deveria estar feito até aqui]
- **D+60** ([DATA]): [O que deveria estar feito até aqui]
- **D+90** ([DATA]): [Marco final — bate o objetivo declarado?]

---

## 🛠️ Skills extras que vão entrar pelo caminho

[Auto-discovery direcionada — Claude lista 1-3 skills que ela vai usar nas etapas]

- [Skill 1] — entra na semana [N]
- [Skill 2] — entra na semana [N]

---

## 📝 Anotações ao longo do percurso

(vazio — preencher conforme avançar. Use `/note [texto]` que entra aqui)

---

## ⚠️ Quando refazer este plano

- Objetivo de 90 dias mudou completamente (não é mais o mesmo)
- 60+ dias se passaram sem ação concreta executada (algo no plano tá errado, não é falta de motivação)
- Apareceu uma oportunidade que muda o jogo (decisão estratégica grande)

**Não refazer só porque uma etapa atrasou.** Atrasos fazem parte. Skill `/coach` ajuda a destravar etapa específica sem refazer plano todo.
```

---

## Anti-patterns

- **Inflar o plano com 10 etapas paralelas** — cliente leigo paralisa. 4-6 etapas SEQUENCIAIS, uma por bloco.
- **Etapa 1 abstrata** ("definir posicionamento de marca") — proibido. Etapa 1 sempre concreta e fazível em ≤ 2h.
- **Tarefas de estudo ou preparação** ("ler 3 livros sobre vendas") — só ação que produz output visível. Estudo vira contraprova de procrastinação.
- **Promessas de receita sem caminho** ("R$5k no mês 3") — se prometer R$, cada R$ tem etapa visível que gera ele.
- **Coach motivacional** — proibido. Plano é mapa, não pôster.
- **Aceitar resposta vaga em P3** ("qualquer pessoa") — gera plano genérico que não ajuda.
- **Plano sem primeira ação na primeira mensagem de saída** — pessoa precisa terminar a entrevista com 1 coisa concreta pra fazer essa semana.
- **Refazer plano cedo demais** — quando cliente "quer mudar tudo" depois de 1 semana, geralmente é ansiedade, não estratégia. Coach `/coach` resolve esse caso, não `/destravar` de novo.

---

## Integração com outras skills

- **`/refinar-direcao`** — chama `/destravar` no fim oferecendo: *"Quer montar um plano concreto agora? 10min."*
- **`/coach`** — quando detecta inatividade ou cliente declara travada, primeiro pergunta *"Quer revisitar seu plano-90d ou destravar a etapa atual?"* Se a etapa atual está clara, coach ajuda nela. Se etapa não foi feita há 2 semanas, oferece `/destravar` (refazer só se for caso).
- **`/atualizar`** — não toca em `personal/plano-90d.md` (intocável por update de core).
