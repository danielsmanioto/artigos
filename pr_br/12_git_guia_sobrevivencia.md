## COMANDOS GIT

### Configurações Iniciais
```bash
# Listar todas as configurações
git config --list

# Configurar nome globalmente
git config --global user.name "Daniel Smanioto"

# Configurar e-mail globalmente
git config --global user.email "daniel.smanioto@gmail.com"

# Configurar nome localmente (apenas neste repositório)
git config user.name "Daniel Smanioto"

# Configurar e-mail localmente (apenas neste repositório)
git config user.email "daniel.smanioto@gmail.com"

# Alterar configurações de nome (recomendado quando há muitas configurações)
git config --global --replace-all user.name danielsmanioto

# Editar arquivo de configurações globalmente
git config --edit --global

INICIAR

# Iniciar repositório
git init

# Visualizar repositórios remotos (por padrão, usamos o origin)
git remote

# Adicionar um repositório origin como remoto
git remote add origin https://github.com/danielsmanioto/SOA

# Subir os arquivos ao servidor remoto pela primeira vez
git push -u origin master

Clonar o Projeto

# Clonar o projeto
git clone caminho_do_projeto

Status
# Verificar o repositório local
git status

Adicionar arquivos
# Adicionar todos os arquivos
git add .

# Adicionar arquivo index.html
git add index.html

# Visualizar as mudanças antes de adicionar
git add -p

Desfazer alteraçoes
# Desfazer o commit
git reset <código_do_commit>

# Limpar tudo não commitado
git reset --hard

# Desatachar o arquivo (untrack)
git reset arquivo

# Tirar o arquivo index.html da área de seleção
git reset HEAD index.html

# Atualizar o git local
git reset --hard origin/feat_o4_s1_seguranca


Remover arquivos
# Remover um arquivo do monitoramento do GIT
git rm <arquivo>

# Remover todos os arquivos e diretórios não rastreados
git clean -fd

### Para Saber as Branches que Pode Remover
```bash
git branch --merged master # Listar branches mergiadas com a master

Renomeando arquivos
git mv <source> <destination> # Mesmo que remover e adicionar

Comitar local
git commit # Comitar local
git commit -m "comentário" # Comitar local com mensagem (ex: "[JIRA] - Mensagem de alteração.")
git commit -a "" # Comitar todos os arquivos alterados
git commit --amend # Possibilita fazer o commit novamente

# Commit Amend
git commit --amend # Possibilita mudar a mensagem do commit

Abortar
git merge --abort # Cancelar merge e voltar ao status inicial

Subir informacoes ao servidor
git push origin <nome_da_branch> # Subir arquivos adicionados com -u
git push # Subir arquivos ao repositório remoto

Capturar do servidor
git pull origin <nome_da_branch> # Atualizar repositório local
git pull # Atualizar repositório local (observação: o pull e merge são mais ou menos a mesma coisa)

Listar branchs
git branch # Mostra todas as branches utilizadas e sinaliza qual você está no momento
git branch -r # Lista todas as branches remotas
git branch -a # Lista todas as branches remotas e locais

Verificar qual branch estou
git branch # Mostra todas as branches utilizadas e sinaliza qual você está no momento
git branch -r # Lista todas as branches remotas
git branch -a # Lista todas as branches remotas e locais

Remover os Untracked
git clean -n --Delete untracked files in the local working directory.

Copiar branch
git checkout -b <nome_branch> # Criar branch local
git push -u origin <nome_branch> # Subir branch para o repositório remoto

Criar branch
git checkout -b <nome_branch> # Criar branch local
git push -u origin <nome_branch> # Subir branch para o repositório remoto

Remover branch
git branch -d <nome_da_branch> # Remover branch local
git branch -D <nome_da_branch> # Remover branch local FORÇA
git push origin --delete <nome_da_branch> # Excluir branch remota
git push origin :<nome_da_branch> # Excluir branch remota (outra forma)

Remover todas as branchs
for i in $(git branch --list "SV*"); do git branch -D $i; done;

Rebase
git rebase master desenvolvimento # Atualiza branch com as alterações da desenvolvimento
git pull --rebase # Não é obrigatório, mas facilita a vida do desenvolvedor que precisa olhar o histórico de commits

Trocae de branchs
git checkout master # Vai para o branch master
git checkout -- benchmarks.rb # Fazer checkout do arquivo benchmarks.rb

Merge
git merge origin <branch> # Merge
git merge clean_up # Merge

Merge tool
git mergetool --tool -help

ignorar arquivos com gitignore
Criar um arquivo chamado .gitignore e colocar o nome dos arquivos dentro (este arquivo fica na raiz do projeto).

Exemplo:
.classpath
.project
.settings/
.meta
.recommenders/
target/
*.ser

Reverter apos commit
git revert <hash> # Reverter alteração pelo hash de commits antigos
git revert HEAD~1

