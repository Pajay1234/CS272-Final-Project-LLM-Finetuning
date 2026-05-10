## CS272-Final-Project-LLM-Finetuning

This repository contains the Jupyter Notebook and trained model weights for fine-tuning the Qwen/Qwen2.5-1.5B-Instruct model on the GSM8K dataset. The project explores improving the model's mathematical reasoning capabilities using Supervised Fine-Tuning (SFT) and Group Relative Policy Optimization (GRPO) via Parameter-Efficient Fine-Tuning (PEFT/LoRA).

# Repository Organization

CS272_FinalProject_GRPO.ipynb: The main Jupyter Notebook containing the data formatting, LoRA setup, SFT training loop, GRPO training loop, and customized evaluation functions (Accuracy, Pass@k, CoT tracking, and Self-Correction monitoring).

Model Weight Archives (.zip files): Four zipped directories containing the fine-tuned LoRA adapters, categorized by their training data formulation:

Trained with formatted, preprocessed answers (includes <think> tags):

- qwen-gsm8k-grpo-final.zip

- qwen-gsm8k-sft-final.zip

Trained on raw dataset answers:

- qwen-gsm8k-grpo-final-base.zip

- qwen-gsm8k-sft-final-base.zip

# Setup and Execution Instructions

To run the code and evaluate the models, please follow these steps:

- Open the CS272_FinalProject_GRPO.ipynb notebook in Google Colab
- Download and unzip the four saved-model-weight folders.
- Upload the unzipped folders and place them directly in the root of your Google Drive (the MyDrive folder)
- In the first code cell of the Jupyter Notebook, verify that the drive_save_path_sft and drive_save_path_grpo variables match the names of the folders you uploaded to your Drive.

# Important Loading Constraint

You can only import one fine-tuned model into memory at a time. Once you load one of the GRPO models, you cannot load one of the SFT models or the other GRPO model in the same session. If you wish to test a different model, you must Restart the Runtime in Colab and run the setup cells again, ensuring you only execute the loading cell for the specific model you want to test.

# Evaluations

Depending on the model you currently have loaded, scroll to the corresponding evaluation section in the notebook (e.g., "SFT Training and Eval" or "GRPO Training and Eval"). Run the cell containing the analyze_standard() or analyze_grpo() function call to test the model against the GSM8K validation set. Alternatively, you can run the sample inference cells to see a direct text output from the LLM on a sample math problem.