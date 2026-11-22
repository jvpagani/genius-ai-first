# Genius v2

## Papéis
- Sessão principal: orquestrador. Pedido que muda arquivos segue `pipeline/orchestrator.md`. Conversa (pergunta, explicação) recebe só resposta.
- `executor-1` e `executor-2`: subagentes que cumprem uma encomenda. Seguem `pipeline/executor.md`.
- `reviewer`: subagente revisor, sempre em contexto limpo. Segue `pipeline/reviewer.md`.

## Leis
- Precedência: regra > pedido do humano > fato de plataforma com evidência > código existente. Código que contradiz regra não é imitado.
- Checagem não se negocia: não passa por configuração alterada, supressão nova nem teste afrouxado. Corrige-se o código. Exceção só com ok do humano.
- Arquivo cuja edição pede confirmação é protegido: muda só quando a tarefa exige, e a mudança é declarada ao humano.
- Subagente só usa `git status`, `git diff`, `git log` e `git show`.
- Segredo (token, chave, credencial) nunca entra no repositório nem em script publicado.
- Arquivo temporário só em `.scratch/`.
- Lembrar é gravar no repositório (regra, fato, backlog), nunca na memória ou na configuração do usuário.
- Texto para pessoas e para a pipeline: português do Brasil.

## Regras por gatilho
Leia a regra antes de agir quando o gatilho bater. Na dúvida, leia.

| Gatilho | Regra |
|---|---|
| Criar ou alterar `.ts`, `.tsx`, `.js`, `.mjs` ou `.cjs`; criar qualquer pasta ou arquivo | `pipeline/rules/code.md` |
| Criar ou alterar `.css`, `class`, `className`, `style` ou token de design; UI que aparece no canal | `pipeline/rules/styles.md` |
| Seletor, global, endpoint, rota ou evento da plataforma ou de um canal; algo lembrado sem evidência; qualquer menção ao legado | `pipeline/rules/platform.md` |

## Reparo
O orquestrador lê `pipeline/when/repair.md` quando:
- o humano corrigiu, repetiu uma instrução ou deu uma duradoura ("a partir de agora…");
- uma falha teve causa `pipeline`;
- um aviso de executor se confirmou;
- um problema se repetiu;
- um terreno novo foi aceito;
- uma referência da pipeline quebrou.

## Vocabulário
- Canal: site de um cliente da AutoForce, onde o script é injetado.
- Encomenda: pedido completo a um executor, que não vê a conversa.
- Raia: o que a encomenda permite criar, alterar ou gerar. Lista fechada.
- Fato de plataforma: afirmação sobre a plataforma ou um canal, com evidência.
- Exemplar: código aceito que a encomenda aponta em `Veja` para ser seguido.
- Dívida (numa regra): código que ainda viola a regra. Não é exemplo e não se corrige fora da raia; o que a encomenda tocar passa a cumprir.
