# Revisão

## Sinais de risco
Sem nenhum sinal, não há revisão: pare de ler aqui.
- formulário ou conversão de lead
- tracking e analytics
- integração de terceiros
- script em todas as páginas ou sensível a desempenho
- peça compartilhada, que afeta vários clientes
- primeira instância de um padrão
- segurança, dados pessoais ou tokens
- configuração de build, publicação ou checagens
- tarefa que deu trabalho: várias tentativas ou subida de nível
- mudança extensa ou espalhada

Os dois últimos surgem na execução: reavalie antes de entregar.

## Quando
- Uma revisão só, do conjunto, depois de integrar e passar as checagens completas. Nunca por encomenda.
- Antecipada e obrigatória: marco arriscado que outras encomendas vão replicar.
- Cada ciclo usa uma instância nova do `reviewer`. No máximo 2 ciclos; o 2º confere só as correções.

## Pedido de revisão
Só estes campos:
- `Objetivo`: o que a mudança deve fazer e os sinais de risco presentes.
- `Critérios`: o que conta como pronto.
- `Escolhas`: decisões fechadas, que não estão em revisão.
- `Base`: o estado de antes (commit ou `git status` registrado).
- `Arquivos`: o que mudou.
- `Achados anteriores`: no 2º ciclo, os achados e as correções.

Nunca leva encomenda, retorno de executor, raciocínio nem conversa.

## Triagem
Para cada achado: confirme no código, classifique (`quebra` ou `destoa`), separe pelo escopo e ache a causa (`pipeline/when/failure.md`).
- Confirmado e dentro do que mudou: corrija por encomenda.
- Fora do que mudou, ou `De passagem:`: vai para o backlog e não bloqueia.
- Não confirmado: descarte.
- `Inconclusivo:`: corrija o pedido e peça de novo.
- `quebra` que sobra do 2º ciclo: entrega `Parcial.`.
