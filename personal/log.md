---
title: "Log — Linha do tempo"
tipo: cronologico
inicio: 0000-00-00
---

# Log — Linha do tempo append-only

> **NÃO EDITAR linhas anteriores.** Só append no fim.
> Cada **consolidação material** escreve 1 linha — `/rem-sleep` com mudança real, decisão grande, ingest de fonte externa.
> Format: `## [YYYY-MM-DD HH:MM] <op> | <título curto>`
>
> Operações: `rem` (consolidação) · `decision` (decisão grande) · `ingest` (fonte externa lida)

---

(vazio — primeiras entradas aparecem após primeiro `/rem-sleep`)
