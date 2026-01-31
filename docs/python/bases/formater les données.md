## Les dates

Package : `datetime`

* `today()` date du jour.
* `date + datetime.timedelta(-31)` ajouter des jours a une date.
* `dt.datetime.strptime('2023-09-12', '%Y-%m-%d')` convertir un champ en date.
* `datetime.date()` récupérer que la date
* `colonne.dt.isocalendar()` renvoie un tableau avec l'année, le numero de la semaine et le jour.
* `dt.datetime.today()` date et heure actuelles.
* `debut + dt.timedelta(days=90)` ajouter un nombre de jours.
### Extraire la partie d'une date

* `date.strftime(format)` extraire la partie d'une date.

Format | Définition
-------|---------
`%Ỳ`   | année
`%m`   | mois numéro
`%B`   | mois nom
`%d`   | jour numéro
`%A`   | jour nom
