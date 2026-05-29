---
name: recall
description: Recupera contexto focado antes de iniciar tarefa nova. Recall focado lê CLAUDE.md + PRIMER local do projeto + última daily. Recall global só quando explicitamente pedido. Usar no início de sessão ou antes de tarefa complexa.
---

# /recall — Recuperar Contexto

> Princípio: **focado por padrão.** Lê só o necessário pro projeto detectado. Não inflar com PRIMER global ou CHECKLIST inteiro a menos que pedido.

## Quando usar

- Início de nova sessão
- Antes de iniciar tarefa nova ou complexa
- Quando contexto parecer incompleto
- Quando cliente perguntar "onde paramos?"

## When NOT to Use

- Continuação direta da mesma sessão (contexto já carregado)
- Pergunta simples que não precisa de contexto cross-projeto
- Quando cliente já forneceu o contexto necessário na própria mensagem
- Tarefa puramente exploratória sem projeto identificado
- Já rodou `/recall` há poucos minutos (não duplicar leitura)

---

## Passo 0 — Detectar projeto

1. **Primeira mensagem do cliente declara projeto?** ("vamos continuar a loja", "mexer no email")
2. **Diretório atual já dá pista?** (`personal/100-PROJETOS/<slug>/` aberto)
3. **Menciona ferramenta/produto associada a projeto conhecido?**

**Em caso de dúvida**: perguntar. *"Recall focado em `<slug>` ou global?"*

Se detectou projeto → **recall focado** (default).
Se cliente pediu explicitamente "/recall global" → **recall global**.

---

## Passo 1 — Ler fontes

### Recall focado (default — projeto detectado)

1. **`core/000-META/CLAUDE-base.md`** + **CLAUDE.md** personalizado (se desabrochado)
2. **PRIMER local** — `personal/100-PROJETOS/<slug>/PRIMER.md`
3. **Última daily do slug** (se houver) — glob `personal/100-PROJETOS/<slug>/daily/*.md`, ler a mais recente
4. **`overrides/`** — qualquer regra customizada do cliente que afete este contexto

**NÃO ler por padrão:** PRIMER global, CHECKLIST global, log inteiro. Se precisar de algo deles, ler sob demanda.

### Recall global (explícito)

1. **CLAUDE.md** personalizado
2. **`personal/PRIMER.md`** — objetivo macro do cliente
3. **`personal/CHECKLIST.md`** — tarefas cross-projeto
4. **Últimas 2-3 entradas de `personal/log.md`** (não o arquivo inteiro)

---

## Passo 2 — Resumo estruturado

### Formato (recall focado)

```
## Recall — <Nome do Projeto>

**Objetivo ativo:** [do PRIMER local]
**Próximo passo:** [do PRIMER local]
**Blockers:** [do PRIMER local, se houver]

**Última sessão:** [data + 1 frase do daily, se houver]

**Alertas:** [se houver pendência crítica]
```

### Formato (recall global)

```
## Recall — Contexto Geral

**Objetivo macro:** [do PRIMER global do cliente]
**Direção 90 dias:** [do CLAUDE.md, seção Direção]

**Últimas consolidações** (do log.md):
- [YYYY-MM-DD HH:MM] <op> | <slug> — 1 frase

**Tarefas cross-projeto pendentes:** [do CHECKLIST global, top 5]
```

---

## Passo 3 — Confirmar prontidão

> "Contexto carregado. Pronto pra continuar."

---

## Notas

- Se PRIMER local não existir, avisar: *"Projeto `<slug>` ainda sem PRIMER local — vai nascer no próximo `/rem-sleep` que tocar nele."* E rodar recall global como fallback.
- Se cliente ainda não rodou `/desabrochar` (CLAUDE.md = template), redirecionar gentil: *"Antes de carregar contexto, precisa rodar `/desabrochar` primeiro pra eu te conhecer."*
