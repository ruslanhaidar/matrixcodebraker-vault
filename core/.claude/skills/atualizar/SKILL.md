---
name: atualizar
description: Puxa atualizações do core via git. Sobrescreve só `core/`, nunca toca `personal/` nem `overrides/`. Use quando cliente digitar "/atualizar" ou quando email mensal chegar avisando de versão nova. Esqueleto inicial — implementação técnica final depende da decisão de stack do instalador (Ahmed).
---

# /atualizar — Puxa Updates do Core

> ⚠️ **Esqueleto v0.1** — implementação técnica final depende da decisão do Ahmed sobre stack do instalador. Lógica conceitual abaixo está correta, mas o comando Bash exato pode mudar.

## Quando usar

- Cliente digita `/atualizar`
- Email mensal de "o que mudou no core" chegou e cliente quer puxar
- Skill nova ou bug fix anunciado na comunidade

## When NOT to Use

- Cliente está mid-task crítica (oferecer adiar pra fim do dia)
- Conexão de internet não disponível
- Repo `core/` não tem origem git configurada (estado inicial pré-instalador)

---

## Workflow conceitual

### Passo 1 — Verificar estado limpo

Conferir que `core/` não tem edições locais (cliente NUNCA deveria editar core direto, mas verificar):

```bash
cd <vault-root>/core
git status --porcelain
```

Se tiver mudanças locais em `core/` → **abortar** e avisar:
> *"Detectei edições manuais em `core/` — isso não devia acontecer. Antes de atualizar, vou mover suas edições pra `overrides/` pra não perder. Confirma?"*

### Passo 2 — Confirmar updates disponíveis

```bash
git fetch origin
git log HEAD..origin/main --oneline
```

Mostrar pro cliente o changelog dos commits que vão entrar:

```
"Atualizações disponíveis:

- abc1234 feat: skill nova /coach (acompanhamento D+0..D+7)
- def5678 fix: /desabrochar agora valida palavras-âncora vazias
- ghi9012 docs: README de overrides reescrito

Aplicar? (s/n)"
```

### Passo 3 — Aplicar

Se confirmado:

```bash
git pull origin main
```

**Crítico:** o repositório do `core-vault` é configurado tal que `personal/` e `overrides/` estão no `.gitignore` global do repo, então `git pull` JAMAIS toca neles. A engine fundamental disso depende da estrutura do repo decidida pelo Ahmed.

### Passo 4 — Confirmar e dar próximos passos

```
"Atualizado pra versão X.Y.Z.

Mudanças que afetam você:
- [tradução em PT do que mudou de relevante pro cliente]

Próxima atualização chega em ~30 dias por email."
```

---

## Roadmap de implementação (a fazer com Ahmed)

- [ ] Definir stack: git CLI exposto direto OU wrapper via app desktop OU script via Claude
- [ ] Configurar `.gitignore` no repo `core-vault` pra ignorar `personal/` e `overrides/`
- [ ] Strategy de merge — `git merge --strategy-option=theirs core/` ou submodule
- [ ] Tratamento de erro: rede off, conflito (não deveria acontecer mas...), permissão
- [ ] Auto-update mensal opt-in via cron/scheduler do SO
- [ ] Email de changelog automático (gerado a partir do log de commits)

---

## Anti-patterns

- Atualizar sem mostrar changelog — cliente leigo precisa saber o que muda
- Tocar em `personal/` ou `overrides/` (qualquer skill que faça isso é bug crítico)
- Forçar atualização (cliente decide quando)
- Atualizar mid-task sem perguntar
