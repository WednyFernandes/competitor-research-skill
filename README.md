# Concorrentes — Competitor Research Skill for Claude Code

**PT-BR:** Skill de análise de concorrentes para Claude Code que se expande a cada achado: varre a Biblioteca de Anúncios da Meta (Facebook/Instagram Ad Library), Google Play, App Store e landing pages, descobre concorrentes que você não conhecia e termina em pivôs, posicionamento e decisões para o seu projeto.

**EN:** Self-expanding competitor analysis skill for Claude Code: sweeps Meta Ad Library (Facebook/Instagram ads), Google Play, App Store and landing pages, finds competitors you didn't know about, and ends with pivots, positioning and decisions for your project.

```
/concorrentes                      # deduz o nicho do repo / infers niche from the repo
/concorrentes finanças casal BR    # nicho + país / niche + country
/concorrentes Pierre, Fikko        # nomes que já conhece / names you already know
```

---

## Instalação · Install

**Skill (recomendado / recommended)**

```bash
npx skills add WednyFernandes/competitor-research-skill
```

**Manual — comando global / global command**

```bash
git clone https://github.com/WednyFernandes/competitor-research-skill
cp competitor-research-skill/skills/concorrentes/SKILL.md ~/.claude/commands/concorrentes.md
```

**Manual — skill de projeto / project skill**

```bash
mkdir -p .claude/skills/concorrentes
cp competitor-research-skill/skills/concorrentes/SKILL.md .claude/skills/concorrentes/
```

Requer / requires: Claude Code com browser embutido (desktop app) ou extensão Claude in Chrome, `WebSearch`, `WebFetch`.

---

## O que faz · What it does

| Etapa / Step | PT-BR | EN |
|---|---|---|
| 0 | Lê README, PRODUCT, ROADMAP e compara tudo contra o que o projeto já decidiu | Reads README, PRODUCT, ROADMAP; every comparison is against what the project already decided |
| 1 | Ad Library da Meta via browser (contorna o 403 dos scrapers), WebSearch, Play Store, App Store, landings | Meta Ad Library via browser (bypasses scraper 403s), WebSearch, Play Store, App Store, landing pages |
| 2 | **Loop de expansão**: cada anunciante, artigo, blog, feature e adjacência vira novos termos; só para quando uma rodada não traz nome novo | **Expansion loop**: every advertiser, article, blog, feature and adjacency becomes new search terms; stops only when a full round finds nothing new |
| 3 | Uma linha por concorrente: dado, privacidade, preço, mídia paga, loja, distribuição | One row per competitor: data entry, privacy, price, paid media, store stats, distribution |
| 4 | O que a mídia ensina, o que as lojas ensinam, top-3 × nós, o que copiar, onde perdem, pivôs, riscos, decisões com gatilho | What ads teach, what stores teach, top-3 vs us, what to copy, where they lose, pivots, risks, decisions with triggers |
| 5 | Grava `docs/CONCORRENTES.md` preservando histórico; resposta de 10 linhas | Writes `docs/CONCORRENTES.md` preserving history; 10-line summary |

### Sinais que valem / Signals that count

- Anúncio rodando **60+ dias** = criativo que converte. / Ad running **60+ days** = a creative that converts.
- **10 mil+ downloads** com avaliações = distribuição real. / **10k+ downloads** with reviews = real distribution.
- Nome citado no copy do concorrente ("vs X") = próximo termo de busca. / Name cited in a competitor's copy ("vs X") = next search term.

---

## Exemplo de saída · Sample output

Trecho real de `docs/CONCORRENTES.md` gerado para um app de finanças de casal (BR, set/2026):

> Resumo em uma linha: casal + privacidade + manual **paga** (R$ 14,90–19,90, provado por Duofi, Fikko, Balance). Ninguém no Brasil importa extrato. O argumento vencedor da mídia paga virou "manda no WhatsApp"; nele a gente perde e não entra.
>
> | | Casal | Privacidade | Como entra o dado | Preço | Mídia paga | Onde está |
> |---|---|---|---|---|---|---|
> | **Pierre** | criativo "sem briga" desde 30/jun | não | Open Finance + WhatsApp | trial 7d | 30+ criativos desde mai/26 | Play 4,7 |
> | **Duofi** | "o seu, o meu e o nosso" | sim | 100% manual | R$ 14,90 | 1 criativo, 11/set | PWA |
> | **Balance** | nativo | parcial | manual | trial 7d | — | Play 50 mil+, 4,7, 1.320 avaliações |

---

## Por que existe · Why

Toda análise de concorrência que eu fazia parava nos 3 nomes que eu já conhecia. O que muda decisão está no 4º, 5º, 12º — o que apareceu no copy de um anúncio, num artigo "melhores apps", no "apps semelhantes" da loja. Esta skill força o loop até acabar.

Every competitor analysis I did stopped at the 3 names I already knew. What changes decisions is the 4th, 5th, 12th — found in an ad's copy, a "best apps" article, the store's "similar apps". This skill forces the loop until it runs dry.

---

## Palavras-chave · Keywords

análise de concorrentes · pesquisa de concorrência · benchmark de concorrentes · biblioteca de anúncios meta · facebook ad library · instagram ads espionar concorrentes · pivô de produto · posicionamento · validação de mercado · claude code skill · claude skill · agent skill · competitor analysis · competitive research · competitor discovery · meta ad library scraper · ad intelligence · app store competitor research · google play competitor analysis · market validation · product pivot · positioning · go-to-market research · AI agent skill · MCP

## Licença · License

MIT
