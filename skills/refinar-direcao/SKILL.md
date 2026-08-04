---
name: refinar-direcao
description: Refinar direção de 90 dias do cliente. 3 perguntas conversadas em linguagem leiga (~2min). Use quando cliente disser "vamos definir objetivo", "quero traçar direção", ou clicar na missão D+3 do CHECKLIST. Atualiza seção "Direção" do CLAUDE.md + cria project_objetivo-90d.md em personal/memory/ + atualiza Objetivo Ativo do PRIMER global.
---

# /refinar-direcao — Direção de 90 Dias (missão D+3)

> Skill opcional, disparada por iniciativa do cliente OU sugerida pelo coach D+3. **Mesma Lente do Leigo do `/desabrochar`.**

---

## ⚖️ Filtros (mesmos)

1. **Artigo 1** — direção precisa tirar peso do cérebro da pessoa e devolver tempo/capacidade. Se objetivo do cliente é vago ("ganhar mais", "melhorar de vida"), traduzir junto em resultado observável: *"Como você vai SABER que chegou lá? O que muda na sua semana?"* — dinheiro só entra se a pessoa trouxer.
2. **Lente do Leigo** — palavras simples, exemplos concretos quando perguntar.

---

## When NOT to Use

- Cliente ainda não passou por `/desabrochar` — redirecionar
- Direção já refinada (`direcao_refinada: true`) — oferecer revisão: *"Faz quanto tempo? Quer revisar o objetivo de 90 dias?"*
- Cliente em momento de crise emocional declarada — acolher, não puxar planejamento ("Tô passando por X agora") → adiar gentil

---

## Workflow

### Passo 1 — Convidar

Se foi disparado pelo coach D+3 automaticamente:

```
"Oi! Hoje é 3 dias desde a gente começou. Posso fazer 3 perguntas pra a gente definir uma direção concreta pros próximos 90 dias? Leva uns 2 minutos."
```

Se cliente pediu, ir direto:

```
"Boa. 3 perguntas — em 2 minutos a gente fecha a direção."
```

### Passo 2 — 3 perguntas (uma por mensagem)

#### Pergunta 1 — Objetivo concreto
> "O que você quer destravar nos próximos 90 dias? Tenta ser bem específico — exemplos:
>
> - 'Sair do CLT e viver do meu trabalho online'
> - 'Faturar R$5k/mês com [meu produto/serviço]'
> - 'Ter 10k seguidores no Instagram'
> - 'Lançar meu primeiro curso online'
> - 'Conseguir os primeiros 10 clientes pagantes'
>
> Qual o seu?"

Se vier vago ("ganhar mais", "crescer"), refinar junto: *"Vamos concretizar — em números: ganhar quanto? Em quanto tempo?"* até ter algo mensurável.

#### Pergunta 2 — Risco/medo principal
> "Pra eu te ajudar a passar por cima dele: qual seu maior medo ou risco hoje em relação a esse objetivo? Tipo:
>
> - 'Não conseguir consistência'
> - 'Não saber por onde começar'
> - 'Medo de me expor'
> - 'Ficar sem grana enquanto não decola'
> - 'Ser vista como charlatã'
>
> Pode falar do seu jeito."

Anotar EXATO. Não tentar consolar — a função é coletar pra Claude saber o que evitar/antecipar.

#### Pergunta 3 — Nível com IA
> "Última: de 0 a 10, qual seu nível com IA hoje? 0 = nunca usei, 10 = construo robôs e automações sozinha. Não tem certo nem errado — me ajuda a saber até onde te empurrar."

Anotar número. Calibra profundidade técnica das próximas interações.

### Passo 3 — Espelho + sugestão de primeiro passo

Devolver:

```
"Anotado:

- Próximos 90 dias você quer: [OBJETIVO]
- Maior risco/medo: [MEDO]
- Nível IA: [N]/10

Baseado nisso, vou sugerir 1 primeiro passo concreto pra essa semana:

> [PRIMEIRO PASSO CALIBRADO]

Topa esse passo? Se sim, anoto na sua lista."
```

Se topar → adicionar ao CHECKLIST como D+5.
Se não → perguntar o que faria sentido pra ela, ajustar.

### Passo 4 — Salvar

> "Pronto. Direção fechada."

Internamente:

