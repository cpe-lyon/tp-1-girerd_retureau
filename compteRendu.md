
# Compte-Rendu TP1
 
 ## Auteurs et date
 *Thomas GIRERD*
 
 *Guillaume RETUREAU*
 
*Date : 06.02.20*

***

## Exercices

### Exercice 1
Mise en place du l'environnement.
***

### Exercice 2
#### Manuel
**1. A l’aide du manuel, identifiez le rôle de la commande which**

*La commande which donne le chemin d'accès de l'exécutable associé à la commande donnée en argument.*

**2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher le terme option dans la page de manuel de which ?**

*Pour rechercher un terme, une fois sur la page du manuel, il suffit de taper :*
``
/termeRecherche
``

**3. Comment quitte-t-on le manuel ?**

*Pour quitter le manuel, il suffit d'appuyer sur la touche 'q'.*

**4. Chaque section du manuel a une première page, qui présente le contenu de la section. Aﬀicher la première page de la section 6; de quoi parle cette section ?**
``
man 6 intro
``
*Cette section décrit les jeux présents sur le système.*
***
#### Navigation dans l'arborescence des fichiers
**1. allez dans le dossier /var/log**
``
cd /var/log
``
&NewLine;

**2. remontez dans le dossier parent (/var) en utilisant un chemin relatif**
``
cd ..
``
&NewLine;

**3. retournez dans le dossier  personnel**
``
cd
``
&NewLine;

**4. revenez au dossier précédent (/var)sans utiliser de chemin**
``
cd -
``
&NewLine;

**5. essayez d’accéder au dossier /root; que se passe-t-il ?**
``
-bash: cd: /root: Permission non accordée
``
*L'accès au dossier /root est réservé au superuser et on ne peut donc pas y accéder sans ses permissions.*
&NewLine;

**6. essayez la commande sudo cd /root; que se passe-t-il ? Expliquez**
``
sudo: cd: command not found
``
*Certains dossiers n'autorisent l'accès qu'au superuser. Ainsi, même avec le sudo, ce n'est pas possible. Il faut **ÊTRE** le superuser pour y rentrer. Pour ce faire, on peut simplement utiliser la commande :*
 ``
sudo su -
``
&NewLine;

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
&NewLine;

**8. revenez dans votre dossier personnel; à l’aide de la commande rm, essayez de supprimer Fichier1, puisDossier1; que se passe-t-il ?**
``
rm Dossier1/Fichier1
``
*Le fichier est supprimé.*
&NewLine;
``
rm Dossier1
``
*On obtient alors l'erreur suivante :*
``
rm: impossible de supprimer 'Dossier1': est un dossier
``
&NewLine;

**9. quelle commande permet de supprimer un dossier?**
``
rm -d Dossier1
``
*On peut utiliser cette commande pour supprimer un dossier **vide**.*
&NewLine;

**10. que se passe-t-il quand on applique cette commande à Dossier2 ?**
``
rm: impossible de supprimer 'Dossier2': Le dossier n'est pas vide
``
&NewLine;

**11. comment supprimer en une seule commande Dossier2 et son contenu**
*Il faut utiliser la commande de suppression récursive:*
``
rm -r Dossier2
``
&NewLine;
***
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

**2. Dans votre dossier personnel, tapez successivement les commandes ls puis la; que peut-on en déduire sur les fichiers commençant par un point ?**
*Les fichiers commençant par un point ne sont pas affichés avec un ``ls`` classique. Pour les afficher, il faut faire ``ls -a`` (ou la qui est un alias de cette commande).*

**3. Où se situe le programme ls ?**
*On utilise la commande suivante :*
``
which ls
``
On obtient ainsi le chemin d'accès du programme ``ls`` :
``
ls: /urs/bin/ls
`` 

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

**5. Quelle commande permet d’aﬀicher les fichiers contenus dans le dossier/bin ?**


**6. Que fait la commande ls .. ?**

**7. Quelle commande donne le chemin complet du dossier courant ?**

**8. Que fait la commande echo 'yo' > plop exécutée 2 fois ?**

**9. Que fait la commande echo 'yo' >> plop exécutée 2 fois ?**

**10. A quoi sert la commande file ? Essayez la sur des fichiers de types différents.**

**11. Créez un fichier toto qui contient la chaîne Hello Toto !; créer ensuite un lien titi vers ce fichier avec la commande ln toto titi. Modifiez à présent le contenu de toto et aﬀichez le contenu de titi: qu’observe-t-on ? Supprimez le fichier toto; quelle conséquence cela a-t-il sur titi ?**

**12. Créez à présent un lien symbolique tutu sur titi avec la commande ln -s titi tutu. Modifiez le contenu de titi; quelle conséquence pour tutu? Et inversement? Supprimez le fichier titi; quelle conséquence cela a-t-il surtutu?**

**13. Aﬀichez à l’écran le fichier/var/log/syslog. Quels raccourcis clavier permettent d’interrompre et reprendre le défilement à l’écran?**

**14. Aﬀichez les 5 premières lignes du fichier/var/log/syslog, puis les 15 dernières, puis seulement les lignes 10 à 20.**

**15. Que fait la commande dmesg | less ?**

**16. Aﬀichez à l’écran le fichier/etc/passwd; que contient-il? Quelle commande permet d’aﬀicher la page de manuel de ce fichier?**

**17. Aﬀichez seulement la première colonne triée par ordre alphabétique inverse**

**18. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement les utilisateurs connectés) ?**

**19. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?**

**20. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine**

**21. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial/dev/null**

**22. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vuprécédemment**

**23. Utilisez la commande locate pour trouver le fichier history.log.**

**24. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?**
