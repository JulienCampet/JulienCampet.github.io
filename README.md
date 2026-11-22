# Site de Julien Campet

Site personnel construit sur le template [Academic Pages](https://github.com/academicpages/academicpages.github.io) (Jekyll + GitHub Pages).

## Mettre en ligne

1. Crée un repo **vide** nommé `TON-PSEUDO.github.io` sur GitHub (par exemple `TheBigJouls.github.io`).
2. Dans `_config.yml`, remplace `TON-PSEUDO-GITHUB` (2 occurrences, champs `url` et `repository`).
3. Pousse le contenu de ce dossier :
   ```bash
   git init && git add . && git commit -m "Premier jet du site"
   git branch -M master
   git remote add origin git@github.com:TON-PSEUDO/TON-PSEUDO.github.io.git
   git push -u origin master
   ```
4. Sur GitHub, va dans **Settings → Pages → Source : GitHub Actions**. Le workflow `.github/workflows` du template construit et publie le site à chaque push.

## Tester en local

```bash
bundle install
bundle exec jekyll serve -l -H localhost   # puis http://localhost:4000
```

## Où est quoi

| Je veux modifier…                     | Fichier                                   |
|---------------------------------------|-------------------------------------------|
| Nom, bio, liens de la barre latérale  | `_config.yml` (bloc `author`)             |
| Photo                                 | `images/profile.jpg` (remplacer le fichier)|
| Menu du haut                          | `_data/navigation.yml`                    |
| Page d'accueil                        | `_pages/about.md`                         |
| Missions du poste actuel              | `_pages/poste-actuel.md`                  |
| CV                                    | `_pages/cv.md`                            |
| Couleurs et style des listes          | `_sass/_custom.scss`                      |
| Les productions                       | `_articles/`, `_evenements/`, `_audiovisuel/`, `_web/` |

## Ajouter une production

Crée un fichier `AAAA-MM-JJ-titre-court.md` dans le bon dossier :

```yaml
---
title: "Titre de la production"
date: 2025-03-14            # sert au tri (le plus récent en haut)
categorie: interviews       # section de la page (voir le front matter de _pages/articles.md, etc.)
role: "Entretien et rédaction"
cadre: "ENS – PSL"
periode: "2025"             # optionnel : texte libre affiché à la place de l'année
statut: "À venir"           # optionnel : badge (À venir, En cours, En développement…)
resume: "Une phrase affichée dans la liste."
liens:
  - label: "Lire"
    url: "https://…"
page_detail: false          # optionnel : le titre renvoie directement au premier lien
citation: 'Campet, J. (2025). « Titre ». <i>Média</i>.'   # optionnel : le clin d'œil bibliographique
---

Texte libre de la page détaillée (Markdown).
```

Pour une **nouvelle section** (par exemple « Podcasts »), ajoute une entrée `cle`/`titre` dans `sections:` de la page concernée et utilise cette `cle` comme `categorie` dans les fiches.

## Points à vérifier

Cherche `✏️` et `⚠️` dans le projet (`grep -rn "✏️\|⚠️" _pages _articles _evenements _audiovisuel _web`) : ce sont les dates, titres ou rôles à confirmer.

- **Missions du poste actuel** : c'est une ébauche à réécrire avec tes vraies missions.
- **Articles Dealers de Science** : le site d'origine est compromis. Les deux articles sont restaurés sur ce site à partir des archives (texte et images dans `images/dealers/`), avec un bandeau « Article archivé ». Pour archiver un autre article, ajoute un bloc `archive:` au front matter (voir `_articles/2024-03-01-dealers-yves-coudiere.md`).
- **Images** : les visuels du Notion (affiches, photos) ne sont pas inclus. Dépose-les dans `images/` et décommente les lignes `![…]` dans les fiches.
