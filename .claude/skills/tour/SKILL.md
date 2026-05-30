---
name: tour
description: Tour rápido pós-/desabrochar. Apresenta o setup criado, ensina 4 comandos básicos, sugere primeira missão concreta. Use logo após /desabrochar gerar os arquivos OU quando cliente digitar "/tour".
---

# /tour — Tour do Setup

> Princípio: **mostrar fazendo, não explicando.** Cliente acabou de passar pela entrevista — agora precisa saber como usar o que foi criado, sem ler manual.

## Quando disparar

- **Automático**: imediatamente após `/desabrochar` terminar de gerar arquivos
- **Manual**: cliente digita `/tour` ou pergunta "como uso isso?"

## When NOT to Use

- Cliente é dev avançado e indicou nível IA ≥ 8 no `/desabrochar` (oferecer atalho: *"Quer pular o tour? Tudo está documentado em README.md"*)
- Cliente já passou pelo tour antes (frontmatter `tour_feito: true` no CLAUDE.md)

---

## Workflow

### Passo 1 — Resumir o que foi criado

```
"Pronto. Calibrei meu setup pra você. Aqui está o que tem agora:

📄 CLAUDE.md  — minhas regras pra trabalhar com você (voz, vocabulário, direção)
📁 personal/memory/  — 4 memórias iniciais sobre você
📄 personal/PRIMER.md  — seu objetivo de 90 dias e próximos passos
📄 personal/CHECKLIST.md  — 5 missões pros próximos 7 dias

Quer ver o que tem nos arquivos ou prefere ir direto pro 'como usar'?"
```

Esperar resposta. Se "ver" → mostrar resumo curto (top do CLAUDE.md + Objetivo do PRIMER). Se "usar" → seguir Passo 2.

### Passo 2 — Ensinar os 4 comandos essenciais

Um por mensagem. Pequeno exemplo prático em cada.

**Comando 1 — `/recall`**

```
"Antes de qualquer tarefa nova, digite `/recall`. Eu carrego o contexto certo —
projeto que estava trabalhando, último passo, blockers, e te trago resumido.

Tenta agora: digita `/recall`."
```

Esperar cliente executar. Confirmar que funcionou.

**Comando 2 — `/memory salva`**

```
"Quando você decidir algo importante e quiser que eu lembre depois,
digite `/memory salva [o fato]`. Eu coloco no lugar certo automaticamente.

Exemplo: '/memory salva: tom de copy é informal, evitar formalidade no e-mail'

Tenta com algo seu — pode ser qualquer regra que apareceu na entrevista."
```

**Comando 3 — `/note`**

```
"Teve uma ideia no meio de outra coisa? `/note [ideia]`. Anotou, segue o jogo.

Sem cerimônia, sem classificar. A gente promove pra ação concreta depois."
```

**Comando 4 — `/rem-sleep`**

```
"No fim do dia, digita `/rem-sleep` (ou fala 'fecha o dia', 'boa noite').
Eu consolido o que mudou — daily, PRIMER, log.
Na primeira vez SEMPRE crio uma daily mínima — assim a gente já fixa o hábito.
Depois disso só toco em arquivo que mudou. Memória limpa, contexto preservado pra amanhã.

Tenta agora: digita `/rem-sleep` (ou 'fecha o dia') pra eu criar a sua daily inicial."
```

Esperar cliente executar (mesmo que rem-sleep só registre "dia de instalação" — fixa hábito + cria 1ª daily).

### Passo 3 — Bônus: Obsidian (opcional, 2min)

Antes de propor a primeira missão, oferecer o bônus visual:

```
"Bônus rápido (opcional, 2min) — sua pasta inteira também abre num programa chamado Obsidian (grátis). Ele mostra os arquivos visualmente, tipo caderno bonito + grafo de conexões. Quer que eu te guie a abrir agora?

(Responde 'Obsidian sim' / 'depois')"
```

Se "sim" → seguir `docs/OBSIDIAN.md` passo a passo (instalar Obsidian → abrir esta pasta como vault → instalar plugin obsidian-skills pra slash-commands rodarem dentro do Obsidian também).
Se "depois" → seguir Passo 4 direto.

### Passo 4 — Sugerir primeira missão

Ler `personal/CHECKLIST.md`, pegar o primeiro item (D+1), e propor:

```
"Sua primeira missão (do CHECKLIST D+1):

> [PRIMEIRA MISSÃO]

Vamos fazer agora? Ou prefere amanhã?"
```

Se "agora" → começar a missão.
Se "amanhã" → marcar `tour_feito: true` no CLAUDE.md e despedir.

---

## Pós-tour

Atualizar frontmatter do CLAUDE.md:

```yaml
tour_feito: true
data_tour: YYYY-MM-DD
```

---

## Anti-patterns

- Despejar 4 comandos numa lista única (cliente leigo perde)
- Explicar conceitos abstratos antes de mostrar uso (memória episódica > memória semântica)
- Tour com mais de 5 minutos (cliente cansa)
- Pular a primeira missão concreta (tour sem ação = perdido em uma semana)
