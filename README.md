## Using Hydra with Weights and Biases

Hydra is a widely used configuaration and experiment management tool developed by Facebook Research. In this repository, we make a minimal implementation of integrating Hydra with [Weights and Biases](wandb.com)

In this repository, we demonstrate how hydra can be used to configure a ML project. Here we reimplement the notebook of the [Group Normalization Report](https://wandb.ai/wandb_fc/GroupNorm/reports/Group-Normalization-in-Pytorch-With-Examples---VmlldzoxMzU0MzMy)
and demonstrate how Hydra can be used to configure the codebase.

## Usage

**NOTE**: This repo relies on a submodule [`normalizations`](https://gist.github.com/captain-pool/5029e7a6e431bc04135de662326ea682)
To properly use the repository clone the repository recursively.
```bash
$ git clone --recursive https://github.com/captain-pool/hydra-example
```
To pull the submodule after cloning:
```bash
$ git submodule update --init
```

### Runing Experiments

For single run (with default architecture):
```bash
$ python3 main.py dataset=mnist
```

For running Hydra-Multirun over different dataset([`dataset/`](configs/dataset)) and architectures ([`experiments/`](configs/experiments))
```bash
$ python3 main.py dataset=cifar10,mnist experiments=group,batch,instance
```

NOTE: Running the codebase creates a project called: `hydra-example` on your W&B account by default. You can configure where to send the runs by editing the [`wandb/defaults.yaml`](configs/wandb/defaults.yaml) configuration file.
