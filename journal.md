# Journal

- 2026-11-25: Setup done (venv, notebook, data downloaded from PolyAI repo).
- 2026-11-25: Built intent->team table (77 rows). Rule: Securite imposed; card object -> Cartes; money movement/fees -> Paiements; identity/general info -> Compte.
- 2026-11-25: Part B done. Checked class distribution train vs test, length stats, top words, hapax, rank-frequency plot, duplicates (normalisation = lowercase + strip punctuation).
- 2026-11-25: Part D done. 85/15 stratified split (seed 42). Pipeline TF-IDF + LogReg fitted on train only. Leaky variant (vectorizer fitted on train+val+test texts) evaluated on val, not test, to keep test labels untouched.
- 2026-11-25: Part E done. Baseline = majority class. Grid of 24 configs on val (BoW/TF-IDF x stop words x ngram x C). Chosen config = best macro-F1 on val only.
- 2026-11-25: Part F done. Final config fitted on train only, evaluated once on test. Manual P/R/F1 for Securite matches sklearn. Threshold table computed on validation (not test).
- 2026-11-25: Part G done. Manual cosine on 2 short corpus messages matches numpy. Retrieval: TF-IDF fitted on train only, top-3 neighbours for 5 val messages, Recall@3 computed.
- 2026-11-25: Part H done. Wrote 30 own messages (10 fr / 10 darija / 10 en with typos), evaluated final model, analysed 8 errors. Main finding: English-only vocabulary fails on French/darija.
- 2026-11-25: Generated results.json from the notebook, requirements.txt via pip freeze, README. Verified with Restart + Run All.
- 2026-11-25: Reviewed results. Added full-validation Recall@3 (the 5 sampled queries had no failure), counts behind the threshold table, OOV diagnostics. Noted: best C=10 is at the edge of the grid (not re-tuned after the test run). Own set: 13/16 errors predicted as Paiements (majority-class fallback on unseen words); only 1/9 Securite messages found.
