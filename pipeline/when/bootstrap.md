# Construção do repositório

- Configuração que todas as encomendas herdam (pacotes, runtime, tipos, lint, formatação, testes, build, publicação, checagens): `executor-2`.
- Arquivo de configuração de checagem, build ou publicação entra em `permissions.ask` do `.claude/settings.json`, como `Edit(/caminho)`, antes de qualquer encomenda criá-lo ou editá-lo.
- Comando, checagem, ferramenta, recurso exclusivo ou agregador entra em `pipeline/facts.md` só depois de existir e rodar aqui. O comando vai no README.
- `em construção` passa a `em uso` quando o humano aprova que uma sessão nova, só com o repositório, levou uma demanda do ticket ao trecho de injeção usando o que `pipeline/facts.md` registra.