Diff
git diff v0.1 v0.2 # Diferença entre as duas tags
git diff HEAD  
git diff <branch_origem> <branch_destino> # Verifica diferenças entre branches
git diff --staged
git diff v01_03 --name-only # Mostrar diferenças apenas nos nomes

Navegar por bugs
git bisect

Verificar arquivos controlados
git ls-files

Log
git log --pretty=format: --name-only | sort | uniq -c | sort -rg | head -10 # Os 10 objetos mais alterados do seu projeto
git log --pretty=format: --name-only | sort | uniq -c | sort -rg  # Os objetos e quantos commits tiveram no seu projeto
git log -g --grepfgit ls-files="BAU-338" --name-only # Objetos alterados da versão
git log --all --grep='Build 0051'
git log develop..pre_release_5.49.0 # Log dos commits branch ante branch
git log # Visualizar todos os logs
git log -1 # Visualizar a última alteração
git log -1 arquivo # Visualiza a última alteração do arquivo 
git log --pretty=format:"%h %an %s" pom.xml # Alteração do arquivo
git log -1 --author dsmanioto # Visualizar últimas alterações do autor
git log --author dsmanioto # Visualizar todas as alterações do autor
git log --stat # Mostra o que foi modificado em cada commit
git log --stat -p # Mostra o que foi modificado em cada commit (mais detalhado)
git log --graph # Mostra gráfico do log
git log --oneline # Visualiza os logs mostrando o hash do commit e a mensagem
git log --pretty=oneline # Visualiza os logs mostrando o hash do commit e a mensagem
git log --pretty=format:"%h %an %s" # Exibe os logs no formato hash, autor, mensagem de commit
git log --since=30.minutes ou 1.hour ou 2.hours # Exibe commits dos últimos 30 minutos, 1h ou 2h
git log --since=10.hours --until=2.hours # Exibe commits entre as últimas 10h e últimas 2h
git log --before="2010-12-25" # Exibe commits antes do dia 25/12/2010
git reflog # Mostra commits apagados pelo git reset
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --oneline # Gráfico

Quando foi primeiro commiit
# Continuação

### Quando Foi o Primeiro Commit Neste Projeto
```bash
git log --date=relative --reverse --format="%ad" | head -n1

Primeiro e ultimo commit
git log --date=relative --reverse --format="Primeiro commit: %ad" | head -n1 && git log --date=relative --format="Ultimo commit: %ad" | head -n1

numero de contribuicoes de cada auythor por arquivo
git blame --line-porcelain <NOME-DO-ARQUIVO>| sed -n 's/^author //p' | sort | uniq -c | sort -rn

Listar os arquivos versionados
git ls-files

Listar quantidades de alteracoes por pessoas
for FILENAME in $(git ls-files)
do
  echo ${FILENAME}
  git blame --line-porcelain ${FILENAME} | sed -n 's/^author //p' | sort | uniq -c | sort -rn
done 
git log --oneline | grep SCC-289 # Procurar por mensagem de commit

### Quantidade de Commits por Devs
```bash
git shortlog -s -n # Quantidade de commit por dev
git shortlog -sn --since=1.month.ago --until=today # Quantidade de commit por dev no mês
git shortlog -sn --no-merges # Quantidade de commit por dev sem merges
git shortlog -sne # Quantidade de commit por dev - com mais informações
git shortlog -s -n --since "AUG 01 2020" # Quantidade de commits por dev após determinada data 
git shortlog -s -n --author daniel.smanioto # Quantidade de commit do usuário danielsmanioto
git shortlog -s -n --no-merges --author daniel.smanioto # Quantidade de commit do usuário danielsmanioto sem merge

Visulizar alterados com detalhe
git whatchanged
git whatchanged -p # Visualizar o que foi alterado em cada arquivo

Tags
git tag v01_01 # Criar 
git push origin v01_01 # Subir
git checkout v01_01 # Ir para a tag
git tag -l v # Para a tag
git tag --delete v01_01 # Remover a tag

Show
git show # Visualizar alteração do último commit

Stash
git stash # Limpar o diretório de trabalho e pode voltar depois
git stash save 'nome do stash'  # Salva o stash igual o comando git stash porém aplica um nome
git stash apply # Aplicar stash atual
git stash list # Listar os stashs feitos
git stash apply --index 
git stash drop stash@{0}  # Apagar stash 0
git stash pop # Para aplicar o stash e logo em seguida apagá-lo da sua pilha
git stash clear # Limpar todos

Fetch - Obter Tudo que o Servidor Tem que o Local Não
git fetch nomebranch # Obter tudo que o servidor tem que o local não
git fetch --all # Executar antes de fazer o checkout de uma branch
git fetch --all -p # Atualiza as branches e remove as que não são mais usadas

Hash
git cat-file -p pasta+hash # Visualizar conteúdo pelo hash
git cat-file -p f066f6f33c4333301e09bc0f01ed9a0e050ceb25 # Exemplo de visualizar o conteúdo da pasta f0 e





