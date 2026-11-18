# Mais de uma encomenda

- Despacho contínuo: cada encomenda sai assim que as dependências dela foram aceitas.
- Cada arquivo, saída gerada e recurso exclusivo tem um dono por vez.
- Dependência só de interface não serializa, se as duas encomendas têm o mesmo `Fixos`.
- Exemplar aceito antes das réplicas.
- Sempre em fila: instalação, lockfile e geração; configuração do mesmo recurso; defeito de causa desconhecida; encomendas do `executor-2`.
- Agregador (arquivo que várias encomendas tocariam): um dono só. As outras pedem em `Pedidos`, e o dono aplica depois.
- Limite de simultâneas, recursos exclusivos e agregadores: `pipeline/facts.md`. Sem limite registrado, uma encomenda por vez.
- Em paralelo, atribua cada mudança do diff à raia que a permite.
