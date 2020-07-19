# Internal Supplemental Action Measurement

This repo is the source code of the paper:

- An Internal Supplemental Action Measurement to Increase the Gap ofAction Values and Reduce theSensitivity of Overestimation.

It is constructed based on the code of Dopamine framework (https://github.com/google/dopamine ).

## Installation

The installation can refer to the [Instructions](https://github.com/google/dopamine#instructions) of Dopamine. 

First install [Anaconda](https://docs.anaconda.com/anaconda/install/), and create an virtual environment:

```sh
conda create --name dopamine-env python=3.6
conda activate dopamine-env
```

Then, download the source code:

```sh
git clone https://github.com/halleanwoo/Internal-Supplemental-ActionMeasurement.git
```

and install the dependencies (Ubuntu):

```sh
sudo apt-get update && sudo apt-get install cmake zlib1g-dev
pip install absl-py atari-py gin-config gym opencv-python tensorflow==1.15
```

## Start experiment

Run the experiment **without** the Internal Supplemental Action Measurement:

```sh
python -um dopamine.discrete_domains.train \
  --base_dir=/dopamine/result/result_without_M \
  --gin_files='dopamine/agents/dqn/configs/without_M.gin'
```

Run the experiment **with** the  Internal Supplemental Action Measurement:

```sh
python -um dopamine.discrete_domains.train \
  --base_dir=/dopamine/result/result_with_M \
  --gin_files='dopamine/agents/dqn/configs/with_M.gin'
```

The default Atari game in the experiment is Asterix. If you want to run other games, just correct the `atari_lib.create_atari_environment.game_name` of the gin file in `/dopamine/agents/dqn/configs/`.

## Results

The results will saved in the '\result',  and the results can be loaded by the file `/dopamine/colab/utils.py`.

Besides, dopamine also provides a baselines for other Atari games.
