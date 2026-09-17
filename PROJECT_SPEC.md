# Spécification de LexLineage

## Finalité

À partir de l’identification d’une disposition et de ses subdivisions, reconstruire leur historique depuis leur création et restituer des pièces vérifiables par un avocat. Le moteur ne produit pas d’interprétation juridique à sa place.

## Cas de référence

Entrée : Code général des impôts ; article 38 ; subdivisions 7 et 7 bis.

Résultats cibles, à établir ultérieurement :

1. Versions de chaque subdivision depuis sa création.
2. Changements textuels entre versions.
3. Textes juridiques responsables de chaque modification.
4. Lois ayant créé ou modifié les dispositions.
5. Dossiers législatifs associés.
6. Rapports de l’Assemblée nationale.
7. Travaux et discussions de la commission des finances lorsqu’ils sont disponibles.
8. Rapports et travaux du Sénat.
9. Amendements pertinents, y compris pour la généalogie de la disposition.
10. Comptes rendus des débats des deux chambres.
11. Sources primaires, passages probants et motifs de rattachement.

**Aucune version, date de création, loi modificative ou filiation de ces subdivisions n’est affirmée ici. Les données de référence restent à constituer à partir des sources primaires.**

## Exigences cibles

- Résoudre l’identité d’une subdivision sans assimiler une simple correspondance de numéro à une continuité juridique.
- Distinguer publication, adoption, entrée en vigueur et collecte ; conserver les dates inconnues explicitement.
- Préserver texte brut, texte normalisé, identifiants officiels et preuves.
- Signaler lacunes, ambiguïtés, contradictions et sources indisponibles ; ne jamais combler ces manques par une invention.
- Expliquer chaque relation par sa source, sa méthode, une preuve localisable, un niveau de confiance et une version d’algorithme.
- Distinguer changement textuel constaté, acte modificatif établi et documents de contexte.
- Conserver les amendements rejetés, retirés ou non retenus comme contexte si pertinents, sans les présenter comme des modifications adoptées.
- Permettre la reproduction à partir d’un corpus figé et d’une configuration identifiée.

## Périmètre de cette livraison

Documentation, packages vides et configuration Python minimale. Aucun algorithme, schéma Pydantic, endpoint, client externe, scraping, base de données ou frontend. Aucun résultat juridique calculé ou annoté.

## Progression envisagée

1. Constituer et faire vérifier le corpus primaire du golden case.
2. Définir les contrats minimaux d’identité, de version et de preuve.
3. Implémenter les connecteurs et la reconstruction déterministe avec tests sur données figées.
4. Évaluer le rattachement aux travaux parlementaires puis la recherche et le classement.
5. Exposer une API et une interface seulement après validation du noyau.

Chaque étape fera l’objet d’un périmètre propre. La collecte réelle, les dépendances et la persistance ne font pas partie de la fondation.
