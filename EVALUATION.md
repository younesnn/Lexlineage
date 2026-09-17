# Évaluation future

Aucun score n’est disponible. Les données de référence du cas CGI 38 restent à constituer à partir des sources primaires. Une référence incomplète ne permet pas d’affirmer une exhaustivité sur tout l’historique.

## Constitution du référentiel

Définir et figer le périmètre temporel, les subdivisions, les catégories documentaires et les critères de pertinence avant évaluation. Collecter les pièces primaires, enregistrer leurs identifiants et empreintes, puis annoter versions, changements, actes modificatifs et documents pertinents avec preuves localisées. Prévoir une vérification indépendante et un arbitrage des désaccords. Séparer les annotations inconnues des cas négatifs vérifiés.

Les données servant à ajuster les règles seront distinguées des données d’évaluation. Les duplications et éditions d’un même document seront traitées selon une politique explicite pour éviter de gonfler les scores. L’unité d’évaluation sera fixée par métrique et les résultats ventilés par subdivision, période, chambre et type documentaire lorsque le corpus le permet.

## Métriques

| Mesure | Définition prévue | Précautions |
| --- | --- | --- |
| Exhaustivité / recall documentaire | Documents pertinents retrouvés / documents pertinents annotés dans le périmètre | Publier le dénominateur et la couverture du référentiel ; absence non vérifiée ≠ non-pertinence |
| Précision documentaire | Documents pertinents retrouvés / documents retournés évaluables | Indiquer aussi le nombre retourné non encore annoté ; mesurer précision@k pour le classement |
| Exactitude des changements | Précision, rappel et F1 des changements face aux opérations annotées, plus taux de paires de versions entièrement correctes | Fixer segmentation et normalisation ; compter faux changements et omissions ; contrôler ordre des versions et dates documentées séparément |
| Exactitude modification → texte modificatif | Rattachements corrects / rattachements proposés évaluables ; rappel des rattachements attendus | Comparer identifiant de l’acte et passage opérant ; gérer causes multiples, faux liens et abstentions ; rapporter la couverture de résolution |
| Traçabilité | Relations établies disposant de tous les champs de provenance / relations établies | Audit distinct de la capacité des preuves à soutenir réellement le lien ; vérifier passage, pièce, empreinte et source |
| Reproductibilité | Résultats canoniques identiques lors de deux exécutions avec même corpus, code et configuration / résultats comparés | Exclure les horodatages techniques du comparatif ; conserver manifeste, versions et paramètres ; un corpus actualisé est une autre expérience |

Un dénominateur nul ou un référentiel absent donne « non mesurable », jamais un score parfait. Les seuils d’acceptation seront fixés après constitution et audit du corpus ; aucun seuil ni score empirique n’est inventé ici.

## Organisation des contrôles

- `tests/unit/` : futures règles déterministes et cas limites sur petites données locales.
- `tests/integration/` : futurs contrats entre composants et adaptateurs, sur fixtures figées ; réseau éventuel explicitement séparé et activé volontairement.
- `tests/golden/cgi_38/` : protocole et futur référentiel primaire validé.

Pour cette fondation : vérifier l’arborescence, parser la configuration TOML, compiler les modules vides, vérifier l’import du package et lancer `git diff --check`. Ces contrôles ne valident aucune assertion juridique et ne remplacent pas de futurs tests métier.
