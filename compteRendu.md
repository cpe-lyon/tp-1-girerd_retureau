
# Compte-Rendu TP1
 
&nbsp;

 ## Auteurs et date
 *Thomas GIRERD*
 
 *Guillaume RETUREAU*
 
*Date : 06.02.20*

&nbsp;

***

&nbsp;

## Exercices

### Exercice 1
Mise en place du l'environnement.

&nbsp;

***

&nbsp;

### Exercice 2
#### Manuel
**1. A l’aide du manuel, identifiez le rôle de la commande which**

*La commande which donne le chemin d'accès de l'exécutable associé à la commande donnée en argument.*

&nbsp;

**2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher le terme option dans la page de manuel de which ?**

*Pour rechercher un terme, une fois sur la page du manuel, il suffit de taper :*

``
/termeRecherche
``

&nbsp;


**3. Comment quitte-t-on le manuel ?**

*Pour quitter le manuel, il suffit d'appuyer sur la touche 'q'.*

&nbsp;


**4. Chaque section du manuel a une première page, qui présente le contenu de la section. Aﬀicher la première page de la section 6; de quoi parle cette section ?**

``
man 6 intro
``

*Cette section décrit les jeux présents sur le système.*

&nbsp;

***
&nbsp;


#### Navigation dans l'arborescence des fichiers
**1. allez dans le dossier /var/log**

``
cd /var/log
``

&nbsp;


**2. remontez dans le dossier parent (/var) en utilisant un chemin relatif**

``
cd ..
``

&nbsp;


**3. retournez dans le dossier  personnel**

``
cd
``

&nbsp;


**4. revenez au dossier précédent (/var)sans utiliser de chemin**

``
cd -
``

&nbsp;


**5. essayez d’accéder au dossier /root; que se passe-t-il ?**

``
-bash: cd: /root: Permission non accordée
``

*L'accès au dossier /root est réservé au superuser et on ne peut donc pas y accéder sans ses permissions.*

&nbsp;


**6. essayez la commande sudo cd /root; que se passe-t-il ? Expliquez**

``
sudo: cd: command not found
``

*Certains dossiers n'autorisent l'accès qu'au superuser. Ainsi, même avec le sudo, ce n'est pas possible. Il faut **ÊTRE** le superuser pour y rentrer. Pour ce faire, on peut simplement utiliser la commande :*

 ``
sudo su -
``

&nbsp;


**7. à partir de votre dossier personnel, créez l’arborescence suivante :**

