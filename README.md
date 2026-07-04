# Human Activity Recognition with Hidden Markov Models

Formative 2 — infer human activity states (still, standing, walking, jumping) from smartphone
accelerometer + gyroscope data using a from-scratch Gaussian HMM (Viterbi + Baum–Welch).

## Repository structure

```
.
├── README.md
├── hmm_activity_recognition.ipynb   # full pipeline: load → features → HMM → evaluation
├── report.pdf                       # 4–5 page report (export from report_template.md)
├── <filled course document>.pdf     # the required "Make a Copy, Fill and Export" document
└── data/
    ├── train/                       # training recordings
    │   ├── walking_alice_01.csv
    │   ├── jumping_bob_01.csv
    │   └── ...
    └── test/                        # UNSEEN recordings (new session — never used in training)
        ├── walking_alice_t1.csv
        └── ...
```

## Data collection instructions (do this with a real phone)

1. Install **Sensor Logger** (free, iOS/Android). Enable **Accelerometer** and **Gyroscope**.
2. Record each activity for **5–10 s** per file:
   - **still** — phone flat on a table
   - **standing** — phone steady at waist level
   - **walking** — consistent pace, phone in hand or pocket
   - **jumping** — continuous jumps
3. Target: **~50 files total** (≥ 1 min 30 s cumulative per activity) for `data/train/`,
   plus **≥ 2 fresh files per activity in a separate session** for `data/test/`.
4. Export as CSV. Two accepted layouts:
   - **Flat CSV** with a time column (`seconds_elapsed` / `time` / `timestamp`) and columns
     `ax, ay, az, gx, gy, gz` (any recognizable accel/gyro column names work), **or**
   - the raw **Sensor Logger export folder** containing `Accelerometer.csv` + `Gyroscope.csv`
     (put the whole folder inside `data/train/`, named like a recording).
5. **Naming convention (required — labels are parsed from it):**
   `<activity>_<member>_<nn>.csv`, e.g. `walking_alice_03.csv`.
6. Note the **native sampling rate of each member's phone** — the notebook prints it per file;
   copy it into the report. All recordings are resampled to a common 50 Hz grid.

## Running

```bash
pip install numpy scipy pandas matplotlib jupyter   # hmmlearn optional
jupyter notebook hmm_activity_recognition.ipynb     # Run All
```

## Task allocation

| Member | Tasks | Approx. share |
|---|---|---|
| _name_ | data collection (activities …), feature extraction | …% |
| _name_ | HMM implementation, evaluation, report | …% |

> Keep this table consistent with the GitHub commit history. Commit incrementally
> (data → features → model → evaluation → report), not in one dump.

## Submission checklist

- [ ] ~50 well-labelled CSVs in `data/train/`, ≥ 2 unseen files per activity in `data/test/`
- [ ] Per-member sampling rates recorded in the report
- [ ] Notebook runs top-to-bottom without errors (`Run All` before committing)
- [ ] Report PDF: 4–5 pages, required section headings, figures captioned
- [ ] Filled course document exported as PDF and added to the repo
- [ ] Balanced, traceable commit history
