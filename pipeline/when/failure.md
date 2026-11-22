# Falha

Falha: encomenda devolvida, conferência rejeitada, checagem quebrada ou achado confirmado.

## Causa
Classifique antes de agir; o caminho vem dela.
- `execução`: o executor errou com encomenda clara.
- `encomenda`: a encomenda faltou, sobrou ou foi ambígua.
- `pipeline`: uma regra ou instrução da pipeline levou ao erro.
- `ambiente`: ferramenta, acesso, dependência ou rede.
- `incerta`: não dá para saber.

## Caminho
- `execução` com defeito diagnosticado: a mesma instância corrige, ou um `executor-1` com o problema e a evidência.
- `execução` sem diagnóstico, ou 2ª falha técnica: `executor-2` em instância nova. Já no `executor-2`: mude a abordagem ou a divisão.
- `encomenda` ou `pipeline`: corrija a encomenda e reenvie. Não conta como falha do executor.
- `ambiente`: bloqueio declarado ao humano.
- `incerta`: explore antes de agir. Não mude regra por suposição.
- 3ª falha da mesma encomenda: entrega `Parcial.`; o resto vira item retomável no backlog.
