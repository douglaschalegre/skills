---
name: cast-review-remarks
description: Publica comentários em Pull Requests no GitHub, incluindo comentários de revisão e respostas a revisões de outros desenvolvedores. Use quando o usuário pedir para comentar em um PR ou responder a uma thread de revisão.
---

# Comentar em Pull Requests

Publique o comentário no PR ou na thread indicada pelo usuário. Se o pedido for apenas preparar ou revisar o texto, entregue o texto sem publicar.

## Leia o contexto

1. Identifique o repositório, o PR e o comentário ou trecho do diff ao qual o pedido se refere.
2. Consulte a descrição, o diff atual e a discussão relevante antes de escrever. Use `gh pr view`, `gh pr diff` e a API do GitHub conforme necessário.
3. Para responder a uma revisão, leia toda a thread e verifique no código o ponto levantado. Se houve mudanças após a revisão, confira os commits posteriores e o estado atual do trecho.
4. Se não for possível identificar o PR ou a thread pelo contexto disponível, peça a informação que falta antes de publicar.

## Escreva o comentário

- Escreva em português do Brasil, salvo orientação diferente do usuário.
- Seja direto, respeitoso e específico. Diferencie uma dúvida, uma sugestão e um problema confirmado.
- Sustente os comentários de revisão com o código e o comportamento observado. Explique o impacto e indique uma mudança concreta quando houver um problema.
- Ao responder a outro desenvolvedor, trate o ponto levantado. Informe o que foi alterado e como foi verificado, ou explique a decisão com evidências.
- Não afirme que uma correção foi feita ou que um teste passou sem verificar. Se faltar evidência, apresente a incerteza como dúvida.
- Não prometa mudanças em nome do usuário nem declare concordância com a revisão sem respaldo no pedido ou no trabalho realizado.

Sempre que responder a uma thread de PR em nome do douglas, inclua o seguinte disclaimer na resposta, exatamente como escrito:

```markdown
> [!NOTE]
> Codex do douglas na área, respondendo com o aval dele!
```

## Publique no local correto

1. Para um comentário geral sobre o PR, use um comentário na conversa do PR.
2. Para um comentário de revisão sobre código, publique no arquivo e na linha corretos do diff. Confira o commit, o caminho e o lado do diff antes de enviar.
3. Para responder a uma revisão, use a thread original. Obtenha o identificador do comentário ou da thread na API, em vez de criar um comentário geral desconectado da discussão.
4. Use as operações de comentários ou revisões da API do GitHub quando a CLI não oferecer o posicionamento ou a resposta necessários. Preserve Markdown e quebras de linha com arquivo temporário e `--body-file`, ou com um corpo estruturado na API.
5. Publique uma revisão com comentários quando esse for o pedido. Só aprove o PR, solicite mudanças formalmente ou resolva uma thread se o usuário pedir essas ações.
6. Se o envio retornar erro, confira se o comentário foi publicado antes de tentar novamente, para evitar duplicatas.
7. Confirme o conteúdo e o destino após a publicação. Entregue o link do comentário ou da revisão publicada.

Respeite as instruções do ambiente para autenticação e execução de `gh`. No ambiente codex-work do douglas, execute todos os comandos `gh` fora do sandbox, com `sandbox_permissions: "require_escalated"` desde a primeira tentativa. A autenticação usa o Keychain do macOS. Respeite as aprovações exigidas pelo ambiente.
