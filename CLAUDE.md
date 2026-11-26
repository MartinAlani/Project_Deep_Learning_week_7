# Project notes for Claude

## Working conventions
- **Conversation with the user: Spanish.** The user is new to deep learning: go step by step,
  explain the *what* and *why* of each cell, and wait for them to run things in Colab.
- **All project work in English:** code, comments, docstrings, notebook text, README, report,
  commit messages.
- **Git authorship:** commits must show only the user as author. Before committing, set
  `user.name` / `user.email` to match the author of the `Initial commit` (74d1b90). Do NOT add
  `Co-Authored-By` or `Claude-Session` trailers to commit messages.
- Commit directly to `main` (user-approved workflow) and push so the user can open notebooks in Colab.
- The repo stays **public** (user decision, so Colab badges work without extra authorization).
  Claude cannot change repo settings through the proxy; the user does it in GitHub Settings.
- One notebook per phase in `notebooks/`, each with an "Open in Colab" badge; add each new
  notebook to the table in `README.md`.
- Notebooks run in **Google Colab (T4 GPU)**, TensorFlow 2.21. The CIFAR-10 download host is
  blocked in the Claude container, so test notebooks there with fake CIFAR-shaped data
  (monkeypatch `keras.datasets.cifar10.load_data`) before pushing.
- Each notebook must be self-contained (reload data with the same `SEED = 42` split:
  45k train / 5k val / 10k test, stratified) because Colab sessions don't share state.

## Decisions taken
- Trained models + history JSON are saved to Google Drive: `MyDrive/project_deep_learning_week_7/models/` (later notebooks load from there).
- Dataset: CIFAR-10. Framework: TensorFlow/Keras (TF Serving bonus planned for deployment).
- Normalization via `Rescaling(1/255)` **inside the model** (raw uint8 images in deployment).
- Augmentation: RandomFlip("horizontal"), RandomTranslation(0.1, 0.1), RandomZoom(0.1).
- `tf.data` pipeline, batch size 64, labels as integers (use sparse categorical cross-entropy).

## Progress
- [x] Phase 0 — Project structure, requirements.txt, README
- [x] Phase 1 — `01_data_preprocessing.ipynb` (user ran it in Colab successfully, up to the augmentation cells)
- [~] Phase 2 — `02_custom_cnn.ipynb` written & tested (552k params; Adam 1e-3, EarlyStopping patience 10, ReduceLROnPlateau, checkpoint). Waiting for the user to run it in Colab and report val accuracy ← **current**
- [ ] Phase 3 — Evaluation (accuracy, precision, recall, F1, confusion matrix)
- [ ] Phase 4 — Transfer learning (try 2-3 pre-trained models, justify the choice)
- [ ] Phase 5 — Flask app (multi-image upload, per-class probabilities) + TF Serving bonus, hosting
- [ ] Phase 6 — PDF report, PPT presentation, test_images/ (5-10 images)
- [ ] Before submission: delete this `CLAUDE.md` file (user request)
