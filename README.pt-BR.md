# GodEye Project Analyzer

[English](README.md)

GodEye Project Analyzer é um fluxo estruturado de prompts para usar o Codex de forma mais segura, rigorosa e consciente do contexto ao analisar e trabalhar em projetos de software.

Ele não é apenas um prompt mágico de auditoria. É um processo em etapas que ajuda o Codex a:

1. ler preferências globais de execução;
2. entender e resumir tecnicamente o projeto alvo;
3. criar um plano prático de smoke test;
4. executar uma auditoria profunda tipo "God Eye" / "Olho de Deus";
5. ajudar o usuário a corrigir problemas depois, por prioridade, sem sair alterando tudo no escuro.

O objetivo é reduzir implementação prematura, perda de contexto, suposições inseguras e correções mal priorizadas durante o trabalho com IA em projetos de software.

## Conteúdo do Repositório

Este repositório inclui duas versões do mesmo fluxo:

- `godeye-ptbr/` — prompts em português do Brasil.
- `godeye-en/` — prompts em inglês.

Escolha um idioma por projeto ou sessão para evitar documentação misturada. Outros idiomas podem ser adicionados futuramente.

```txt
godeye-projectanalyzer/
├─ godeye-ptbr/
│  ├─ 1_user_preferences.md
│  ├─ 2_codex_resumo_do_projeto.txt
│  ├─ 3_codex_smoke_test.txt
│  └─ 4_codex_project_analyzer.txt
├─ godeye-en/
│  ├─ 1_user_preferences_en.md
│  ├─ 2_codex_project_summary.txt
│  ├─ 3_codex_smoke_test.txt
│  └─ 4_codex_project_analyzer.txt
├─ README.md
└─ README.pt-BR.md
```

## Por que usar?

Sessões longas com IA podem falhar de formas previsíveis. O assistente pode:

- começar a codar antes de entender o projeto;
- perder contexto com o tempo;
- assumir regras de negócio que nunca foram definidas;
- misturar análise com implementação;
- corrigir sintomas em vez de causas;
- introduzir regressões tentando ajudar.

O GodEye tenta reduzir esses riscos com um fluxo mais lento e claro:

1. definir regras de execução;
2. criar um resumo técnico factual;
3. criar um checklist de smoke test;
4. executar uma auditoria profunda apenas quando necessário;
5. corrigir problemas em lotes controlados.

## Fluxo Recomendado

Use os arquivos em ordem numérica:

```txt
1_user_preferences
        ↓
2_project_summary / 2_resumo_do_projeto
        ↓
3_smoke_test
        ↓
4_project_analyzer
        ↓
correções P0
        ↓
smoke test + testes + build
        ↓
correções P1
        ↓
validação final
```

## O que cada arquivo faz

### `1_user_preferences...`

Define regras globais de comportamento para o Codex, incluindo controle de escopo, atenção a riscos, validação, perguntas quando a confiança for baixa, prevenção de mudanças perigosas e proibição de inventar arquivos, comandos ou resultados de testes.

Use no começo da sessão ou como preferências de execução do usuário para o projeto.

### `2_project_summary...`

Pede ao Codex para inspecionar o projeto alvo e criar um resumo técnico neutro e factual.

Esta etapa não é auditoria. Ela não deve sugerir melhorias, classificar qualidade, corrigir problemas ou criar roadmap. O objetivo é documentar o estado atual do projeto para que sessões futuras continuem com melhor contexto.

### `3_smoke_test...`

Pede ao Codex para criar um checklist rápido de validação para o projeto alvo.

O smoke test deve ajudar a verificar se o projeto ainda instala, executa, faz build, abre corretamente e mantém os fluxos principais funcionando depois de mudanças.

### `4_project_analyzer...`

Executa a auditoria profunda "God Eye" / "Olho de Deus".

