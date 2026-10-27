---
name: make-bugs-confess
description: Investiga bugs em ondas, testa uma solução simples e confronta o resultado com uma análise independente usando how e why. Use para diagnosticar bugs, investigar regressões ou corrigir comportamentos incorretos.
---

# Investigar bugs em ondas

Investigue a causa do bug antes de concluir pela correção. Uma solução simples que passa no teste inicial é uma candidata, não uma conclusão.

Leia as skills `principle-subtract-before-you-add`, `how` e `why` entre as skills disponíveis. Use a primeira para orientar a solução inicial e delegue o uso das outras duas na terceira onda. Não copie suas instruções para esta skill. Se faltar uma dependência ou a ferramenta de delegação, avance no que puder e informe a limitação. Não apresente uma autoavaliação como análise independente.

## Onda 1. Formule uma hipótese verificável

1. Registre o comportamento esperado, o observado e as condições que disparam o bug.
2. Reproduza o problema e identifique o fluxo de execução relevante. Guarde os comandos, entradas e resultados necessários para repetir a reprodução.
3. Formule uma hipótese causal e indique qual observação a confirmaria ou refutaria. Separe fatos observados de inferências.
4. Preserve a referência do código anterior à correção e as evidências originais para a análise independente.

Se não conseguir reproduzir, investigue com os dados disponíveis e declare a lacuna. Não trate a hipótese como causa confirmada.

## Onda 2. Teste a solução simples

Use `principle-subtract-before-you-add` para procurar a menor correção que atua sobre a causa proposta. Considere remover caminhos redundantes, estado duplicado ou uma condição incorreta antes de adicionar mecanismos.

Não remova validações, proteções ou comportamentos exigidos apenas para fazer o teste passar. Preserve os requisitos demonstrados pelo código, pelos testes e pelo pedido do usuário.

Quando a tarefa incluir corrigir o bug, implemente a candidata e repita a reprodução. Quando o pedido for apenas diagnóstico, faça o experimento em um ambiente isolado ou descreva o experimento ainda necessário, sem alterar o trabalho do usuário.

Confira o caso que falhava e os comportamentos próximos afetados pela mudança. Use um teste de regressão quando ele capturar a falha real. Registre o resultado antes e depois, inclusive os casos que contradizem a hipótese. Se a candidata falhar, revise a hipótese em vez de acumular remendos.

Mesmo que a candidata resolva o caso inicial, prossiga para a próxima onda antes de considerá-la ideal.

## Onda 3. Delegue uma investigação independente

Delegue a outro agente a investigação com as skills `how` e `why`. Use um contexto novo, sem herdar a conversa quando a ferramenta permitir, como `fork_turns: "none"`.

Na primeira mensagem, forneça somente o relato do bug, o comportamento esperado, a reprodução, as evidências originais e a referência anterior à correção. Não forneça a hipótese inicial, o diff da candidata ou sua conclusão. Se a candidata já estiver no diretório compartilhado, indique a referência original e oriente o agente a analisá-la primeiro. Use uma cópia isolada quando necessário para executar o código original sem interferir no trabalho em andamento.

Peça ao agente que:

- Use `how` para reconstruir o fluxo, as responsabilidades, o estado e as interações que produzem a falha.
- Use `why` para investigar histórico, decisões, requisitos e restrições que expliquem o comportamento. Consulte as fontes disponíveis segundo a skill e registre as lacunas.
- Formule sua própria hipótese causal, alternativas e verificações capazes de distingui-las.
- Retorne evidências com caminhos, símbolos, commits ou fontes, separando fatos, inferências e pontos não verificados.
- Identifique comportamentos que a correção precisa preservar.

O agente pode executar verificações sem modificar a implementação compartilhada. Adapte as ferramentas de `how` e `why` às disponíveis no ambiente, mantendo a investigação de funcionamento e motivação. Não dependa de nomes de ferramentas ou modelos indisponíveis.

Depois que o agente apresentar sua análise inicial, envie a hipótese e a candidata da segunda onda. Peça que confronte a solução com as evidências e aponte contraexemplos, restrições violadas ou correções alternativas. Isso mantém o diagnóstico inicial independente e permite revisar a solução concreta.

## Onda 4. Confronte os resultados e decida

Compare a hipótese inicial, os resultados do experimento e a investigação independente. Verifique se as novas evidências mudam a causa provável, revelam um requisito ou indicam uma solução melhor.

- Se a solução simples continuar sustentada, mantenha-a e explique quais evidências justificam essa escolha.
- Se surgir uma restrição ou um caso não coberto, refine a solução e verifique novamente o bug e os comportamentos afetados.
- Se as evidências refutarem a hipótese inicial, descarte a candidata e teste uma nova hipótese. Retome as ondas afetadas pela mudança.
- Se houver discordância entre as análises, execute uma verificação que diferencie as hipóteses. Não escolha apenas pela confiança do agente ou pelo tamanho do diff.

Só conclua a correção quando as evidências sustentarem a solução escolhida e as verificações relevantes passarem. Se faltarem acesso, dados ou uma reprodução confiável, informe o que permanece em aberto e a próxima verificação necessária.

## Entregue o resultado

Explique a causa sustentada pelas evidências, a solução simples testada, o que a análise independente acrescentou e a decisão de manter, refinar ou substituir a candidata. Resuma as verificações executadas e suas limitações. Diferencie uma correção implementada de uma recomendação ainda não testada.
