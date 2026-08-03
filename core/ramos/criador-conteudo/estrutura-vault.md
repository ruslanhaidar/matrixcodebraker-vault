# Estrutura de Vault — Ramo Criador de Conteúdo

> Template de pastas que `/montar-ambiente` cria automaticamente em `personal/` pro cliente do ramo criador-conteudo. Estrutura sugerida — cliente pode mudar.

---

## Estrutura

```text
personal/
├── 100-PROJETOS/                       ← um por iniciativa/projeto
│   └── (vazio inicialmente — cliente cria conforme nasce projeto)
│
├── 200-PRODUCAO/
│   ├── Reels/                          ← 1 pasta por Reel
│   │   └── exemplo-001/
│   │       ├── roteiro.md
│   │       ├── transcricao.md          ← preenchido pelo reel-pos-postagem
│   │       ├── metricas.md
│   │       └── imagens/
│   ├── Posts/                          ← carrosséis, posts estáticos
│   │   └── exemplo-001/
│   │       ├── copy.md
│   │       └── imagens/
│   ├── Stories/                        ← rascunhos de stories
│   └── Bio/                            ← versões da bio do perfil
│
├── 300-RECURSOS/
│   ├── Pinterest/                      ← biblioteca de B-roll
│   ├── Referencias/                    ← criadores que inspiram
│   └── Transcricoes/                   ← áudio/vídeo transcrito pra reuso
│
├── 400-ARQUIVO/                        ← conteúdo posted antigo
│
├── memory/                             ← memórias persistentes
│   └── MEMORY.md
│
├── PRIMER.md                           ← objetivo e próximos passos
├── CHECKLIST.md                        ← tarefas
└── log.md                              ← linha do tempo
```

---

## Por que essa estrutura

- **200-PRODUCAO/Reels/** pasta-mãe com 1 subpasta por Reel: roteiro+transcrição+métricas no mesmo lugar = aprendizado óbvio. Skill `reel-pos-postagem` automatiza.
- **300-RECURSOS/Pinterest/** centraliza biblioteca de imagens pra reuso. Skill `scrape-reel` despeja aqui.
- **300-RECURSOS/Referencias/** força hábito de catalogar inspiração com motivo (não só salvar). Combate "li 100 posts, lembro de 0".
- **Bio/** versionada porque bio é experimento — testa, mede, ajusta.

---

## O que o cliente NÃO vê

A pasta nasce pronta no `/montar-ambiente` — cliente abre Obsidian/Claude Desktop e a estrutura já tá lá. Ele não precisa criar nada manualmente.

O cliente pode RENOMEAR ou MUDAR. Claude detecta a mudança no próximo `/recall` e respeita a nova estrutura sem reclamar.

---

## Quando NÃO criar essa estrutura

- Cliente já tem Obsidian/sistema próprio organizado — perguntar antes de criar (não bagunçar o trabalho dele)
- Cliente declarou "tô começando do zero, não tenho nada" — criar livre
- Cliente é nível IA 8-10 — perguntar se prefere estrutura própria
