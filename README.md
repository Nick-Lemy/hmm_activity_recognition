# Human Activity Recognition with a Hidden Markov Model

Author: Nick-Lemy Kayiranga

This project infers a person's activity (still, standing, walking, or jumping) from phone
accelerometer and gyroscope data. It uses a Gaussian Hidden Markov Model built from scratch with
numpy, trained with Baum-Welch and decoded with Viterbi. The use case is a low-cost fitness tracker
that separates rest from active movement.

## What is in this repo

```
README.md
hmm_activity_recognition.ipynb   the full pipeline: load, features, HMM, evaluation
data/
    train/   recordings used for training
    test/    unseen recordings, never used in training
```

Each recording is a folder that holds `Accelerometer.csv` and `Gyroscope.csv` from the Sensor
Logger app. The activity label is read from the folder name, for example `walking_03` or
`still_t1`.

The report is written up as a separate PDF and submitted on its own. The notebook produces every
figure used in it.

## The data

- App: Sensor Logger on an iPhone 13 mini.
- Sampling rate: the app default of 100 Hz. Every recording is resampled to a common 50 Hz grid.
- Four activities: still (phone flat on a table), standing (phone at waist level), walking, and
  jumping.
- 50 recordings in total, about 9 seconds each. This gives more than 1 minute 30 seconds per
  activity.
- Split: 42 recordings for training and 8 kept aside as unseen test data (two per activity).

## How to run

```bash
python3 -m venv .venv
.venv/bin/pip install numpy scipy pandas matplotlib jupyter hmmlearn
.venv/bin/jupyter notebook hmm_activity_recognition.ipynb
```

Then run all cells. The notebook loads the data, extracts time and frequency features, trains the
HMM, and prints the evaluation table and figures.

## Results in short

- Baum-Welch converges at iteration 12 using a log-likelihood stopping check.
- On the unseen test data the overall accuracy is about 0.76.
- Walking and jumping are recognised very well (about 0.97 accuracy each).
- Standing is the hardest, because it looks almost the same as still. For a fitness tracker this is
  fine, since both count as rest.

## Notes

- This is an individual submission, so all the work was done by one person.
- The report and the required course document are submitted as separate PDF files.
