#### Example coter mep/client :
- Pour push le travail effectuer dans sa branch
   - git checkout le_nom_de_sa_branch
   - git add . ou selectionner les fichiers 
   - git commit -m ""
   - git push origin develop
   
- Pour mettre à jour la branch develop
   - cd mep/client
   - git checkout develop
   - git stash si besoin ( pas faire de commit juste pour cette opération)
   - git pull 
   - git checkout le_nom_de_sa_branch 
   - git stash pop (pour récup son taff)
   
   - git merge --abort : permet d'annuler les merges si on ne les veut pas faire ( très déconseiller)
   - commande à faire en dernière solution pour maj sa branch develop et effacer tous son travail : git reset --hard origin/develop
   
- Pour mettre à jour sa branch par rapport à develop
   - git stash
   - git checkout le_nom_de_sa_branch
   - git pull origin develop
   - resoudre conflit si il y en a dans VCS/Git/ResolveConflict
   - git stash pop
   
#### Example coter mep/api :

- Pour mettre à jour la branch api
   - cd mep/api
   - git checkout develop
   - git pull 
   
- Mettre à jour la bdd avec les fixtures
   - Supprimer toute les tables dans Oracle Sql server : MEP_SIR.sql, rajouter le code suivant dans la feuille de calcul SQL puis cliquez sur la fleche verte pour lancez la commande
     - begin
        for i in (select * from tabs) loop
        execute immediate ('drop table ' || i.table_name || ' cascade constraints');
        end loop;
        end; 
    - Revenir sur son projet : cd mep/api branch develop
      - sudo docker-compose exec api php bin/console doctrine:schema:update --force
      - Commenter dans `api/src/Entity/Etablissements.php` la propriété `$aspPhyss` (~ l.1072) puis passer cette commande :
      - sudo docker-compose exec api php bin/console doctrine:fixture:load
      - Ecrire yes quand on le demande 
      - Décommenter la propriété `$aspPhyss`.
   
   
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

# Faire un tag sur un commit précis
- git log = voir les commits et choisir le numero du commit à tager
- git tag +le nom du tag +le num du commit

# Envoyer ses tags sur GitHub
- git push origin v1.0 = envoie que ce commit
- git push origin --tags = envoie tous les tags

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

# Supprimer un dossier et ce qu'il y a dedans
- git rm -r +nom du  dossier = selectionner undossier + les fichiers à l'intérieur
- git commit -m " "
- git push = dossier supr

# Relier son dépot local et github
- retrouver le dossier en local et faire git init
- git add --all
- git  commit -m ""
- git remote add origin + url = faire le lien
- git push  -u origin master = envoyer les fichiers

# Utiliser VCS avec webstorm

- ouvrir le bon project à modifier dans file new project
- changer le fichier dans github
- changer notre fichier en manuel
- faire un vcs + git + commit files et cocher le commit
- ensuite faire git + push 
- faire merge jusqu'à voir les 3 tableaux
- choisir dans le tableau du milieux ce qu'on veut pour le fichier final 
- faire apply
- finir avec git + push

# Creer une branche avec issue

 - creer une issue sur github
 - git branch + nom de la branche = une nouvelle branche
 - du coup on a master et la nouvelle branche
 - travailler sur la branche git checkout + nom de la branche
 - git add +nom du fichier
 - git commit -m ""
 - git push --set-upstream origin +nom de la branche
 - sur github rafraichir + faire pull request
 - faire fixes #+nom de l'issue
 - valider + suprimmer issue sur github directement
 - suprimmer la branche sur git en local = git branch -d + nom de la branch
 
 # Conflit pendant le push
  
  - Sa veut dire que la version du fichier qu'on a n'est pas à jour en local
  - donc mettre à jour notre local (master) et le comparer à notre branche où on a modif le fichier
  - faire la modif en manuel sur le fichier webstorm
  - début de la procédure
  - git switch master = revenir sur la branche master
  - git pull = mettre à jour la branche master
  - git switch sur la branche = on revient sur nos modif
  - git rebase master = on compare le fichier master à notre fichier de la branche
  - faire nos modif sur webstorm exemple
  - git add +nom du fichier
  - git rebase --continue
  - git push --force
  - allez sur github et pas de conflit mtn
