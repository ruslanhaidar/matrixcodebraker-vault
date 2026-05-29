# Ramo: Criador de Conteúdo

> Pacote pra cliente que vive de criar conteúdo nas redes — Reels, TikTok, posts, YouTube, podcast. Carrega vocabulário do nicho, exemplos de copy, estrutura de pastas e auto-recomenda skills extras relevantes.

**Persona-âncora:** criador iniciante a intermediário. Tem 100-50k seguidores. Posta com regularidade mas sente que poderia escalar. Maior dor: produção (tempo) ou alcance (algoritmo) ou conversão (não vira venda).

---

## O que esse pacote carrega

| Arquivo | Função |
|---|---|
| `CLAUDE-additions.md` | Bloco anexado ao CLAUDE.md — regras de copy do nicho, padrões de Reel/post |
| `vocabulario.md` | Termos do nicho que Claude pode usar (gancho, CTA, b-roll, etc) |
| `exemplos-copy.md` | Exemplos calibrados de hooks, CTAs, copy de bio |
| `skills-recomendadas.md` | Lista de skills extras pra `/desabrochar` auto-recomendar |
| `estrutura-vault.md` | Template de pastas que faz sentido pra criador |

---

## Quando ativar

`/desabrochar` detecta este ramo quando a resposta da Pergunta 3 (atividade) contém:
- "Reels", "TikTok", "Instagram", "Stories"
- "criador de conteúdo", "criadora de conteúdo", "influencer"
- "YouTube", "vlog", "vídeos"
- "podcast", "podcaster"

OU quando Pergunta 4 (plataformas) lista 2+ redes sociais sem mencionar venda direta.

---

## Como o cliente sente isso

Ele não vê esses arquivos. O que ele percebe:

- Claude já conhece o vocabulário dele desde o D+0 (não precisa ensinar o que é "gancho" ou "B-roll")
- Pasta do vault dele tem estrutura óbvia pra criador (pasta de Reels, pasta de Posts, pasta de Pinterest)
- Skills extras chegam pré-recomendadas (scrape-reel, reel-pos-postagem)
- Exemplos de copy nos prompts vêm já contextualizados pro mundo de criação
