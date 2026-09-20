# ai-starter-kit

Base de tooling de IA para novos projetos. Este repositório **não contém
código** — sem `src/`, `test/` ou devcontainer. Ele traz só a configuração do
Claude Code:

| Arquivo                | Função                                                              |
| ---------------------- | ------------------------------------------------------------------- |
| `.claude/settings.json` | Declara o marketplace `my-skills` e habilita o plugin `workflow`.   |
| `CLAUDE.md`            | Template genérico de instruções, com placeholders a preencher.      |

## Este repositório não é autossuficiente

Ele é uma camada que se **combina** com outra base, não a substitui. Para um
projeto .NET/Azure Functions, a base de código vem do
[limaj-framework](https://github.com/limajsolutions/limaj-framework)
(`template-backend/`), e o conteúdo deste repositório é copiado por cima. Para
outras stacks, este repositório é o ponto de partida e você traz a stack.

## Fluxo de uso

### Projeto novo usando limaj-framework (.NET/Azure Functions)

```bash
git clone https://github.com/limajsolutions/limaj-framework.git
cp -r limaj-framework/template-backend <Produto>
cd <Produto> && rm -rf .git && git init -b main

git clone https://github.com/thalleslima8/ai-starter-kit.git /tmp/ai-base
cp -r /tmp/ai-base/.claude ./.claude
cp /tmp/ai-base/CLAUDE.md ./CLAUDE.md
# preencher os placeholders do CLAUDE.md (camadas e identidade vêm do
# CLAUDE.md do limaj-framework; Segurança e Migrations são do produto —
# ver comentário dentro do arquivo) e seguir o rename Template→Produto
# documentado no README do limaj-framework
```

### Projeto novo em outra stack (sem limaj-framework)

```bash
git clone https://github.com/thalleslima8/ai-starter-kit.git <Produto>
cd <Produto> && rm -rf .git && git init -b main
# preencher CLAUDE.md do zero para a stack real
# substituir este README.md pelo README do projeto
```

### Em ambos os casos, dentro do projeto

```bash
code . && claude
```

```
/plugin marketplace add thalleslima8/my-skills
/plugin install workflow@my-skills
# opcional, só em projeto .NET/EF Core:
/plugin install dotnet@my-skills
```

O `.claude/settings.json` já declara o marketplace e habilita o `workflow`, então
ao abrir o projeto e confiar na pasta o Claude Code oferece a instalação. Os
comandos `/plugin` acima são o caminho manual equivalente.

> `extraKnownMarketplaces` só vale depois que você confia na pasta do projeto.
> Antes disso o marketplace não é carregado e nenhum plugin é instalado.

### Plugin opcional: `dotnet`

O `settings.json` deste repositório **não** habilita `dotnet@my-skills`, porque
ele é específico de stack e só faz sentido depois de saber se o projeto usa
EF Core. Se usar, escolha um dos dois caminhos:

- rodar `/plugin install dotnet@my-skills`, ou
- adicionar a linha ao `enabledPlugins` do `.claude/settings.json` do projeto:

```json
"enabledPlugins": {
  "workflow@my-skills": true,
  "dotnet@my-skills": true
}
```

## Onde vivem commands, agents e skills

Os commands, agents e skills do Claude Code (`analyst`, `arquiteto`, `flow`,
`spike`, `qa`, `infra` e as skills de teste, review e commit) **não vivem
aqui**. Eles ficam em
[thalleslima8/my-skills](https://github.com/thalleslima8/my-skills) e chegam a
este ou a qualquer projeto apenas via `/plugin install`. Não adicione arquivos
de command, agent ou skill a este repositório — a mudança deve ser feita no
`my-skills`.
