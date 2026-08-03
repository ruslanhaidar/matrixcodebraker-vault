---
name: montar-ambiente
description: Monta o ambiente visual e a estrutura de pastas do cliente pós-/desabrochar — guia a instalação do Obsidian, copia a config pronta (.obsidian/) pra pasta do cliente, materializa a estrutura de pastas do ramo, e oferece VS Code só pra perfil avançado ou pedido explícito. Idempotente — detecta o que já existe e só faz o que falta. Use após /tour, ou quando o cliente pedir "montar ambiente", "instalar obsidian", "deixar bonito", "organizar vault/pastas".
---

# /montar-ambiente — Ambiente visual + vault organizado

> Mesma lente do `/desabrochar`: **a pessoa pode ser a mãe do Ahmed.** Nada de jargão, uma fase por vez, checkpoint humano em cada etapa. E o mesmo aprendizado do teste #1: **instrução de escrita/cópia é AÇÃO REAL com tool explícita** — nunca narração simbólica. Se você declarar "ambiente montado" sem ter rodado os Bash/Write/Read desta skill, você falhou.

---

## ⚖️ Princípios

1. **Idempotente:** cada fase checa o que já existe ANTES de agir. Rodar 2x não quebra nada.
2. **Cliente não configura nada manualmente:** toda config possível é escrita por você (Claude) via tools. Humano só instala programas e clica em "abrir pasta".
3. **Nunca sobrescrever o que é do cliente sem perguntar.**
4. **Jargão proibido na conversa:** skill, plugin, vault (fora do botão do Obsidian), repo, JSON, config, path. Falar "caderno", "pasta", "programa", "configurações".

## When NOT to Use

- Cliente ainda não passou pelo `/desabrochar` (sem `CLAUDE.md` com `desabrochado: true`) — rodar `/desabrochar` primeiro
- Cliente está mid-task — terminar a tarefa, oferecer depois
- Cliente recusou Obsidian esta semana (frontmatter `obsidian: recusado` no CLAUDE.md) — não oferecer de novo tão cedo; a Fase 3 (pastas) ainda pode rodar se ele pedir

---

## Fase 0 — Detecção silenciosa (RODAR ANTES DE FALAR COM O CLIENTE)

Executar via tools, sem narrar:

1. `Read` → `CLAUDE.md` (raiz da CWD) → pegar do frontmatter: `ramo`, e se existirem `obsidian` / `ambiente_montado`
2. `Bash` → `ls -d .obsidian 2>/dev/null; ls personal/ 2>/dev/null` → mapear o que já existe
3. `Read` → `${CLAUDE_PLUGIN_ROOT}/core/ramos/<RAMO>/estrutura-vault.md` (só se o arquivo existir — ramo `generico` não tem)

Com o mapa, abrir com UMA linha:

> "Dei uma olhada aqui: falta [X e Y]. Vamos resolver juntos em poucos passos — eu faço a parte técnica, você só instala um programa e clica em 'abrir pasta'. Bora?"

Se `ambiente_montado: true` e nada falta → *"Seu ambiente já tá completinho — não falta nada."* + encerrar.

---

## Fase 1 — Obsidian instalado (programa visual)

**Perguntar:**

> "Primeiro passo: um programa grátis chamado Obsidian — é ele que mostra seus arquivos com cara de caderno bonito. Você já tem ele instalado no computador? (responde 'tenho' / 'não tenho' / 'não sei')"

- **"tenho"** → seguir pro passo de abrir a pasta.
- **"não sei"** → `Bash` best-effort:
  - Windows: `ls "$LOCALAPPDATA/Obsidian/Obsidian.exe" 2>/dev/null`
  - Mac: `ls -d /Applications/Obsidian.app 2>/dev/null`

  Encontrou → *"Achei ele aqui no seu computador — já tá instalado."* Não encontrou → tratar como "não tenho".
- **"não tenho"** → guiar:

> "Tranquilo, 3 minutinhos:
> 1. Abre o navegador e entra em **obsidian.md**
> 2. Clica no botão grande de **Download** (ele já detecta seu Windows/Mac)
> 3. Abre o arquivo baixado e segue o instalador
>
> Me avisa quando ele abrir pela primeira vez."

**Checkpoint humano 1:** esperar o cliente confirmar que o Obsidian abriu. Erro de instalação → tabela Troubleshooting no fim.

**Abrir a pasta como vault:**

> "Ele vai perguntar sobre 'vault' (é o nome que ele dá pra 'pasta de caderno'). Clica em **'Open folder as vault'** (ou 'Abrir pasta como cofre') e escolhe ESTA pasta aqui:
>
> `[CAMINHO ABSOLUTO DA CWD]`
>
> É a mesma pasta onde a gente trabalha. Me avisa quando abrir."

