# Comandos linux

## Manual
man comando - Ex: man tar ( manual do comando )

## Permissão de root
sudo comando - Usar o sudo na frente do comando
su - permissão de root
sudo su - entrar como root no linux
sudo - usa permissão de root
chmod a+rx my-script.sh   ( dar permissao de executar para o arquivo e pode executar ./script.sh )

## Permissões   
sudo chmod -R 755 <nome da pasta> permissao de escrita
env Env ver todas variaveis de ambiente

## Instalar programas
sudo apt -get install <nome do programa>

## Listar / visualizar arquivos  
ls mostra arquivos de diretórios.
ls -l mostra informações como dono, grupo, tamanho dos arquivos.
ls -a mostrar arquivos ocultos.
ls -la mostra informações como dono, grupo, tamanho dos arquivos e mostra os arquivos 
ocultos.
ls -lrt  Mostrar informações e data
ls <nome do arquivo> lista somente o arquivo

## Sair editor de textos
control + x - sair do editor de textos nano por exemplo 
:q - git bash no windows principalmente ou vi / vim

## Comandos auxiliares
clear limpa a tela e posiciona o cursor no canto superior esquerdo do vídeo.

## Navegar entre diretorios
cd usa-se para mudar de diretório, por exemplo, cd /home/user/ vai para a pasta /home/user/.
cd .. vai para o diretório anterior ao seu atual.
cd /  retornará ao diretório raiz.
cd - - retornará ao diretório anteriormente acessado.
pwd mostra o nome e caminho diretório em que você está.

## Diretórios - criando, alterando e removendo
mkdir - criar um diretório no sistema, por exemplo mkdir [caminho/diretório] em que caminho = caminho onde o diretório será criado, e diretório = nome do diretório que será criado.
rmdir - remove um diretório do sistema, mas o diretório deve estar vazio e você deve ter permissão de gravação, por exemplo, rmdir [caminho/diretório] em que caminho = caminho onde o diretório será removido, e diretório = nome do diretório que será removido.
cat - mostra conteúdo de arquivo binário ou de texto, por exemplo cat [diretório/arquivo] em que diretório/arquivo = localização do arquivo que deseja visualizar o conteúdo.
rm -rf nomedodiretorio - remover o diretorio e tudo que existe dentro

## Console e criar arquivos
echo "mensagem" Exibe uma mensam no console
echo "mensagem" > arquivo.txt Exibe uma mensagem no console no arquivo.txt(insere)
echo "mensagem" >> arquivo.txt Exibe uma mensagem no console no arquivo.txt(altera)
cat arquivo.txt Visualizar o que tem no arquivo

## Remover arquivos e diretórios
rm remove arquivos, por exemplo rm [caminho] [arquivo/diretório] em que caminho = localização do arquivo que deseja apagar, e arquivo/diretório = arquivo que será apagado. Se o caminho for omitido assume-se que o arquivo esteja no diretório atual.
rm -r remove arquivos em subdiretórios.( de forma recursiva)
rm - rf remover tudo da pasta

## Copiar / Mover arquivos
cp -a usuario out usuario copiar a pasta e seu conteudo usuario  para out/usuario  
cp origem destino copia arquivos
cp -r diretorioOrigin diretorioDestino copiar diretórios
 
MV - Mover 
mv atual novo renomear arquivo


## Compactar / descompactar arquivos (zip) 
zip pasta.zip pasta - compactar ( não usar este)
zip -r pasta.ziprm pasta - compactar de forma recursiva ( todos os arquivos)
zip -rq pasta.zip pasta - compactar de forma recursiva ( todos os arquivos) com q (menos log)
unzip -l pasta.zip - mostra o que tem dentro do arquivo
unzip pasta.zip - descompactar arquivos
unzip -q pasta.zip - descompactar arquivos de forma sileciosa sem logs

## Compactar / descompactar arquivos (tar.gz)
tar -cz pasta > pasta.tar.gz  compactar criando um tar.gz zipado
tar -czf pasta.tar.gz pasta/  compactar criando um tar.gz zipado
descompactar o arquivo
tar -xzf pasta.tar.gz  descompactar

## Alterar data - touch
touch pasta.tar.gz Alterar - data do arquivo

## Capturando data atual do sistema
Date - visualizar data atual do sistema

Cat 
cat ~/.bashrc
cat ~/.bashrc | more

