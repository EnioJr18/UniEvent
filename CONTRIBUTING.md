# Contribuindo com o UniEvent

## Branches

- `main`: versão estável.
- `develop`: integração das funcionalidades.
- `feature/<issue>-descricao`: novas funcionalidades.
- `fix/<issue>-descricao`: correções.
- `docs/<issue>-descricao`: documentação.

## Fluxo

1. Escolha uma Issue em `Ready`.
2. Crie uma branch a partir de `develop`.
3. Implemente somente o escopo da Issue.
4. Execute os testes aplicáveis.
5. Faça commits pequenos e objetivos.
6. Abra Pull Request para `develop`.
7. Vincule a Issue com `Closes #<numero>`.
8. Aguarde revisão antes do merge.

## Convenção de commits

- `feat(events): add event creation service`
- `fix(registration): prevent duplicate registration`
- `docs(uml): add registration sequence diagram`
- `test(checkin): add duplicate check-in tests`
- `chore: update dependencies`

## Definition of Done

Uma tarefa só é considerada concluída quando:
- o código foi implementado;
- os testes relevantes passam;
- o PR foi revisado;
- a integração foi validada;
- a documentação foi atualizada quando necessário;
- a Issue está vinculada ao PR.
