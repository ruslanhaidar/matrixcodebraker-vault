---
desabrochado: false
versao_core: 0.1.0
---

# CLAUDE.md — Setup Matrix Code Braker

> Este arquivo é o **template inicial**. Ele será sobrescrito pela skill `/desabrochar` na sua primeira conversa com Claude. Não edite manualmente — use `overrides/` se quiser regras próprias.

---

## ⚖️ Artigo 1 — Norte do projeto

> **Liberar a pessoa do trabalho fazendo ≥ R$1.500/mês com IA.**

Toda interação Claude ↔ você se ajoelha pra essa frase. Se uma sugestão minha não te aproxima desse objetivo, ela não vale.

---

## 📍 Estado: setup inicial

Você acabou de instalar. Eu ainda não te conheço — vou rodar a entrevista `/desabrochar` na primeira mensagem pra calibrar.

Depois da entrevista, este arquivo será reescrito com:
- Quem você é
- O que você faz
- Sua voz (palavras-âncora + palavras proibidas)
- Sua direção 90 dias

---

## 🛠️ Estrutura do seu vault

```
core/        ← gerenciado pelo Matrix Code Braker. Não edite.
             Atualizações chegam via /atualizar.
personal/    ← seu espaço. Eu nunca toco aqui via update.
             100-PROJETOS/, memory/, PRIMER.md, log.md
overrides/   ← suas regras próprias.
             Têm precedência sobre core/.
```

**Regra:** quer mudar comportamento meu? Edite `overrides/`, não `core/`.

---

## 🧭 Comandos básicos

- **`/desabrochar`** — entrevista de personalização (uma vez só, normalmente)
- **`/recall`** — eu trago contexto antes de tarefa nova
- **`/memory salva [...]`** — guardo fato/decisão importante
- **`/note [...]`** — capturo ideia rápida
- **`/rem-sleep`** — consolido sessão (fim de dia)
- **`/atualizar`** — puxa atualizações do core

---

## 🔗 Links

- [README do core-vault](../README.md)
- [Como usar overrides](../../overrides/README.md)
