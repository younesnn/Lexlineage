# Modèle de données conceptuel

Aucun modèle exécutable ni schéma de base n’est créé. Les attributs ci-dessous décrivent des besoins à préciser. Un identifiant interne stable sera distingué des identifiants officiels, qualifiés par fournisseur et espace de noms. Les valeurs inconnues resteront absentes avec un motif, sans valeur inventée.

| Concept | Rôle et attributs envisagés |
| --- | --- |
| LegalProvision | Disposition ou subdivision : identifiant interne, références officielles, corpus, libellé, chemin de subdivision, parent éventuel. La continuité d’identité doit être établie. |
| LegalVersion | État textuel d’une disposition : provision, texte brut, texte normalisé, période de validité documentée, dates de publication, sources, empreinte, version de normalisation. |
| ChangeEvent | Changement observé : versions avant/après, segments touchés, type de changement, dates et statut de résolution. Création ou suppression peuvent n’avoir qu’une version. |
| Law | Loi identifiée : titre, identifiants officiels, numéro et dates documentées, référence de publication. Ne représente pas à elle seule tous les types d’actes modificatifs. |
| Bill | Projet ou proposition : identifiants propres aux chambres, titre, nature, références de dossier. Les dépôts successifs ne sont pas automatiquement une même identité. |
| LegislativeStage | Étape de procédure : dossier, chambre ou instance, lecture, type, dates et statut documentés. |
| Document | Pièce source : identifiants officiels, type, auteur institutionnel, titre, URL, dates, format, empreinte, version de collecte, contenu brut ou référence au contenu. Peut représenter un acte modificatif autre qu’une loi. |
| Amendment | Amendement : document support, numéro qualifié par chambre/étape/texte, cible, auteur, texte, sort documenté ; sous-amendements et liens de filiation restent sourcés. |
| Debate | Séance ou discussion : chambre ou commission, date, étape, compte rendu support et repères. |
| DocumentPassage | Passage vérifiable : document et version exacte, page, ancre ou offsets avec convention explicite, extrait, méthode d’extraction et empreinte. |
| Relationship | Lien orienté typé entre deux entités : provenance complète, preuves, méthode, confiance, version d’algorithme et statut. |
| Source | Producteur ou jeu de données : autorité, périmètre, accès, rôle probatoire, conditions d’usage à vérifier et état de disponibilité. À distinguer d’une pièce individuelle. |

## Relations envisagées

Une disposition possède des versions ; un changement compare ces versions ; un changement est attribué à une loi ou à un autre acte documenté. Un dossier relie textes déposés, étapes et pièces ; rapports, amendements et débats documentent ces étapes. Un passage justifie un rattachement à un changement. Une relation de contexte n’équivaut pas à une relation de modification normative.

Ces liens devront être représentés ou accompagnés par `Relationship`, y compris les liens structurels lorsqu’ils expriment une assertion issue d’une source. Aucun type de relation n’autorise à omettre sa provenance.

## Provenance obligatoire d’une relation

- `id`, `subject_id`, `predicate`, `object_id` : identité et sens du lien.
- `source_ids` : sources ayant fourni les éléments, au moins une pour un lien établi.
- `evidence` : une ou plusieurs références vers documents et passages exacts, avec identifiant/URL, version ou empreinte de la pièce et localisation ; une URL seule ne suffit pas à justifier l’assertion.
- `matching_method` : identifiant officiel, référence explicite, règle déterministe ou validation humaine, avec paramètres et justification lisible.
- `confidence` : niveau technique et justification ; échelle et seuils à arbitrer, sans fausse probabilité numérique.
- `algorithm_version` : version exacte du code ou de la procédure d’annotation ayant produit le lien.
- `run_id`, `created_at` : exécution et date de production ; configuration et manifeste de corpus référencés par l’exécution.
- `status` : candidat, étayé, validé humainement, rejeté ou contradictoire ; historique des validations et motif.

Les candidats sans preuve suffisante ne sont pas des liens établis. Une validation humaine conserve auteur, date et preuve ; elle ne remplace pas la provenance. Les preuves concurrentes sont conservées sans écrasement silencieux.

## Temps, identité et reproductibilité

Séparer temps de validité juridique et temps d’observation technique. Ne pas inférer l’entrée en vigueur à partir de la seule date de publication. Un diff est une observation textuelle et n’établit pas seul sa cause normative. Empreintes des pièces, version de l’extracteur, normalisation, règles, paramètres et code devront permettre de rejouer une exécution. Déduplication, cardinalités et contraintes seront précisées après examen du corpus primaire.
