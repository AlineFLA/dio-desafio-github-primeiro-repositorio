# Anotações do Curso de Introdução ao Git e ao GitHub



## Versão de instalação

GIT 2.37.2 - DIO

------------------------------------
### Data:16/08/2022 - terça

WINDOWS							UNIX

- cd (entrar e sair)				cd
- dir (ver)						ls
- mkdir (criar)					mkdir
- del/rmdir /s/q (excluir)		rm -rf
- cls (limpar)					clear (ctrl+L)
- (tab): completa
- seta: comandos anteriores
- echo hello>hello.txt (criar arquivo)



------------------------------------
### Data:23/08/2022 - terça

- Instalando GIT 2.37.2
- O curso instalou o 2.33.0
- Não foi instalado o "GIT CREDENCIAL MANAGER CORE"
- Executável> Git Bash



------------------------------------
### Data:23/08/2022 - terça

- openssl sha1



------------------------------------
### Data:23/08/2022 - terça

BLOBS(BOLHA): guarda o couteúdo
echo -e 'conteudo' | git hash-object --stdin

echo -e 'conteudo' | openssl sha1

echo -e 'blob 9\0conteudo' | openssl sha1

TREE(ÁRVORE): guarda os blobs e outras tree, guarda os conteúdos e as pastas

COMMIT: além dos conteúdos e as pastas, guarda, parentes, autor, mensagem, timestamp



------------------------------------
### Data:23/08/2022 - terça

- Chave SSH e Tokens

#### Gerando SSH Keys

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/OneDrive/Área de Trabalho
$ ssh-keygen -t ed25519 -C aflessaazevedo@gmail.com
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/feliz/.ssh/id_ed25519):
Created directory '/c/Users/feliz/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/feliz/.ssh/id_ed25519
Your public key has been saved in /c/Users/feliz/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:GH+TK72YApKndPssV/CofT2KxaxZSZl4Ranrc7H7Av4 aflessaazevedo@gmail.com
The keys randomart image is:
+--[ED25519 256]--+
|          ..     |
|         ..      |
|      .  ..      |
|      .=.+ .     |
|   .  o+S.+      |
|  + + .==+.o     |
| . = = +Booo     |
|  . +.+*=+*.     |
|     +*o+=E=.    |
+----[SHA256]-----+

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/OneDrive/Área de Trabalho
$(cltr+L)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/OneDrive/Área de Trabalho
$ cd /c/Users/feliz/.ssh/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/.ssh
$ ls
id_ed25519  id_ed25519.pub

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/.ssh
$ cat id_ed25519.pub
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIEotatoziLYUUEfn5rdnSrZpYo6CTl0fW26qKW54gDTI aflessaazevedo@gmail.com

<Colocar essa chave pública gerada no GitHub>

#### Passando a chave gerada para o agent

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/.ssh
$ ls
id_ed25519  id_ed25519.pub

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/.ssh
$ pwd
/c/Users/feliz/.ssh

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/.ssh
$ eval $(ssh-agent -s)
Agent pid 922

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/.ssh
$ ls
id_ed25519  id_ed25519.pub

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/.ssh
$ ssh-add id_ed25519
Enter passphrase for id_ed25519:
Identity added: id_ed25519 (aflessaazevedo@gmail.com)

#### Clonando:




------------------------------------
### Data:23/08/2022 - terça

- Iniciar com GIT
- Iniciar versionamento no GIT
- Criar um COMMIT

git init
git add
git commit

ls -a (lista arquivos ocultos)

#### Configuração inicial do GIT:

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas
$ git init
Initialized empty Git repository in C:/Users/feliz/workspace/livro-receitas/.git/
---Isso cria arquivo oculto dentro da pasta

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls -a
./  ../  .git/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ cd .git

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas/.git (GIT_DIR!)
$ ls
HEAD  config  description  hooks/  info/  objects/  refs/


feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --global user.email "aflessaazevedo@gmail.com"

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --global user.name Aline



#### Markdown

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git add *

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git commit -m "commit inicial"
[master (root-commit) ad082f1] commit inicial
 1 file changed, 10 insertions(+)
 create mode 100644 strogonoff.md.txt

