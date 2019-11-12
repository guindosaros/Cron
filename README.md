# Cron 
### 
- cron est un programme qui permet aux utilisateurs des systèmes Unix d’exécuter automatiquement des scripts, des commandes ou des logiciels à une date et une heure spécifiée à l’avance, ou selon un cycle défini à l’avance.

- Cron est le diminutif de crontab, lui-même le diminutif de chrono table qui signifie « table de planification ».

- cron peut jouer un fichier ogg tous les jours à sept heures sauf le samedi et le dimanche afin de se réveiller en musique.

-  cron est un daemon, ce qui, dans le jargon informatique, désigne un programme qui s'éxécute en arrière-plan. Le service cron (crond) attend ainsi jusqu’au moment spécifié dans le fichier de configuration (que l’on appelle la crontab) puis effectue l’action correspondante et se rendort jusqu’à l’événement suivant.

-Utilisation	Modifier
Lecture de la table	Modifier
La ligne de commande suivante affiche le contenu de la table cron pour l'utilisateur courant :

```python $ crontab -l ```
Cette commande ne permet pas d'afficher la table centralisée (/etc/crontab).

Modification de la table	Modifier
La commande suivante permet de modifier la table cron pour l'utilisateur courant :

```bash $ crontab -e ```
Cette commande a pour effet de lancer l'éditeur par défaut[3] (en général vi). L'éditeur affiche alors la table actuelle. Lors du premier lancement de crontab, la table est vierge, éventuellement composée de commentaires d'aide (lignes commençant par le caractère #).

L'éditeur par défaut se configure à l'aide des variables d'environnement $EDITOR ou $VISUAL. Par exemple, pour configurer l'éditeur vim :

```bash $ export EDITOR=vim ```
Cette commande ne permet pas non plus de modifier la table centralisée (/etc/crontab).

Remplacement de la table	Modifier
crontab peut aussi écraser la table courante par une nouvelle. Cette nouvelle table peut être fournie dans un fichier en paramètre :

$ crontab fichier-contenant-la-nouvelle-table.txt
Suppression de la table	Modifier
La ligne de commande suivante supprime le contenu, sans confirmation, de la table cron pour l'utilisateur courant :

```bash $ crontab -r ```
Syntaxe de la table	Modifier
Notation	Modifier
Chaque entrée de la table (chaque ligne) correspond à une tâche à exécuter et doit respecter cette notation :

mm hh jj MMM JJJ tâche
mm représente les minutes (de 0 à 59)
hh représente l'heure (de 0 à 23)
jj représente le numéro du jour du mois (de 1 à 31)
MMM représente l'abréviation du nom du mois (jan, feb, ...) ou bien le numéro du mois (de 1 à 12)
JJJ représente l'abréviation du nom du jour ou bien le numéro du jour dans la semaine :
0 = dimanche
1 = lundi
2 = mardi
…
6 = samedi
7 = dimanche (représenté deux fois pour les deux types de semaine)
Pour chaque valeur numérique (mm, hh, jj, MMM, JJJ) les notations possibles sont :

* : à chaque unité (0, 1, 2, 3, 4…)
5,8 : les unités 5 et 8
2-5 : les unités de 2 à 5 (2, 3, 4, 5)
*/3 : toutes les 3 unités (0, 3, 6, 9…)
10-20/3 : toutes les 3 unités, entre la dixième et la vingtième (10, 13, 16, 19)
Si, sur la même ligne, le « numéro du jour du mois » et le « jour de la semaine » sont renseignés, alors cron exécutera la tâche quand l'un des champs correspond. Par exemple, la ligne suivante indique que la tâche doit être exécutée les vendredis ainsi que le 13 de chaque mois, à minuit :
