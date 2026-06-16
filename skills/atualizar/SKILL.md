---
name: atualizar
description: Puxa atualizações do plugin Matrix Code Braker via Claude Code marketplace. Skills, ramos e templates novos chegam por aqui. Use quando cliente digitar "/atualizar", "atualiza tudo", "puxa as novidades", ou quando email mensal de versão nova chegar. NÃO toca em CLAUDE.md, personal/ nem overrides/ — só atualiza o que o plugin entrega.
---

# /atualizar — Puxa Updates do Plugin

> O plugin Matrix Code Braker é distribuído via marketplace do Claude Code. Updates de skills, ramos e templates chegam por `/plugin update`. **Nada do que você escreveu (CLAUDE.md, personal/, overrides/) é tocado.**

---

## Quando usar

- Cliente digita `/atualizar`
- Email mensal de "o que mudou" chegou e cliente quer puxar
- Skill nova ou bug fix anunciado na comunidade
- Cliente reportou problema que já foi corrigido em versão posterior

## When NOT to Use

- Cliente está mid-task crítica (oferecer adiar pra fim do dia)
- Conexão de internet não disponível
- Cliente acabou de instalar há minutos (já está na versão mais nova)

---

## Workflow

### Passo 1 — Avisar e confirmar

```
"Vou puxar as novidades do Matrix Code Braker — skills novas, correções, ramos novos.

Isso NÃO mexe em nada seu (seu CLAUDE.md, suas pastas personal/ e overrides/ ficam intactas). Só o que vem do plugin é atualizado.

Topa? (sim/depois)"
```

Se "depois" → marcar pra reoferecer e seguir tarefa anterior.

### Passo 2 — Atualizar o marketplace

Rodar via Bash (pega versão mais nova do catálogo):

```bash
claude plugin marketplace update matrixcodebraker-vault
```

Se cair com erro (rede off, marketplace não registrado, etc), avisar:

> *"Deu erro puxando as novidades — pode ser internet ou marketplace não registrado. Tenta de novo daqui a pouco, ou me passa o erro pra eu ajudar a destravar."*

### Passo 3 — Atualizar o plugin

```bash
claude plugin update matrixcodebraker@matrixcodebraker-vault
```

Output mostra versão antiga → nova + lista de mudanças.

### Passo 4 — Recarregar dentro da sessão

```
/reload-plugins
```

Pega skills/ramos/templates novos SEM precisar reiniciar o Claude Code.

### Passo 5 — Mostrar resumo pro cliente

Pegar última seção do CHANGELOG do plugin (`${CLAUDE_PLUGIN_ROOT}/CHANGELOG.md` se existir, senão output do `plugin update`) e traduzir pra fala humana:

```
"Atualizado. Novidades dessa versão:

- [TRADUÇÃO EM PT DO QUE MUDOU DE RELEVANTE PRA ELA]
- [...]

Próximo update chega quando o time soltar uma versão nova — ou você pode digitar /atualizar a qualquer momento."
```

---

## O que esta skill NUNCA faz

- ❌ Tocar `CLAUDE.md` (gerado pelo `/desabrochar`)
- ❌ Tocar `personal/` (seu espaço — PRIMER, CHECKLIST, memory, log, projetos)
- ❌ Tocar `overrides/` (suas regras customizadas)
- ❌ Forçar atualização (cliente decide quando)
- ❌ Rodar mid-task sem perguntar

## Como o plugin é isolado

O plugin mora em `~/.claude/plugins/matrixcodebraker-vault-matrixcodebraker/` (ou path equivalente do seu SO). A pasta onde você abre o Claude Code é OUTRA — é onde seus arquivos pessoais vivem. As duas nunca se misturam.

Quando `/atualizar` roda, o Claude Code só mexe na pasta do plugin. Sua pasta de trabalho (com CLAUDE.md, personal/, overrides/) fica intacta.

---

## Anti-patterns

- Atualizar sem mostrar resumo do que mudou — cliente leigo precisa saber
- Tocar em arquivo da pasta de trabalho do cliente (qualquer skill que tente é bug)
- Forçar atualização sem perguntar
- Atualizar mid-task sem combinar
- Esquecer `/reload-plugins` depois — cliente fica vendo versão antiga
