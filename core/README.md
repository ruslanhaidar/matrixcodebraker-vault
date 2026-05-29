# core/ — Gerenciado pela equipe Matrix Code Braker

> **NÃO EDITE ESTES ARQUIVOS DIRETAMENTE.**
>
> Quando você roda `/atualizar`, esta pasta é sobrescrita com a versão mais recente do repositório oficial. Qualquer edição manual aqui será **perdida**.
>
> Pra customizar comportamento, use `overrides/`. Detalhes em `../overrides/README.md`.

---

## O que tem aqui

```text
(raiz do vault)
├── .claude/                   ← carrega na raiz pro Claude Code achar as skills
│   ├── skills/                ← 12 skills que dão poderes ao Claude
│   │   ├── desabrochar/       ← entrevista de personalização (uma vez por cliente)
│   │   ├── memory/            ← salvar fato/decisão em destino único
│   │   ├── recall/            ← recuperar contexto antes de tarefa nova
│   │   ├── rem-sleep/         ← consolidação fim de dia (gates de mudança real)
│   │   ├── note/              ← captura rápida de ideia (zero fricção)
│   │   ├── tour/              ← tour pós-desabrochar (4 comandos + primeira missão)
│   │   ├── o-que-voce-faz/    ← revela capacidades calibradas (estágio + ramo)
│   │   ├── refinar-voz/       ← ajusta a voz do Claude pra do cliente (D+1)
│   │   ├── refinar-direcao/   ← ajusta direção 90d (D+3)
│   │   ├── destravar/         ← plano estratégico de 90 dias (D+5)
│   │   ├── atualizar/         ← puxa updates do core via git (esqueleto v0.1)
│   │   └── coach/             ← acompanhamento D+0..D+7 (esqueleto v0.1)
│   └── settings.json          ← settings padrão
│
core/                          ← gerenciado pela equipe · NÃO EDITE
├── 000-META/
│   ├── CLAUDE-base.md         ← template do CLAUDE.md (sobrescrito por /desabrochar)
│   ├── skills-catalogo.md     ← catálogo de skills extras pra auto-discovery
│   └── templates/             ← templates de PRIMER (cliente + projeto)
│
└── README.md                  ← este arquivo
```

---

## Versão atual

`0.1.0` — pré-release. Ainda em desenvolvimento ativo.

**Skills universais 100% funcionais:** `desabrochar`, `memory`, `recall`, `rem-sleep`, `note`, `tour`.

**Skills em esqueleto v0.1** (lógica conceitual pronta, implementação técnica final pendente):

- `atualizar` — depende de decisão Ahmed sobre stack do instalador
- `coach` — lógica de tracking automático ainda em desenho

**Skills extras** disponíveis via auto-discovery em `000-META/skills-catalogo.md`. Algumas existem em versão NM5D-específica e ainda precisam ser portadas pra versão genérica.

---

## Como atualizações chegam

Quando lançamos uma versão nova:

1. Você recebe email com changelog ("o que mudou esse mês")
2. Roda `/atualizar` (ou aceita atualização automática mensal)
3. `core/` é sobrescrito · `personal/` e `overrides/` ficam intocados

---

## Reportando bugs

Bugs no core: GitHub Issues do repo oficial (link a publicar)
Sugestões de skills novas: comunidade Telegram/Discord (link a publicar)
