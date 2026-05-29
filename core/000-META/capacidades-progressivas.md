# Capacidades Progressivas

> Catálogo de capacidades de Claude organizadas por estágio do cliente, ramo e nível IA. Consumido pela skill `/o-que-voce-faz` e pela lógica de oferta proativa do `/coach`. **Capacidades aparecem PROGRESSIVAMENTE** — cliente leigo no D+0 não precisa saber tudo que existe.

---

## Princípio do progressive disclosure

Cliente leigo (a mãe do Ahmed) não precisa saber sobre WebFetch ou scraping no D+0. Ela precisa saber que pode pedir "escreve um post" e receber um post no jeito dela.

Capacidades são reveladas em 4 ondas:

1. **Onda 1 — Básicas (D+0..D+7):** o que justifica a instalação. Claude conversa, escreve, lembra.
2. **Onda 2 — Médias (D+8..D+30):** quando cliente já teve primeira vitória. Claude analisa, busca, organiza.
3. **Onda 3 — Avançadas (D+31..D+90):** quando cliente entende o jogo. Claude integra, automatiza, audita.
4. **Onda 4 — Técnicas (D+91+):** quando cliente é autônomo. Skills custom, scripts, APIs.

Saltar onda = afogar leigo. Ficar atrás da onda = subutilizar Claude.

---

## ONDA 1 — Básicas (Estágio Iniciação · D+0..D+7)

### Escrever copy no jeito do cliente
- **Tradução pra leigo:** "Eu escrevo seu próximo post / e-mail / mensagem usando seu jeito de falar"
- **Exemplo aplicado a criador-conteudo:** "Vou montar um post sobre seu trabalho — me cola um post antigo que você curtiu e eu faço outro melhor"
- **Exemplo aplicado a infoprodutor:** "Vou rascunhar e-mail de venda do seu próximo lançamento"
- **Tempo estimado:** 5min
- **Nível IA mínimo:** 0
- **Pré-requisito:** voz não precisa estar refinada (mas resultado melhora muito após `/refinar-voz`)

### Lembrar contexto
- **Tradução:** "Lembro de tudo que a gente falou. Pode pedir 'lembra do que a gente conversou' que eu volto"
- **Exemplo:** "Ontem você me disse seu objetivo é R$3k/mês. Hoje quando você pedir 'me ajuda com post', vou lembrar disso e mirar lá."
- **Tempo:** instantâneo
- **Nível IA mínimo:** 0

### Anotar ideia rápida
- **Tradução:** "Você teve uma ideia? Joga aqui que eu guardo. Não precisa categorizar nada."
- **Exemplo:** "'Anota: ideia de bolo low carb pra postar mês que vem' — pronto, salvei. Você não vai esquecer."
- **Tempo:** instantâneo
- **Nível IA mínimo:** 0

### Listar opções organizadas
- **Tradução:** "Te dou opções pra escolher quando você não sabe por onde começar"
- **Exemplo aplicado a criador-conteudo:** "Posso listar 5 ideias do que postar essa semana baseadas no que você faz"
- **Exemplo aplicado a empregada-buscando-saida:** "Posso listar 5 jeitos de transformar o que você sabe fazer em renda extra"
- **Tempo:** 3-5min
- **Nível IA mínimo:** 0

### Resumir um texto longo
- **Tradução:** "Você tem um texto grande pra ler? Cola aqui que eu te resumo nos pontos principais"
- **Exemplo:** "Cola um e-mail longo que veio de cliente, eu te entrego em 3 linhas o que ela tá pedindo"
- **Tempo:** 1-2min
- **Nível IA mínimo:** 0

---

## ONDA 2 — Médias (Estágio Aprofundamento · D+8..D+30)

### Buscar informação na internet
- **Tradução:** "Posso ir na internet, ler sites e te trazer informação atualizada"
- **Exemplo aplicado a criador-conteudo:** "Vou pesquisar 5 confeiteiras famosas no Brasil, ver o que elas postam, e te trazer 10 ideias inspiradas pra você adaptar"
- **Exemplo aplicado a infoprodutor:** "Vou buscar como [concorrente] precifica produto similar e te trazer comparação"
- **Tempo:** 5-10min
- **Nível IA mínimo:** 2 (cliente precisa entender que demora um pouquinho)

### Analisar perfis de redes sociais
- **Tradução:** "Posso olhar 3 perfis de pessoas parecidas com você no Instagram e te dizer o que elas fazem que dá certo"
- **Exemplo:** "Olho 3 confeiteiras com 5-20k seguidores, leio os últimos 30 posts, te entrego: padrão de horário, tipos de post, hooks que repetem, hashtags que usam"
- **Tempo:** 10-15min
- **Nível IA mínimo:** 3
- **Pré-requisito:** cliente precisa fornecer @ dos 3 perfis

### Transformar áudio em texto
- **Tradução:** "Você grava um áudio falando, eu transformo em texto pronto pra post"
- **Exemplo:** "Grava 1min falando sobre seu bolo de cenoura — eu transformo em post pronto pra Instagram, sem você precisar escrever"
- **Tempo:** 3-5min
- **Nível IA mínimo:** 2
- **Skill associada:** `reel-pos-postagem` (adapta pra esse uso)

### Compilar lista organizada
- **Tradução:** "Te ajudo a montar listas que você precisa — clientes, ideias, fornecedores, qualquer coisa"
- **Exemplo:** "Vamos compilar sua lista de clientes recorrentes, com info de contato e o que cada uma costuma comprar — pra você não perder ninguém"
- **Tempo:** depende da lista
- **Nível IA mínimo:** 1

