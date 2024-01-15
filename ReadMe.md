# Git 
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
