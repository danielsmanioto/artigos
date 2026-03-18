# Git Worktree na prática (para quem já cansou de abrir 15 abas)

Se você é sênior e ainda resolve contexto paralelo com `stash`, checkout frenético e oração, este artigo é pra você.

`git worktree` permite ter **múltiplas branches ativas ao mesmo tempo**, cada uma em sua pasta. Sem gambiarra, sem conflito de contexto e sem perder ritmo.

Referência do projeto: [ds-git-and-github](https://github.com/danielsmanioto/ds-git-and-github)

---

## Por que usar no dia a dia de time sênior

No mundo real, você está em feature A e, do nada:

- produção quebra (hotfix);
- precisa revisar comportamento entre duas branches;
- quer validar uma hipótese sem sujar o que já está estável.

Com `worktree`, você não interrompe o fluxo atual. Só abre outra pasta e segue o jogo.

---

## Cenários onde ele brilha

- **Hotfix paralelo** sem sair da feature atual.
- **Comparação lado a lado** de branches (refatoração vs legado).
- **Spike técnico** isolado sem risco de misturar mudanças.
- **Code review avançado** com execução local de duas versões.

---

## Setup rápido (modelo clássico)

Dentro do repositório principal:

```bash
# cria uma nova worktree já na branch desejada
git worktree add ../ds-hotfix hotfix/login-timeout

# lista worktrees ativas
git worktree list

# remove worktree quando não precisar mais
git worktree remove ../ds-hotfix

# limpa referências antigas
git worktree prune
```

---

## Estrutura recomendada com repositório bare (modo “organizado de verdade”)

Se você quer escalar isso com disciplina, use um diretório central com **repo bare** e worktrees ao redor.

### Exemplo de estrutura

```text
workspace/
├── ds-git-and-github.git/      # repositório bare (metadados Git)
├── ds-main/                    # worktree da main
├── ds-feature-ai/              # worktree de feature
└── ds-hotfix-auth/             # worktree de hotfix
```

### Como montar

```bash
# 1) clone bare
git clone --bare git@github.com:danielsmanioto/ds-git-and-github.git ds-git-and-github.git

# 2) cria worktree da main
git --git-dir=ds-git-and-github.git worktree add ds-main main

# 3) cria worktree de feature
git --git-dir=ds-git-and-github.git worktree add ds-feature-ai -b feature/ai-review origin/main

# 4) cria worktree de hotfix
git --git-dir=ds-git-and-github.git worktree add ds-hotfix-auth -b hotfix/auth origin/main
```

### Por que esse formato é ótimo

- centraliza o histórico Git em um lugar só;
- facilita automação e scripts;
- reduz chance de confusão em times com várias frentes simultâneas.

---

## Boas práticas para times sêniores

- Nomeie worktrees com objetivo claro: `repo-hotfix-x`, `repo-feature-y`.
- Use branches curtas e focadas por contexto.
- Não deixe worktree “zumbi” parada por semanas.
- Antes de remover worktree, garanta commit/push (ou descarte consciente).
- Padronize no time: quando abrir, quando remover, como nomear.

---

## Gatilho real: Worktree + IA para comparar duas bases e destravar merge impossível

Caso prático:

- você removeu um bloco de código em uma branch por decisão arquitetural;
- em outra branch, houve evolução em volta daquele bloco;
- `cherry-pick` virou caos (contexto incompatível, conflito atrás de conflito).

### O que fazer

1. Abra duas worktrees lado a lado (ex.: `feature/cleanup` e `feature/evolucao`).
2. Use IA no editor para comparar os diretórios e identificar:
	- o que foi removido de propósito;
	- o que ainda precisa ser reaproveitado;
	- onde adaptar sem reintroduzir dívida técnica.
3. Aplique a solução final numa terceira branch limpa.

Resultado: resolução rápida, efetiva e **sem retrabalho desnecessário**.

Esse é o tipo de uso que transforma `git worktree` de “comando legal” para **ferramenta estratégica de delivery**.

---

## Fechando

Se você lidera entregas, `git worktree` é um multiplicador de contexto.

Menos troca de branch, menos perda de foco, mais previsibilidade.

Para time sênior, isso não é “nice to have”. É eficiência operacional.
