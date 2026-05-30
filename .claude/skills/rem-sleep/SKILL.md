---
name: rem-sleep
description: Consolidação de sessão. 3 passos com gates de mudança real — daily só se houve entrega, PRIMER só se estado vivo mudou, log só se consolidação material. Sessão sem entrega não escreve nada.
---

# /rem-sleep — Consolidação de Sessão

> Princípio: **gates de mudança real.** Não consolida só porque a sessão acabou — consolida só se algo material aconteceu. Sessão exploratória sem entrega não gera daily, PRIMER imutado não é tocado, log só registra consolidação material.

---

## Quando disparar

**Automático** — ao detectar qualquer sinal de encerramento:
- Despedidas: "boa noite", "até amanhã", "vou dormir", "tchau", "bye"
- Fechamento: "encerrar", "é isso por hoje", "pode fechar"
- Contexto atingindo 80%+

**Manual** — via `/rem-sleep`.

## When NOT to Use

- Já rodou rem-sleep nesta sessão (não duplicar daily)
- Mid-task — interromper consolidaria estado parcial confuso

> **Exceção primeira sessão (D+0).** Se `personal/log.md` ainda não tem nenhuma entrada (cliente acabou de passar pelo `/desabrochar`), os gates de "houve material" são RELAXADOS — sempre criar uma daily inicial mínima ("dia de instalação · setup calibrado") + linha de log. Objetivo: fixar o hábito + garantir que cliente VEJA o output do rem-sleep funcionando na primeira tentativa. Sem essa exceção, leigo digita `/rem-sleep` no fim do D+0 e não vê nada acontecer → assume que "não funciona".

---

## Passo 0 — Detecção de primeira sessão (D+0)

**Antes de qualquer gate**, checar se `personal/log.md` existe e tem ≥ 1 entrada:

- **Existe + tem entrada** → fluxo normal (Passos 1-3 com gates).
- **Não existe OU vazio** → modo D+0: criar daily inicial mínima (template abaixo) + linha de log "instalação"; SKIPAR Passos 1-3 dos gates rigorosos. Resposta final: *"Primeira daily criada. Hábito fixado — amanhã eu volto sabendo onde a gente parou."*

### Template D+0 — `personal/100-PROJETOS/onboarding/daily/YYYY-MM-DD.md`

```markdown
---
data: YYYY-MM-DD
projeto: onboarding
---

# YYYY-MM-DD — Dia 0 · Instalação Matrix Code Braker

- Setup calibrado via `/desabrochar` (ramo: [RAMO], gargalo: [GARGALO])
- Primeira tarefa concreta: [TAREFA OU "não executada hoje"]
- Hábito fim-de-dia (`/rem-sleep`) fixado

## Links
- [[../../PRIMER]]
```

### Linha D+0 de `personal/log.md`

```markdown
## [YYYY-MM-DD HH:MM] rem | onboarding
Dia 0 · setup instalado · hábito fim-de-dia fixado
→ [[100-PROJETOS/onboarding/daily/YYYY-MM-DD]]
```

---

## Passo 1 — Escopo + decisão de checkpoint

Identificar **qual projeto foi tocado**. Prioridade:

1. **Primeira mensagem do cliente** — tema declarado. Vence path dominante em conflito.
2. **Path dominante** — arquivos mais editados na sessão.
3. **Skills invocadas** — ex: skill específica de produto → projeto desse produto.

**Sessão meta/multi-projeto** (memória, setup, onboarding): tema descritivo curto e **pular Passo 2 (PRIMER)**.

### Contar tópicos materiais (entrega/decisão/pendência real):

- **0 tópicos:** não escrever nada. Encerrar.
- **1 tópico claro:** salvar direto no PRIMER local. Sem perguntar.
- **Escopo ambíguo OU 2+ tópicos:** listar e perguntar:
  > "Tópicos: 1. [X] 2. [Y] — Quais salvar? (numera ou 'todos')"

  Esperar resposta. Salvar SÓ os aprovados.

---

## Passo 2 — Daily + PRIMER local + PRIMER global

### Daily (gate: houve material?)

**Só escrever daily se aconteceu pelo menos uma destas:**
- Entrega concreta (arquivo criado/editado, deploy, integração)
- Decisão tomada (não só explorada)
- Pendência nova ou pendência fechada

Sessão puramente exploratória **NÃO gera daily**.

Path: `personal/100-PROJETOS/<slug>/daily/YYYY-MM-DD.md`

Se já existe daily do mesmo projeto no dia: sufixar `-2`, `-3`.

**Template enxuto:**

```markdown
---
data: YYYY-MM-DD
projeto: <slug>
---

# YYYY-MM-DD — <Título descritivo>

- Máximo 3 bullets do que rolou (1 linha cada)
- Decisões e pendências entram inline ("decidido X", "pendente Y")

## Links
- [[../PRIMER]]
```

### PRIMER local (gate: estado vivo mudou?)

**O PRIMER local é o destino natural pra estado de projeto.** Estrutura mínima:

```markdown
# <Projeto> — PRIMER

**Objetivo Ativo:** [o que está sendo trabalhado agora]
**Próximo Passo:** [ação imediata]
**Blockers:** [impedimentos atuais; vazio se nenhum]
```

**Só escrever PRIMER local se MUDOU pelo menos um dos campos vivos:**
- Objetivo Ativo virou outro
- Próximo Passo virou outro
- Blockers novos / blockers resolvidos

Se a sessão fez trabalho dentro do mesmo Objetivo + mesmo Próximo Passo + sem novo Blocker → **não tocar o PRIMER**. O daily já registra.

**Se PRIMER não existe:** criar com template mínimo acima.

### PRIMER global (gate: mudança estrutural?)

**Só tocar `personal/PRIMER.md` se:**
- Projeto novo nasceu / arquivado
- Blocker cross-projeto novo ou resolvido
- Objetivo macro mudou
- Ferramenta ativa mudou

Sessão de rotina dentro do projeto **NÃO toca o global**.

---

## Passo 3 — log.md

**Só logar se houve consolidação material:**
- Daily foi escrita, OU
- PRIMER local mudou, OU
- Decisão arquitetural foi tomada

Sessão sem nenhum dos acima → **não logar**.

Append-only em `personal/log.md`. 1 linha por escopo:

```markdown
## [YYYY-MM-DD HH:MM] rem | <slug-projeto>
1 frase · principais mudanças
→ [[100-PROJETOS/<slug>/daily/YYYY-MM-DD]] · [[100-PROJETOS/<slug>/PRIMER]]
```

---

## Resposta final

> "Sessão consolidada."

Em contexto alto (80%+):
> "Contexto em [X]%. Memória consolidada. Recomendo iniciar nova sessão."

---

## Anti-patterns

- Listar 5 tópicos e perguntar quando há 1 assunto claro — salvar direto
- Escrever daily em sessão exploratória sem entrega
- Tocar PRIMER local quando Objetivo/Próximo passo/Blockers não mudaram
- Tocar PRIMER global com detalhe de 1 projeto só
- Daily com subseções repetindo o que tá no PRIMER
- Logar sessão que não produziu nada material
- Criar PRIMER local pra sessão meta/multi-projeto

---

## Fluxo resumido

```
despedida / contexto-alto
  ↓
[Passo 1]  Escopo → contar tópicos → checkpoint só se ambíguo/2+
  ↓
[Passo 2]  Daily (gate) + PRIMER local (gate) + PRIMER global (gate)
  ↓
[Passo 3]  log.md (gate: consolidação material?)
  ↓
resposta final
```
