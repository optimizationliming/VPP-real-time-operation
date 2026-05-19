# Prediction Code Based on BiLSTM

This repository contains anonymized forecasting code, historical VPP scenario data, and pretrained BiLSTM/LSTM models used for the numerical case studies.

## Structure

- `BiLSTM/`: entry scripts for univariate/multivariate forecasting.
- `data/`: historical VPP scenario data in CSV format.
- `models/`: pretrained model parameters.
- `args.py`, `data_process.py`, `models.py`, `util.py`: required source files.
- `outputs/`: generated prediction results after running the scripts.

## Environment

Install the required packages:

```bash
pip install -r requirements.txt
```

The code is compatible with Python 3.7+ and PyTorch.

## How to run

From the repository root, run one of the following commands:

```bash
python BiLSTM/multivariate_single_step.py
python BiLSTM/multivariate_multi_step.py
python BiLSTM/univariate_single_step.py
```

By default, if a pretrained model exists in `models/`, the script skips training and directly performs prediction. To retrain the model, add:

```bash
python BiLSTM/multivariate_single_step.py --retrain true
```

Prediction results are saved to:

```text
outputs/prediction_results.csv
outputs/prediction_plot.png
```

## Notes

The default target column is the second numeric column in the dataset. Custom target or feature columns can be specified, for example:

```bash
python BiLSTM/multivariate_single_step.py --target_col P_load_MW
```


The default target column is `P_load_MW` when this column exists; otherwise the second numeric column is used.
The default batch size is set to 512 for efficient inference with the pretrained models.