### Comparar opções
- **Tradução:** "Tá em dúvida entre A e B? Eu listo prós e contras pra você decidir"
- **Exemplo:** "Devo cobrar R$30 ou R$50 por bolo? Vou pesquisar concorrentes em BH, comparar, e te ajudar a decidir baseado no seu posicionamento"
- **Tempo:** 5-10min
- **Nível IA mínimo:** 2

---

## ONDA 3 — Avançadas (Estágio Operação · D+31..D+90)

### Ler PDF / planilha / documento
- **Tradução:** "Você tem PDF de receita ou planilha de vendas? Cola que eu leio e te ajudo com o que estiver lá"
- **Exemplo:** "Cola sua planilha de vendas dos últimos 3 meses — vou te dizer quais bolos vendem mais, em quais dias, e qual margem de cada um"
- **Tempo:** 5-15min
- **Nível IA mínimo:** 4
- **Skill associada:** `business-metrics-calculator`

### Resumir vídeo / podcast
- **Tradução:** "Vídeo longo no YouTube ou podcast? Me passa o link, eu te resumo nos pontos principais"
- **Exemplo:** "Aquele vídeo de 1h sobre marketing pra confeiteiras — vou te entregar em 5 bullets o que importa pra você aplicar essa semana"
- **Tempo:** 5-10min
- **Nível IA mínimo:** 4

### Análise de métricas
- **Tradução:** "Você posta há um tempo, mas não sabe o que tá funcionando? Vou olhar suas métricas e te dizer onde focar"
- **Exemplo:** "Olho seus últimos 10 posts no Instagram, vejo qual teve mais engajamento, comparo com os piores, e te entrego: continue fazendo X, pare de fazer Y"
- **Tempo:** 15-20min
- **Nível IA mínimo:** 5
- **Skill associada:** `reel-pos-postagem` (versão analítica)

### Auditar tom de voz cross-canal
- **Tradução:** "Sua voz é consistente em todos os lugares? Vou comparar seu Instagram, e-mail e WhatsApp pra ver"
- **Exemplo:** "Olho seus 5 últimos posts IG + 3 últimos e-mails + 5 últimas conversas em WhatsApp Business. Aponto onde você soa diferente, sugere unificar"
- **Tempo:** 10-15min
- **Nível IA mínimo:** 5

### Criar landing page do zero
- **Tradução:** "Te entrego uma página de venda pronta pro seu produto"
- **Exemplo:** "Vamos fazer uma página de venda do seu pacote de bolos pra festa — copy, estrutura, cores. Só falta você publicar."
- **Tempo:** 30-60min
- **Nível IA mínimo:** 4
- **Skill associada:** `lp-template`

---

## ONDA 4 — Técnicas (Estágio Autonomia · D+91+)

> Esta onda só aparece pra cliente que demonstrou nível IA ≥ 7 ou pediu explicitamente capacidades técnicas. Cliente leigo NÃO recebe essas ofertas — não precisa.

### Rodar scripts simples
- **Tradução:** "Posso rodar pequenos programas pra automatizar tarefa repetitiva"
- **Exemplo:** "Toda semana você renomeia 50 fotos antes de postar? Vou rodar script que renomeia tudo de uma vez."
- **Nível IA mínimo:** 7

### Construir automações
- **Tradução:** "Posso conectar 2 ferramentas que você usa pra elas conversarem entre si"
- **Exemplo:** "Quando alguém comprar no Hotmart, automaticamente entrar no seu grupo de WhatsApp e receber áudio de boas-vindas"
- **Nível IA mínimo:** 7

### Skills custom
- **Tradução:** "Posso aprender uma rotina sua específica e virar um botão pra você usar"
- **Exemplo:** "Toda segunda você analisa concorrentes do mesmo jeito? Viro skill `/analise-segunda` que faz tudo de uma vez."
- **Nível IA mínimo:** 8

### Webhooks e integrações
- **Tradução:** "Conecto Claude com sites e APIs externas pra puxar/enviar dados em tempo real"
- **Exemplo:** "Toda venda nova no Hotmart, recebo notificação aqui e atualizo seu painel automaticamente"
- **Nível IA mínimo:** 8

---

## Mapeamento por ramo (filtro adicional)

Capacidades têm aplicações específicas por ramo. Quando `/o-que-voce-faz` filtra, prioriza por relevância:

### Ramo: criador-conteudo
**Top 3 onda 1:** Escrever copy · Listar ideias · Anotar ideia rápida
**Top 3 onda 2:** Analisar perfis · Áudio→texto · Buscar inspiração
**Top 3 onda 3:** Métricas · Auditar tom · Resumir referência

### Ramo: e-commerce
**Top 3 onda 1:** Escrever descrição produto · Resumir feedback cliente · Listar opções
**Top 3 onda 2:** Comparar precificação · Compilar lista clientes · Buscar concorrência
**Top 3 onda 3:** Ler planilha vendas · Análise métricas · LP de produto

### Ramo: infoprodutor
**Top 3 onda 1:** Escrever copy venda · Lembrar contexto · Listar ideias
**Top 3 onda 2:** Buscar concorrência · Comparar precificação · Áudio→texto
**Top 3 onda 3:** LP completa · Resumir vídeo curso · Análise métricas

### Ramo: empregada-buscando-saida
**Top 3 onda 1:** Listar opções (de renda) · Lembrar contexto · Anotar ideia
**Top 3 onda 2:** Buscar mercado pra habilidade · Compilar plano · Comparar opções
**Top 3 onda 3:** LP de serviço · Análise métricas (após primeiros testes)

---

## TODO de manutenção

- [ ] Validar com casos reais (5 clientes em estágios diferentes) se as ondas batem
- [ ] Adicionar capacidade nova quando criar skill nova no core
- [ ] Mapear ramos que ainda não têm "Top 3" listado
- [ ] Auditar trimestralmente: capacidade que ninguém topou em 90 dias = retirar ou reformular
