# Estilos

## STYLE-1 Tokens de design
- Porque: valor avulso diverge da marca e entre scripts.
- Vale para: cor e espaçamento, em CSS, classes e estilo em linha.
- Como: só token, definido via `@theme`. Sem token para o valor: crie o token; nunca o valor avulso.
- Garantia: checagem prevista (cor ou espaçamento fora de token). Até ela existir, o revisor.

## STYLE-2 Isolamento por escopo
- Porque: utilities compiladas por script se repetem entre folhas; a ordem de carga decide quem vence e quebra breakpoints entre scripts; tokens em `:root` conflitam. Em canal real, sem escopo, 5 a 7 de 17 estilos saíram certos; com escopo, 17.
- Vale para: script que adiciona elementos visuais ao canal.
- Como:
  - O CSS do script só atinge os elementos dele.
  - O núcleo monta a UI no modo `scope`, o padrão, sem Shadow DOM.
  - O build escopa a folha sob a raiz do script, inclusive reset (preflight) e tokens. Nunca em `:root`.
  - O build remove os `@layer` do Tailwind: CSS do site sem camada vence qualquer camada, independente de especificidade.
- Garantia: checagem prevista (seletor fora da raiz do script em folha gerada pelo Tailwind). Até ela existir, o revisor.

## STYLE-3 Shadow DOM como reserva
- Porque: tracking de terceiros e scripts da plataforma não enxergam dentro do shadow root.
- Vale para: componente fechado, num canal cujo CSS invade a UI mesmo com escopo.
- Como:
  - Modo `shadow`, por componente.
  - O build extrai os `@property` do Tailwind para uma folha única no documento.
  - Custos: `@font-face` só vale no documento, fora do shadow root; fonte e cor são herdadas do site.
- Exceto: formulário de lead e elemento observado por tracking de terceiros nunca usam shadow.
- Garantia: o revisor.

## STYLE-4 Script que altera a página do site
- Porque: utilities valem sob a raiz do script, e os elementos do site não estão nela.
- Vale para: script que muda elementos da própria página do canal.
- Como: sem utilities. CSS escopado aos seletores da plataforma, cada um apoiado em fato com evidência (PLAT-1).
- Garantia: o revisor.

## STYLE-5 Unidade rem
- Porque: a escala do Tailwind é em `rem`, e o protótipo em canal real a validou.
- Vale para: tamanhos.
- Como: `rem`, sem conversão para `px`.
- Garantia: o revisor.
