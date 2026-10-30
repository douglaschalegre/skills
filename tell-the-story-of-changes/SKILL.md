---
name: tell-the-story-of-changes
description: Use quando o usuário pedir para criar, preparar, revisar ou atualizar a descrição de um Pull Request.
---

# Descrição de Pull Request

Produza uma descrição curta, concreta e fiel ao conteúdo do PR.

## Processo

1. Identifique o repositório e o número ou URL do PR informado pelo usuário.
2. Consulte o PR antes de escrever. Use `gh pr view` para obter título, corpo, commits e arquivos alterados. Use `gh pr diff` para entender o comportamento modificado.
3. Não deduza as mudanças apenas pelo título ou pelas mensagens dos commits. Confirme cada item no diff.
4. Identifique o objetivo principal do PR e escreva uma frase introdutória.
5. Agrupe alterações relacionadas e liste apenas resultados relevantes para revisão. Evite narrar detalhes internos sem impacto no comportamento ou na manutenção.
6. Se houver alteração de UI no frontend, capture evidências visuais conforme as regras de captura abaixo e inclua-as na descrição do PR. Revise o texto para remover repetições, termos vagos e afirmações que o diff não sustenta.
7. Entregue somente o texto pronto em Markdown, salvo se o usuário pedir explicações adicionais ou solicitar a atualização do PR no GitHub.
8. Para anexar imagens no PR deve ser utilizado `gh pr edit 190 --repo OWNER/REPO \
--body-file descricao.md \
--attach ./antes.png \
--attach ./depois.png`. De forma alguma adicione imagens no repositório e faça commit delas.

## Captura de evidências visuais

- Toda alteração de frontend que adicionar ou modificar a UI exige evidência visual no PR, na seção `Imagem de antes/depois`.
- Para produzir qualquer evidência visual, reproduza a tela executando exatamente os mesmos componentes usados na aplicação. Importe os componentes reais do projeto e mantenha seus estilos, temas, assets e providers necessários.
- Use valores mockados apenas nos dados, nas respostas das APIs e no estado necessário para reproduzir o cenário. Não substitua os componentes reais por mocks.
- Nunca recrie a UI do zero em HTML/CSS, em componentes paralelos ou em uma página estática que apenas imite a aplicação. Semelhança visual não comprova a alteração no código real.
- Capture o antes com os componentes da versão base e o depois com os componentes da versão do PR. Use os mesmos dados e condições de captura para permitir a comparação. Para uma tela nova, capture o resultado e informe que não existe uma versão anterior.
- Registre junto à evidência a tela ou o estado demonstrado e quais dados foram mockados. Preserve um comando ou procedimento reproduzível para obter a captura com os componentes reais.
- Se não conseguir executar os componentes reais ou capturar a evidência, informe o impedimento e a evidência pendente. Não apresente uma recriação como evidência nem considere a descrição concluída enquanto faltar a evidência obrigatória.

## Template obrigatório

```markdown
> [!NOTE]
> Esta descrição foi gerada por IA, usando a skill [tell-the-story-of-changes](https://github.com/douglaschalegre/skills).

## 1. Descreva o Pull Request (\*)

Este PR [resume o objetivo principal em uma frase].

### Alterações realizadas (\*)

- [Alteração concreta e verificável.]
- [Alteração concreta e verificável.]

### Imagem de antes/depois

### Documentação C4
```

1. Use os títulos exatamente como aparecem no template. Escreva os itens no passado, com frases curtas e ponto final.
2. Sempre que uma alteração de frontend adicionar ou modificar a UI, inclua evidências na seção `Imagem de antes/depois`, seguindo as regras de captura. Essa seção é obrigatória nesses casos.
3. Omita as seções sem (\*) quando não se aplicarem. A seção `Imagem de antes/depois` só pode ser omitida se não houver alteração de UI no frontend. Omita `Documentação C4` quando não houver documentação C4 para exibir.
4. Sobre a documentação C4, o nível de profundidade do diagrama fica a critério do conteúdo do PR. https://c4model.com/diagrams
5. Executar await mermaid.parse(diagrama) em todos os blocos Mermaid antes de publicar.
6. Inclua sempre o disclaimer de geração por IA no início da descrição, exatamente como aparece no template, mesmo quando omitir as seções opcionais.

## Critérios de escrita

- Escreva em português do Brasil.
- Utilize Google developer documentation style guide (+ASD-STE100 Simplified Technical English) para escrever.
- Explique o que mudou e, quando ajudar a entender a mudança, o problema corrigido.
- Use uma alteração por item.
- Una detalhes técnicos que fazem parte da mesma correção.
- Preserve nomes do produto, telas, tarefas, artefatos e integrações usados no código ou informados pelo usuário.
- Não mencione arquivos, funções ou refatorações internas quando elas não ajudam o revisor a entender o resultado.

## Exemplo

```markdown
> [!NOTE]
> Esta descrição foi gerada por IA, usando a skill [tell-the-story-of-changes](https://github.com/douglaschalegre/skills).

## 1. Descreva o Pull Request

Este PR corrige o redirecionamento para os detalhes das tarefas e ajusta o estado de publicação e download dos artefatos no modal de exportação do projeto.

### Alterações realizadas

- Centralizada a definição das abas disponíveis e da aba inicial de cada tarefa.
- Corrigido o redirecionamento para a primeira aba disponível nos detalhes da tarefa.
- Ajustada a identificação de tarefas publicadas com base no estado das revisões.
- Corrigida a coleta de arquivos para incluir artefatos com arquivo único, múltiplos arquivos e documentos de insumo.
- O estado de download agora é controlado pelo identificador do arquivo, evitando marcações incorretas em artefatos com vários documentos.

### Imagem de antes/depois

### Documentação C4
```