Este prompt pede ao Codex para procurar bugs, riscos ocultos, dívidas técnicas, problemas de UX, gargalos de performance, riscos de segurança e privacidade, gaps de testes, inconsistências de dados, problemas de build/release e riscos de produto.

A auditoria é diagnóstica por padrão: deve relatar achados e prioridades, não aplicar correções automaticamente.

## Níveis de Prioridade

### P0 — Corrigir imediatamente

Problemas críticos como crashes, perda de dados, riscos graves de segurança ou privacidade, build quebrado, fluxo principal inutilizável, texto user-facing gravemente quebrado ou dado crítico incorreto.

### P1 — Corrigir antes de beta/release

Bugs funcionais importantes, UX confusa em fluxos centrais, persistência frágil, permissões mal tratadas, inconsistências de dados, risco de performance em telas importantes ou testes críticos ausentes.

### P2 — Melhorias importantes

Dívida técnica relevante, problemas de manutenção, lógica duplicada, cobertura adicional de testes, melhorias de organização, consistência visual e trabalho preventivo de performance.

### P3 — Futuro/polimento

Refinamentos opcionais, ideias de produto, polimento visual, melhorias de experiência e itens que podem esperar.

## Como usar

1. Escolha um idioma: `godeye-en/` ou `godeye-ptbr/`.
2. Abra o projeto alvo no Codex.
3. Envie ou aplique o arquivo `1_user_preferences...`.
4. Execute o prompt `2_project_summary...`.
5. Revise o resumo gerado antes de continuar.
6. Execute o prompt `3_smoke_test...`.
7. Execute o prompt `4_project_analyzer...` apenas quando quiser uma auditoria profunda.
8. Corrija problemas por lotes: P0 primeiro, depois P1, depois P2/P3.
9. Rode smoke test, testes relevantes e build depois de cada lote importante de mudanças.

## Exemplo em um Projeto Alvo

Quando usado dentro de outro projeto, o fluxo pode criar arquivos como:

```txt
target-project/
├─ user_preferences.md
├─ myapp_summary.md
├─ myapp_smoke_test.md
├─ src/
├─ tests/
└─ README.md
```

Para o fluxo em português do Brasil:

```txt
projeto-alvo/
├─ user_preferences.md
├─ meuapp_resumo.md
├─ meuapp_smoke_test.md
├─ src/
├─ tests/
└─ README.md
```

## Prompts Curtos para Começar

Inglês:

```txt
Use the GodEye workflow in this project.
First, read and follow the global preferences.
Do not change any files yet.
Wait for my next prompt.
```

Português do Brasil:

```txt
Vou usar o fluxo GodEye neste projeto.
Primeiro, leia e siga as preferências globais.
Não altere nenhum arquivo ainda.
Aguarde meu próximo prompt.
```

Pedido seguro de auditoria:

```txt
Execute a auditoria GodEye neste projeto.
Não altere arquivos.
Não refatore.
Não faça commits.
Entregue apenas o relatório priorizado em P0/P1/P2/P3.
```

## Quando usar

GodEye é útil antes de:

- beta fechado;
- release público;
- refatorações grandes;
- mudanças de arquitetura;
- publicação em loja;
- monetização;
- preparação para revisão de segurança;
- manutenção de projeto legado;
- retomada de projeto depois de muito tempo;
- entrega do projeto para outra pessoa ou equipe.

## Limitações

GodEye é um apoio para análise, documentação e priorização. Ele não substitui:

- QA real;
- revisão humana de código;
- auditoria profissional de segurança;
- testes em aparelhos reais;
- testes automatizados;
- validação manual de produto.

Ele não garante ausência de bugs. A qualidade da análise depende dos arquivos disponíveis, do contexto fornecido ao Codex, da capacidade do modelo de inspecionar o projeto e das validações que forem realmente executadas.

Use os relatórios como apoio à decisão, não como prova absoluta de qualidade ou segurança.

## Licença

Você pode usar, modificar e adaptar estes prompts nos seus próprios projetos.
