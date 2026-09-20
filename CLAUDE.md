# CLAUDE.md

> Template genérico. Cole em qualquer projeto novo e preencha os placeholders
> `{preencher}`. Este arquivo não assume nenhuma linguagem ou stack.

## Propósito do projeto

{preencher}

## Convenções de código

{preencher por projeto/stack}

## Task management

Trabalho planejado vive em `docs/epics/`, em três pastas que representam o
estado do épico:

```
docs/epics/
├── backlog/         # planejado, ainda não iniciado
├── in-progress/     # em execução
└── done/            # concluído
```

- Um épico avança movendo o arquivo: `backlog/` → `in-progress/` →
  `done/`.
- Tarefas são checkboxes: `- [ ]` pendente, `- [x]` concluída.
- Todo épico tem o campo `Última revisão: YYYY-MM-DD`, atualizado sempre que
  o arquivo for alterado.
- Decisões são registradas no próprio épico como `DA-###` (numeração
  sequencial), sempre com a justificativa — o porquê, não só o quê.

## Convenções de commit

Conventional Commits (`feat`, `fix`, `chore`, `docs`, `refactor`, `test`, ...),
com mensagens em inglês.

```
<type>(<scope opcional>): <descrição no imperativo, minúscula>
```

## Stack e camadas específicas do projeto

<!-- Se este projeto usa o limaj-framework como base (.NET/Azure
Functions), cole aqui o que o CLAUDE.md do limaj-framework documenta:
a tabela de camadas (Abstractions → Application / Persistence.EFCore /
Web) e a regra de identidade via IUserIdentityGateway (seções
"Architecture: package layering" e "Core patterns to reuse"). Segurança
(ownership/BOLA) e Migrations (dotnet ef database update) NÃO estão
documentadas no limaj-framework — escreva-as aqui, no próprio produto.
Se este projeto usa outra linguagem/stack, descreva a stack real aqui em
vez disso — este arquivo não deve depender do limaj-framework por
padrão. -->
