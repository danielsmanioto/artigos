COMANDOS GIT

Configurações iniciais
git config --list (listar todas as configurações)
git config --global user.name  "Daniel Smanioto" (configurar nome - por padrão colocar usuário do bitbucket GLOBALMENTE)
git config --global user.email  "daniel.smanioto@gmail.com" (Configurar e-mail GLOBALMENTE
git config user.name  "Daniel Smanioto" (configurar nome - por padrão colocar usuário do bitbucket LOCAL SOMENTE NESTE REPOSITÓRIO)
git config user.email  "daniel.smanioto@gmail.com" (Configurar e-mail LOCAL SOMENTE NESTE REPOSITÓRIO)
git config --global --replace-all user.name danielsmanioto (Alterar configuraçoes de nome comandos recomendados quando tem muita config definida)
git config --edit --global  Editar arquivo de configurações

Iniciar
git init (iniciar repositório)
git remote (visualizar repositorios remotos - de padrao usamos o origin)
git remote add origin https://github.com/danielsmanioto/SOA (Adiciona um repositório origin como remoto) 
git push -u origin master  (subir os arquivos ao servidor remoto  uma primeira vez, utilizar quando branch não existe no remoto)   


Clonar o projeto
git clone caminho do projeto (Clonar o projeto)

Status - ter um feedback da situação do repositório local
git status (verificar o repositório local)         

Adicionar arquivos
git add .             (Adicionar todos os arquivos)
git add index.html (Adicionar arquivo index.html)        
git add -p (para visualizar as mudanças antes de adicionar (você tera a opção de aceitar ou não cada alteração, antes de ir para o git)  


Desfazer alterações
git reset <código do commit> -  (desfazer o commit - caso tenha commitado sem querer e não enviado ainda)
git reset --hard (limpar tudo feito, e nao foi comitado ainda - obs> todos tem que ter sido add)
git reset arquivo (desatacha o  arquivo (untrack))
git reset HEAD index.html (tirar o arquivo index.html da area de seleção)
git reset --hard origin/feat_o4_s1_seguranca (atualizar o git local)
git reset --hard origin/pre_release_6.4.0 (atualizar o git local)



Remover arquivo(comando linux)
git rm <arquivo>  (remove um arquivo do monitoramento do GIT (e inclusive remove o arquivo caso ele não tenha sido removido)
git rm --cached arquivo.txt
git clean -fd (remove todos arquivos e diretórios)

Para saber as branchs que pode remover
git branch --merged master Listar branchs mergiadas com a master

Renomear arquivos
git mv <source> <destination> -  (Mesmo que remover e adicionar)


Comitar local
git commit (comitar local)
git commit -m “comantário”     (comitar local com mensagem ex “[JIRA] - Mensagem de alteraçao.”)  
git commit -a ""
git commit --amend  (posibilita fazer o commit novamente)

Commit ammend
git commit --amend (posibilita mudar a mensagem do commit)

Abort
git merge --abort Cancelar merge e voltar ao status inicial

Subir informações ao servidor
git push origin <nome_da_branch>     (subir arquivos adicionados cmd -u)
git push (subir arquivos ao repositório remoto)

Capturar do servidor
git pull origin <nome da branch> (Atualizar repositório local)
git pull 		       (Atualizar repositório local)
observacao: o pull e merge e mais ou menos mesma coisa

Listar branchs e verificar qual branch estou
git branch (mostra todas as branchs já utilizadas e sinaliza qual vc está no momento)
git branch -r (lista todos as branchs remotos)
git branch -a (lista todos as branchs remotos e locais)

Remover os untracked
git clean -n —Delete untracked files in the local working directory.

Criar branch
git checkout -b <nome_branch> (criar branch local)
git push -u origin<nome_branch> (subir branch o repositório remoto)

Remover branch  (deve estar em outra branch)
git branch -d <nome_da_branch> (remover branch local)
git branch -D <nome_da_branch> (remover branch loca FORCE)
git push origin --delete <nome_da_branch> (excluir branch remota)
git push origin : <nome_da_branch> (excluir branch remota ‘testar’ - outra forma)

Remover todas as branchs
for i in $(git branch --list "SV*"); do  git branch -D $i;  done;

Rebase (mais fácil de resolver conflitos por que mostra um de casa vez)
git rebase master  desenvolvimento (Atualiza branch com as alterações da desenvolvimento)
git pull --rebase Não é obrigatório, mas facilita a vida do desenvolvedor que precisar olhar o histórico de commits para caçar um bug novo e entender o que houver.

Checkout - trocar de branch
git checkout master   (Vai para o breach master)
git checkout -- benchmarks.rb (fazer checkout do arquivo benchmarks.rb)

Merge (o merge é parecido com o pull) 
git merge origin <breach> (merge)
git merge clean_up

Merge Tool
 git mergetool --tool -help

Ignorar e não enviar arquivo (.gitignore)
Criar um arquivo chamado .gitignore e colocar o nome dos arquivos dentro ( este arquivo fica na raiz do projeto) 

Exemplo: 

.classpath
.project
.settings/
.meta
.recommenders/
target/
*.ser

Reverter(reverter apos commit)
git revert <hash> (reverter alteracao pelo hash - de commits antigos)
git revert HEAD~1


Diff
git diff v0.1 v0.2 (diferença entre as duas tags)
git diff HEAD  
git diff <breach origem> <breach destino> (verifica diferenças breach)
git diff - staged
git diff v01_03 --name-only (Mostrar difrenças somente nomes)


Navegar por bugs
git bisect

Verificar arquivos controlados
git ls-files

Log

git log --pretty=format: --name-only | sort | uniq -c | sort -rg | head -10 (os 10 objetos mais alterados do seu projeto)
git log --pretty=format: --name-only | sort | uniq -c | sort -rg  (os objetos e quantos comitês tiveram no seu projeto)
git log -g --grepfgit ls-files="BAU-338" --name-only (objetos alterados da versão)
git log --all --grep='Build 0051'
git log develop..pre_release_5.49.0 (log dos commits branch ante branch)
git log (visualizar todos os logs)
git log -1 (Visualizar a última alteração)
git log -1 arquivo (visualiza) a última alteração do arquivo 
git log --pretty=format:"%h %an %s" pom.xml (alteração do arquivo)
git log -1 --author dsmanioto (visualisar última as auteraçõs do autor)
git log --author dsmanioto (visualisar todas as auteraçõs do autor)
git log --stat (Mostra o que foi modificado em cada commit)
git log --stat -p (Mostra o que foi modificado em cada commit(mostra mais detalhado))
git log --graph (Mostra gráfico do log)
git log --oneline (visualiza os logs de forma que mostra o hash do commit, linha rcommit)
git log --pretty=oneline (visualiza os logs de forma que mostra o hash do commit, linha rcommit)
git log --pretty=format:"%h %an %s" (exibe os log no formato hash, autor, mensagem de commit)
git log --since=30.minutes ou 1.hour ou 2.hours (Exibe commits dos últimos 30 minutos, 1h ou 2h)
git log --since=10.hours --until=2.hours (Exibe commits entre as últimas 10h e últimas 2h)
git log --before="2010-12-25" (Exibe commits antes do dia 25/12/2010)
git reflog (Mostra commits apagados pelo git reset)
 
git log \
  --graph \
  --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' \
  --oneline gRAFICO


Quando foi o primeiro commit neste projeto
git log --date=relative --reverse --format="%ad" | head -n1

Primeiro e Último commit 
git log --date=relative --reverse --format="Primeiro commit: %ad" | head -n1 && git log --date=relative --format="Ultimo commit: %ad" | head -n1

Número de contribuições cada autor teve no arquivo
git blame --line-porcelain <NOME-DO-ARQUIVO>| sed -n 's/^author //p' | sort | uniq -c | sort -rn


Listar os arquivos versionados
git ls-files


Listando arquivo e quantidade de alteracoes por pessoa
for FILENAME in $(git ls-files)
do
echo ${FILENAME}
git blame --line-porcelain ${FILENAME} | sed -n 's/^author //p' | sort | uniq -c | sort -rn
done 
git log --oneline | grep SCC-289  Procurar por mensagem de comite

Quantidade de commits por devs
git shortlog -s -n quantidade de commit por dev
git shortlog -sn --since=1.month.ago --until=today  quantidade de commit por dev no mes
git shortlog -sn --no-merges - quantidade de commit por dev se mmerges
git shortlog -sne quantidade de commit por dev - com mais informações
git shortlog -s -n --since "AUG 01 2020" - quantidade commits por dev após determinada data 
git shortlog -s -n --author daniel.smanioto quantidade de commit do username danielsmanioto
git shortlog -s -n --no-merges --author daniel.smanioto quantidade de commit do username danielsmanioto sem merge

Logs dos commits por dev
Se  logs do user nama daniel.smanioto
 
Visualizar arquivos alterados com detalhes
git whatchanged
git whatchanged -p (visualizar o que foi alterado em cada arquivo)




Tags
git tag v01_01 Criar 
git push origin v01_01 Subir
git checkout v01_01 Ir para a tag
git tag -l v para a tag
git tag --delete v01_01 remover a tag

Show
git show ( visualizar alteracao do ultimo commit)

Strash
git stash (limpar o diretório de trabalho e pode voltar depois)
git stash save ‘nome do stash’  (salva o stash igual o comando git stash porém aplica um nome) 
git stash apply (aplicar stash atual)
git stash list (listar os stashs feitos)
git stash apply --index 
git stash drop stash@{0}  (apagar stash 0)
git stash pop (para aplicar o stash e logo em seguida apagá-lo da sua pilha) *
git stash clear (Limpar todos)

Fetch obter tudo que o servidor tem que o local não 
git fetch nomebranch (obter tudo que o servidor tem que o local não)
git fetch --all (executar antes de fazer o checkout de uma branch)
git fetch --all -p (atualiza as branches e remove as que não são mais usadas)

Hash
git cat-file -p pasta+hash (visualizar conteudo pelo hash)
git cat-file -p f066f6f33c4333301e09bc0f01ed9a0e050ceb25 (exemplo de visualizar o conteudo da pasta f0 e o hash)
git show 319ce51fd9cc5a314ceb4309665ead5b47eb919b (vizualisar arquivo alterado)


Cherry pick
git cherry-pick <SHA1>  (Aplica as alterações de um commit especifico na branch atual).
git cherry-pick abcd..1234 ()

Você deve usar a opção -n ou --no-commit. Para não gerar um novo commit

Lock
apagar arquivo .git/index.lock

BLAME 
git blame my_file Verificar quem e quando alterou o arquivo


ALIAS 
(alterar o arquivo .gitconfig) 
Exemplo meus alias  → git config --edit --global

[alias]
st = status
ci = commit
publica = !git checkout master && git pull && git checkout dev && git rebase master &&  git checkout master && git merge dev && git push
envia = !git checkout master && git pull && git checkout desenvolvimento && git rebase master && git checkout master && git merge desenvolvimento && git push
historico = !git log --pretty='Commit %h de %an em %ad: %s' --graph -5



Resolvendo conflitos
Intelijj


Bit Bash
:q
:w
ctrl = x


Keys
SSH KEY
https://git-scm.com/book/en/v2/Git-on-the-Server-Generating-Your-SSH-Public-Key

GIHUB → https://github.com/settings/keys 
GITLAB → http://gitlab.dextra.com.br/profile/keys 
