---
name: o-que-voce-faz
description: Apresenta capacidades de Claude pro cliente de forma PROGRESSIVA, calibrada pelo estágio (D+0..D+90+), ramo e nível IA. Não é dump — mostra 3-5 capacidades relevantes pra ela AGORA. Use quando cliente disser "o que você sabe fazer", "do que você é capaz", "me ajuda com o quê", "me dá ideias", "me mostra opções", ou clicar em missão equivalente.
---

# /o-que-voce-faz — Capacidades Progressivas

> Cliente leigo não sabe o que pedir porque não sabe o que é possível. Maria nunca vai dizer "use WebFetch" — ela não sabe que existe. Esta skill **revela capacidades progressivamente**, calibradas pra fazer sentido pra ela AGORA. Sem dump, sem afogamento.

---

## ⚖️ Filtros

### Filtro 1 — Artigo 1
Cada capacidade apresentada se ajoelha ao Artigo 1: tira peso do cérebro da pessoa e põe no vault que eu opero — ou devolve tempo/capacidade a ela. Capacidade técnica que não tem aplicação prática pro caminho dela, **não menciona**.

### Filtro 2 — Lente do Leigo
- Capacidade descrita em 1 linha de fala humana, não jargão técnico
- Sempre vem com **1 exemplo concreto** aplicado ao ramo da pessoa
- Tempo estimado mostrado (3min / 10min / etc) pra ela calibrar

---

## When NOT to Use

- Cliente está mid-task pedindo outra coisa — não interromper. Anotar pra oferecer depois.
- Cliente avançado (nível IA ≥ 8) — oferecer atalho: *"Posso te dar a lista completa de capacidades técnicas em vez disso. Ou prefere ver organizado por estágio?"*
- Cliente acabou de chegar (≤ 30min pós-/desabrochar) — não despejar capacidades. Esperar primeiro uso real.

---

## Workflow

### Passo 1 — Detectar contexto

Ler:
- `CLAUDE.md` (raiz da CWD) — frontmatter pra saber estágio, ramo, nível IA, voz_refinada, direcao_refinada
- `personal/CHECKLIST.md` — quantas missões marcadas (proxy do estágio real)
- `personal/log.md` — última atividade real (calibra se cliente está em flow ou parado)
- `${CLAUDE_PLUGIN_ROOT}/core/000-META/capacidades-progressivas.md` — catálogo com capacidades por nível (mora no plugin)

### Passo 2 — Calcular estágio efetivo

Não é só dia desde install. É:

| Marcador | Estágio efetivo |
|---|---|
| Acabou de fazer `/desabrochar`, 0-1 missões marcadas | **Iniciação inicial** (D+0..D+3) |
| ≥ 2 missões marcadas + voz refinada | **Iniciação tardia** (D+4..D+7) |
| ≥ 1 projeto em `personal/100-PROJETOS/` + uso ≥ 3x/semana | **Aprofundamento** (D+8..D+30) |
| Reportou resultado concreto (venda / automação / entrega) | **Operação** (D+31..D+90) |
| Sem atividade há ≥ 14 dias OU declarou autonomia | **Autonomia** (D+91+) |

### Passo 3 — Selecionar 3-5 capacidades

Do `capacidades-progressivas.md`, filtrar:

```text
candidatas = []

para cada capacidade no catálogo:
  if capacidade.estagio_minimo ≤ estagio_efetivo:
    if capacidade.aplica_a_ramo(ramo_cliente):
      if capacidade.nivel_ia_minimo ≤ nivel_ia_cliente:
        score = relevancia_pro_gargalo(capacidade, gargalo)
        candidatas.append((capacidade, score))

ordenar por score
top 5 → apresentar
```

**Regra dura:** se Maria está no D+0..D+3, máximo **3 capacidades**. D+4..D+30, máximo **5**. D+30+, pode até **7**. Cliente leigo afoga rápido.

### Passo 4 — Apresentar