![tree view](https://github.com/cpe-lyon/tp-1-girerd_retureau/blob/master/arborescence.png)

```
mkdir Dossier1
mkdir Dossier2
mkdir Dossier2/Dossier2.1
mkdir Dossier2/Dossier2.2
echo '' > Dossier1/Fichier1
echo '' > Dossier2/Dossier2.2/Fichier2
echo '' > Dossier2/Dossier2.2/Fichier3
```

&nbsp;


**8. revenez dans votre dossier personnel; à l’aide de la commande rm, essayez de supprimer Fichier1, puisDossier1; que se passe-t-il ?**

``
rm Dossier1/Fichier1
``

*Le fichier est supprimé.*

``
rm Dossier1
``

*On obtient alors l'erreur suivante :*

``
rm: impossible de supprimer 'Dossier1': est un dossier
``

&nbsp;


**9. quelle commande permet de supprimer un dossier?**

``
rm -d Dossier1
``

*On peut utiliser cette commande pour supprimer un dossier **vide**.*

&nbsp;


**10. que se passe-t-il quand on applique cette commande à Dossier2 ?**

``
rm: impossible de supprimer 'Dossier2': Le dossier n'est pas vide
``

&nbsp;


**11. comment supprimer en une seule commande Dossier2 et son contenu**

*Il faut utiliser la commande de suppression récursive:*

``
rm -r Dossier2
``

&nbsp;


***

&nbsp;


#### Commandes importantes

**1. Quelle commande permet d’aﬀicher l’heure? A quoi sert la commande time ?**

*Pour afficher l'heure, on utilise la commande suivante :*

``
date
``

*La commande ``time`` suivi d'une autre commande et de ses arguments permet d'obtenir trois informations :*
- *le temps réel écoulé entre le début et la fin de l'exécution de la commande*
- *le temps CPU*
- *le temps CPU système*

&nbsp;


**2. Dans votre dossier personnel, tapez successivement les commandes ls puis la; que peut-on en déduire sur les fichiers commençant par un point ?**

*Les fichiers commençant par un point ne sont pas affichés avec un ``ls`` classique. Pour les afficher, il faut faire ``ls -a`` (ou la qui est un alias de cette commande).*

&nbsp;


**3. Où se situe le programme ls ?**

*On utilise la commande suivante :*

``
which ls
``

On obtient ainsi le chemin d'accès du programme ``ls`` :

``
ls: /urs/bin/ls
`` 

&nbsp;

**4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande.**

``ll`` *affiche de nombreuses informations sur les fichiers et dossiers contenus dans le répertoire courant :*
 * *la taille totale de son contenu*
 * *une ligne pour chaque fichier/dossier avec :*
   - *le premier caractère désignant le type*
   - *les 9 caractères suivant montrant les permissions pour l'utilisateur, le groupe et d'autres*
   - *le nombre de liens physiques vers ce fichier/dossier*
   - *le nom du propriétaire et son groupe*
   - *sa taille en octets*
   - *la date de modification*
   - *le nom complet (pour les liens, montre aussi la cible du lien)*

*Exemple :*

``rw------- 1 herysia herysia    5 févr.  6 10:25 .bash_history``

&nbsp;


**5. Quelle commande permet d’aﬀicher les fichiers contenus dans le dossier/bin ?**

``
ls /bin
``

&nbsp;


**6. Que fait la commande ls .. ?**

*La commande ``ls ..`` affiche le contenu du dossier parent au répertoire courant.*

&nbsp;

**7. Quelle commande donne le chemin complet du dossier courant ?**

*C'est la fonction ``pwd`` qui donne le chemin complet du dossier courant.*

&nbsp;

**8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?**

*La commande ``echo 'yo' > plop`` écrit 'yo' dans un fichier nommé plop en écrasant son contenu (si ce dernier n'existe pas, il le crée). L'exécuter une deuxième fois écrase le premier fichier et le recrée à l'identique.*

&nbsp;

**9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?**

*La commande ``echo 'yo' >> plop`` écrit 'yo' dans un fichier nommé plop en écrivant à la suite de son contenu (si ce dernier n'existe pas, il le crée). L'exécuter une deuxième fois écrira 'yo' une deuxième fois.*

&nbsp;

**10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents.**

*La commande ``file`` décrit le type d'un fichier ainsi que son encodage.*

&nbsp;

**11. Créez un fichier toto qui contient la chaîne Hello Toto !; créer ensuite un lien titi vers ce fichier avec la commande ln toto titi. Modifiez à présent le contenu de toto et aﬀichez le contenu de titi: qu’observe-t-on ? Supprimez le fichier toto; quelle conséquence cela a-t-il sur titi ?**

*On observe que le contenu de titi est le même que celui de toto. Après modification de toto, on remarque que titi a été modifié aussi. En revanche, si on supprime toto, titi est toujours présent et contient toujours les données qui étaient contenues dans toto.*

&nbsp;

**12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le contenu de titi; quelle conséquence pour tutu? Et inversement? Supprimez le fichier titi; quelle conséquence cela a-t-il sur tutu?**

*tutu a le même contenu que titi, les modifications d'un fichier affecte l'autre. Supprimer titi a pour conséquence de rendre invalide le lien symbolique tutu (il devient inutilisable).*

&nbsp;

**13. Aﬀichez à l’écran le fichier/var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran?**

*On peut afficher le fichier complet avec la commande less /var/log/syslog.*

*On peut naviguer dans le fichier avec les flèches directionnelles.*

*On peut sortir avec la touche q.*

&nbsp;

**14. Aﬀichez les 5 premières lignes du fichier/var/log/syslog, puis les 15 dernières, puis seulement les lignes 10 à 20.**

```
head -5 /var/log/syslog
tail -15 /var/log/syslog
head -20 /var/log/syslog | tail -$(20-10)
```

&nbsp;

**15. Que fait la commande dmesg | less ?**

*``dmesg`` affiche des informations sur le kernel.*

*``dmesg | less`` affiche toutes les informations et permet de naviguer dans ces dernières (c'est l'effet de ``less `` sur le retour de ``dmesg``)*

&nbsp;

**16. Aﬀichez à l’écran le fichier/etc/passwd; que contient-il ? Quelle commande permet d’aﬀicher la page de manuel de ce fichier ?**

*Il contient la liste des utilisateurs, ainsi que des informations sur ces derniers.*

&nbsp;

**17. Aﬀichez seulement la première colonne triée par ordre alphabétique inverse**

``cut -d: -f1 /etc/passwd | sort -dr``

*``cut récupère`` le premier élément (``-f1``) de chaque ligne, séparés par ``: (-d:)``.*

*``sort -dr`` trie par ordre l’alphabétique inversé.*

&nbsp;

**18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement les utilisateurs connectés) ?**

``wc -l /etc/passwd | cut -d\  -f1``

*``wc -l /etc/passwd`` récupère le nombre de lignes du fichier, avec son nom.*

*``cut -d\  -f1``	extrait le nombre de lignes uniquement.*

&nbsp;

**19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?**

``man -k conversion | wc -l``

*Quatre pages du manuel contiennent le mot clé conversion dans leur description.*

&nbsp;

**20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine**

``sudo find / -name "passwd" | wc -l``

*Il y a 7 fichiers appelés **passwd**.*

*Note: on utilise ``sudo`` pour pouvoir chercher dans les dossier protégés.*

&nbsp;

**21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial/dev/null**

``find / -name "passwd" > ~/list_passwd_files.txt 2>/dev/null``

*``2>/dev/null`` redirige les erreurs vers le fichier ``/dev/null``.*

&nbsp;

**22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment**

``grep -e 'ls -alF' -d recurse``

*Retour obtenu :*

``.bashrc:alias ll='ls -alF'``

*L'alias ll est présent dans le fichier .bashrc.*

&nbsp;

**23. Utilisez la commande locate pour trouver le fichier history.log.**

``locate history.log``

*Retour obtenu :*

``/var/log/apt/history.log``

*Note: la commande n'est pas installée par défault, on utilise donc sudo apt install mlocate pour l'installer*

&nbsp;

**24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?**

*Il n'est pas trouvé car ``locate`` ne scan pas tous les fichiers, mais les fichiers référencés dans une base de données. Cette base étant mise à jour tous les jours à 7h30 (ou 5 minutes après le démarrage de la machine si elle n'était pas allumée à cette heure), le fichié créé n'est donc pas présent dans cette dernière.*

&nbsp;

***

&nbsp;

### Exercice 3. Découverte de l’éditeur de texte nano

**1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec nano.**

*Depuis le répertoire personnel :*

```
cp /var/log/syslog ./log.txt
nano log.txt
```

&nbsp;

**2. Remplacez toutes les occurrences du mot kernel par le mot noyau.**

*Pour activer le mode remplacement, on appuie sur ``ALT+M``.*

*On choisit le terme à remplacer : ``kernel``.*

*On choisit ensuite le terme par lequel on le remplace : ``noyau``.*

*La première occurence trouvée est affichée, on appuie sur la touche ``T`` pour remplacer toutes les occurences.*

*On sauvegarde avec ``CTRL+S``.*

&nbsp;

**3. Déplacer les 10 premières lignes à la fin du fichier.**

*On place le curseur au début du fichier (par défault).*

*On passe en mode sélection en appuyant sur ``ALT+M``.*

*On sélectionne les 10 premières lignes en appuyant 10 fois sur la flèche du bas.*

*On coupe le texte en appuyant sur la touche ``CTRL+K``.*

*On navigue jusqu'à la fin du fichier en appuyant sur ``CTRL+/`` puis ``CTRL+V``.*

*On appuye sur ``CTRL+U`` pour coller.*

*Et enfin ``CTRL+S`` pour sauvegarder.*

&nbsp;

**4. Annulez cette action5. Enregistrez le fichier avant de quitter nano.**

*On annule l'action précédente en appuyant deux fois sur ``ALT+U`` (une fois pour annuler le coller, une autre pour le copier).*

&nbsp;

***

&nbsp;

### Exercice 4. Personnalisation du shell

**1. Commencez par créer une copie de ce fichier, que vous appellerez.bashrc_bak**

``cp .bashrc .bashrc_backup``

&nbsp;

**2. Editez le fichier.bashrcavecnanoet décommentez la ligneforce_color_prompt=yes pour activerla couleur. Enregistrez le fichier et quittez nano.**

``nano .bashrc``

*On trouve la ligne avec ``ctrl+w``, ``force_color_prompt`` puis ``Enter``.*

*On supprime le ``#`` puis on sauvegarde et quitte avec ``CTRL+X``.*

&nbsp;

**3. Le fichier.bashrc est lu au démarrage du shell; pour le recharger, il faudrait donc se déconnecter puis se reconnecter; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite de commande devrait immédiatement passer en couleurs.**

*Fait.*

&nbsp;

**4. Modifiez l’invite de commande pour qu’elle s’affiche sous la forme suivante :**

![colored syntax](https://github.com/cpe-lyon/tp-1-girerd_retureau/blob/master/exempleCouleur.png)

**où l’heure est affichée en violet et entre crochets, et le chemin du dossier courant en cyan**

``nano .bashrc``

``ctrl+W``, ``alt+C`` (pour respecter la casse), avec PS1+ en paramètres

*On a :* 

```if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```
	
*On remplace par :* 

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\e[95m[\t]\e[0m - \[\033[01;32m\]\u@\h\[\033[00m\]:\e[36m\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
```

![colored syntax](https://github.com/cpe-lyon/tp-1-girerd_retureau/blob/master/resultatCouleur.png)
