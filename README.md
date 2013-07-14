Dive Into Python 3
==================

Projet de traduction fr
-----------------------

TODO: expliquer le projet, à quelle heure on mange, pourquoi les escargots n'ont pas de dents…

Comment participer ?
--------------------

Pour discuter, on a une mailing-list : plongez-dans-python-3@framalistes.org. Inscrivez-vous sur [http://www.framalistes.org/sympa/subscribe/plongez-dans-python-3](http://www.framalistes.org/sympa/subscribe/plongez-dans-python-3).

Ensuite, il faut nous envoyer un petit mail sur cette liste en nous donnant votre pseudo github, qu'on vous ajoute au groupe qui a les droits sur ce dépôt, histoire de pouvoir bosser.

La façon de travailler est assez simple, mais il est primordial de s'y tenir, sinon ça va être le gros bazar.
1. Passer le statut à "En cours" dans l'en-tête du fichier que vous allez traduire, dans la branche master.
2. Pousser cette modification (ou la refaire) dans la branche gh-pages.
3. Créer, à partir de la branche master, une nouvelle branche portant le nom du fichier à traduire.
4. Traduire.
5. Passer le statut du fichier à "Relecture" dans la branche du fichier, la branche master et la branche gh-pages
6. Faire une pull-request pour pousser la branche du fichier dans la branche master
7. Relecture par les autres membres de l'équipe, quand ils sont ok pour pousser, ils mettent un :1 dans les commentaires de la pull-request
8. Quand on a 4 ou 5 :1 dans les commentaires, le coordinateur (ldidry) pousse dans master, update le statut à "Publié" dans les branches master et gh-pages.
9. goto 1

GIT : petit guide à l'usage du débutant
---------------------------------------

Git est un système de gestion de versions décentralisé [DVCS](https://en.wikipedia.org/wiki/Distributed_revision_control). Voilà pour les gros mots. Passons maintenant à quelque chose de compréhensible pour l'humain courant.

### Git : kesako ?

Git permet de gérer des versions de fichiers. Grâce à Git, on sait qui a fait quoi et à quel moment. Le savoir c'est bien, mais en faire quelque chose c'est mieux. Grâce à cette faculté de versionning, il est ainsi possible de voyager dans le temps : essayer de nouvelles choses, revenir en arrière... Moultes possibilités à découvrir.

### Je n'y connais rien. Que fais je ?

Eh bien vous apprenez. Pas de panique : inutile d'avoir fait Polytechnique. La courbe d'apprentissage des commandes de base est très rapide.

#### Installation

Pour utiliser Git, il vous faut tout d'abord [l'installer sur votre poste](http://git-scm.com/book/fr/D%C3%A9marrage-rapide-Installation-de-Git). L'installation est très simple et surtout, Git est disponible sur de nombreux systèmes, même si vous n'utilisez pas un système libre (tant pis pour vous). 

Cette installation ne concerne que le moteur. Vous n'aurez besoin de rien d'autre mais vous pouvez aussi faire le choix d'y ajouter une interface graphique. Le présent guide vous donnera les bases de l'utilisation en ligne de commande (donc sans interface graphique).

#### Principes de fonctionnement

Les principes sont assez simples :
  * Créer un nouveau dépôt ou copier un dépôt existant. En langage Git, copier s'appelle cloner.
    
    Dans les deux cas, cela revient au même : vous disposez localement d'un dépôt sur lequel vous allez pouvoir travailler.
    
  * Travailler sur votre dépôt.
  * Versionner vos modifications -> Créer un commit. 
  
    Une fois satisfait de votre modification ou de votre ajout, vous pouvez versionner vos modifications. En langage Git, on parle de commit. Ce commit crée une nouvelle version du fichier. S'il s'agit d'un nouveau fichier, ce sera la première version.

  * Publier vos modifications.
  
    Vos commits sont dans votre dépôt local. Vous avez alors la possibilité de les publier vers le dépôt initial ou même vers un autre dépôt. En langage Git, on parle de push. Si vous ne disposez pas des droit de publication sur dépôt distant, vous pouvez aussi proposer vos modifications au responsable du dépôt. En langage Git on parle de pull request.
    
En résumé, vous créez un dépôt local, vous travaillez, vous committez et vous publiez. Facile, non ?

#### Du rêve à la réalité

Concrètement, voici ce que ça donne pour ce projet. Commençons pas cloner joyeusement le projet. Dans votre dossier personnel, placez vous à l'endroit où vous souhaitez créer votre dépôt local puis exécutez la commande de clonage

```bash
git clone https://github.com/framasoft/plongez-dans-python3.git
```

Vous devriez obtenir le résultat suivant. Vous remarquerez que cette opération crée automatiquement un dossier dans lequel figurera votre dépôt :
    
```bash
Cloning into 'plongez-dans-python3'...
remote: Counting objects: 5482, done.
remote: Compressing objects: 100% (3893/3893), done.
remote: Total 5482 (delta 1587), reused 5471 (delta 1579)
Receiving objects: 100% (5482/5482), 25.51 MiB | 1.92 MiB/s, done.
Resolving deltas: 100% (1587/1587), done.
```

Faites une modification. Vous pouvez obtenir à tout moment le statut de votre dépôt :

```bash
Blake:plongez-dans-python3 gcoulais$ git status
# On branch master
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	README.md
nothing added to commit but untracked files present (use "git add" to track)
```

Ici un fichier README.md a été ajouté mais n'a pas encore été committé. Git le voit et vous informe qu'il existe mais ne le suit. Vous pouvez obtenir d'autres types de réponses de statut pour les fichiers déjà suivis et ayant fait l'objet d'une modification

```bash
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
```
    
Ajoutons maintenant le fichier au suivi de version et committons. L'opération se déroule donc en deux fois : add puis commit. Un commit est toujours accompagné d'un message expliquant ce que vous avez fait.

```bash
Blake:plongez-dans-python3 gcoulais$ git add README.md 
Blake:plongez-dans-python3 gcoulais$ git commit -m "Ajout du README.md" 
[master 2c53431] Ajout du README.md
 1 file changed, 80 insertions(+)
 create mode 100644 README.md
```

Il ne reste plus qu'à publier la modification sur le dépôt distant :

```bash
Blake:plongez-dans-python3 gcoulais$ git push origin master
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 2.14 KiB, done.
Total 3 (delta 1), reused 0 (delta 0)
To https://github.com/framasoft/plongez-dans-python3.git
   67ef8e6..2c53431  master -> master
```

#### C'est bien joli, mais je ne suis pas tout seul

Effectivement, d'autres que vous travaillent sur cette traduction. Il faut donc que vous puissiez récupérer leurs modifications. Encore une fois, c'est un jeu d'enfant. Placez vous simplement dans votre dépôt et magie :

```bash
Blake:plongez-dans-python3 gcoulais$ git pull origin master
From https://github.com/framasoft/plongez-dans-python3
 * branch            master     -> FETCH_HEAD
Already up-to-date.
```

Ici ce n'est pas très parlant : le dépôt local était déjà à jour. Mais c'est bien là que vous verrez apparaître toutes les modifications de vos petits camarades. Attention, si vous avez des modifications en cours, Git refusera de faire l'opération de pull. Il suffit de mettre de côté vos modifications, de récupérer la dernière version du dépôt distant puis d'y appliquer vos modifications en cours. En langage git, ça donne ça :

```bash
Blake:plongez-dans-python3 gcoulais$ git stash
Saved working directory and index state WIP on master: 7583460 README : coloration syntaxique pour les blocs de code
HEAD is now at 7583460 README : coloration syntaxique pour les blocs de code
```

puis 

```bash
Blake:plongez-dans-python3 gcoulais$ git pull origin master
```

et enfin 

```bash
Blake:plongez-dans-python3 gcoulais$ git stash apply
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   README.md
#
no changes added to commit (use "git add" and/or "git commit -a")
```

#### Origin master : c'est quoi cette bouteille de lait ?

#### À propos des branches

TODO: expliquer brièvement les branches.
TODO: expliquer brièvement les remote. Pourquoi origin master


