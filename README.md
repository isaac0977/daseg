# Daseg

A library for working with dialog acts.



## Installation

In my experience, I found using venv was easier than anaconda

Installing requirements and downloading datasets:

```bash
git clone https://github.com/isaac0977/daseg.git
cd daseg


# Installs the rest of requirements from pip
pip install -r requirements.txt 

# Downloads and "installs" SWDA and MRDA
./install.sh

# Installs daseg in your python env so that you can "import daseg"
# "-e" means that if you can modify the code in this directory,
# and the changes are visible next time you import without re-installation
pip install -e .
```

## Preparing the dataset

Use this Colab page (needs a columbia.edu account)

https://colab.research.google.com/drive/1A9KGLSVo9s5nYn1UWbs0Re87HsPSuIuZ?usp=sharing

Adjust the location of the textgrids in the second cell.

FILEPATH = '/content/drive/My Drive/SWBD_aeneas/fixed_textgrids_42_tags/'


Once you run all the cells, it should output a `labels.pkl` and `dataset.pkl`. Move these under `daseg/exp-swda-longformer-512` directory.


## Running the experiments

Experiments can be run using dasg CLI:

```bash
# Run actual training for 10 epochs, with batch size 10, 1 GPU and half-precision.
$ dasg train-transformer exp-swda-longformer-512 -e 10 -g 1 -b 10 -f
# Run model evaluation on the test split with the checkpoint from epoch 9, displaying progress bar.
$ dasg evaluate 'exp-swda-longformer-512/checkpointepoch=9.ckpt' --device cuda -b 1 -o exp-swda-longformer-512/results.pkl -v
```
