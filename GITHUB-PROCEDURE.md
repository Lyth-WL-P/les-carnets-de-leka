# Remplacer proprement l’ancien contenu du dépôt

Oui, tu peux supprimer les fichiers actuellement ajoutés sur GitHub et les remplacer par ce dossier.

## Méthode simple depuis GitHub

1. Supprimer les anciens fichiers `CHANGELOG.md`, `HISTORIQUE-DATE.md`, `README.md` et l’ancien dossier `historique/`.
2. Conserver le dépôt lui-même : inutile de recréer le repository.
3. Envoyer à la racine le contenu de ce dossier.
4. Vérifier que la racine contient notamment `README.md`, `EVOLUTION-CODE.md`, `CHANGELOG.md`, `HISTORIQUE-DATE.md`, `historique/` et `patches/`.
5. Faire un commit avec un message comme : `Reconstruction de l'historique complet du développement`.

## Pourquoi remplacer plutôt que superposer

L’ancienne présentation recensait surtout les paquets de correctifs et les chemins de fichiers. Cette nouvelle présentation raconte directement l’évolution du code, les bugs corrigés et les décisions prises à chaque version.

Le dépôt Git conserve de toute façon l’ancien commit dans son historique : supprimer les anciens fichiers de la branche actuelle ne supprime pas le passé Git.
