# Fine_Tune_Llama_2

Llama 2 is a collection of second-generation open-source LLMs from Meta that comes with a commercial license. It is designed to handle a wide range of natural language processing tasks, with models ranging in scale from 7 billion to 70 billion parameters

Llama-2-Chat, which is optimized for dialogue, has shown similar performance to popular closed-source models like ChatGPT and PaLM. We can even improve the performance of the model by fine-tuning it on a high-quality conversational dataset.

Fine-tuning in machine learning is the process of adjusting the weights and parameters of a pre-trained model on new data to improve its performance on a specific task.

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

## Output:

Guanaco is a high-quality dataset that has been used to fine-tune state-of-the-art LLMs in the past. The entire Guanaco dataset is available on Hugging Face and it has the potential to achieve even greater performance on a variety of natural language tasks.

# Conclusion
The tutorial provided a comprehensive guide on fine-tuning the LLaMA 2 model using techniques like QLoRA, PEFT, and SFT to overcome memory and compute limitations. By leveraging Hugging Face libraries like transformers, accelerate, peft, trl, and bitsandbytes, we were able to successfully fine-tune the 7B parameter LLaMA 2 model on a consumer GPU.
