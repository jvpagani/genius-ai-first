# Código

## CODE-1 Ordem alfabética
- Porque: uma ordem só, nada a decidir, diffs menores.
- Vale para: imports, chaves de objeto, props e demais listas.
- Exceto:
  - onde a ordem muda o comportamento (execução, cascata, spread, argumentos posicionais);
  - classes do Tailwind: ordem do plugin oficial do Prettier.
- Garantia: checagem prevista (lista fora de ordem). Até ela existir, o revisor.

## CODE-2 Sem comentários
- Porque: comentário envelhece sem que nada o verifique. O que precisa durar vai para nomes, tipos, testes ou a pipeline.
- Vale para: todo código.
- Exceto: diretivas de ferramenta: `/// <reference>`, `@ts-expect-error` com motivo, diretivas de lint.
- Garantia: checagem prevista (comentário que não é diretiva). Até ela existir, o revisor.

## CODE-3 Sem imports relativos
- Porque: o import não depende de onde o arquivo está, e a direção entre áreas fica verificável.
- Vale para: todo import, sem exceção, inclusive entre partes da mesma pasta de script.
- Como: tudo por alias. A configuração de aliases cobre a pasta de cada script, igual em tipos, build e testes.
- Garantia: checagem prevista (import com `./` ou `../`). Até ela existir, o revisor.

## CODE-4 Tipagem estrita
- Porque: erro de tipo é pego antes de chegar ao canal.
- Vale para: todo código, inclusive o uso de globais da plataforma.
- Como: TypeScript estrito, sem `any` explícito nem implícito. Dado de fora sem tipo conhecido (global, resposta de API, configuração de injeção) entra como `unknown` e é validado.
- Garantia: checagem prevista (erro de tipo ou `any`, sobre todo o código). Até ela existir, o revisor.

## CODE-5 Nomes
- Porque: nome de pasta e de arquivo vira URL pública.
- Vale para: pastas, arquivos e identificadores.
- Como:
  - Inglês.
  - Pastas e arquivos: ASCII, minúsculas, kebab-case.
  - Pasta de script: ação-elemento-local.
- Garantia: checagem prevista (nome fora do padrão). Até ela existir, o revisor.

## CODE-6 Solução de mais de um script
- Porque: cópia entre scripts diverge; a peça única corrige todos.
- Vale para: solução que um segundo script precisa, do mesmo cliente ou de outro.
- Como: promova, nunca copie. A peça vai para `features/`, com uma função de montagem configurável. Cada script tem um ponto de entrada enxuto que só configura e chama essa função.
- Exceto: a primeira ocorrência fica no script.
- Garantia: o revisor.
