# Matrix Code Braker

> Plugin Claude Code que monta seu Jarvis pessoal. Setup guiado por entrevista (5 perguntas, 2 min). Um segundo cérebro offline que te conhece e executa.

[![Plugin Claude Code](https://img.shields.io/badge/plugin-claude--code-purple)](https://docs.claude.com/en/docs/claude-code/plugins)

---

## ⚖️ Artigo 1

**O cérebro humano não foi feito pra guardar tanta informação. Este setup é a extensão dele: um Jarvis offline, na sua máquina, que guarda tudo, te conhece de verdade e executa — rápido, prático, sem expor sua vida a ninguém.**

Toda skill, ramo, sugestão. Se não tira peso do seu cérebro nem te devolve tempo, não entra.

---

## 🚀 Como instalar (3 comandos, sem terminal)

> **Nunca usou o Claude Code?** Começa pelo guia do zero, com todos os cliques: [docs/INSTALACAO.md](docs/INSTALACAO.md) (~15 min).

### Pré-requisitos

1. **[Claude Code](https://claude.com/claude-code)** instalado e logado
2. **MarkItDown** (1 linha no terminal, opcional mas recomendado):
   ```bash
   pip install "markitdown[all]"
   ```
   → permite eu ler PDF, Word, PowerPoint, Excel, imagem, áudio que você mandar
3. **Python 3.10+** (se ainda não tiver, instalar de [python.org/downloads](https://python.org/downloads))

### Instalação

Abre o Claude Code em qualquer pasta (vazia, de preferência — vai virar sua pasta de trabalho). Cola na conversa, um por vez:

```text
/plugin marketplace add ruslanhaidar/matrixcodebraker-vault
```

```text
/plugin install matrixcodebraker@matrixcodebraker-vault
```

```text
/matrixcodebraker:desabrochar
```

Pronto. Responde as 5 perguntas (~2 min) e seu setup tá calibrado.

---

## 🧭 Comandos que você vai usar

Todos os comandos são prefixados com `/matrixcodebraker:` quando rodando no Claude Code (pra não conflitar com outros plugins).

| Comando | Quando |
|---|---|
| `/matrixcodebraker:desabrochar` | Primeira sessão — entrevista de calibração |
| `/matrixcodebraker:montar-ambiente` | Ambiente completo — Obsidian configurado + pastas organizadas (guiado) |
| `/matrixcodebraker:recall` | Antes de tarefa nova — eu trago contexto |
| `/matrixcodebraker:memory` | Guardar fato/decisão importante |
| `/matrixcodebraker:note` | Capturar ideia rápida sem cerimônia |
| `/matrixcodebraker:rem-sleep` | Fim do dia — consolido o que mudou |
| `/matrixcodebraker:tour` | Tour pós-entrevista (4 comandos básicos) |
| `/matrixcodebraker:o-que-voce-faz` | "Me mostra o que você sabe fazer pra mim agora" |
| `/matrixcodebraker:refinar-voz` | Missão D+1 — Claude imita seu jeito de falar |
| `/matrixcodebraker:refinar-direcao` | Missão D+3 — direção de 90 dias |
| `/matrixcodebraker:destravar` | Missão D+5 — plano concreto de 90 dias |
| `/matrixcodebraker:coach` | Sugestão de próximo passo quando travada |
| `/matrixcodebraker:atualizar` | Puxa updates do plugin |

> **Atalho:** se a pessoa só falar "oi" ou "começar", a skill `/desabrochar` é disparada automaticamente quando o plugin detecta primeira sessão.

---

## 📁 Como ficam as pastas

### Plugin (mora em `~/.claude/plugins/...` — auto-gerenciado)

```
matrixcodebraker/
├── .claude-plugin/
│   ├── plugin.json         ← manifest do plugin
│   └── marketplace.json    ← catálogo
├── skills/                 ← 13 skills (desabrochar, montar-ambiente, recall, memory, note, ...)
├── core/                   ← templates + ramos por nicho (read-only)
└── docs/                   ← documentação (Obsidian, FAQ)
```

Você nunca toca aqui. Updates chegam via `/matrixcodebraker:atualizar`.

### Sua pasta de trabalho (onde você abriu o Claude Code)

Depois do `/desabrochar`, sua pasta fica assim:

```
sua-pasta/
├── CLAUDE.md               ← suas regras pro Claude (gerado pela entrevista)
├── personal/
│   ├── PRIMER.md           ← seu objetivo ativo + próximos passos
│   ├── CHECKLIST.md        ← suas tarefas
│   ├── log.md              ← linha do tempo do que aconteceu
│   ├── memory/             ← memórias persistentes sobre você
│   └── 100-PROJETOS/       ← um folder por projeto/cliente
└── overrides/              ← regras suas que sobrescrevem o padrão
```

**Regra de ouro:** seu CLAUDE.md, personal/ e overrides/ são INTOCÁVEIS pelo plugin. Updates só mexem na pasta do plugin (que mora fora).

> **Ambiente completo:** rodando `/matrixcodebraker:montar-ambiente` depois da entrevista, a pasta ganha a config do Obsidian (`.obsidian/` — diário automático, corretor pt-BR, anexos organizados) + a estrutura de pastas do seu ramo (`200-PRODUCAO/`, `300-RECURSOS/`, `400-ARQUIVO/`...). Tudo guiado, você não configura nada na mão.

---

## 🔄 Atualizações

Quando lançamos skills novas, ramos novos ou correções:

```text
/matrixcodebraker:atualizar
```

Ou direto:

```text
/plugin update matrixcodebraker@matrixcodebraker-vault
/reload-plugins
```

Nada do seu CLAUDE.md, personal/ ou overrides/ é tocado.

---

## 🌳 Ramos por nicho

O plugin detecta seu ramo na entrevista (`/desabrochar`) e carrega regras específicas do nicho:

- `criador-conteudo` — Reels, TikTok, posts, copy de conteúdo (ativo)
- `e-commerce` (planejado)
- `infoprodutor` (planejado)
- `espiritual` (planejado)
- `fitness` (planejado)
- `financas` (planejado)
- `profissional-clt` (planejado)
- `educacao` (planejado)
- `generico` — fallback se não bater com nada

Ramos vivem em `core/ramos/<ramo>/` dentro do plugin.

---

## 🆘 Travou em algum passo?

- **Erro no `/plugin marketplace add`:** confirma que está logado no Claude Code (`/login`)
- **`/matrixcodebraker:desabrochar` não aparece:** rodar `/reload-plugins`
- **MarkItDown não instala:** instalar Python primeiro ([python.org](https://python.org/downloads))
- **Outros:** abrir issue em [github.com/ruslanhaidar/matrixcodebraker-vault/issues](https://github.com/ruslanhaidar/matrixcodebraker-vault/issues)

---

## 📜 Licença

Uso pessoal. Não redistribuir sem autorização. Detalhes em `LICENSE.md` (a criar antes da release pública).

---

## 🛠️ Para devs/colaboradores

Estrutura do plugin segue [doc oficial Claude Code](https://code.claude.com/docs/en/plugins). Pra testar local:

```bash
git clone https://github.com/ruslanhaidar/matrixcodebraker-vault
claude --plugin-dir ./matrixcodebraker-vault
```

Skills moram em `skills/<nome>/SKILL.md`. Manifest do plugin em `.claude-plugin/plugin.json`. Marketplace em `.claude-plugin/marketplace.json`.

PRs e issues bem-vindas.
