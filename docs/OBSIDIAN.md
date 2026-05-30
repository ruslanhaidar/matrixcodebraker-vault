---
title: "Obsidian — bônus visual opcional"
tipo: documentacao
publico: cliente-final
---

# Obsidian — bônus visual opcional

> **Esse passo é opcional.** O setup funciona 100% só no Claude Code. Obsidian é um plus se você curte navegar visualmente.

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
2. Navega até a pasta `matrixcodebraker-vault` (a mesma que você abriu no Claude Code)
3. Confirma — Obsidian já carrega tudo, inclusive a configuração que vem no `.obsidian/` do repo (file explorer ligado, grafo ligado, daily notes apontando pra `personal/100-PROJETOS/onboarding/daily/`)

Pronto. Você já vê sua pasta com cara de caderno.

---

## Passo 3 — Instalar o plugin **obsidian-skills** (opcional, +5 min)

O plugin `obsidian-skills` faz os mesmos comandos `/desabrochar`, `/recall`, `/memory`, `/note`, `/rem-sleep` funcionarem **dentro do Obsidian também** — não só no Claude Code.

### Como instalar

1. No Obsidian, abre **Settings** (ícone de engrenagem, canto inferior esquerdo)
2. **Community plugins** → **Turn on community plugins** (confirma o aviso de segurança)
3. **Browse** → busca "**Claude Skills**" ou "**obsidian-skills**"
4. **Install** → **Enable**
5. Reinicia o Obsidian

### Como usar

- Abre a Command Palette (`Ctrl+P` / `Cmd+P`)
- Digita `Skill: ` e escolhe o comando (ex: `Skill: recall`)
- Ou cria atalho de teclado em **Settings → Hotkeys**

> **Atalho que funciona em qualquer momento:** `Ctrl+P` → `Skill: rem-sleep` no fim do dia. Equivalente a digitar `/rem-sleep` no Claude Code.

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
R: Não — é só configuração visual do Obsidian. Pode customizar à vontade (mas vai pro `overrides/` se quiser preservar em update de core).

---

## Quando NÃO usar Obsidian

- Você nunca usou aplicativo de notas e não quer aprender uma ferramenta nova agora — fica só com Claude Code, sem culpa
- Seu computador é fraco e Obsidian pesa
- Você prefere editar markdown direto no VS Code (também funciona — qualquer editor abre)

---

## Próximo passo

Depois de instalar e abrir o vault, volta pro Claude Code e digita:

```
/tour
```

Eu te mostro como os arquivos conversam entre Claude Code e Obsidian na prática.
