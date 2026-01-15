# Uso de Git Worktree

Esta documentação descreve de forma simples como utilizar **git worktree** para trabalhar com múltiplos branches ao mesmo tempo, sem a necessidade de ficar alternando (`checkout`) entre eles.

---

## O que é Git Worktree?

O `git worktree` permite que um mesmo repositório Git tenha **múltiplas pastas de trabalho**, cada uma associada a um branch diferente.

Com isso, é possível:
- Trabalhar em mais de uma feature ao mesmo tempo
- Criar hotfix sem interromper o desenvolvimento atual
- Evitar uso excessivo de `git stash`
- Aumentar a produtividade

---

## Estrutura Exemplo

```text
ds-clientes-server/      -> branch main
wt-feature-ai/           -> branch feature/ai
wt-hotfix-login/         -> branch hotfix/login
```

## Comandos basicos
```
git worktree list
```

```
git worktree add -b feature/ai ../wt-feature-ai
```

```
git worktree remove ../wt-feature-ai
```



