# Catálogo de Skills Extras

> Skills além do core universal (memory, recall, rem-sleep, note, tour, atualizar, coach, desabrochar). A skill `/desabrochar` consulta este catálogo no Passo 5 (auto-discovery) e sugere instalação baseada no perfil declarado pelo cliente.

---

## Como funciona

1. Cliente passa pela entrevista `/desabrochar`
2. No Passo 5, Claude lê este catálogo + cruza com:
   - Plataformas declaradas (pergunta 5 do bloco Negócio)
   - Tipo de atividade (pergunta 4 do bloco Negócio)
   - Nível IA (pergunta 13 — afeta complexidade aceitável)
3. Sugere top 2-3 skills mais relevantes pro perfil
4. Cliente confirma → skills baixadas e ativadas

**Não recomendar mais de 3 de uma vez** — cliente leigo afoga em opções.

---

## Skills disponíveis

### Conteúdo & Marketing

#### `scrape-reel`
- **O que faz:** raspa imagens do Pinterest pra montar B-roll de Reels/TikTok automaticamente. Recebe número do reel, extrai temas do roteiro, baixa imagens organizadas.
- **Quem precisa:** criadores que fazem Reels/TikTok com b-roll de imagens (não só talking head)
- **Triggers no `/desabrochar`:** plataforma "Instagram" ou "TikTok" + atividade "criador de conteúdo"
- **Status:** existe versão NM5D-específica · genérica a portar

#### `reel-pos-postagem`
- **O que faz:** pipeline pós-publicação — baixa vídeo + prints, transcreve com Whisper, captura métricas reais, gera análise de copy pra calibrar próximos roteiros.
- **Quem precisa:** quem posta Reel/TikTok e quer aprender com cada postagem (não só publicar e esquecer)
- **Triggers:** mesmas do scrape-reel + nível IA ≥ 3
- **Status:** existe versão NM5D-específica · genérica a portar

#### `lp-template`
- **O que faz:** gera landing page a partir de template canônico — Find&Replace de placeholders, ajuste de paleta, copy seção a seção. Acelera de horas pra minutos.
- **Quem precisa:** infoprodutores, e-commerce, quem vende online com LP própria
- **Triggers:** plataforma "Hotmart" / "Kiwify" / "Yampi" / "loja própria" + atividade "infoproduto" / "comércio"
- **Status:** a criar (template existe, virar skill)

#### `email-copy`
- **O que faz:** ajuda a escrever emails de venda, sequências D+0..D+7, broadcasts. Respeita voz do cliente (regras do CLAUDE.md). Templates por tipo: lançamento, reativação, pós-venda.
- **Quem precisa:** quem usa email-marketing como canal principal de venda
- **Triggers:** plataforma "Brevo" / "MailerLite" / "ActiveCampaign" / "RD Station"
- **Status:** a criar

### Comunidade & Atendimento

#### `telegram-refina`
- **O que faz:** lapida texto bruto pro canal Telegram — corrige acentos/pontuação + adiciona emoji estratégico, sem reescrever a voz. NÃO escreve do zero.
- **Quem precisa:** quem mantém canal Telegram com posts próprios (não copia de outros)
- **Triggers:** plataforma "Telegram" + perfil "criador" ou "infoprodutor"
- **Status:** existe versão NM5D-específica · genérica a portar

#### `whatsapp-atendimento`
- **O que faz:** templates de resposta rápida pra WhatsApp Business. Responde dúvida frequente sem soar robô.
- **Quem precisa:** quem atende cliente direto no WhatsApp
- **Triggers:** plataforma "WhatsApp" + atividade que envolva atendimento
- **Status:** a criar

### Publicação & Editorial

#### `kdp-book-publishing`
- **O que faz:** prepara manuscrito pra KDP (impresso/ebook), Hotmart (PDF). Formatação, especificações, correção de erros, padronização de fonte.
- **Quem precisa:** quem está escrevendo livro ou já tem manuscrito pra publicar
- **Triggers:** objetivo declarado mencionar "livro", "ebook", "publicar"
- **Status:** existe versão genérica · adaptar pra core-vault

### Análise & Métricas

#### `business-metrics-calculator`
- **O que faz:** cálculo de métricas SaaS/e-commerce com benchmarks (MRR, churn, LTV, CAC).
- **Quem precisa:** SaaS, infoprodutor recorrente, e-commerce
- **Triggers:** plataforma "Hotmart" assinatura / "Stripe" / atividade "SaaS"
- **Status:** existe (skill da Anthropic)

### Nicho específico

#### `jyotish-leitura`
- **O que faz:** estrutura interpretação de mapa Jyotish (astrologia védica) seguindo método NM5D
- **Quem precisa:** astrólogos védicos especificamente
- **Triggers:** atividade declarada mencionar "astrologia védica", "Jyotish"
- **Status:** existe (NM5D-específica) · não portar genérica (é nicho)

#### `numerologia`
- **O que faz:** sistema de numerologia Ruslan Haidar — interpreta Destino, Dia, Mês, Ano Pessoal
- **Quem precisa:** numerólogos específicos (sistema Ruslan)
- **Triggers:** atividade "numerologia" + cliente vinculado a Dharma NM5D
- **Status:** existe (NM5D-específica)

---

## Lógica de auto-discovery (pseudocódigo)

```
para cada skill no catálogo:
  se triggers da skill matcham perfil do cliente:
    score += 1 por trigger matched
    se nível IA do cliente ≥ skill.complexidade_minima:
      adicionar à lista de candidatas

ordenar candidatas por score
top 3 → sugerir ao cliente
```

**Regras de tiebreaker:**
1. Skill que automatiza o gargalo declarado vence skill que automatiza periférico
2. Skill com versão genérica vence skill nichada (a menos que cliente seja do nicho)
3. Skill mais leve (< 100 linhas SKILL.md) vence pesada quando empate

---

## Adicionando skill nova ao catálogo

Quando criar skill nova no `.claude/skills/` (raiz):

1. Adicionar entrada neste catálogo na categoria certa
2. Definir triggers específicos (não vagos como "todos") — auto-discovery precisa precisão
3. Marcar status: `existe` / `a criar` / `versão genérica disponível` / `nicho`
4. Testar a auto-discovery rodando `/desabrochar` simulado com perfil hipotético

---

## TODO

- [ ] Portar skills marcadas "existe versão NM5D-específica · genérica a portar"
- [ ] Criar `lp-template`, `email-copy`, `whatsapp-atendimento` do zero
- [ ] Adaptar `kdp-book-publishing` pra core-vault genérico
- [ ] Validar o pseudocódigo de auto-discovery rodando 3 perfis simulados (criador Reels, infoprodutor, autor de livro)
