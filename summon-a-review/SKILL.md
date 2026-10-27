---
name: summon-a-review
description: Abre Pull Requests no GitHub, atribui ao próprio usuário e usa a skill tell-the-story-of-changes para escrever a descrição. Use quando o usuário pedir para abrir ou criar um PR.
---

# Abrir Pull Request

Conclua a abertura do PR no GitHub. Não encerre entregando apenas um título, uma descrição ou um comando para o usuário executar.

## Defina a base

1. Identifique o repositório, a branch de trabalho e as instruções do usuário.
2. Se o usuário indicar uma base, use essa branch.
3. Caso contrário, use a branch de onde a branch de trabalho surgiu. Consulte o contexto da sessão, o reflog e a configuração `branch.<branch>.gh-merge-base` para identificar essa origem.
4. Confirme a base no histórico e confira os commits e o diff com `git log BASE..HEAD` e `git diff BASE...HEAD`.

O Git não registra uma relação permanente entre a branch e sua origem. O upstream pode apontar para a própria branch remota e não identifica necessariamente a base. Um ancestral comum, sozinho, também não prova a origem. Se as evidências forem insuficientes ou conflitantes, pergunte qual base usar antes de criar o PR. Não assuma a branch padrão do repositório.

## Escreva a descrição

Use obrigatoriamente a skill `tell-the-story-of-changes`. Localize e leia seu `SKILL.md` entre as skills disponíveis. Neste repositório, ela está em [tell-the-story-of-changes](../tell-the-story-of-changes/SKILL.md).

Identifique as evidências disponíveis antes de chamar `tell-the-story-of-changes`:

- Se o PR ainda não existir, forneça o repositório, a branch de trabalho, a base escolhida, os commits de `git log BASE..HEAD` e o diff de `git diff BASE...HEAD`. Nesse caso, substitua a consulta a um PR existente prevista em `tell-the-story-of-changes` por essas evidências.
- Se o PR já existir, identifique seu número ou URL. Consulte `gh pr view` para obter título, corpo, commits e arquivos alterados, e `gh pr diff` para entender o comportamento modificado.

Confirme cada alteração no diff. Não deduza o conteúdo apenas pelo título ou pelas mensagens dos commits. Siga o template e os critérios de escrita de `tell-the-story-of-changes`. Salve a descrição em um arquivo temporário fora do repositório para passá-la com `--body-file`.

Se `tell-the-story-of-changes` não estiver disponível, informe a dependência ausente antes de publicar. Não substitua seu template por uma descrição improvisada.

## Abra e confira o PR

1. Confira se já existe um PR aberto para a mesma branch e base. Se existir, reutilize o PR e retorne sua URL, sem criar uma duplicata. Garanta a atribuição ao próprio usuário.
2. Publique a branch no remoto correto se necessário, sem usar force push.
3. Crie o PR com base e head explícitos, título coerente com o diff e a descrição produzida por `tell-the-story-of-changes`:

   ```sh
   gh pr create --repo OWNER/REPO --base BASE --head HEAD --title 'TÍTULO' --body-file CAMINHO_DA_DESCRICAO --assignee '@me'
   ```

4. Use `--assignee '@me'` para atribuir o PR ao usuário autenticado no GitHub. Não presuma o login a partir do autor dos commits.
5. Não adicione labels, tags ou revisores, a menos que o usuário solicite explicitamente. Não inclua `--label` nem `--reviewer` por padrão. Não remova atribuições feitas por automações do repositório.
6. Consulte o PR criado com `gh pr view` e confirme URL, base, head, descrição e assignee. Se a atribuição não tiver sido aplicada, corrija com `gh pr edit URL --add-assignee '@me'`.
7. Se a criação retornar erro, verifique se o PR foi criado antes de tentar novamente.
8. Entregue a URL e informe a base e o assignee confirmados.

Abrir o PR não autoriza executar o merge. Só faça o merge se o usuário pedir.
