# Registre prévisionnel des sources

Ce registre prépare les connecteurs ; aucun accès externe n’a été effectué pour cette fondation. Les méthodes d’accès sont envisagées, pas validées. Couverture historique, schémas, authentification, quotas, licences, stabilité et disponibilité devront être vérifiés dans les documentations officielles avant intégration. Les limites ci-dessous sont des risques à vérifier, pas un audit des services.

Le statut de source de vérité est limité à l’assertion concernée : une pièce parlementaire atteste son propre contenu et ne prouve pas seule qu’un amendement a modifié le droit en vigueur.

| Source / autorité | Données attendues | Méthode d’accès envisagée | Rôle dans LexLineage | Limites / points à vérifier | Fallback | Statut probatoire |
| --- | --- | --- | --- | --- | --- | --- |
| Légifrance / DILA ; PISTE comme canal d’accès | Textes, versions, identifiants, références de publication et liens de modification disponibles | API Légifrance via PISTE, conditions et couverture à vérifier | Résolution des dispositions, collecte des versions et recherche des actes modificatifs | Granularité des subdivisions, profondeur historique, exhaustivité des liens et distinction des dates à vérifier | Pièces officielles de publication et pages officielles ; extraction ciblée documentée si nécessaire ; sinon lacune explicite | Source primaire de référence pour les textes collectés ; chaque causalité doit être prouvée par l’acte concerné |
| Assemblée nationale | Dossiers, textes déposés, rapports, amendements, étapes, comptes rendus publics et travaux de la commission des finances disponibles | Open Data et téléchargements structurés officiels ; schémas à vérifier | Reconstituer les étapes et retrouver les pièces de l’Assemblée | Couverture selon législature et type de document, identifiants et disponibilité des travaux de commission à vérifier | Pages, PDF et archives officiels ; scraping ciblé seulement si le structuré ne suffit pas ; signalement des absences | Source primaire documentaire pour les pièces et événements de l’Assemblée ; pas une preuve autonome d’effet normatif |
| Sénat | Dossiers, textes, rapports, amendements, comptes rendus et travaux publics disponibles | Open Data et téléchargements structurés officiels ; modalités à vérifier | Reconstituer les étapes et retrouver les pièces du Sénat | Couverture historique, formats, correspondances entre chambres et granularité des débats à vérifier | Pages, PDF et archives officiels ; extraction ciblée tracée ; lacune si pièce introuvable | Source primaire documentaire pour les pièces et événements du Sénat ; pas une preuve autonome d’effet normatif |

## Règles communes de collecte future

Préférer les données structurées et identifiants officiels. Conserver requête ou référence de téléchargement, horodatage, réponse brute ou pièce, URL d’origine, empreinte et version d’extraction. Une copie collectée conserve son autorité d’origine et sa chaîne de provenance.

Le scraping est une méthode d’accès subsidiaire, jamais une nouvelle autorité. Un résultat de moteur de recherche, une synthèse ou une sortie de LLM ne sont pas des preuves de rattachement. Toute découverte doit revenir à une pièce primaire vérifiable.

Une source indisponible ne doit pas être remplacée silencieusement. Documenter la tentative, la limite de couverture et le fallback employé. En cas de contradiction, exposer les références concurrentes et soumettre l’arbitrage à vérification humaine.
