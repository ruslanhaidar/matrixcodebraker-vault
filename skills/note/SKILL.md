---
name: note
description: Captura ideia rápida sem cerimônia. Use quando o cliente disser "anota essa ideia", "joga na lista", "depois eu vejo isso", "ideia rápida". Não promove a tarefa, não classifica — só registra. Promoção pra CHECKLIST/PRIMER vem depois.
---

# /note — Captura Rápida de Ideia

> Princípio: **zero fricção.** O cliente teve uma ideia, registra rápido, segue o que estava fazendo. Classificação e priorização vêm depois (via `/memory` ou manualmente).

## Quando usar

- "Anota essa ideia"
- "Depois eu volto nisso"
- "Joga na lista"
- "Esquece, mas registra"
- Cliente comenta algo entre parênteses durante outra tarefa

## When NOT to Use

- Decisão arquitetural já tomada (vai pra `/memory`)
- Tarefa concreta com prazo (vai direto pra CHECKLIST com `- [ ]`)
- Bug crítico que precisa atenção AGORA (não enfileirar — resolver)

---

## Workflow

### Passo 1 — Capturar verbatim

Anexar 1 linha em `personal/notes.md` (criar se não existir):

```markdown
# Notas — captura rápida

> Ideias soltas. Sem priorização. Promover pra CHECKLIST/PRIMER quando virar ação concreta.

---

## YYYY-MM-DD

- HH:MM — <texto da ideia, verbatim do cliente>
```

### Passo 2 — Confirmar curtíssimo

> "Anotado."

Não pergunta. Não classifica. Não pede contexto. Não inflar.

---

## Promoção (separado da skill)

Quando o cliente disser "vamos pegar aquela nota da semana passada":
1. Ler `personal/notes.md`
2. Identificar nota relevante
3. Perguntar: *"Promover pra (a) tarefa no CHECKLIST, (b) próximo passo no PRIMER de algum projeto, (c) memória persistente?"*
4. Mover (não copiar) — apagar do notes.md depois de promover

---

## Anti-patterns

- Pedir pro cliente classificar na hora ("é tarefa ou ideia?") — fricção mata o fluxo
- Tentar entender contexto da ideia antes de anotar — só anota
- Notas com mais de 1 linha (vira essay) — se o cliente quer detalhar, sugerir promover pra PRIMER ou criar projeto
- Inflar `notes.md` indefinidamente — sugestão mensal: "Tem N notas em notes.md, vamos promover/apagar?"
