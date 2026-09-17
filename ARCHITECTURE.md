# Architecture cible

## Pipeline

```text
Legal Entity Resolver → Version Engine → Diff Engine → Source Resolver
                     → Legislative Graph → Document Retrieval / Ranking
```

Ce pipeline décrit des responsabilités futures, pas des composants déjà exécutables.

| Composant | Responsabilité | Emplacement prévu |
| --- | --- | --- |
| Legal Entity Resolver | Résoudre code, article et subdivision, identités et ambiguïtés | core/ |
| Version Engine | Ordonner les versions et leurs périodes documentées | versioning/ |
| Diff Engine | Comparer les textes, préserver les repères et distinguer normalisation et changement | versioning/ |
| Source Resolver | Rattacher un changement à un texte modificatif sur preuve | matching/ |
| Legislative Graph | Représenter actes, étapes, documents et relations qualifiées | core/ et models/ |
| Document Retrieval / Ranking | Retrouver et classer les documents et passages pertinents | retrieval/ |

Les chemins de modules sont relatifs à `src/lexlineage/`. `sources/` accueillera les adaptateurs propres aux fournisseurs ; `api/` l’exposition future des contrats ; `models/` les modèles partagés, encore non définis en code.

## Décisions de fondation

- Un seul package Python `lexlineage`, organisé en disposition `src`, sans microservices.
- Les adaptateurs de sources fourniront les pièces et métadonnées ; ils ne décideront pas seuls de la signification juridique d’un lien.
- Le noyau devra pouvoir fonctionner sur un corpus local figé, sans appels réseau dans les tests unitaires ou golden.
- Le graphe est un modèle logique. Il n’implique ni moteur de graphe ni base de données à ce stade.
- Priorité aux identifiants officiels, données structurées, règles déterministes et preuves documentaires.
- Une suggestion sémantique ou un score de ranking ne suffira jamais à établir un lien juridique. Les LLM pourront ultérieurement aider la recherche, le ranking ou la synthèse sourcée.
- Pas de dépendances FastAPI/Pydantic avant besoin effectif ; pas de serveur ni de point d’entrée artificiel.

## Flux de données futur

Les pièces brutes seront conservées avec URL, identifiant, horodatage de collecte et empreinte. Extraction et normalisation produiront des dérivés versionnés sans écraser les pièces. La comparaison produira des changements observés ; le matching ajoutera des relations justifiées. La restitution séparera faits documentés, candidats à vérifier et lacunes.

Une relation non résolue restera non résolue. Les contradictions seront conservées avec leurs preuves concurrentes. La confiance est un indicateur technique, jamais une certitude juridique.

## Arbitrages ouverts

Granularité et continuité d’identité des subdivisions ; traitement des renumérotations, abrogations et effets différés ; représentation des intervalles temporels ; règles de validation humaine ; conservation des pièces et politique de mises à jour ; contrats API ; dépendances et CI. PostgreSQL est envisagé pour la persistance, pgvector seulement après démonstration d’un besoin. Next.js et Vercel sont envisagés pour une interface future.