------------------------------------
### Data:24/08/2022 - quarta*/

- Untracked: fora do GIT
- Tracked: dentro do GIT

1) Unmodified	-	ainda não foi modificado
2) Modified	-	foi modificado
3) Staged	-	quando a alteração é adicionada ao GIT (git add)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~
$ cd workspace

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace
$ ls
livro-receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace
$ cd livro-receitas

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls
strogonoff.md.txt

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
nothing to commit, working tree clean

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ mkdir receitas

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls
receitas/  strogonoff.md.txt

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ mv strogonoff.md.txt ./receitas

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls
receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ cd receitas

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas/receitas (master)
$ ls
strogonoff.md.txt

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas/receitas (master)
$ cd ..

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    strogonoff.md.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        receitas/

no changes added to commit (use "git add" and/or "git commit -a")

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git add strogonoff.md.txt receitas

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    strogonoff.md.txt -> receitas/strogonoff.md.txt


feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git commit -m "cria pasta receitas, move arquivo para receitas"
[master 33d4a60] cria pasta receitas, move arquivo para receitas
 1 file changed, 0 insertions(+), 0 deletions(-)
 rename strogonoff.md.txt => receitas/strogonoff.md.txt (100%)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
nothing to commit, working tree clean

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls
receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ echo > README.md

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls
README.md  receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git add *
warning: in the working copy of 'README.md', LF will be replaced by CRLF the next time Git touches it

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls
README.md  receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   README.md


feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git commit -m "adiciona index"
[master bb2828f] adiciona index
 1 file changed, 5 insertions(+)
 create mode 100644 README.md



------------------------------------
### Data:24/08/2022 - quarta

- Trabalhando com GitHub



-------------------------------------------------------------------------
#### Verificando configurações:

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager-core
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.email=aflessaazevedo@gmail.com
user.name=Aline
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true

-------------------------------------------------------------------------
#### Comando para remover configuração:

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --global --unset user.email

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --global --unset user.name

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager-core
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true

-------------------------------------------------------------------------
#### Comando para incluir configuração:

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --global user.email "aflessaazevedo@gmail.com"

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --global user.nome "Aline"

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git config --list
diff.astextplain.textconv=astextplain
filter.lfs.clean=git-lfs clean -- %f
filter.lfs.smudge=git-lfs smudge -- %f
filter.lfs.process=git-lfs filter-process
filter.lfs.required=true
http.sslbackend=openssl
http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
core.autocrlf=true
core.fscache=true
core.symlinks=false
pull.rebase=false
credential.helper=manager-core
credential.https://dev.azure.com.usehttppath=true
init.defaultbranch=master
user.email=aflessaazevedo@gmail.com
user.nome=Aline
core.repositoryformatversion=0
core.filemode=false
core.bare=false
core.logallrefupdates=true
core.symlinks=false
core.ignorecase=true

-------------------------------------------------------------------------
#### Publicando no GitHub

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ ls
README.md  receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
nothing to commit, working tree clean

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git remote add origin https://github.com/AlineFLA/livro-receitas.git

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git remote -v
origin  https://github.com/AlineFLA/livro-receitas.git (fetch)
origin  https://github.com/AlineFLA/livro-receitas.git (push)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git status
On branch master
nothing to commit, working tree clean

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git push origin master
--Vai pedir uma autenticação
--Após colocar meu email e senha:
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (8/8), 911 bytes | 911.00 KiB/s, done.
Total 8 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/AlineFLA/livro-receitas.git
 * [new branch]      master -> master

-------------------------------------------------------------------------
#### Resolvendo conflitos:

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git pull origin master
From https://github.com/AlineFLA/livro-receitas

 * branch            master     -> FETCH_HEAD
Already up to date.

#### Fazer a alteração e:

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ git commit -m "resolve conflitos"

-------------------------------------------------------------------------
#### Baixando repositórios de GitHub:

#### Copiar a URL do repositório no Git Hub: 

#### https://github.com/python/cpython.git



feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/livro-receitas (master)
$ cd ..

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace
$ ls
livro-receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace
$ git clone https://github.com/python/cpython.git
Cloning into 'cpython'...
remote: Enumerating objects: 909946, done.
remote: Counting objects: 100% (215/215), done.
remote: Compressing objects: 100% (164/164), done.
remote: Total 909946 (delta 117), reused 115 (delta 50), pack-reused 909731
Receiving objects: 100% (909946/909946), 498.04 MiB | 13.33 MiB/s, done.
Resolving deltas: 100% (721213/721213), done.
Updating files: 100% (4976/4976), done.

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace
$ ls
cpython/  livro-receitas/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace
$ cd cpython

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/cpython (main)
$ ls
Doc/      Lib/             Modules/  Parser/     Tools/         configure*
Grammar/  Mac/             Objects/  Programs/   aclocal.m4     configure.ac
Include/  Makefile.pre.in  PC/       Python/     config.guess*  install-sh*
LICENSE   Misc/            PCbuild/  README.rst  config.sub*    pyconfig.h.in

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/cpython (main)
$ ls -a
./                 .gitignore  Makefile.pre.in  Programs/      configure*
../                Doc/        Misc/            Python/        configure.ac
.azure-pipelines/  Grammar/    Modules/         README.rst     install-sh*
.editorconfig      Include/    Objects/         Tools/         pyconfig.h.in
.git/              LICENSE     PC/              aclocal.m4
.gitattributes     Lib/        PCbuild/         config.guess*
.github/           Mac/        Parser/          config.sub*

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/workspace/cpython (main)
$ git remote -v
origin  https://github.com/python/cpython.git (fetch)
origin  https://github.com/python/cpython.git (push)








------------------------------------
### Data:24/08/2022 - quarta

- Desafio de Projeto do Git/GitHub



feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git
$ ls
DIO/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git
$ cd DIO

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO
$ git clone https://github.com/AlineFLA/dio-desafio-github-primeiro-repositorio.git
Cloning into 'dio-desafio-github-primeiro-repositorio'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 12 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (2/2), done.

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO
$ cd dio-desafio-github-primeiro-repositorio/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ ls
'Introdução ao Git e ao GitHub'/   README.md

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        "Introdu\303\247\303\243o ao Git e ao GitHub/"

nothing added to commit but untracked files present (use "git add" to track)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ cd Introdução\ ao\ Git\ e\ ao\ GitHub/

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio/Introdução ao Git e ao GitHub (main)
$ ls
Anotações.txt

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio/Introdução ao Git e ao GitHub (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ./

nothing added to commit but untracked files present (use "git add" to track)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio/Introdução ao Git e ao GitHub (main)
$ cd ..

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ ls
'Introdução ao Git e ao GitHub'/   README.md

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git add *

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   "Introdu\303\247\303\243o ao Git e ao GitHub/Anota\303\247\303\265es.txt"


feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git commit -m "adiciona pasta de Introdução ao Git e ao GitHub"
[main abc8968] adiciona pasta de Introdução ao Git e ao GitHub
 1 file changed, 498 insertions(+)
 create mode 100644 "Introdu\303\247\303\243o ao Git e ao GitHub/Anota\303\247\303\265es.txt"

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git remote -v
origin  https://github.com/AlineFLA/dio-desafio-github-primeiro-repositorio.git (fetch)
origin  https://github.com/AlineFLA/dio-desafio-github-primeiro-repositorio.git (push)

feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git push origin master
error: src refspec master does not match any
error: failed to push some refs to 'https://github.com/AlineFLA/dio-desafio-github-primeiro-repositorio.git'

#### Deu erro, pois coloquei o nome "master" ou invés de "main"



feliz@LAPTOP-1KEJMEO0 MINGW64 ~/Git/DIO/dio-desafio-github-primeiro-repositorio (main)
$ git push origin main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 3.77 KiB | 1.88 MiB/s, done.
Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/AlineFLA/dio-desafio-github-primeiro-repositorio.git
   cc39379..abc8968  main -> main