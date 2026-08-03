---
title: "Obsidian — bônus visual opcional"
tipo: documentacao
publico: cliente-final
---

# Obsidian — bônus visual opcional

> **Esse passo é opcional.** O setup funciona 100% só no Claude Code. Obsidian é um plus se você curte navegar visualmente.

> **Caminho normal (recomendado):** a skill `/matrixcodebraker:montar-ambiente` faz tudo isso guiada — inclusive escreve as configurações do Obsidian por você. Este doc é a versão manual, pra quem quer entender ou fazer na mão.

---

## Por que usar Obsidian junto?

- Vê seus arquivos numa interface bonita (tipo caderno digital)
- Wikilinks `[[arquivo]]` viram clicáveis — pula entre notas num clique
- Grafo visual mostra como as ideias se conectam
- Daily notes (uma anotação por dia) fica fácil de criar
- **Mesma pasta dos dois lados** — o que você editar no Obsidian, o Claude Code vê. E vice-versa. Sem duplicação.

---

## Passo 1 — Instalar Obsidian (3 min)

1. Vai em [obsidian.md](https://obsidian.md)
2. Clica em **Get Obsidian for Windows** (ou Mac, ou Linux — qual for seu sistema)
3. Roda o instalador, abre

---

## Passo 2 — Abrir esta pasta como vault (1 min)

Quando abrir Obsidian pela primeira vez:

1. Clica em **Open folder as vault**
2. Navega até **a mesma pasta** que você abriu no Claude Code (a pasta onde tá seu `CLAUDE.md` + `personal/` + `overrides/`)
3. Confirma — Obsidian gera config default e carrega tudo

Pronto. Você já vê sua pasta com cara de caderno.

> **Diário automático:** se o Claude já escreveu a config via `/matrixcodebraker:montar-ambiente`, o diário já aponta pra `personal/100-PROJETOS/onboarding/daily/` — não precisa ajustar nada em Settings. Fazendo manual (sem a skill), ajuste em **Settings → Core plugins → Daily notes** o "New file location" pra esse mesmo path.

---

## Passo 3 — Plugin **obsidian-skills** (experimental, opcional)

O plugin `obsidian-skills` existe na comunidade Obsidian e tenta rodar comandos `/recall`, `/memory`, etc. dentro do Obsidian. **Importante:** ele lê skills de `.claude/skills/` ou `~/.claude/skills/`, mas o Matrix Code Braker é distribuído como plugin Claude Code (mora em `~/.claude/plugins/`). Pode ser que `obsidian-skills` não enxergue as skills automaticamente.

**Recomendação por enquanto:** roda os comandos no Claude Code mesmo. Obsidian fica só pra navegação visual. Quando `obsidian-skills` suportar lookup de plugins Claude Code, atualizo este doc.

Se quiser tentar mesmo assim:

1. No Obsidian, abre **Settings** → **Community plugins** → **Turn on community plugins**
2. **Browse** → busca "**Claude Skills**" ou "**obsidian-skills**"
3. **Install** → **Enable** → reinicia Obsidian
4. Testa: `Ctrl+P` → digita `Skill:` — se aparecer lista, funcionou. Se vier vazio, plugin não pegou as skills do Matrix Code Braker.

---

## Passo 4 — Atalhos úteis (depois você customiza)

| Atalho | Faz |
|---|---|
| `Ctrl+O` | Pula pra qualquer arquivo (busca por nome) |
| `Ctrl+P` | Command Palette (executa qualquer comando, incluindo skills) |
| `Ctrl+G` | Abre/fecha grafo de conexões |
| `Ctrl+E` | Alterna entre edição e visualização |
| `Ctrl+Click` em `[[wikilink]]` | Abre o arquivo em painel ao lado |

---

## Dúvidas frequentes

**P: Preciso usar Obsidian? Não dá só com Claude Code?**
R: Dá. Obsidian é só pra navegação visual. Skills, memória, calibração — tudo funciona 100% só no Claude Code.

**P: Se eu editar um arquivo no Obsidian, o Claude Code perde?**
R: Não. É a MESMA pasta. O Claude lê o arquivo atualizado na próxima sessão.

**P: O plugin `obsidian-skills` é obrigatório?**
R: Não. É só pra rodar `/rem-sleep` etc. dentro do Obsidian. Você pode sempre voltar pro Claude Code pra rodar comandos.

**P: Mexer no `.obsidian/` quebra alguma coisa?**
R: Não — é só configuração visual do Obsidian. Pode customizar à vontade. Vive na sua pasta, não tem nada a ver com o plugin Matrix Code Braker.

---

## Quando NÃO usar Obsidian

- Você nunca usou aplicativo de notas e não quer aprender uma ferramenta nova agora — fica só com Claude Code, sem culpa
- Seu computador é fraco e Obsidian pesa
- Você prefere editar markdown direto no VS Code (também funciona — qualquer editor abre)

---

## Próximo passo

Depois de instalar e abrir o vault, volta pro Claude Code e digita:

```text
/matrixcodebraker:tour
```

Eu te mostro como os arquivos conversam entre Claude Code e Obsidian na prática.
