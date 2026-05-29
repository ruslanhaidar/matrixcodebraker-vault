---
name: memory
description: Salva fatos, decisões e configurações em UM destino único, escolhido pela classificação. Use quando o cliente disser "lembra que", "salva isso", "anota", "guarda" ou quando uma decisão importante for tomada. Cada fato vai pra um único lugar — sem espelhar.
---

# /memory — Salvar em Memória Persistente

> Princípio: **um destino único, escolhido pela classificação.** Duplicação destrói o índice. Antes de salvar, identifica o tipo do fato e escolhe um único lugar.

## When NOT to Use

- Estado temporário de uma sessão (não precisa persistir além dela)
- Informação derivável lendo outros arquivos do vault (não duplicar — usar Read)
- Decisão já documentada em PRIMER do projeto (já está no lugar certo)
- Senhas, tokens, credenciais ou dados sensíveis (risco de leak)
- "Salvar pra não esquecer" sem categoria — virar lixeira destrói o índice
- Conversa exploratória sem decisão tomada (espera a decisão sair)
- Fato que não será reutilizado em 3+ sessões futuras — vai pro PRIMER local
- Assunto já coberto por uma skill específica (editar a skill em vez de criar entrada nova)

---

## Regra — UM destino, escolhido pela classificação

| Tipo de fato | Destino | Quando usar |
|---|---|---|
| **Regra durável / preferência permanente** | `core/000-META/CLAUDE-base.md` (se override) ou `overrides/voice-rules.md` | "Sempre fazer X", "Nunca usar Y", convenção que vale pra todos os projetos do cliente |
| **Estado de projeto específico** (objetivo, próximo passo, blocker) | `personal/100-PROJETOS/<slug>/PRIMER.md` | Decisão que muda o que está sendo feito num projeto |
| **Tarefa pendente** | `personal/100-PROJETOS/<slug>/CHECKLIST.md` se existir, senão `personal/CHECKLIST.md` global | "Fazer X até Y" |
| **Acontecimento cronológico** (decisão grande, milestone) | `personal/log.md` (append-only) | Algo digno de linha do tempo |
| **Fato sobre cliente, ferramenta externa, referência reutilizável** | `personal/memory/<tipo>_<slug>.md` + entrada em `personal/memory/MEMORY.md` | Fato que volta em sessões futuras |

**Regra de ouro:** se o fato cabe em mais de um destino, escolha o mais específico. Estado de projeto vence regra global. Tarefa vence acontecimento.

---

## Workflow

### Passo 1 — Classificar
Identificar o tipo do fato consultando a tabela acima.

### Passo 2 — Confirmar destino se ambíguo
Se cabe em 2+ destinos, perguntar:
> "Salvar como (a) regra global em overrides/, (b) estado de `<projeto>` no PRIMER, (c) tarefa no CHECKLIST? Qual?"

Não duplicar pra "garantir". Duplicação é o que destrói o índice ao longo do tempo.

### Passo 3 — Salvar no destino único
- **`overrides/voice-rules.md`**: append na seção apropriada. Se a seção não existe, criar.
- **PRIMER local**: atualizar Objetivo / Próximo Passo / Blockers, ou adicionar a `## Decisões Arquivadas` (só se for decisão arquitetural).
- **CHECKLIST**: adicionar item com `- [ ] descrição`.
- **`personal/log.md`**: append no fim com formato `## [YYYY-MM-DD HH:MM] decision | <título>` + 1 frase + links.
- **`personal/memory/`**: criar arquivo `<tipo>_<slug>.md` com frontmatter (name, description, type) + corpo. Adicionar linha em `MEMORY.md` na seção apropriada (Usuário / Feedback / Projeto / Referência).

### Passo 4 — Confirmar
> "Salvo em `<destino>`: [resumo do fato]"

---

## Exemplos genéricos

```
"Sempre escrever em PT-BR mesmo quando perguntar em EN"
→ Regra durável → overrides/voice-rules.md

"Loja online: próximo passo é cadastrar 7 produtos novos"
→ Estado de projeto → personal/100-PROJETOS/loja-online/PRIMER.md (Próximo Passo)

"Configurar pixel Meta antes de postar próximo Reel"
→ Tarefa → personal/CHECKLIST.md (## Reels)

"Decidi formalizar pacote premium com upsell de mentoria 1:1"
→ Acontecimento cronológico → personal/log.md (decision)

"Cliente Maria fatura R$8k/mês via Hotmart, quer chegar a R$30k em 6 meses"
→ Fato sobre cliente → personal/memory/user_maria.md
```

---

## Anti-patterns

- Salvar em duas camadas pra "garantir" — escolher uma e confiar
- Usar memory pra coisa que já tá no PRIMER local
- Inflar regras globais com decisão de 1 projeto só (vai pro PRIMER)
- Inflar PRIMER local com regra global (vai pra overrides)
- Inflar log.md com tarefa pendente (vai pro CHECKLIST)
- Sugerir "vale salvar agora?" após toda tarefa — só se for claramente reutilizável em 3+ sessões futuras
- Criar entrada em memory pra regra que pertence a uma skill — editar a skill diretamente
