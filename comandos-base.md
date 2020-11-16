# Comandos para começar a brincar com o git

Dado que existe um repositório de exemplo disponível em "[github.com/maisdevbr/ola-mundo](https://github.com/maisdevbr/ola-mundo)" vamos rodar alguns exemplos de comandos para interagir com o git, ao mesmo tempo que você pode aproveitar para começar seus primeiros passos. 

Um repositório é um local onde armazenamos todos os arquivos que fazem parte do projeto. Estes arquivos podem estar organizando em branches diferentes. Estes branches podem representar versões diferentes do projeto, e podem servir para documentar versões fechadas ou indicar a versão de trabalho. 

No caso do repositório de exemplo, o alô mundo, ele está com apenas um arquivo chamado README.txt dentro do branch main, o único existente neste projeto. 

Importante: Dificilmente você vai me ver falando sobre branches. Eu acredito e trabalho em [trunk based development](https://pt.slideshare.net/guilhermeslacerda/trunk-based-development-cbsoft-2011-9447286), e neste formato eu sempre [desenvolvo código no branch principal](https://blog.danielwildt.com/2015/05/22/voce-desenvolve-software-de-que-jeito/). 

Eu costumo usar "main" como sendo o branch principal. No github existe um local nas configurações para trocar o nome do branch principal para quando você criar novos repositórios, em [github.com/settings/repositories](https://github.com/settings/repositories).  

## Clonando o ambiente

O primeiro passo pode ser clonar o ambiente localmente e você pode fazer isso antes fazendo um fork no github para poder ter o repositório no seu perfil. 

Depois de fazer o fork, você pode clonar o ambiente:
``` 
$ git clone git@github.com:<user>/ola-mundo.git
``` 

- [X] Checked

## Modifique o README.md

Adicione algo no arquivo README.md, modifique uma palavra. Agora precisamos verificar o que está diferente no nosso repositório. Para isso usamos o"git status":

```
$ git status
On branch main
Your branch is up-to-date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

- [X] Checked

## Levando os arquivos para o servidor

Criar um pacote de atualização dos arquivos: primeiro adicione os arquivos que devem fazer parte do seu update. Aqui entra o git add:

```
$ git add README.md 
```

Com isso, agora temos mudanças que estão "staged", e prontas para serem adicionadas para um commit:

```
$ git status
On branch main
Your branch is up-to-date with 'origin/main'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md
``` 

- [X] Checked

Se você adicionou o arquivo por engano, o próprio git retornou o comando que você pode usar para desfazer o add, usando git reset especificando o arquivo. 

Agora que temos as mudanças para serem enviadas, precisamos usar o git commit:

```
dwildt:~/environment/maisdevbr/ola-mundo (main) $ git commit -m "markdown"
[main 5c2f365] markdown
 1 file changed, 1 insertion(+), 1 deletion(-) 
```

- [X] Checked

Indiquei através do "-m" a mensagem do commit. Depois de ter feito, gostaria de mudar, para "link para tutorial de markdown". Para poder mudar a mensagem do commit recém feito, antes dele ser enviado para a origem, podemos usar --amend indicando uma nova mensagem de commit. 

```
$ git commit --amend -m "link para tutorial de markdown"
[main b9e5b41] link para tutorial de markdown
 Date: Mon Nov 16 04:36:05 2020 +0000
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Faça pacotes de commit somente com o que precisar. Commits pequenos são importantes para explicar o que você está fazendo, e vale para poder contar histórias das suas modificações. 

E para enviar os arquivos para a origem usamos git push:

```
$ git push origin main
Counting objects: 3, done.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 446 bytes | 446.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:maisdevbr/ola-mundo.git
   558268c..b9e5b41  main -> main
```

- [X] Checked

O comando "git push origin main" está dizendo que queremos enviar todos pacotes de commit que organizamos para o remoto "origin" e para o branch "main". O git é um sistema de controle de versão distribuído, então na prática podemos ter diversos "remotes". O uso de origin é uma convenção. 

Antes de iniciar o seu trabalho é sempre importante verificar se você está com tudo o que precisa no seu repositório. Para isso você pode usar o git pull: 

```
$ git pull origin main
``` 

Esse seria um ciclo simples de baixar um repositório, modificar um arquivo, e subir ele novamente para a origem. 

-- Daniel Wildt