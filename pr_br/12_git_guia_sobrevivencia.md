# 🗂️ Git Commands — Cheat Sheet Completo

> Referência rápida de comandos Git para o dia a dia. Salva e usa!

---

## 📋 Índice

- [Configurações Iniciais](#-configurações-iniciais)
- [Iniciar Repositório](#-iniciar-repositório)
- [Status e Diff](#-status-e-diff)
- [Adicionar e Comitar](#-adicionar-e-comitar)
- [Desfazer Alterações](#-desfazer-alterações)
- [Branches](#-branches)
- [Merge e Rebase](#-merge-e-rebase)
- [Push e Pull](#-push-e-pull)
- [Tags](#-tags)
- [Stash](#-stash)
- [Log e Histórico](#-log-e-histórico)
- [Fetch](#-fetch)
- [Utilitários](#-utilitários)

---

## ⚙️ Configurações Iniciais

```bash
git config --list                                          # Listar todas as configurações

# Globais
git config --global user.name "Daniel Smanioto"
git config --global user.email "daniel.smanioto@gmail.com"
git config --global --replace-all user.name danielsmanioto # Útil quando há config duplicada
git config --edit --global                                 # Editar config global no editor

# Apenas neste repositório
git config user.name "Daniel Smanioto"
git config user.email "daniel.smanioto@gmail.com"
```

---

## 🚀 Iniciar Repositório

```bash
git init                                          # Iniciar repositório local
git clone <caminho_do_projeto>                    # Clonar projeto existente

git remote                                        # Listar repositórios remotos
git remote add origin https://github.com/user/repo # Adicionar remote origin
git push -u origin master                         # Subir arquivos pela primeira vez
```

---

## 🔍 Status e Diff

```bash
git status                                        # Verificar estado do repositório local

git diff HEAD                                     # Diff do estado atual
git diff --staged                                 # Diff dos arquivos em stage
git diff <branch_origem> <branch_destino>         # Diff entre branches
git diff v0.1 v0.2                               # Diff entre tags
git diff v01_03 --name-only                       # Apenas nomes dos arquivos alterados
```

---

## ➕ Adicionar e Comitar

```bash
# Adicionar
git add .                                         # Adicionar todos os arquivos
git add index.html                                # Adicionar arquivo específico
git add -p                                        # Revisar mudanças antes de adicionar (interativo)

# Comitar
git commit                                        # Abre editor para mensagem
git commit -m "[JIRA-123] - Descrição da alteração"
git commit -a -m "mensagem"                       # Adiciona e comita todos os alterados
git commit --amend                                # Reescrever o último commit (mensagem ou conteúdo)
```

---

## ↩️ Desfazer Alterações

```bash
git reset <hash_do_commit>                        # Desfaz commits até o hash (mantém arquivos)
git reset --hard                                  # Descarta TUDO que não foi commitado ⚠️
git reset --hard origin/feat_branch               # Sincroniza local com remoto (descarta local) ⚠️
git reset HEAD index.html                         # Tira arquivo do stage (unstage)
git reset <arquivo>                               # Desatacha arquivo do tracking

git revert <hash>                                 # Reverte commit criando um novo commit (safe)
git revert HEAD~1                                 # Reverte o último commit

git checkout -- benchmarks.rb                     # Descarta alterações de um arquivo específico
```

---

## 🌿 Branches

```bash
# Listar
git branch                                        # Branches locais (★ = atual)
git branch -r                                     # Branches remotas
git branch -a                                     # Todas (locais + remotas)
git branch --merged master                        # Branches já mergiadas com master

# Criar e trocar
git checkout -b <nome_branch>                     # Cria e já vai pra branch
git checkout master                               # Volta para master
git push -u origin <nome_branch>                  # Sobe nova branch pro remoto

# Remover
git branch -d <nome_branch>                       # Remove local (com validação)
git branch -D <nome_branch>                       # Remove local FORÇADO ⚠️
git push origin --delete <nome_branch>            # Remove remota
git push origin :<nome_branch>                    # Remove remota (forma alternativa)

# Remover várias branches de uma vez (ex: padrão "SV*")
for i in $(git branch --list "SV*"); do git branch -D $i; done

# Renomear arquivo
git mv <origem> <destino>
```

---

## 🔀 Merge e Rebase

```bash
# Merge
git merge origin <branch>
git merge clean_up
git merge --abort                                 # Cancelar merge em andamento

# Merge tool (resolver conflitos)
git mergetool --tool-help                         # Lista ferramentas disponíveis

# Rebase
git rebase master desenvolvimento                 # Atualiza branch com alterações da master
git pull --rebase                                 # Pull com rebase (histórico mais limpo)
```

---

## 📤 Push e Pull

```bash
git push origin <nome_branch>                     # Subir branch específica
git push                                          # Subir branch atual (se já tem tracking)

git pull origin <nome_branch>                     # Atualizar local com branch específica
git pull                                          # Atualizar branch atual
```

---

## 🏷️ Tags

```bash
git tag v01_01                                    # Criar tag
git push origin v01_01                            # Subir tag para remoto
git checkout v01_01                               # Ir para a tag
git tag -l "v*"                                  # Listar tags (com filtro)
git tag --delete v01_01                           # Remover tag
```

---

## 📦 Stash

```bash
git stash                                         # Guarda alterações sem commitar
git stash save 'nome do stash'                    # Guarda com nome descritivo
git stash list                                    # Lista todos os stashes
git stash apply                                   # Aplica o stash mais recente
git stash apply --index                           # Aplica mantendo o stage
git stash pop                                     # Aplica e remove da pilha
git stash drop stash@{0}                          # Remove stash específico
git stash clear                                   # Remove TODOS os stashes ⚠️
```

---

## 📜 Log e Histórico

```bash
# Básico
git log                                           # Log completo
git log -1                                        # Último commit
git log --oneline                                 # Resumido (hash + mensagem)
git log --stat                                    # Arquivos modificados por commit
git log --stat -p                                 # Detalhado (com diff)
git log --graph                                   # Visualização em árvore

# Filtros por autor/data
git log -1 --author dsmanioto
git log --author dsmanioto
git log --since=30.minutes                        # Aceita: 1.hour, 2.hours, etc.
git log --since=10.hours --until=2.hours
git log --before="2010-12-25"

# Filtros por mensagem
git log --all --grep='Build 0051'
git log --oneline | grep SCC-289

# Formato customizado
git log --pretty=format:"%h %an %s"               # hash | autor | mensagem
git log --pretty=format:"%h %an %s" pom.xml       # ...em arquivo específico

# Log bonito com gráfico (salva como alias!)
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --oneline

# Commits apagados
git reflog                                        # Mostra commits removidos pelo reset

# Entre branches/tags
git log develop..pre_release_5.49.0
git log --date=relative --reverse --format="%ad" | head -n1  # Primeiro commit do projeto

# Primeiro e último commit
git log --date=relative --reverse --format="Primeiro commit: %ad" | head -n1 \
  && git log --date=relative --format="Ultimo commit: %ad" | head -n1
```

---

## 🔎 Contribuições por Arquivo/Autor

```bash
# Contribuições de cada autor em um arquivo
git blame --line-porcelain <ARQUIVO> | sed -n 's/^author //p' | sort | uniq -c | sort -rn

# Top 10 arquivos mais alterados no projeto
git log --pretty=format: --name-only | sort | uniq -c | sort -rg | head -10

# Todos os arquivos e quantidade de commits
git log --pretty=format: --name-only | sort | uniq -c | sort -rg

# Commits por dev
git shortlog -s -n                                # Geral
git shortlog -sn --since=1.month.ago --until=today # No mês atual
git shortlog -sn --no-merges                      # Sem merges
git shortlog -sne                                 # Com e-mail
git shortlog -s -n --since "AUG 01 2020"          # A partir de uma data
git shortlog -s -n --author daniel.smanioto       # De um autor específico
git shortlog -s -n --no-merges --author daniel.smanioto

# Contribuições por pessoa em todos os arquivos
for FILENAME in $(git ls-files); do
  echo "${FILENAME}"
  git blame --line-porcelain "${FILENAME}" | sed -n 's/^author //p' | sort | uniq -c | sort -rn
done
```

---

## 📡 Fetch

```bash
git fetch <nome_branch>                           # Busca branch específica do remoto
git fetch --all                                   # Busca tudo do remoto
git fetch --all -p                                # Busca tudo e remove branches deletadas no remoto
```

---

## 🛠️ Utilitários

```bash
# Arquivos
git ls-files                                      # Lista arquivos versionados
git rm <arquivo>                                  # Remove arquivo do tracking
git clean -fd                                     # Remove arquivos e dirs não rastreados ⚠️
git clean -n                                      # Simula o clean (dry-run, seguro)

# Inspecionar
git show                                          # Alterações do último commit
git whatchanged                                   # O que foi alterado
git whatchanged -p                                # Com detalhes de cada arquivo
git cat-file -p <pasta+hash>                      # Inspeciona objeto pelo hash

# Navegar por bugs
git bisect                                        # Busca binária para encontrar o commit do bug

# .gitignore
# Crie na raiz do projeto com os padrões a ignorar:
# .classpath
# .project
# .settings/
# target/
# *.ser
```

---

> 💡 **Dica:** Salve o log bonito como alias:
> ```bash
> git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --oneline"
> ```
> Aí é só rodar `git lg` 🚀