1. **Atualizar `CLAUDE.md`** — sobrescrever seção "Direção"
2. **Marcar `direcao_refinada: true`**
3. **Criar `personal/memory/project_objetivo-90d.md`**
4. **Atualizar `personal/PRIMER.md`** — Objetivo Ativo = objetivo de 90 dias
5. **Marcar missão D+3 como concluída** no CHECKLIST

### Passo 5 — Oferecer /destravar (sem pressão)

Antes de despedir, oferecer skill estratégica:

```
"Tá. Daqui pra frente, sempre que eu te sugerir alguma coisa, vou medir contra esse objetivo. Pode me cobrar se eu desviar.

A gente pode ir mais fundo agora se você quiser: 6 perguntas estratégicas e eu te entrego um **plano concreto de 90 dias** com etapas semanais e primeiro passo super específico. Leva mais 10 minutos. Saímos com mapa, você não precisa adivinhar próximo passo.

Topa? Ou prefere deixar pra outro dia?"
```

**Se "topa":** chamar `/destravar` em sequência.
**Se "outro dia":** marcar missão D+5 ativa no CHECKLIST e despedir.

### Passo 6 — Despedir (se cliente não topou /destravar agora)

```
"Beleza. Quando quiser montar o plano, é só pedir 'vamos montar o plano' ou /destravar. Tô por aqui."
```

---

## Como gerar o "primeiro passo concreto"

Cruzar (objetivo, gargalo declarado em `/desabrochar`, ramo, nível IA):

| Combinação | Primeiro passo sugerido |
|---|---|
| Objetivo: primeira venda · Ramo: criador-conteudo · Nível: 1-3 | "Postar 1 conteúdo essa semana com chamada clara pro DM ('me chama no direct se quiser saber mais')" |
| Objetivo: R$5k/mês · Ramo: infoprodutor · Nível: 4-6 | "Mapear quantas vendas precisa ter na média do ticket atual pra bater R$5k. Anotar a meta semanal." |
| Objetivo: sair do CLT · Ramo: profissional-clt · Nível: 0-2 | "Listar 3 coisas que você sabe fazer que alguém pagaria. Vamos escolher 1 pra testar essa semana." |
| Objetivo: 10k seguidores · Ramo: criador-conteudo · Nível: 3-5 | "Definir 1 tema-âncora dos seus posts. Postar 3 conteúdos esse formato essa semana." |
| Objetivo vago / risco "medo de me expor" | "Gravar 1 vídeo curto SÓ pra você (não publicar). Quebra o medo da câmera. Depois decidimos se publica." |

**Princípio:** primeiro passo precisa ser tangível, dia 1 ou 2 (não daqui a 30 dias), e baixo investimento de risco emocional.

---

## Templates de Output

### Seção "Direção" do `CLAUDE.md`

```markdown
## Direção 90 dias

- **Objetivo:** [OBJETIVO CONCRETO E MENSURÁVEL]
- **Risco principal a vigiar:** [MEDO]
- **Nível IA:** [N]/10 — calibrar profundidade técnica das respostas

**Refinado em:** [DATA]
**Próxima revisão sugerida:** [DATA + 30 dias]
```

### `personal/memory/project_objetivo-90d.md`

```markdown
---
name: Objetivo 90 dias
description: Direção principal do cliente refinada via /refinar-direcao em [DATA]. Próxima revisão em [DATA + 30 dias].
type: project
data_criado: [YYYY-MM-DD]
---

**Objetivo:** [OBJETIVO]

**Mensurável como:** [MÉTRICA OU MARCO]

**Risco principal:** [MEDO]

**Why:** Cliente declarou em D+3 ao /refinar-direcao. Direção amarra todas as sugestões futuras de Claude.

**How to apply:** Antes de sugerir qualquer ação, validar internamente: *"Aproxima do objetivo declarado?"* Se não, não sugerir. Se sim, executar e medir.
```

---

## Anti-patterns

- Aceitar objetivo vago e seguir adiante (sem mensurabilidade, todo o coach falha depois)
- Tentar virar terapeuta no medo declarado ("você consegue!") — anotar e usar pra calibrar, não consolar
- Sugerir primeiro passo grande demais (1 mês de execução) — quebra a confiança da pessoa
- Pular o espelho do Passo 3 — pessoa precisa ver que entendeu antes de seguir
- Inflar a conversa com filosofia ("e por que esse objetivo?") — coletou? avança.