Formato escaneável, sem inflar:

```
"Algumas coisas que eu posso fazer pra você AGORA:

1. **[CAPACIDADE 1]** — [1 linha do que faz]
   Exemplo: [APLICADO AO RAMO DELA]
   Tempo: [X min]

2. **[CAPACIDADE 2]** — ...

3. **[CAPACIDADE 3]** — ...

Topa alguma agora? Ou quer que eu te mostre mais?"
```

**Importante:** sempre numerar (1, 2, 3) — cliente leigo escolhe pelo número, não precisa decorar nome técnico.

### Passo 5 — Executar OU adiar

Se cliente disser "1" / "a primeira" / nome da capacidade → executar
Se "depois" / "agora não" → marcar capacidades vistas em `personal/memory/feedback_capacidades.md` (não repetir essas mesmas em proximos disparos)
Se "quer mais" → mostrar próximas 3 capacidades disponíveis pro estágio
Se cliente perguntar "como você faz isso?" → explicar em 2-3 frases sem jargão técnico ("Pra ler perfil de outras confeiteiras, eu vou no Instagram delas, leio os 30 últimos posts, e te trago um resumo do que rola.")

### Passo 6 — Salvar histórico

Em `personal/memory/feedback_capacidades.md`:

```markdown
---
name: Capacidades já apresentadas
description: Lista de capacidades que Claude já mostrou ao cliente — evita repetir. Atualizado a cada /o-que-voce-faz.
type: feedback
---

## Capacidades já apresentadas

- [DATA] — [CAPACIDADE 1] · cliente reagiu: [topou / adiou / ignorou]
- [DATA] — [CAPACIDADE 2] · ...
```

---

## Como o Coach usa isso (oferta proativa)

`/coach` detecta gargalo declarado E capacidade que o resolve, e oferece NA HORA DA DOR — sem esperar cliente pedir `/o-que-voce-faz`.

**Tabela de triggers (referência rápida pro coach):**

| Gargalo declarado | Capacidade que destrava | Quando oferecer |
|---|---|---|
| "Não sei o que postar" | "Ler 3 perfis de [ramo dela] e trazer 10 ideias adaptadas" | Quando cliente repete a frase 2x ou faz ≥ 5 dias sem postar |
| "Falta tempo" | "Transformar áudio que você gravar em texto pronto pra post" | Após 1ª aplicação prática (cliente já viu valor) |
| "Não sei se tá funcionando" | "Resumir métricas dos seus últimos 10 posts" | Após cliente ter postado 5+ posts pós-instalação |
| "Como meus concorrentes fazem" | "Análise de 3 perfis concorrentes — o que postam, ritmo, hooks" | Quando cliente pergunta sobre concorrência |
| "Preciso de catálogo / lista" | "Compilar lista de [coisa] em formato organizado" | Sob menção direta |

Coach NÃO oferece tudo de uma vez. **1 capacidade no momento da dor.** Se cliente topar, segue. Se não topar, anota e não repete por 7 dias.

---

## Anti-patterns

- **Dump de capacidades** — "eu sei fazer X, Y, Z, W, V, U" perde leigo em 3 segundos
- **Jargão técnico** — "WebFetch", "scraping", "API", "tool use" — proibido. Sempre traduzir.
- **Capacidade sem exemplo aplicado** — "posso analisar dados" → vago. "Posso pegar suas vendas dos últimos 3 meses e te dizer qual produto vende mais" → concreto.
- **Apresentar capacidade que cliente NÃO TEM uso pra agora** — Maria no D+0 não precisa saber sobre integração com API Hotmart. Capacidade certa = capacidade que ela aplica essa semana.
- **Repetir capacidades já vistas** — coach lembra do que já ofereceu via `feedback_capacidades.md`
- **Esquecer Filtro 1 (Artigo 1)** — capacidade técnica fofa que não tira peso do cérebro nem devolve tempo, fora.
