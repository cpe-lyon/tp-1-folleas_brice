
# Compte Rendu TP1 - Admin Linux

## Exercice 1 - Installation du serveur

Installation de la VM

## Exercice 2 - Prise en main de l'interpreteur de commande
### Manuel 
1. D'après le manuel, la commande `which` permet de localiser une commande.
2. On peut utiliser la command `/pattern` en remplaçant 'patern' avec le terme souhaité pour avoir la n ième itération du terme en question.
3. Pour quitter le manuel, on utilise la commande `q`
4. La section 'MISCELLANEOUS COMMANDS' présente une liste de commandes divers qui peuvent être utiles. On peut prendre l'exemple de `whoami` qui permet d'afficher sur la console le nom de l'utilisateur courant.  

### Navigation dans l'arborescence des fichiers
1. `cd /var/log`
2. `cd ..`
3. `cd ~`
4. `cd -`
5. `cd /root`
' Permission non accordée'
6. `sudo cd /root` permet de lancer la commande en tant qu'administrateur et donc d'avoir les droits relatifs à l'éxécution de la commande. Pour cela, je dois rentrer mon mot de passe utilisateur.
7. On utilise les commandes `mkdir`pour créer un répertoire et `touch` pour créer un fichier vide (et intialement de modifier le timestamp de dernier accès et de dernière modification de ce fichier, si ce dernier existe).
8. La commande `rm Dossier1/Fichier1` n'est pas valide car `rm`est une commande qui permet de supprimer un fihcier et non un dossier.
9. Pour cela on utilise la commande `rmdir` ou `rm -d`
10. La commande ne peut pas être effectuée sur Dossier2 car ce dernier n'est pas vide.
11. Pour cela il faut utiliser la commande `rm -r`. L'option `-r` ici utilisée permet de faire un 'remove' récursif et donc de suprimé les fichiers du dossier parent.

### Commandes importantes
1. En utilisant la commande `date` on peut afficher l'heure ainsi que la date système.
2. La commande `ls -la` permet d'afficher le contenu d'un dossier, l'option `-a` permet d'afficher également les fichiers cachés et l'option `-l` permet elle, d'afficher plus de détails relatifs au fichiers (permissions d'accès, le nombre de liens physiques, le nom du propriétaire et du groupe,etc...).
3. La commande `ls` étant une commande de base linux, elle se trouve dans le répertoire /bin.
4. La commande `ll` n'existe pas en tant qu'entrée manuelle. Cette commande est en réalité un alias de la commande `ls -alF` qui permet d'afficher la liste des fichiers, avec des details relatifs à ces derniers (`-l`), d'afficher tous les fihciers y compris les fichiers cachés (`-a`), et de les trier par type (`-F`).
5. Pour cela, il faut utiliser la commande `ls /bin`.
6. Comme dit précédemment, la commande `ls` permet d'afficher le contenu d'un dossier.
7. Il s'agit de la commande `pwd` pour 'Print Working Directory'.
8. La commande `echo 'yo' > plop` permet de rediriger la sortie standard vers le fichier 'plop' et donc d'écrire dans ce dernier le contenu de echo c'st à dire : `yo`.
9. La commande `echo 'yo' >> plop` permet de 
10. La commande `file` permet de déterminer le type du fichier donné en argument. 

    - $ file image.png
    image.png: PNG image, 60 x 46, 8-bit/color RGBA, non-interlaced

    - $ file plop
    plop: ASCII text

11. 
`echo 'Hello Toto !' > toto`
`ln toto titi`
`echo 'Goodbye Toto !' > toto`
`cat titi`

On peut voir que le contenu de titi a également changé mais une fois que toto est supprimé le contenu de titi restera inchangé
12. 
`echo 'Hello Titi !' > titi`
`ln -s titi tutu`
`echo 'Goodbye Tutu !' > tutu`
`cat titi`
On peut voir que le contenu de titi a changé
`echo 'Hello Test' > titi`
`cat tutu`
On peut voir que le contenu de tutu a changé
`rm titi`
Si titi est supprimé il est impossible de lire le contenu de tutu


13. Pour afficher le contenu de /var/log/syslog il suffit d'utiliser la commande `cat /var/log/syslog`, pour interrompre le processus il faut utiliser `Ctrl + c`
14.  Pour afficher les 5 premières
* `head -n 5 /var/log/syslog`
Pour afficher les 15 dernières
* `tail -n 15 /var/log/syslog`
Pour afficher entre les lignes 10 et 20
* `head -n 20 | tail -n 10 var/log/syslog`
15. La commande `dmseg | less` permet d'afficher la mémoire tampon de message du noyau (`dmseg`) par partie/pages et de rechercher une chaine de caractère dans le message affiché (`less`).
16. La commande `cat /etc/passwd` permet d'afficher le contenu de `/etc/passwd` c'est à dire les attributs des différents comptes utilisateurs du système (nom d'utilisateur, informations pour valider le mot de passe, identifiant utilisateur, identifiant du groupe, etc...).
17. Pour trier la première colonne par ordre alphabétique inverse il faut saisir :
`cut -d: -f1 /etc/passwd | sort +1`.
18. Pour afficher le nombre d'utilisateurs de la machine il s'uffit d'utiliser : `getent passwd | grep -c bash$`
19. Il faut saisir la commande suivante : `apropos conversion man | wc -l`
20. Il faut saisir la commande suivante : `sudo find / -name passwd`
21. On modifi donc la commande comme suit : `find / -name passwd 2> /dev/null > ~/list_passwd_files.txt`
22. `grep -rl "alias ll='ls -alF'" / 2> /dev/null`
23. `locate history.log`
24. Le fichier n'apparait pas car la table qu'utilise la commande locate n'a pas été mise à jour.

## Exercice 3 - Découverte de l’éditeur de texte nano

1. La commande pour copier le fichier /var/log/syslog dans le dossier personnel sous le nom log.txt et de l'ouvrir avec nano est :
`cp /var/log/syslog ~/log.txt && nano ~/log.txt`

2. Pour remplacer toutes les occurences il faut saisir les commandes suivante :
`nano ~/log.txt`
`ALT+R`
Écrire le mot à remplacer.
Écrire le mot de remplacement.
Saisir T pour remplacer toutes les occurences.

3. Pour déplacer les 10 premières lignes à) la fin du fichier il faut :
Ouvrir l'édition du fichier avec `nano ~/log.txt`.
Commencer la selection du bloc avec `Ctrl+Shift+6`.
Descendre 10 lignes avec ↓.
Couper avec `Ctrl + k`.
Aller à la fin du fichier avec `Ctrl + ↓`.
Coller avec `Ctrl + u` pour coller.

4.  Effectuer 2 fois `Ctrl + u` pour annuler le copier/coller.

5.  Enregistrer le fichier avec `Ctrl + o` puis quitter nano avec `Ctrl + x`.

## Exercice 4 - Personnalisation du shell


1. Création de la copie du fichier `~/bashrc` : 
`cp ~/.bashrc ./bashrc_bak`

2. On édite donc ce fichier avec `nano ~/bashrc`.

La ligne `force_color_prompt=yes` une fois décommenté dans le fichier `~/.bashrc` permet d'afficher des couleurs dans le shell.

3. `source .baschrc`

4. La commande à saisir pour afficher l'invité de commande comme indiqué est : 
`\[\e[35\][\A] - \[\e[32\]\u@\h:\[\e[36m\]\w\[\033[00m\]`

## Exercice 5 - Pour les plus rapides
