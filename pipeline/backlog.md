# Backlog

Uma linha por item, com critério de entrada e de saída. Item só vira escopo com o humano.

## Pipeline
- Saída da Fase 1 — entra: pipeline escrita — sai: uma tarefa pequena e real da Fase 2 percorre encomenda, executor, conferência e entrega; um revisor novo começa em contexto limpo; editar arquivo protegido pede confirmação; "a partir de agora" vira regra; nenhum arquivo da pipeline passa de 150 linhas.
- Configuração de checagem, build e publicação em `permissions.ask` — entra: cada encomenda que cria uma delas — sai: todas protegidas.
- Checagem do teto de 150 linhas por arquivo da pipeline — entra: Fase 2 — sai: a checagem recusa arquivo acima do teto.
- Checagem anticontaminação (PLAT-2) — entra: Fase 2 — sai: checagem ativa; a lista de termos passa para a configuração dela, e PLAT-2 aponta para lá.
- Hook por agente que bloqueia git de escrita nos subagentes (ideia não testada) — entra: um subagente usar git de escrita — sai: hook testado e adotado, ou descartado.

## Decisões adiadas
- Infraestrutura: serviço e espaço na CDN separado do legado, host do repositório e CI, homologação, quem injeta a tag, nível de acesso aos canais — entra: antes da Fase 3 — sai: decisões do humano registradas.
- Navegadores-alvo — entra: Fase 3, com dados reais de acesso aos canais — sai: alvo definido no build.
- Estratégia de assets — entra: com a infraestrutura — sai: decisão do humano registrada.
- Tokens em script que altera a página do site (STYLE-1 × STYLE-4: não há raiz do script) — entra: primeira demanda desse tipo, como terreno novo — sai: solução fechada, regra ajustada e exemplar aceito.
- CSS escopado menor: preflight e tokens se repetem por script (cerca de 9 KB a mais, sem minificar) — entra: Fase 3 — sai: medida e decisão registradas.

## Stack aprovada
Cada item sai quando o código o mostra.
- pnpm + Node LTS — entra: Fase 2.
- TypeScript estrito — entra: Fase 2.
- ESLint + Prettier, com o plugin oficial do Tailwind para a ordem das classes — entra: Fase 2.
- Vitest + happy-dom — entra: Fase 2.
- esbuild por script próprio: um IIFE por ponto de entrada declarado; o metafile alimenta build incremental, manifesto e hash; o Tailwind roda numa etapa própria — entra: Fase 3.
- Tailwind CSS v4, tokens via `@theme`, folha conforme STYLE-2 e STYLE-3 — entra: Fase 3.
- Preact — entra: Fase 4.
- Playwright para captura e preview, injetando o script local na página real por interceptação de requisições — entra: Fase 5.

## Fases
- Fase 2, fundação e guarda-corpos: áreas `core`, `ui`, `platform`, `features`, `clients`, `fixtures`, `tools`, `docs`; tipos estritos; checagem de cada regra verificável; metadados validados de cada script e lista única de plataformas e produtos; estrutura (raiz fechada, direção das dependências, superfície pública por área, nomes, slug de cliente único); formato de commit com cliente existente; varredura de segredos; checagem antes do commit — entra: Fase 1 aprovada — sai: cada violação, feita de propósito, falha localmente com mensagem que diz como corrigir.
- Fase 3, build e publicação: só pontos de entrada declarados geram saída; reconstrução por dependência; falha interrompe e não entra em cache; manifesto de saída; publicação só da saída e dos assets declarados; homologação; limpeza de cache por endereço exato; rollback — entra: Fase 2 aprovada e infraestrutura decidida — sai: mudar uma peça compartilhada reconstrói os dependentes; script quebrado bloqueia a publicação; rollback demonstrado.
- Fase 4, núcleo: runtime genérico, cada capacidade com tipos, documentação, testes e exemplo — entra: Fase 3 aprovada — sai: testes do núcleo passando.
- Fase 5, verificação e entrega: criação guiada de script, captura sanitizada de página, execução sobre página real em desktop e mobile, verificação única por script, trecho de injeção a partir dos metadados, inventário de scripts ativos — entra: Fase 4 aprovada — sai: um script de exemplo vai da criação ao trecho de injeção sem configuração manual.
- Fase 6, pipeline calibrada: ferramentas ligadas ao fluxo; formato e verificação dos fatos de plataforma; três exemplares num cliente fictício não publicável (alteração de página sem UI, componente de UI, integração ou tracking); pipeline enxugada — entra: Fase 5 aprovada — sai: uma sessão nova, só com o repositório, leva uma demanda fictícia do ticket ao trecho de injeção pelo caminho curto.
- Fase 7, piloto: 5 a 10 demandas reais pela pipeline, calibrando os níveis — entra: Fase 6 aprovada — sai: nenhuma reexplicação de convenção no chat, nenhuma violação vista só pelo humano, nenhum build quebrado publicado, todos os fatos com evidência, caminho curto na maioria.
- Fase 8, expansão: promoções recorrentes, outra plataforma na primeira demanda dela, onboarding do time — entra: Fase 7 aprovada — sai: todo o time entrega pela pipeline.
