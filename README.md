# LexLineage

Moteur de provenance juridique destiné à reconstruire l’historique d’une disposition et à retrouver les documents sources associés à ses modifications.

LexLineage collecte, reconstruit la chronologie, compare, relie, classe et source. Il doit expliquer pourquoi un document est rattaché à une modification. **L’avocat reste responsable de l’interprétation juridique.** Un LLM ne constitue jamais la source de vérité d’un lien juridique.

## État du projet

Fondation documentaire et structurelle uniquement : aucun moteur métier, serveur API, accès externe, frontend ou stockage n’est implémenté. Aucune dépendance applicative n’est installée. Les modules Python sont des emplacements réservés.

Le premier cas de validation est le Code général des impôts, article 38, subdivisions 7 et 7 bis. **Les données de référence restent à constituer à partir des sources primaires ; aucun résultat juridique n’est établi dans ce dépôt.**

## Documents

- [Spécification](PROJECT_SPEC.md) : objectifs, périmètre et étapes.
- [Architecture](ARCHITECTURE.md) : pipeline et responsabilités.
- [Modèle conceptuel](DATA_MODEL.md) : entités et provenance des relations.
- [Registre des sources](SOURCE_REGISTRY.md) : usages et accès envisagés.
- [Évaluation](EVALUATION.md) : métriques et protocole.
- [Golden case CGI 38](tests/golden/cgi_38/README.md) : références à constituer.

## Structure

```text
src/lexlineage/
  api/
  core/
  sources/
    legifrance/
    assemblee_nationale/
    senat/
  versioning/
  matching/
  retrieval/
  models/
tests/
  unit/
  integration/
  golden/cgi_38/
```

## Vérification locale

Python 3.11 ou supérieur est la cible déclarée, à confirmer par une future matrice CI. Aucun environnement applicatif n’est nécessaire pour cette fondation.

```sh
python3 -m compileall -q src
python3 -c 'import pathlib, tomllib; tomllib.loads(pathlib.Path("pyproject.toml").read_text())'
PYTHONPATH=src python3 -c 'import lexlineage'
git diff --check
```

Il n’existe encore aucun test métier ; ces commandes vérifient uniquement la structure, la syntaxe et la configuration. FastAPI et Pydantic seront ajoutés au moment d’implémenter les contrats et l’API. PostgreSQL, pgvector, Next.js et Vercel restent des choix futurs.