**Checkpoint humano 2:** *"Você tá vendo seus arquivos na barra lateral esquerda? (CLAUDE.md, personal...)"* — só seguir com "sim".

**Se o cliente não quiser Obsidian** ("não quero", "depois", "pra que serve?"): respeitar, sem insistir.

> "Sem problema — tudo funciona aqui na conversa mesmo. Se um dia quiser ver bonitinho, é só me pedir 'montar ambiente'."

`Edit` no frontmatter do `CLAUDE.md`: adicionar `obsidian: recusado`. Pular a Fase 2 e ir direto pra Fase 3 (estrutura de pastas vale independente do Obsidian).

---

## Fase 2 — Config visual pronta (VOCÊ escreve, cliente não configura nada)

> ⚠️ **AÇÃO REAL OBRIGATÓRIA.** Não é narração — você TEM que rodar o Bash abaixo de verdade.

**Condição (decidir pelo que a Fase 0 encontrou):**

- **(a) `.obsidian/` NÃO existe na CWD** → copiar tudo.
- **(b) `.obsidian/` existe** → `Read` em `.obsidian/daily-notes.json`:
  - Contém `personal/100-PROJETOS/onboarding/daily` → a config já é a nossa. Pular pra Fase 3.
  - Não contém (ou arquivo não existe) → é o default que o Obsidian acabou de criar ao abrir a pasta. Sobrescrever com a nossa (caso normal de onboarding — ver exceção abaixo).
- **Exceção de respeito:** cliente disse na Fase 1 que **já usava ESTA pasta como vault dele antes** (raro) → perguntar antes de sobrescrever: *"Você já tinha configurações suas aqui. Posso aplicar as do nosso caderno? Suas preferências visuais podem mudar."*

Mensagem (enquanto executa):

> "Agora minha parte: vou deixar todas as configurações prontas — diário automático, corretor em português, lugar certo pros anexos. 5 segundos."

`Bash`:

```bash
cp -rf "${CLAUDE_PLUGIN_ROOT}/.obsidian/." ./.obsidian/ && ls .obsidian
```

**Checkpoint via tool (obrigatório):** `Read` em `.obsidian/app.json` e `.obsidian/daily-notes.json` → confirmar que existem e têm conteúdo. Se falhar → `Bash` `mkdir -p .obsidian` e recriar cada arquivo com `Write`, lendo antes o conteúdo de `${CLAUDE_PLUGIN_ROOT}/.obsidian/<arquivo>` via `Read`.

**Se o Obsidian estava aberto durante a cópia**, pedir:

> "Fecha o Obsidian e abre de novo (só pra ele ler as configurações novas)."

Fechar a fase:

> "Pronto — ele já abre configurado: diário automático no lugar certo, corretor em português, anexos organizados. Você não precisa mexer em nenhuma engrenagem de configuração."

---

## Fase 3 — Estrutura de pastas (vault organizado)

> ⚠️ **AÇÃO REAL OBRIGATÓRIA via Bash.**

**Guarda de segurança:** se a Fase 0 mostrou pastas de trabalho já criadas pelo cliente dentro de `personal/` (ex: `personal/200-PRODUCAO/` com conteúdo próprio), PERGUNTAR antes:

> "Vi que você já tem pastas suas aqui. Quer que eu complete com a estrutura padrão (sem tocar nas suas), ou prefere manter do seu jeito?"

### 3a — Ramo COM estrutura-vault.md (lida na Fase 0)

`Bash` — criar a espinha dorsal. Exemplo abaixo é o criador-conteudo; **adaptar a lista ao doc do ramo lido na Fase 0:**

```bash
mkdir -p personal/anexos "personal/100-PROJETOS/onboarding/daily" personal/200-PRODUCAO/Reels personal/200-PRODUCAO/Posts personal/200-PRODUCAO/Stories personal/200-PRODUCAO/Bio personal/300-RECURSOS/Pinterest personal/300-RECURSOS/Referencias personal/300-RECURSOS/Transcricoes personal/400-ARQUIVO
```

NÃO criar as subpastas `exemplo-001/` do doc — são ilustrativas. Só a espinha.

### 3b — Ramo SEM estrutura própria (generico ou ramo ainda planejado)

```bash
mkdir -p personal/anexos "personal/100-PROJETOS/onboarding/daily" personal/300-RECURSOS personal/400-ARQUIVO
```

**Checkpoint via tool (obrigatório):** `Bash` → `ls personal/` → conferir que as pastas nasceram. Se faltou alguma → refazer o `mkdir` dela.

**Mensagem (1 linha por pasta, linguagem de caderno — listar SÓ o que foi criado de fato):**

