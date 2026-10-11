# Publier uniquement les correctifs sur GitHub

L'objectif est de rendre visibles les évolutions sans publier le site complet.

## 1. Créer un dépôt GitHub séparé

Sur GitHub :

1. Cliquer sur **New repository**.
2. Choisir par exemple `leka-correctifs`.
3. Le dépôt peut être **public** si tu veux que les correctifs soient visibles publiquement.
4. Ne pas utiliser ce dépôt pour héberger le site complet.

## 2. Décompresser ce pack

Le dossier obtenu doit contenir uniquement :

- `README.md`
- `CHANGELOG.md`
- `HISTORIQUE-DATE.md`
- `GITHUB-PROCEDURE.md`
- `historique/`
- `patches/`

Il ne doit pas contenir le dossier complet du site.

## 3. Avec GitHub Desktop

1. Ouvrir GitHub Desktop.
2. **File > Add local repository** ou créer un nouveau dépôt local dans ce dossier.
3. Vérifier dans la liste des changements qu'il n'y a que les fichiers ci-dessus.
4. Faire un premier commit, par exemple : `V165 - correctif contact et signature`.
5. Cliquer sur **Publish repository** et sélectionner le dépôt `leka-correctifs`.

Avant de publier, vérifier une dernière fois qu'aucun fichier du site complet n'apparaît dans la liste.

## 4. Avec le terminal

Dans ce dossier :

```bash
git init
git add README.md CHANGELOG.md GITHUB-PROCEDURE.md patches/
git commit -m "V165 - correctif contact et signature"
git branch -M main
git remote add origin ADRESSE_DU_DEPOT_GITHUB
git push -u origin main
```

## 5. Pour les prochaines versions

Ne copie jamais tout le site dans ce dépôt. Génère seulement un nouveau fichier `.patch`, puis ajoute une entrée au `CHANGELOG.md`.

Exemple :

```text
patches/V166-correction-menu-mobile.patch
patches/V167-optimisation-contact.patch
```

Ainsi, GitHub montre les corrections et leur historique sans rendre le projet complet téléchargeable.

## Important

Un fichier `.patch` contient tout de même quelques lignes de contexte autour des modifications. Il révèle donc uniquement les portions de code concernées par les correctifs, pas l'arborescence complète ni tous les fichiers du site.
