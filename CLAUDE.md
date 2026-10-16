# clarity-releases — conventions

**Dépôt PUBLIC.** Tout ce qui est écrit ici — fichiers, messages de commit, notes de version, journaux d’Actions —
est lisible par tous. Jamais : un chemin ou un document interne, une donnée personnelle, un secret. Ne nomme aucun
autre dépôt que celui-ci.

## Ce qui vit ici

- La page de téléchargement (`index.html`, `README.md`), servie par GitHub Pages (branche `main`, racine).
- Les installateurs, publiés en versions (Releases `v<version>`). L’appli installée s’y met à jour. Le contenu de la
  page et les versions sont déposés par la publication de l’appli : ne pas les éditer à la main sans raison.

## Minutes et stockage Actions

Dépôt public : minutes des exécuteurs standard gratuites. Il n’y a aucun workflow ici. Un premier workflow suivrait la
règle commune :

1. Déclencheurs : `push` sur `main`, `workflow_dispatch`, `schedule`. Jamais `pull_request` ni branche de travail.
2. `timeout-minutes` sur chaque job ; `concurrency` avec `cancel-in-progress: true`, sauf pour un workflow qui publie
   (`false`).
3. Coût estimé écrit en tête du fichier.
4. Pas d’`actions/upload-artifact` : un installateur va directement dans une Release. Si un artefact était vraiment
   nécessaire : `retention-days: 1` et petits fichiers seulement. Pas de gros cache.
5. Si le dépôt repassait privé : le quota (minutes et 500 Mo de stockage) devient partagé, et la rétention des
   artefacts se règle à 1 jour (Settings › Actions › General, par le propriétaire).

## Git

Auteur `Claude <noreply@anthropic.com>` ; pas de lien de session dans les commits ; `Co-Authored-By` gardé.
