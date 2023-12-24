# WebScraping : TikTok Projet Etudiant

Projet étudiant UTC (IC05) visant à récolter des métriques sur les vidéos TikTok. Les pages PourToi et tendances sont analysées. Le dossier `data` contient les bases de données. Le dossier `plots`contient les graphiques utilisés pour l'analyse.

## Auteurs

- Alexandre Amrani - alexandre.amrani@etu.utc.fr

- Robert Antaluca - robert.antaluca@etu.utc.fr 

- Matthis Legal - matthis.legal@etu.utc.fr


## Utilisation

Docker doit impérativement être installé et lancée. Les programmes présentés ici se connectent directement. Depuis une invite de commande, lancez : `sudo docker run -d -p 4445:4444 -p 5901:5900 selenium/standalone-firefox-debug`

Puis utiliser un logiciel de virtual network computing viewer pour afficher ce qui se passe dans le docker. Sous Windows, le logiciel [TightVNC Viewer](https://www.tightvnc.com/download.php) peut être utilisé. D'après la ligne ci-dessus, il faut le paramétrer pour écouter `127.0.0.1:5901`. Par défaut, le mot de passe est "*secret*".

## Contenu

Les fichiers principaux sont cités ici :

- `decouverte_videos.R` : à partir d'une bdd contenant les liens des tendances, parcourt les tendances et crée les bases tendances. Ne récupère que les liens vidéos/utilisateurs et le username.

- `foryou_decouverte.R`: analyser la page PourToi. Les données récupérées sont "names", "likes", "coms", "signets", "partages", "descriptions", "hashtags", "urls". Enregistre dans une bdd dédiée aux ForYou.

- `mots_hashtags.R`: création des nuages de mots hashtags pour les trends et la page PourToi.

- `recuperation_commentaires.R`: script utilisé pour récupérer les commentaires des vidéos tendances dont l'url a déjà été stockées dans l'une des 14 bdd de la tendance. Parcourt des 14 bdd tendances puis parcourt chaque vidéo. Processus long (environ 1 heure), enregistre
chaque bdd une fois la tendance finie.

- `stats_desc_plot.R` : programme utilisé pour générer les graphiques. Il suffit de lancer une fonction pour que l'image correspondante soit enregistrée.

- `update_stats_videos.R` : programme utilisé pour METTRE A JOUR les données tendances avec Selenium. Une fois les bdd tendances créées, lancer ce script ajoute 4 colonnes pour les 4 métriques, avec comme nom "<métrique> \<Date\>". Il faut rester proche pour résoudre les captcha.

Ancien script : 

- `musique_avec_docker.R` Programme utilisé pour récupérer les données des vidéos à partir d'une page musique.
