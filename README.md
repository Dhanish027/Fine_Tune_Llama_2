# Fine_Tune_Llama_2

We will reformat our instruction dataset to follow Llama 2 template.
Orignal Dataset: https://huggingface.co/datasets/timdettmers/openassistant-guanaco
Reformat Dataset following the Llama 2 template with 1k sample: https://huggingface.co/datasets/mlabonne/guanaco-llama2-1k
Complete Reformat Dataset following the Llama 2 template: https://huggingface.co/datasets/mlabonne/guanaco-llama2
To know how this dataset was created, you can check this notebook.

https://colab.research.google.com/drive/1Ad7a9zMmkxuXTOh1Z7-rNSICA4dybpM2?usp=sharing

## Note:
You don’t need to follow a specific prompt template if you’re using the base Llama 2 model instead of the chat version.

## How to fine tune Llama 2
Free Google Colab offers a 15GB Graphics Card (Limited Resources --> Barely enough to store Llama 2–7b’s weights)
We also need to consider the overhead due to optimizer states, gradients, and forward activations
Full fine-tuning is not possible here: we need parameter-efficient fine-tuning (PEFT) techniques like LoRA or QLoRA.
To drastically reduce the VRAM usage, we must fine-tune the model in 4-bit precision, which is why we’ll use QLoRA here.

## Step 3
!.Load a llama-2-7b-chat-hf model (chat model)
2.Train it on the mlabonne/guanaco-llama2-1k (1,000 samples), which will produce our fine-tuned model Llama-2-7b-chat-finetune
3.QLoRA will use a rank of 64 with a scaling parameter of 16. We’ll load the Llama 2 model directly in 4-bit precision using the NF4 type and train it for one epoch
