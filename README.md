# Multi-objective Prompt Optimization for Clinical Case Summarization

This repository contains the code for clinical (biomedical) summarization experiments on the **MULTICLINSUMM "GOLD"** dataset. It compares several prompt-optimization strategies — **APO**, **ISP**, **Zero-Shot**, and genetic/multi-objective prompt search (**Worst-to-Good**, **Good-to-Good**, **MultiGood**) — across four open LLMs (`qwen2.5`, `qwen3`, `ministral_8b`, `llama3.1_8b`), reporting ROUGE-L-F1, BERTScore-F1, a combined summarization score and grammar Score.
## Required Setup

1. **WandB Key:** Set up your own [Weights & Biases](https://wandb.ai/) account and add your API key in the notebook/code (used by the genetic-search notebooks in `Worst to Good/`, `Good to Good/`, and `MultiGood/`).
2. **API Keys & Tokens:**
   * Add your Hugging Face token (required for the gated models `llama3.1_8b` and `ministral_8b`; `qwen2.5` and `qwen3` are open).
   * Add any other required API keys (e.g., for model access).
3. **Initial Prompt:** The initial prompt needs to be chosen by the user based on the scenario (Good-to-Good, Worst-to-Good, etc.) they want to run. For **MultiGood**, the user has to generate different paraphrases equivalent to the population size and add them at the required place (the initial population list).
4. **Parameter Configuration:** Change the following parameters in the code:
   * Population size
   * Number of instances to be taken
   * Number of iterations
   * Number of operations
   * Patience criteria
   * WandB file names
5. **Kaggle Path:** Set up the correct Kaggle dataset path in the notebook/code (point it to your `Data/Short` folder containing `fulltext/` and `summaries/`).

## Note for Model Selection

* In the standalone notebooks (`APO.ipynb`, `ISP_Code.ipynb`, `ZeroShot_Code.ipynb`), switch between models by changing the single `SELECTED_MODEL` parameter:
   * `SELECTED_MODEL="qwen2.5"` for Qwen2.5-7B
   * `SELECTED_MODEL="qwen3"` for Qwen3-8B
   * `SELECTED_MODEL="ministral_8b"` for Ministral-8B
   * `SELECTED_MODEL="llama3.1_8b"` for Llama-3.1-8B
* In the genetic-search folders (`Worst to Good/`, `Good to Good/`, `MultiGood/`), the model is fixed per file — just open the notebook for the model you want (`llama`, `ministral`, `qwen2-5`, `qwen3`).

Update the value in your script or notebook as needed.

## Instructions

* Before running, ensure all required keys and tokens are set.
* Adjust parameters for your experiments as needed.
* Refer to comments in the code for locations to update prompts, keys, and parameters.
* Run all cells top to bottom; results (CSVs, best prompt, metrics JSON, and plots) are written to the working directory / `logs` folder.

We have also given the dataset for you to use. It is in zip format, You can find the clincial cases in fulltext and the corresponding summary in the Summaries folder.
