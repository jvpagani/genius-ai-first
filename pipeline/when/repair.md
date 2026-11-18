# Reparo da pipeline

Gatilhos: `CLAUDE.md`. Não é gatilho: tarefa que correu bem; instrução sem sinal de duração, que vale só para a tarefa.

## Causa
Da linha envolvida: ausente, ambígua, contraditória, velha, não lida ou ignorada.

## Remédio
O primeiro que serve:
1. nada;
2. menos texto: apagar ou simplificar;
3. checagem ou código que recuse o erro;
4. mudar a linha de lugar, para onde o gatilho a faz ser lida;
5. texto novo;
6. o humano.

Depois, releia o trecho como um agente novo e confirme que o erro não se repetiria.

## Admissão de texto
Uma linha entra só se:
- um agente competente, lendo código, árvore, configuração e documentação oficial, erraria sem ela;
- nenhuma checagem recusa o erro a custo razoável;
- nenhuma outra linha cobre o assunto.

Nunca entra: local, nome ou assinatura de algo do código, lista do que existe, forma de um tipo de arquivo, histórico, intenção, exemplo que não muda decisão, preâmbulo.
- Cada regra num lugar só. Nos outros, aponte.
- Comandos só no README. Arquivos protegidos só no `.claude/settings.json`.
- Teto de 150 linhas por arquivo: corte antes de acrescentar.

## Regra
- Assunto novo: arquivo próprio e linha na tabela de gatilhos do `CLAUDE.md`.
- ID: prefixo do assunto e número, nunca reaproveitado.
- Rótulos, nesta ordem, vazio sai: Porque, Vale para, Como, Exceto, Garantia, Fonte, Dívida.
- `Garantia`: a checagem que recusa a violação. Sem ela: "checagem prevista (o que ela recusa). Até ela existir, o revisor." Sem checagem prevista: "o revisor."
- `Fonte`: aponta, nunca descreve.

## Aplicação
- Aplique sem pedir ok e declare numa linha da entrega e no corpo do commit.
- Só com o humano, como proposta no backlog: as leis do `CLAUDE.md`, regra nova ou mais exigente, regra que cria dívida, a stack aprovada, e modelo, esforço, ferramentas e permissões dos agentes.
- Pedido explícito do humano já é o ok.
