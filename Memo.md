# MemoGit

- git log = voir tous les commits

# Envoyer un fichier 
- git add = selectionner un fichier
- git commit -m " le commentaire à mettre " = commenter sa modif obligatoire
- git push = envoyer mon fichier

# Recuperer un fichier
- git pull + le nom du fichier = recuperer un fichier sur github

# Faire un tag sur un commit juste après le commit 
- git tag -a + le nom du tag ex : v1.0 + -m " ma version v1.0" = creer un tag pour un commit
- git show v1.0 = montre ce commit
- git push origin v1.0 = envoie que ce commit
- git push origin --tags = envoie tous les tags

# Faire un tag sur un commit précis
- git log = voir les commits et choisir le numero du commit à tager
- git tag +le nom du tag +le num du commit

# Revenir sur une version antérieur et à la version actuel
- git checkout + numero commit/nom du tag = on revient temporairement à la version qu'on à choisit
- git switch master = revenir à la version actuel

# Se balader dans notre répertoire
-  cd = revient au repertoire ex : au bureau
-  cd - = permet de revenir au répertoire précedent
-  cd .. = permet de remonter au répertoire parent (ne pas oublier l'espace contrairement à windows)
-  cd / = permet de remonter à la racine de l'ensemble du système de fichiers
-  cd /usr/bin/ = se place dans le répertoire /usr/bin/

# Supprimer un ou plusieur fichier sois même et mettre à jour son repositories
- supprimer le ou les ficchier
- faire git add --all = selectionner les fichiers supprimer
- faire git commit -m " j'ai supprimer des fichiers"
- faire git push = met à jours github