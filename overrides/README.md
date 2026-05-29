# Overrides — suas regras próprias

> Esta pasta é **sua**. Tudo o que você colocar aqui tem **precedência sobre `core/`**. É como você customiza Claude sem editar o core.

---

## Por que existe?

O `core/` é gerenciado pela equipe Matrix Code Braker. Quando lançamos atualizações (skills novas, fixes, melhorias), você puxa via `/atualizar` — e nada que você customizou se perde, **porque você não editou o core. Editou aqui.**

É o mesmo padrão que frameworks (Rails, Next.js, Laravel) usam: você não edita o framework, você sobrescreve.

---

## Como usar

Crie arquivos aqui com o mesmo nome dos arquivos do core que você quer ajustar. Quando Claude carrega regras, lê primeiro `core/`, depois sobrescreve com o que tiver em `overrides/`.

### Exemplos

**Adicionar regra de copy só sua:**
```
overrides/copy-rules.md
```
Crie esse arquivo com regras como "sempre usar 'cliente' em vez de 'lead'", "preço sempre em formato R$ X,XX". Claude vai aplicar antes de qualquer regra do core.

**Sobrescrever uma skill:**
```
overrides/skills/desabrochar/SKILL.md
```
Sua versão modificada da skill. Claude usa a sua.

**Adicionar regras de voz extras:**
```
overrides/voice-rules.md
```
Por exemplo: "evitar adjetivos em copy de venda — Hemingway-like", "usar 'você' nunca 'tu'".

---

## Quando NÃO usar overrides

- **Tarefa pendente** → vai pra `personal/CHECKLIST.md`
- **Memória de fato** → vai pra `personal/memory/` via `/memory salva`
- **Estado de projeto** → vai pra `personal/100-PROJETOS/<projeto>/PRIMER.md`

`overrides/` é só pra **regras de comportamento de Claude que sobrescrevem o core**.

---

## Regras de mim mesmo

Pode listar aqui, num documento solto, hábitos pessoais que quer que Claude respeite mesmo que o core não saiba. Ex: trabalhar em modo silencioso entre 7h-9h, não responder fora de horário comercial, etc.