> "Organizei suas gavetas:
> • **100-PROJETOS** — cada projeto seu ganha uma pasta aqui
> • **200-PRODUCAO** — onde nasce o que você cria (posts, roteiros...)
> • **300-RECURSOS** — material de referência e inspiração
> • **400-ARQUIVO** — o que ficou pra trás, guardado
> • **anexos** — imagens e arquivos que você arrastar pro caderno"

---

## Fase 4 — VS Code (OPCIONAL — só perfil avançado ou pedido explícito)

**NÃO oferecer por padrão.** Leigo absoluto não precisa de editor de código — o Obsidian já abre e edita tudo.

Oferecer SOMENTE se:
- o cliente pediu ("quero mexer nos arquivos eu mesma", "tem como editar fora do Obsidian?"), OU
- o perfil detectado no `/desabrochar` é técnico (programadora, designer que já usa ferramentas pro)

Mensagem:

> "Existe um editor mais pesado, o **Visual Studio Code** (grátis, da Microsoft). Ele é pra quem mexe em muitos arquivos de uma vez — você não precisa dele, o Obsidian já resolve. Quer instalar mesmo assim? ('instala' / 'deixa pra depois')"

Se "instala": guiar **code.visualstudio.com** → Download → instalador → **File → Open Folder** → a mesma pasta `[CWD]`. Checkpoint humano: *"Conseguiu abrir a pasta nele?"*

Se "deixa pra depois": *"Fechado — se um dia precisar, é só me pedir 'instalar VS Code'."*

---

## Fase 5 — Checkpoint final + registro (OBRIGATÓRIO)

> Mesma regra do Passo 4.5 do `/desabrochar`: **não declarar pronto sem verificar via tool.**

1. `Bash` → `ls -d .obsidian personal/anexos personal/100-PROJETOS 2>/dev/null` (cobrar só os itens que a sessão devia ter criado — se o cliente recusou Obsidian, `.obsidian` não entra na cobrança)
2. Se algo falta → voltar na fase correspondente e refazer. Não seguir até tudo verde.
3. `Edit` no frontmatter do `CLAUDE.md`:
   - `ambiente_montado: true`
   - `data_ambiente: [YYYY-MM-DD]`
   - `obsidian: sim` (manter `obsidian: recusado` se ele pulou a Fase 1)

**Fechamento pro cliente (ajustar os bullets ao que foi feito de verdade):**

> "Tudo pronto! Agora você tem:
> • Seu caderno visual configurado (Obsidian)
> • Suas gavetas organizadas
> • E eu, calibrado, lembrando de tudo
>
> Amanhã tem uma missãozinha nova te esperando. É só voltar e conversar."

---

## Troubleshooting

| Sintoma | Resposta |
|---|---|
| Download do Obsidian não inicia | Trocar de navegador; ou baixar pelo link direto da página |
| Instalador bloqueado pelo Windows (aviso azul SmartScreen) | "Mais informações" → "Executar assim mesmo" (instalador oficial do obsidian.md) |
| Obsidian abriu tela de Sync/Login | Pular — conta Obsidian NÃO é necessária ("Skip" / fechar a aba de login) |
| Cliente abriu a pasta errada como vault | Refazer: File → Open vault → escolher `[CWD]` |
| `cp` do `.obsidian` falhou (permissão) | `mkdir -p .obsidian` + `Write` cada arquivo, lendo antes o conteúdo de `${CLAUDE_PLUGIN_ROOT}/.obsidian/` |
| Obsidian não mostra as pastas novas | Botão direito na barra lateral → Refresh; ou fechar e reabrir |
| Cliente em Mac não acha "Documentos" | Finder → Documentos; a pasta pode ficar em qualquer lugar, Documentos é só convenção |

---

## Anti-patterns

- Declarar "ambiente montado" sem ter rodado os Bash/Read de cada fase — mesmo bug do teste #1, agora com outra roupa
- Copiar o `.obsidian/` por cima de config existente sem ler `daily-notes.json` antes (Fase 2 condição b) — e sem perguntar quando o vault já era do cliente
- Criar pastas por cima de estrutura existente sem perguntar (guarda da Fase 3)
- Oferecer VS Code pra leigo absoluto no automático — Fase 4 é só por pedido ou perfil técnico
- Ensinar o cliente a configurar Daily notes na mão (Settings → Core plugins...) — a Fase 2 já entrega isso pronto no `daily-notes.json`
- Despejar as 4 fases numa mensagem só — uma fase por vez, checkpoint humano entre elas
- Usar "vault", "config", "JSON", "plugin" na conversa — "caderno", "configurações", "programa"
- Insistir no Obsidian após recusa — registrar `obsidian: recusado` e seguir a vida
