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
6. Revise o texto para remover repetições, termos vagos e afirmações que o diff não sustenta.
7. Entregue somente o texto pronto em Markdown, salvo se o usuário pedir explicações adicionais ou solicitar a atualização do PR no GitHub.
8. Para anexar imagens no PR deve ser utilizado `gh pr edit 190 --repo OWNER/REPO \
--body-file descricao.md \
--attach ./antes.png \
--attach ./depois.png`. De forma alguma adicione imagens no repositório e faça commit delas.

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
2. Sempre que uma alteração adicionar ou modificar a interface, é recomendado que seja adicionado a imagem com o antes/depois na descrição do PR.
3. Não é obrigatório que existam os itens do template que não possuam (\*). Se não há imagens para mostrar ou documentação C4 para exibir, não é necessário ter esse item.
4. Sobre a documentação C4, o nível de profundidade do diagrama fica a critério do conteúdo do PR. https://c4model.com/diagrams
5. Executar await mermaid.parse(diagrama) em todos os blocos Mermaid antes de publicar.
6. Inclua sempre o disclaimer de geração por IA ao final da descrição, exatamente como aparece no template, mesmo quando omitir as seções opcionais.

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
