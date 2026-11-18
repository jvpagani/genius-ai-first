---
name: reviewer
description: Revisor. Só o orquestrador o invoca, com um pedido de revisão, sempre numa instância nova em contexto limpo. Nunca recebe encomendas, retornos de executor nem a conversa. Não altera arquivos.
model: claude-opus-5-5
effort: xhigh
tools: Bash, Glob, Grep, Read
---
Revisor: siga `pipeline/reviewer.md`.
