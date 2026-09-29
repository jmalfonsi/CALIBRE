# CALIBRE

Modèle de décision bilingue (EN/FR) embarqué, successeur de LAYA et concurrent de Jev
sur cinq axes : contexte, vitesse sur l'appareil, options illimitées, champs en parallèle, français.

- `CONCEPTION.md` — architecture, technologie, données, plan, risques. **v0.3 du 2026-09-29**,
  révisée après revue d'expert (journal au §12). Étape 1 engagée : JUDGE local EN/FR (§8.1).
- `spike/` — bancs à poids aléatoires : ils mesurent la vitesse, jamais la justesse.
  - `cost_model.py` : première architecture (v1) ; `--onnx` ajoute le Lecteur en ONNX fp32/int8.
  - `cost_model_v2.py` : architecture corrigée après le v1 (étage 2 raccordé depuis la v0.2).
  - `verif_revue.py` : vérifications demandées par la revue (mémoire à 32k/128k, mémoire causale,
    invariance au lot, rejeu).
  - `results_v1.json`, `results_v2.json`, `results_revue.json` : mesures sur le Xeon D-1521 de ce serveur.
  - Relancer : `cd spike && ./.venv/bin/python cost_model_v2.py`

- `spike/web/` — Phase 0b, vitesse dans le navigateur :
  - `export_web.py` : graphes ONNX sans poids + manifeste (`out/models.json`) ; `decompose.py` : lecture contre Décideur.
  - `page/chrono.html` : banc publié (« Chronomètre CALIBRE ») ; `page/` contient aussi ONNX Runtime Web 1.30
    (le wasm WebGPU est coupé en deux parts de moins de 15 Mo, limite des Artifacts).
  - `reference_xeon_chromium_*.json` : première mesure sur ce serveur (§6.6).
- `gold/` — Phase 0c/0d, jeu or : `extract_candidates.py`, `build_sheet.py`, `REGISTRE.md` (sources, licences,
  exclusions), `sheet/annoter.html` (feuille publiée « Jeu or CALIBRE »). Aucune étiquette de modèle.

Règle de salle blanche (CONCEPTION.md §5.1) : aucun appel à Jev, aucune sortie de Jev ni de Gemini
dans les données d'entraînement ou d'évaluation.
# CALIBRE
# CALIBRE
