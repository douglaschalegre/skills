---
name: conjure-a-local-review
description: Use quando o usuário pedir uma revisão profunda de código sem publicar comentários no Pull Request, incluindo análise do escopo do card, arquitetura, blast radius e complexidade do código novo.
---

# Conjurar uma revisão local

Revise o código e entregue os achados na conversa. Não publique comentários, revisões, aprovações ou pedidos de mudança no PR. Não altere o card no Jira. A revisão não autoriza corrigir a implementação.

## Estabeleça o contexto

1. Leia as instruções do repositório. Identifique a branch ou o PR sob revisão, sua base e a chave do card pelo pedido, pela branch e pela descrição do PR.
2. Consulte o PR apenas para leitura quando houver um. Use a base real do PR ou a comparação indicada pelo usuário. Para uma branch local sem base conhecida, consulte o histórico e o contexto. Se a comparação continuar ambígua, pergunte antes de atribuir mudanças ao PR.
3. Examine os commits e o diff entre a base e a branch. Registre as referências comparadas e inclua alterações locais apenas quando fizerem parte do pedido.
4. Localize e leia as skills `blast-radius` e `principle-build-the-lever` entre as skills disponíveis. Se uma dependência não for encontrada, procure em outras localizações configuradas. Não substitua silenciosamente a skill por outra.

## Confronte as mudanças com o card

Use o MCP Atlassian para consultar o card, sua descrição, critérios de aceite e discussões ou documentos vinculados relevantes. Compare cada mudança de comportamento com os requisitos do card.

Identifique código fora do escopo e explique por que ele não é necessário para cumprir os requisitos. Considere alterações técnicas necessárias à implementação, mesmo quando não aparecem literalmente no card. Diferencie um desvio confirmado de uma dúvida sobre o requisito.

Se o MCP não estiver disponível ou o card não puder ser identificado ou consultado, registre essa lacuna. Continue as outras frentes e peça apenas o contexto que falta. Não invente critérios de aceite nem conclua que uma mudança está fora do escopo apenas pela ausência de uma frase no título.

## Confira a arquitetura

Leia os módulos afetados e seus consumidores, não apenas as linhas do diff. Identifique as regras documentadas, decisões de arquitetura, responsabilidades das camadas e convenções sustentadas pelo código existente.

Procure violações de direção de dependências, responsabilidades deslocadas, acoplamento indevido, duplicação de regras de negócio e contratos quebrados entre módulos. Para cada achado, cite a regra ou o padrão existente e mostre como a mudança o viola. Separe preferência de estilo de uma violação demonstrável. Se as referências divergirem, exponha o conflito.

## Investigue o blast radius

Execute a investigação orientada pela skill `blast-radius`. Siga os efeitos da mudança além do diff, incluindo consumidores indiretos, contratos, persistência e comportamento em execução quando forem relevantes.

Identifique a condição da qual depende a segurança da mudança e procure demonstrá-la executando o código real. Use testes ou reproduções locais e mantenha artefatos temporários fora do repositório. Não altere a implementação revisada. Registre o que foi executado, o resultado e quais riscos continuam sem comprovação.

## Analise a complexidade do código novo

Use `principle-build-the-lever` para produzir uma verificação reproduzível da complexidade ciclomática das funções adicionadas ou modificadas. Essa skill orienta a criação da ferramenta de verificação, não define uma métrica de complexidade. Compare com a base para separar complexidade preexistente daquela introduzida pela mudança.

Crie o menor script que execute o analisador do projeto e compare os resultados da base e da branch nas funções afetadas. Mantenha o script e os resultados em um diretório temporário fora do repositório revisado e informe como executá-lo novamente. Confira o resultado de uma função diretamente no analisador antes de automatizar a comparação. Não adicione nem faça commit de arquivos no projeto durante a revisão.

Prefira a ferramenta de análise já configurada no projeto. Registre a ferramenta, o comando, a métrica por função e o limite definido pelo projeto quando houver. Não confunda complexidade ciclomática com complexidade cognitiva, tamanho do arquivo ou quantidade de linhas. Não invente valores nem um limite universal.

Para os achados relevantes, explique quais decisões, caminhos ou combinações tornam o código difícil de verificar e sugira uma simplificação concreta que preserve o comportamento. Evite propor abstrações apenas para reduzir a métrica.

Se `principle-build-the-lever` estiver ausente, informe a dependência faltante e deixe essa frente explicitamente pendente. Pode registrar observações verificadas sobre o código, mas não declare que executou a skill ou mediu a complexidade sem fazê-lo.

## Entregue a revisão e ofereça a publicação

Apresente primeiro os achados, ordenados por gravidade. Cada achado deve conter o local no código, a categoria da revisão, o cenário afetado, a evidência, o impacto e uma recomendação concreta. Não publique suspeitas como defeitos confirmados.

Resuma as verificações realizadas e a cobertura das quatro frentes, incluindo dependências e fontes indisponíveis. Se não houver achados, diga isso e exponha as limitações da revisão. Uma frente pendente não conta como aprovada.

Ao terminar a revisão local, pergunte: "Quer que eu use a skill cast-review-remarks para publicar os achados no PR?"

Espere a resposta antes de chamar `cast-review-remarks` para publicar. Se o usuário autorizar, leia a skill e use os achados selecionados, com Conventional Comments e as evidências desta revisão. Não repita a investigação inteira sem necessidade.
