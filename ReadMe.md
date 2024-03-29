# Jour 1: 
Read.md (Markdown) obligatoire (Markdown.org si question)
Obsidian pour organiser les notes

**Git**

:
Permet de revenir à une version antérieure.
Comparer les changements.
Déterminé qui a fait une modification.
De travailler en même temps que les autres sur des choses différentes sans perturber leurs travails.

**Importance du Versionning**:

Traçabilité
Collaboration
Backup et Rétablissement
Branching et Merging

**Nomenclature de Versoning**

Majeur
Mineur
Correctif
Exemple : 2.3.1
2= majeur
3= mineur
1= correctif

**Aperçu des Systèmes de Versoning**:

SVN est Centralisé donc il faut être connecter au réseau

**Opration et fonctionnalités**

Chekout/Update/commit :Commit sauvegarder une version du logiciel localement

Branching et Merging : se qui permet de travailler à plusieurs

Atomic Commit :on en reparle plus tard

**Git**:

crée en 2005 par Linus Torvalds il a aussi créé le noyau Linux 

Serveur a système distribuer fort plus il y a de monde 
Serveur a système centraliser faible plus il y a du monde

**Opération et Fonctionnalités**:

Branching et Merging :
Staging Area :
Flexibilité :


**La principale différence entre Git et d’autre SCMs, réside dans la façon dont Git considère les données**.

Alors que Git considère les données comme un ensemble de snapshot d’un mini système de fichiers. Chaque fois que vous validez un changement, ou que vous enregistrez l’état de votre projet dans Git, il prend une photo de ce que tous vos fichiers ressemblent à ce moment-là et stocke une référence à cette copie instantanée. Pour être efficace, si les fichiers à nouveau, mais un lien vers le fichier identique précédemment stocké. Git considère ses données plus comme un ensemble de mini-système de fichiers

**Avec Git la quasi-totalité des opérations sont locales**

Git se charge de gérer l’intégrité des données
Avant la plupart des opérations effectuées avec Git, Git effectue une « somme de contrôle », et obtient une signature unique qui sert de référence. On peut ainsi vérifier l’intégralité des données. Cela signifie qu’il est impossible de modifier le contenue d’un fichier sans que Git ne le sache pas.

Le mécanisme utilise par Git est appelé un empreint SHA-1. Une chaine de caractères composés de 40 caractères hexadécimaux qui ressemble à cela
```24b9da6552252987aa493b52f8696cd6d3b00373``` 

Avec Git très peu d’opérations sont destructives

Git à trois états principaux dans lesquels peuvent se trouver vos fichiers

#### La première utilisation de Git

Git posssède un outil appelé Git config qui permet de configuer les paramètres de Git sur votre système. ces paramètres peuvent être stockes dans trois endroits diffétens:

- Fichier ~/.gitconfig : Spécifique à votre utilisateur. Vous pouvez forcer Git à lire et écrire dans ce fichier en passant l'option --global.

