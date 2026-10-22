# ai_from_scratch

best way to learn is to build, so building from scratch in line with the historical development

## path

| # | Notebook | What I built | Data |
|---|----------|--------------|------|
| 1 | [`linear_regression`](linear_regression.ipynb) | A single neuron learning a straight line, plus why least squares falls out of maximum likelihood | Made-up projectile data |
| 2 | [`logistic_regression`](logistic_regression.ipynb) | Pass/fail classification with sigmoid + binary cross-entropy, gradient worked out by hand | Made-up study hours + sleep |
| 3 | [`activation_functions`](activation_functions.ipynb) | Sigmoid, tanh, the ReLU family and softmax: stable versions, derivatives, plots | — |
| 4 | [`nn_from_scratch`](nn_from_scratch.ipynb) | My first full network with backprop, one neuron object at a time, pure Python | XOR |
| 5 | [`nn_from_scratch_np`](nn_from_scratch_np.ipynb) | Same network, vectorised with NumPy, checked against PyTorch | XOR |
| 6 | [`fixed_feature_cnn_from_scratch`](fixed_feature_cnn_from_scratch.ipynb) | A CNN with three hand-picked kernels (edge detectors + sharpen) feeding my pure-Python network | MNIST |
| 7 | [`learnable_feature_cnn_from_scratch`](learnable_feature_cnn_from_scratch.ipynb) | Conv, max-pool and dense layers with full backprop, so the kernels learn too | MNIST |
| 8 | [`rnn_from_scratch`](rnn_from_scratch.ipynb) | A vanilla RNN trained with backprop through time | Seattle weather, 2012–2015 |

[`tutorials/`](tutorials/) is just me following the official PyTorch quickstart and tensors tutorials, not my own work.

## How it went

| Model | Task | Result | Baseline to beat |
|-------|------|--------|------------------|
| Linear regression | Recover `range = (2/9.81)·energy + 29` | w = 0.205, b = 29.0 | True: 0.2039, 29 |
| Pure-Python + NumPy NNs | XOR | All 4 correct | — |
| Fixed-feature CNN | MNIST | **94.46%** test | 11.35% (always guess "1") |
| Learnable CNN | MNIST | **92.25%** test | 11.35% (always guess "1") |
| Vanilla RNN | Tomorrow's weather (5 classes) from the past week | **59.15%** test | 47.4% (always guess "sun") |

## setup

```bash
git clone https://github.com/op-poyo/ai_from_scratch.git
cd ai_from_scratch
pip install -r requirements.txt
jupyter notebook
```

## datasets
The datasets aren't in the repo (`data/` is gitignored), so grab them and put them here:

```
data/
├── mnist/
│   ├── mnist_train.csv
│   └── mnist_test.csv
└── seattle_weather.csv
```

- **MNIST:** [MNIST in CSV on Kaggle](https://www.kaggle.com/datasets/oddrationale/mnist-in-csv). One row per image: the label, then 784 pixel values (0–255), with a header row. 60,000 train, 10,000 test.
- **Seattle weather:** [`seattle-weather.csv` from vega-datasets](https://github.com/vega/vega-datasets/blob/main/data/seattle-weather.csv). Save it as `data/seattle_weather.csv`. Daily rain, max/min temp, wind and a weather label for 1,461 days.

The PyTorch tutorials download FashionMNIST on their own into `tutorials/data/`.