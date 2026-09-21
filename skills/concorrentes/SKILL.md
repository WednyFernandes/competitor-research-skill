---
name: concorrentes
description: Pesquisa de concorrentes que se expande a cada achado — Ad Library da Meta, Play Store, App Store, landings — e termina em pivôs e decisões pro projeto atual. Use quando o usuário pedir análise de concorrência, benchmark, "quem faz isso", "vale entrar nesse mercado", pivô, posicionamento, ou antes de gastar em mídia. Trigger: /concorrentes [nicho | país | nomes].
---

# Concorrentes

Pesquisa de concorrentes e pivôs pro projeto atual. Argumento opcional: nicho, país ou nomes que já conheço. Se vazio, deduz do repo.

## 0. Contexto (antes de buscar)

Lê `README.md`, `docs/PRODUCT.md` (ou equivalente), `ROADMAP.md`, `CONCORRENTES.md` se existir. Extrai em 5 linhas: o que é, pra quem, como o dado entra, preço, o que já foi decidido *não* fazer. Toda comparação abaixo é contra essas 5 linhas.

## 1. Fontes (nesta ordem, todas)

1. **Ad Library da Meta** — quem paga mídia agora. Scrapers headless levam 403; usa o browser embutido direto:
   `https://www.facebook.com/ads/library/?active_status=active&ad_type=all&country=BR&q=TERMO&search_type=keyword_unordered&media_type=all`
   → `wait 6s` → `scroll` 2× → `get_page_text`. Pra ver landing/URL de um anúncio: `?id=ID_DA_BIBLIOTECA` + `find "link"`.
   Anota por anunciante: nº de criativos, "N anúncios usam esse criativo", data de início, copy repetido, CTA, domínio.
2. **WebSearch** — `"app X Brasil 2026"`, `"melhores apps para Y"`, `site:play.google.com Y`, `site:apps.apple.com br Y`, e o próprio nome do projeto (conflito de marca/domínio).
3. **Play Store / App Store** via browser: busca literal do nicho, depois ficha de cada app (downloads, nota, nº avaliações, última atualização, preço in-app, descrição). Sem a ficha, não conta.
4. **WebFetch** da landing de cada concorrente: como o dado entra, privacidade, preço em BRL, trial, plataforma, CNPJ/fundadores, prova social, FAQ, blog.
5. **Registro MCP** (`search_mcp_registry`) e AdWhispr se conectado — só pra achar mais nomes.

## 2. Loop de expansão (o núcleo)

Cada rodada gera termos pra próxima. Repete até uma rodada inteira não trazer nome novo (mínimo 3 rodadas).

- Termo → anunciantes → **nomes citados no copy deles** ("vs Mobills", "adeus Splitwise") → novos termos.
- Artigo "melhores apps" → todos os listados → ficha de cada.
- Play Store "mais de [dev]" e "apps semelhantes" → mais nomes.
- Landing do concorrente → blog comparativo dele → mais nomes.
- Cada feature que aparece em 3+ concorrentes vira um termo de busca próprio (ex.: "proporcional à renda", "conta conjunta").
- Cada **adjacência** vira uma rodada: quem resolve a mesma dor com outro produto (banco, planilha, curso, bot no Whats, agregador).

Não pula rodada porque "já sei". Registra o que buscou e o que cada termo rendeu.

## 3. O que anotar por concorrente

Uma linha na tabela: nome (empresa/dev) · público · como entra o dado · privacidade · preço BRL e trial · mídia paga (criativos, desde quando) · onde está (loja, downloads, nota, avaliações) · distribuição (ads / SEO / influencer / afiliado / loja).

Marca em negrito quem gasta mídia há 60+ dias e quem tem 10 mil+ downloads — são as únicas evidências de que algo converte.

## 4. Análise (só depois de fechar o loop)

- **O que a mídia ensina**: copies que se repetem, inimigo nomeado, formato, âncora de preço, trial. Quem sobreviveu 60+ dias.
- **O que as lojas ensinam**: quem ganhou e por quê (ASO, nome literal, multi-plataforma), quem morreu (0 avaliações), o que ninguém faz.
- **Os 2–3 que importam** × nós, tabela lado a lado.
- **O que copiar** (frase, feature barata, canal) e **onde eles perdem** (nosso argumento, em frases prontas de landing).
- **Pivôs**, cada um com: o espaço vazio que abre, o que já temos que serve, o que teria que codar, quem já está lá, gatilho pra decidir. Inclui sempre o pivô "não pivota, reposiciona" e o pivô de adjacência (público vizinho com dor mais obrigatória).
- **Riscos**: nome/domínio/marca, preço fora do piso, feature que todo mundo está migrando (e se seguir ou não).
- **Decisões**: o que *não* fazer, ordem de ação, gatilho de revisão com número e data.

## 5. Saída

Escreve/atualiza `docs/CONCORRENTES.md` no repo: cabeçalho com data e país, seção nova em cima, seções antigas preservadas abaixo. Termina com a lista de fontes (termos buscados, URLs). Não commita sem pedir.

No chat: 10 linhas no máximo — os 3 achados que mudam decisão, o pivô recomendado, o risco nº 1.
