<!-- ...existing code... -->

# TP — petit projet Python

Introduction
------------
Je présente ici un petit projet Python contenant un module qui retourne l'heure et un script principal. Ce README décrit les actions Git que j'ai effectuées et explique un conflit rencontré et sa résolution.

Fichiers
--------
- `module.py` : contient `obtenir_temps()` (utilise `datetime`).
- `code.py` : script principal qui importe `obtenir_temps()` et affiche un message.
- `README.md` : ce document.

Chronologie des actions (explication personnelle)
-------------------------------------------------
1. Initialisation et premier commit
   - J'ai initialisé le dépôt : `git init`
   - J'ai ajouté les fichiers et fait mon premier commit :  
     `git add .` puis `git commit -m "Ajout du fichier TP"`
   - J'ai créé la remote et poussé la branche `master` vers GitHub :  
     `git remote add origin https://github.com/Andre-francisca/TPclass`  
     `git push -u origin master`

2. Tentative de renommage de la branche
   - J'ai voulu renommer ma branche locale en `main` : `git branch -M main`
   - Le push vers `main` a été rejeté car le dépôt distant contenait déjà un historique que je n'avais pas localement. J'ai donc laissé `master` suivi par `origin/master`.

3. Refonte et ajout du module
   - J'ai créé une branche `refonte` : `git checkout -b refonte`
   - J'y ai ajouté `module.py` et modifié `code.py`, puis commit :  
     `git commit -m "Ajout du module et mise à jour du code"`
   - J'ai poussé `refonte` puis fusionné (fast-forward) `refonte` dans `master` et supprimé `refonte` (localement et à distance).

4. Simulation d'un conflit et résolution
   - À partir du même commit de base j'ai créé deux branches concurrentes :
     - `conflit-a` : modification de `code.py` — commit "Modification version A"
     - `conflit-b` : modification différente de `code.py` — commit "Modification version B"
   - J'ai mergé d'abord `conflit-a` dans `master` (fast‑forward). Ensuite, en tentant de merger `conflit-b` dans `master`, Git a détecté des modifications concurrentes sur les mêmes lignes de `code.py` et a déclenché un conflit :
     ```
     Auto-merging code.py
     CONFLICT (content): Merge conflict in code.py
     Automatic merge failed; fix conflicts and then commit the result.
     ```
   - Pour résoudre le conflit j'ai :
     1. Ouvert `code.py`, supprimé les marqueurs (`<<<<<<<`, `=======`, `>>>>>>>`) et choisi le contenu final désiré.
     2. Ajouté le fichier résolu : `git add code.py`
     3. Fait le commit de résolution :  
        `git commit -m "Résolution du conflit entre conflit-a et conflit-b"`
     4. Poussé la branche `master` vers l'origine : `git push origin master`
   - Après cela le working tree était propre : `nothing to commit, working tree clean`.

Pourquoi le conflit est apparu (en termes simples)
-------------------------------------------------
- J'ai modifié le même fichier (`code.py`) sur deux branches partant du même commit de base, avec des modifications différentes sur des lignes qui se chevauchent. Git ne pouvait pas déterminer automatiquement laquelle des deux modifications devait être conservée, d'où le conflit.

Comment j'ai résolu le conflit (résumé)
--------------------------------------
- Fusion manuelle du contenu souhaité dans `code.py`, puis `git add` et `git commit` pour valider la résolution, enfin `git push` pour synchroniser avec le dépôt distant.

Exécution du projet
-------------------
Dans PowerShell :
```
cd C:\Users\T-Plug\Desktop\TP
python code.py
```

Notes finales
-------------
Si vous souhaitez, je peux fournir :
- Les diffs exacts des commits qui ont provoqué le conflit (ex. `git show <commit>`).
- Un petit fichier CHANGELOG.md listant ces étapes de façon chronologique.
```// filepath: c:\Users\T-Plug\Desktop\TP\README.md
<!-- ...existing code... -->
