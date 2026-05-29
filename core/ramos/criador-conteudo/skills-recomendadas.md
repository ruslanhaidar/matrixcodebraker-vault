# Skills extras recomendadas — Ramo Criador de Conteúdo

> Lista priorizada que `/desabrochar` consulta no Passo 5 (auto-discovery). Top 2-3 viram sugestão concreta pro cliente.

---

## Tier 1 — recomendadas pra TODO criador (independente de plataforma)

### `scrape-reel`
- **Faz:** baixa imagens do Pinterest pra montar B-roll automaticamente
- **Por que recomendar:** elimina horas procurando imagem manual
- **Ativa quando:** plataforma "Instagram" OU "TikTok" + nível IA ≥ 2
- **Status:** existe versão NM5D · genérica a portar

### `reel-pos-postagem`
- **Faz:** pipeline pós-publicação — transcreve, captura métricas, gera análise
- **Por que recomendar:** transforma cada post em aprendizado calibrado
- **Ativa quando:** mesma plataforma + nível IA ≥ 3 (precisa um pouquinho de paciência técnica)
- **Status:** existe versão NM5D · genérica a portar

---

## Tier 2 — recomendadas se aparecer plataforma específica

### Se plataforma inclui "Telegram"
- `telegram-refina` — lapida texto bruto pro canal sem reescrever a voz
- Status: existe versão NM5D · genérica a portar

### Se plataforma inclui "WhatsApp"
- `whatsapp-atendimento` — templates de resposta rápida sem soar robô
- Status: a criar

### Se gargalo declarado é "tempo"
- `note` (já no core) — captura ideia rápida zero fricção
- Reforçar uso na missão D+2

### Se plataforma inclui "e-mail" / "Brevo" / "MailerLite"
- `email-copy` — sequências calibradas
- Status: a criar

---

## Tier 3 — só se cliente sinalizar interesse explícito

### Se cliente menciona "vou lançar curso" ou "ebook"
- `kdp-book-publishing` — preparação de manuscrito KDP
- `lp-template` — landing page

### Se cliente menciona "consultoria 1:1" ou "atendimento"
- `whatsapp-atendimento`
- Estrutura de pasta `100-CLIENTES/` adicional

---

## Lógica de seleção pra `/desabrochar`

```text
candidatas = []

para skill em Tier 1:
  if plataformas do cliente match skill.triggers:
    if nível IA ≥ skill.minimo:
      candidatas.append(skill, score=2)

para skill em Tier 2:
  if plataformas/gargalo match skill.triggers:
    candidatas.append(skill, score=1)

# Tier 3 SÓ se cliente mencionou ativamente o trigger no /desabrochar

ordenar candidatas por score (Tier 1 vence Tier 2)
top 2 → sugerir ao cliente
```

**Regra dura:** nunca sugerir mais de 3 skills numa só vez pra leigo. Afoga. Se 5 são candidatas, escolher top 2 + dizer *"Tem outras 3 que faria sentido pra você. Posso te mostrar daqui a uns dias quando você já tiver pegado o jeito dessas."*