## Visualizar coisas dentro de um arquivo ( log por exemplo)
cat arquivo.txt  Visualizar o arquivo inteiro
head arquivo.txt Trazer as 10 primeiras linhas
head -n 3 arquivo.txt  Trazer as primeiras 3 linhas
tail Trazer as 10 últimas linhas
Tail -n 3 arquivo.txt  Trazer as últimas 3 linhas
Less arquivo.txt visualizar o arquivo completo porém com opção de navegar dentro dele

## Buscando dentro de arquivos com grep

sudo find . -name mycarol.txt  procurando pelo arquivo mycarol.txt
grep conteudo file.txt (buscar dentro do arquivo selecionado)
grep -iR 'windows' *.* (buscar dentro de textos no diretório atual)
find . |xargs grep -i -s 'java_home' (buscar dentro de textos , dentro de todos os diretório)
Buscando arquivos - com find
find . |xargs grep -i -s 'java_home' (buscar arquivos pelo nome)
find -name daniel.txt  ( buscar pelo nome exato
find -atime 0 ( busca arquivos que foram acessados em 0 zero dias)
find name danielsmanioto ( busca arquivos do usuário danielsmanioto)
 Monitoramento serviço / aplicação
ps -ef |grep nomeaplicacao (buscar se aplicaçao está ativa no tomcat)

## Java versions
Which java Local onde o java está instalado
Java -version Versao do java
echo $JAVA_HOME
echo $PATH
echo $CLASSPATH

## Onde esta instalado o chrome ? 
which google-chrome-stable

## Arquivos essenciais linux
cat ~/.bashrc 
cat /etc/hosts
cat /etc/hostname

## MONITORAMENTO SERVIDOR LINUX e Espaços utilizados

VERIFICAR ESÇO UTILIZADO RECURSIVO
for dirs in $(ls -l | grep "^d" | awk '{print $9}'); do tamanho=$(du -hs $dirs| awk '{print $1}'); arquivos=$(ls $dirs | wc -l); echo diretorio $dirs ocupa $tamanho e possui $arquivos arquivos; done >> dados_arquivos_anexos.txt
VERIFICAR ESÇO UTILIZADO PASTA E TAMANHO

## DESCOBRIR IP NO UBUNTU

hostname -I
ifconfig  
ifconfig -a
ip addr show
ip a 
curl ifconfig.me

## Caminhando nos diretórios

pwd 		        Verifica qual diretório você está	
cd	                     Vai para a raiz
cd /                          Vai para a raiz
cd ~                         Vai para a pasta do usuário
cd - 	                    Volta para o último dirretório visitado  
cd ..                         Volta 1 diretório na estrutura 
cd /home                Vai até o diretório desejado

## Habilitar SSH no Ubuntu

sudo mv /etc/init/ssh.conf.back /etc/init/ssh.conf
sudo start ssh

## Desabilitar SSH no Ubuntu
sudo stop ssh
sudo mv /etc/init/ssh.conf /etc/init/ssh.conf.back

## Arquivos bash - shellscript
bash script.sh ( executar bash shellscript )
sh script.sh ( executar bash shellscript )
chmod a+rx my-script.sh   ( dar permissao de executar para o arquivo e pode executar ./script.sh )

## ARQUIVO BATCH DE EXEMPLO / Bash aplicação internal services ( startup.sh )

#!/bin/sh
JAVA_HOME=/export01/java/jdk1.7.0_79
DIR_HOME=/export01/tomcat-wccjira-7.0.72/internal-services
JAVA_OPTS=-Dserver.port=8092
exec $JAVA_HOME/bin/java -jar $DIR_HOME/internal-services.jar

Arquivo ~/.bashrc Personal

## JAVA
export JAVA_HOME="/usr/lib/jvm/java-21-oracle"

## MAVEN
export M2_HOME=/opt/apache-maven-3.3.3
export M2=$M2_HOME/bin
export PATH=$M2:$PATH
export MAVEN_OPTS="-Xms512m -Xmx2048m -Xss1024k"

## Copiar arquivos na rede - SCP
scp -r alexandre.albuquerque@172.16.120.60:/home/usuario/arquivo /home/danielsmanioto

## Salvando via scp
scp /home/danielsmanioto/nome_do_arquivo  maquina@172.16.120.60:/home/danielsmanioto  

## Conectando via SSH
ssh maquina@172.16.120.60

## Removendo pacode de atualizar no sudo apt-get update
/etc/apt/sources.list.d   ( remover desta pasta )

## Atualizar sistema
sudo apt-get update
sudo apt-get upgrade

