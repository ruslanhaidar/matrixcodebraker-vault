# claude-mobile/

Pasta de trabalho do **Claude Code rodando no celular** (app Claude Code mobile via GitHub).

Aqui ficam rascunhos, anotações, experimentos e tarefas curtas que o Ruslan toca direto do celular quando está fora do desktop. O desktop continua sendo o ambiente principal — esta pasta é a ponte mobile.

---

## Por que existe

O Claude Code no celular acessa GitHub direto (não o vault local). Pra trabalhar pelo celular, precisa de um repo público com pasta dedicada onde dá pra:

- Escrever rascunhos de copy, ideias, roteiros
- Anotar tarefas que aparecem em movimento
- Editar arquivos pequenos sem precisar do notebook
- Sincronizar trechos pro vault depois (manual)

Esta pasta **não substitui o vault** (`C:\Users\Nitro Five\Documents\Ruslan Vault\`). Funciona como caixa de entrada mobile.

---

## Como usar (pelo celular)

1. Abrir o app **Claude Code** no celular
2. Logar com a conta GitHub (`ruslanhaidar`)
3. Selecionar o repo `matrixcodebraker-vault`
4. Navegar até a pasta `claude-mobile/`
5. Pedir pro Claude criar/editar arquivo dentro desta pasta
6. O Claude commita direto no repo (sem PR — push pra `main`)

### Fluxo típico

- **Captura rápida:** "Cria `ideia-reel-X.md` com essa ideia: ..."
- **Rascunho de copy:** "Lapida esse texto em `copy-rascunho.md`: ..."
- **Tarefa:** "Anota essa pendência em `pendencias.md`"

---

## Limites do Claude Code mobile

- Não roda comando local (sem terminal, sem dev-browser, sem scripts)
- Não acessa o vault Obsidian (só este repo público)
- Não invoca skills customizadas do desktop
- Não dispara hooks (memória, REM-sleep, regen-editorial)
- Sem acesso a APIs privadas (Brevo, Hotmart, Yampi etc) — só leitura/escrita de arquivo
- Sem segredo no repo (público) — **nunca colar token, chave, email privado, .env aqui**

---

## Workflow recomendado

```
Celular (Claude Code mobile)
  └─ commita em claude-mobile/<arquivo>.md
       └─ push pra main no GitHub

Desktop (sessão Claude Code normal)
  └─ git pull (puxa o que foi commitado pelo celular)
  └─ revisa arquivos novos em claude-mobile/
  └─ promove conteúdo relevante pro vault (copy/, diario/, projeto/)
  └─ arquiva ou apaga após migrar
```

A pasta funciona como **inbox** — não deve crescer indefinidamente. Conteúdo migra pro vault e é apagado daqui.

---

## Convenções de arquivo

- **Nome em kebab-case:** `ideia-reel-jyotish.md`, `copy-email-rascunho.md`
- **Prefixo opcional por tipo:**
  - `ideia-` — brainstorm bruto
  - `rascunho-` — texto em construção
  - `pendencia-` — tarefa anotada
  - `nota-` — observação genérica
- **Markdown sempre.** Sem PDF, sem DOCX, sem imagem grande (peso desnecessário em repo público).

---

## Segurança — proibido nesta pasta

- ❌ Tokens, chaves de API, senhas
- ❌ Email privado de cliente, CPF, dados pessoais
- ❌ Conteúdo de produto pago (manuscritos, audio-fonte)
- ❌ Trecho de leitura Jyotish de cliente
- ❌ Variáveis de ambiente, paths absolutos do servidor

Tudo que entra aqui vira **público** no GitHub. Em dúvida, não comita — anota no celular pra mover depois pelo desktop.

---

## Migração pro vault (desktop)

Quando puxar pelo desktop:

```bash
cd ~/Documents/Ruslan\ Vault/  # ou path equivalente
# git pull no clone local do matrixcodebraker-vault
# revisar arquivos em claude-mobile/
# mover conteúdo relevante pra:
#   - 200-PRODUCAO/copy/ (copy lapidada)
#   - 200-PRODUCAO/Reels-videos/_inbox/ (ideias de reel)
#   - 100-PROJETOS/<slug>/PRIMER.md (pendência de projeto)
#   - 000-META/log.md (decisão durável)
# apagar arquivo de claude-mobile/ após migrar
# commit + push
```

---

**Última atualização:** 2026-06-14
