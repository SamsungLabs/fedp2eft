# [FedP²EFT: Federated Learning to Personalize PEFT for Multilingual LLMs](https://arxiv.org/abs/2502.04387)

#### Update (7 Nov 2026): FedP²EFT is accepted @ AAAI-26.

#### Note: If you find this project useful, please check out our other related FL research: [FedL2P (NeurIPS'23)](https://github.com/royson/fedl2p) and [ReeFL (ICML'24)](https://github.com/royson/reefl).

## Environment

```
conda create -n fedp2eft python=3.10
conda activate fedp2eft
pip install -r requirements.txt
```

## General Usage

This codebase is modified from [FedL2P](https://github.com/royson/fedl2p). Please refer to FedL2P for instructions on general usage. 

## Configs

All configs are stored in `configs`. Please modify `server.yaml` in `configs/fedaya`, `configs/masakha`, and `configs/xnli` with your own system paths. Additionally, modify `configs/xnli/ft_dept.yaml` and `configs/xnli/ft_feddpa.yaml` with your own system paths for experiments with existing pFL methods.

By default, we use wandb to log our experiments. Please modify `wandb.entity` in `configs/default.yaml` with your own entity.

## Datasets

All datasets are to be placed in `data.args.path_to_data`. Data is automatically partitioned in `data.args.dataset_fl_root`.

- XNLI - automatically downloads to `data.args.path_to_data` 

- MasakhaNEWS - automatically downloads to `data.args.path_to_data` 

- Fed-Aya - download from [FedLLM-Bench](https://github.com/rui-ye/FedLLM-Bench), unzip, and place in `data.args.path_to_data`

## Train & Evaluation

In FedP²EFT, the <em>base model</em> refers to the initial model(s) used for FL personalization; the model(s) to learn a personalization strategy generator (PSG) with. For more details, please refer to the setup found in the Evaluation section in our paper. We provide the following scripts to reproduce all results found in our paper:

- run_xnli.sh - <em>base model</em> includes mBERT further trained with standard FL

- run_xnli_pfl.sh - <em>base model</em> includes mBERT further trained with existing personalized FL approaches 1. FedDPA-T and 2. DEPT (SPEC)

- run_maskha.sh - <em>base model</em> includes mBERT further trained with standard FL

- run_fedaya.sh - <em>base model</em> includes 1. MobileLLaMA-1.4B further trained with standard FL and 2. off-the-shelf Llama-3.2-3B-Instruct

Note: Set the maximum GPU memory allocated for each client by overwriting argument `vram`.

## Licenses

The license for our code can be found in [LICENSE](LICENSE). We used code from [Transformers](https://github.com/huggingface/transformers), [PEFT](https://github.com/huggingface/peft), [Evaluate](https://github.com/huggingface/evaluate), [Flower](https://github.com/adap/flower), and [learn2learn](https://github.com/learnables/learn2learn), all of their licenses can be found [here](LICENSES).
