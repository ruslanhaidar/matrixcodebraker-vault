# Matrix Code Braker — Core Vault

> Setup Claude pré-configurado pra você caminhar rumo a R$1.500+/mês via IA. **Esse é o seu vault.**

---

## ⚖️ Artigo 1

**Liberar a pessoa do trabalho fazendo ≥ R$1.500/mês com IA.**

Toda decisão deste setup se ajoelha pra essa frase. Conteúdo, ferramenta, sugestão minha — se não te aproxima do objetivo, não entra.

---

## 🚀 Primeiro uso — 5 minutos

1. **Instale o Claude Code** ([baixar aqui](https://claude.com/claude-code))
2. **Abra esta pasta no Claude Code** (File → Open Folder)
3. **Digite `/desabrochar`** (ou só "oi" — eu te chamo)
4. Respondo 5 perguntinhas rápidas (~2 min) e seu setup tá calibrado

Pronto. Daí já vai pra primeira tarefa concreta — algo entregue em 5 min.

---

## 📁 Estrutura do vault

```
matrix-code-braker-vault/
├── .claude/skills/      ← skills que dão poderes ao Claude (carregam na raiz)
│
├── core/                ← gerenciado por nós · NÃO EDITE
│   ├── 000-META/
│   │   ├── CLAUDE-base.md      ← template (vira CLAUDE.md após /desabrochar)
│   │   └── templates/
│   └── README.md
│
├── personal/            ← seu espaço · 100% seu
│   ├── 100-PROJETOS/    ← um por projeto/cliente/iniciativa
│   ├── memory/          ← suas memórias persistentes
│   ├── PRIMER.md        ← seu objetivo ativo
│   ├── CHECKLIST.md     ← suas tarefas
│   └── log.md           ← linha do tempo do que aconteceu
│
└── overrides/           ← suas regras próprias · precedência sobre core
    └── README.md
```

**Regra de ouro:** mudou minha cabeça? Edite `overrides/`, não `core/`. Atualizações do core chegam via `/atualizar` sem quebrar suas customizações.

---

## 🧭 Comandos que você vai usar todo dia

| Comando | Quando |
|---|---|
| `/desabrochar` | Primeira sessão — entrevista de calibração |
| `/recall` | Antes de qualquer tarefa nova — eu te dou contexto |
| `/memory salva [fato]` | Guardar fato/decisão importante |
| `/note [ideia]` | Capturar ideia rápida sem cerimônia |
| `/rem-sleep` | Fim do dia — consolido o que mudou |
| `/atualizar` | Quando quiser puxar updates do core |
| `/tour` | Tour rápido depois da entrevista |

---

## 🔄 Como funcionam as atualizações

Sua versão do core fica linkada ao repositório oficial via Git. Quando lançamos:
- Skills novas
- Bug fixes
- Templates melhorados

Você roda `/atualizar` (ou aceita atualização automática mensal). **Nada do seu `personal/` ou `overrides/` é tocado.** Apenas `core/` é atualizado.

---

## 🆘 Travou em algum passo?

- Comunidade peer-to-peer: [link Telegram/Discord — preencher na release]
- Suporte direto Ruslan + Ahmed: 1x/semana ao vivo
- FAQ vivo: [link — preencher na release]

---

## 📜 Licença

Uso pessoal. Não redistribuir sem autorização. Detalhes em `LICENSE.md` (a criar antes da release).