- Fichier config dans le répertoire Git d'un dépôt en cours d'utilisation (c'est à dire .git/config):
Specifique au seul dépot. Chaque niveau surcharge les valreus du niveau précédent, donc les valeurs dans git/config écrasent celles de /etc/gitconfig.

Sur les OS windows, Git recherche le fichier ```Gitconfig```
dans le répertoire $HOME

Pour en savoir plus entrez la commande :

```sh
git config --list --show-origin
```

#### Configurer votre identité

La première chose que vous devriez faire lorsque vous intallez Git est de définir votre nom d'utilisateur et votre adresse e-mail. Ceci est important car chaque validation dans Git utilise cette information, et elle est imuablement attachée aux commit que vous validez :

```sh
$ git config --global user.name "John Doe"
$ git config --global user.email mon@email.com
```
#### Votre éditeur de texte

Vim 
mode insersion = ```i``` 

pour quitter et sauvegarder =```:wq```

quitter sans sauvegarder =```:q!```

```git config --global core.editor emacs```

Sur windows obligé de spécifier le chemin complet de l'éditeur de texte.

Voici un exemple : 

```sh
git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe'
-multiInst -notabbar -nosession -noPlugin"
```

#### Le nom de branche par défaut

```sh
git config --global init.defaultBranch main
```

#### Vérifier vos paramètres

```sh
git config --list

git config user.name
```

#### Obtenir de l'aide

```sh
githelp <commande>
man git <commande>
git <commande> --help
```

#### Les bases de Git

```sh
git init
```
#### TP SSHkey

```sh
ssh-keygen -t ed25519 -C "yohann.mathieux@ecole-isitech.fr"
```

mettre la clé public sur github

```sh
git push -u origin main
```
-u à utiliser que la première fois

Pour supprimer le remote 
```sh
git remote rm origin
```

Pour les push suivant il suffira d'écrire la commande 
```sh
git push
```

Pour cloner 

```sh
git clone "URL"
```

#### Ignorer des fichiers

Pour ignorer des fichiers il suffit de créer un fichier .gitignore et d'y ajouter les fichiers et les dossiers 

#### Valider des modifications 

```sh
git commit -m "message"
```

#### Effacer des fichiers

```sh
rm

git status

git rm <fichier>
```

cette dernière commande vas indexer le fichier pour qu'il soit supprimé lors du prochain commit.

Il existe une autre forme de suppression de fichier qui consiste à utiliser la commande suivante

```sh
git rm --cached <fichier>
```

cette commande va supprimer le fichier de l'index mais pas du disque dur.

#### Visualiser l'historique

```sh
git log
```

#### Désindexer des éléments déjà commits

TP à faire

```sh
git remote show origin
```

#### Création de tags

En plus d'identifier les commits par des identifiants unique, Git vous permet aussi d'étiqueter un certain état de l'historique (commit) comme étant important. Cela peut être utile pour marquer des versions de votre code source.

```sh
git tag -a V1.0 -m "Version 1.0"
```

On peut lister les tags avec la commande suivante :

```sh
git tag
```

on peut aussi filtrer

```sh
git tag -l ""
```

Pour visualiser une étiquette, on utilise la commande suivante :

```sh
git show V1.4
```


# Jour 2:

#### Les branches

Pour créer une branche il suffit de faire la commande :

```sh
git branch <nom-de-branche>
```
git branch créer une nouvelle branche mais ne vous fait pas basculer dessus.


Pour afficher les branches on peut faire la commande :

```sh
git log --oneline --decorate --graph --all
```

Pour créer une branche et directement basculer dessus on peut faire la commande 

```sh
git checkout -b <nom-de-branche>
```

#### Fusionner des branches

```sh
git checkout -b iss53
```

On va commencer à travailler sur l'issue 53 et effectuer un premier commit:

```sh
git commit -m "commit 3"
```

On va ensuite rebasculer sur la branche master afin d'effectuer un hotfix:

```sh
git checkout master
```

```sh
git branch hotfix
git commit -m "commit 4"
```
Nous sommes satisfait du hotfix et nous allons le valider:

```sh
git checkout master
git merge hotfix
```

La branche hotfix n'a plus lieu d'être et nous allons la supprimer

```sh
git branch iss53
```

On effectue un nouveau commit afin de valider notre travail

```sh
git commit -m "commit 5"
```
![alt text](Img6.jpg)

On vas maintenant retourner sur master et effectuer un merge avec iss53

```sh
git checkout master

git merge iss53
```

La stratégie de merge est alors différente de celle utilisée précédemment: Merge commit

Au lieu d'avancer la branche master, Git crée un nouveau commit qui contien les différences entre les deux branches.

![alt text](Img7.jpg)

On peut supprimer la branche iss53:

```sh
git branch -d iss53
```

#### Résoudre des conflits

Un conflit a lieu lorsque deux branches différentes ont modifiées la même partie du même fichier, ou si un fichier a été supprimé dans un branche alors qu'il a été madifié dans une autre.

![Alt text](Img8.jpg)

Physiquement, un conflit est reporésenté paar des caratères spéciaux qui apparaissent dans le fichier.

![Alt text](Img9.jpg)

Après résolution du conflit il suffit de commit.

Vous avez un outil qui permet de résoudre les conflits avec git :

```sh
git mergetool
```

# Jour 3 :

#### Suite conflit

Afficher toutes les chranches :

```sh
git branch -a
git branch --all
```

Parlons un peu de la commande `git fetch` : elle permet de synchroniser vos travaux, elle va rechercher le serveur qui heberge <distant> et va récupérer les modifications qui ont été effectuées sur le serveur distant.

#### Pousser des modifications

```sh
git push <distant> <branche>

git push origin master

git push -u origin master
```

Pour récupérer les modifications effectuées sur le serveur distant à propos de nouvelles branches ou de branches existantes :

```sh
git fetch <distant>
```

Pour récupérer des modifications et les fusionner avec vos branches locales :

```sh
git pull <distant> <branche>
```

La règle d'or lorsqu'on debute avec Git:

`commit` -> `pull` -> `push`

Lorsque vous récupérer des branches distantes avec la commande fetch, vous ne créez pas atuomatiquement une branche locale qui suit la branche distante. vous devez créer une branche locale et la lier à la branche distante.

```sh
git checkout -b <nom-de-branche> <distant>/<nom-de-branche>
```

On a un raccourci pour cette commande : 

```sh
git checkout --track <distant>/<nom-de-commande>
```

Encore plus court, si la branche locale n'éxiste pas encore : 

```sh
git checkout <nom-de-branche>
```

Afin de visualiser tout ça on peut utiliser la commande suivante :

```sh
git fetch --all

git branch -vv
```

Analysons un peu la commande suivante :

```sh
git push origin --delete une-branche
```

#### Rebaser votre travail

Avec git il y a daux manières d'intégrer les modifications d'un branche dans une autre : 
-La fusion (merge)
-le rebasage (rebase)

![Alt text](Img10.jpg)

Après un merge on obtient cela :

```sh
git checkout master

git merge experiment
```

![Alt text](Img11.jpg)

Avec le rebase on aurait entré les commandes suivantes :

```sh
git checkout experiment

git rebase master
```

Et voici le résultat :

![Alt text](Img12.jpg)

et maintenant le résusltat final :

![Alt text](Img13.jpg)

la commande rebase surprime une partie de l'historique de la branche sélectionné donc elle est dangeureuse.

