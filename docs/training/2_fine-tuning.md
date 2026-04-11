Finetuning is training the LLM to do a particular task. 



## Instruction Tuning- training a model to follow human instructions

    Step 2: Instruction tuning- 'template important'

    Train on data like (like a jsonl formate):

    Instruction: Summarise this text
    Input: long paragraph
    Output: short summary

    Model learns:

        what the task is
        how to respond properly

    ## Instruction tuning format

    Many instruction-tuned models use special tokens to separate roles and text:

    - `|begin_of_text|` marks the start of the whole prompt.
    - `|start_header_id|` and `|end_header_id|` wrap the role labels like `system`, `user`, or `assistant`.
    - `|eot_id|` marks the end of each message.

    That means the model sees a structured conversation like (three roles: system, user, and assistant):

    - system message: what the assistant should do
    - user message: the question or instruction
    - assistant message: the response

    This helps the model know:

    - when the instruction starts
    - who is speaking
    - when one message ends and the next begins

    Using these special tokens makes instruction-following more reliable and easier for the model to learn.

## LoRA - Low-Rank Adaptation

    LoRA is a parameter-efficient fine-tuning technique that freezes the original model weights and introduces small low-rank matrices to adapt the model to new tasks, significantly reducing training cost and memory usage.

    ## The LoRA Equation

    ```
    W_ft = W_pt + (α/r) × A × B
    ```

    where:
    - `W_ft` is the fine-tuned weight matrix
    - `W_pt` is the original pretrained weight matrix
    - `α` is the scaling factor (controls how much the adaptation affects the result)
    - `r` is the rank (inner dimensions of A and B - determines model capacity)
    - `A` and `B` are small low-rank matrices being trained

    ## How it works

    - **Keep pretrained weights frozen**: The original model `W_pt` doesn't change
    - **Add small updates**: Instead of tuning all weights, train two small matrices A and B
    - **Combine them**: The final weight is the original plus a scaled combination of A and B
    - **Much fewer parameters**: If the model has millions of parameters, LoRA only trains thousands

    For example:
    - Original weight matrix: 1000 × 1000 = 1 million parameters
    - A: 1000 × 8, B: 8 × 1000 = 16,000 parameters to train (99.98% fewer!)

    ## Key decisions

    - **α (scaling factor)**: Higher α means the fine-tuning adapts more strongly. Must be tuned for each task.
    - **r (rank)**: Higher r gives more flexibility but uses more memory. Common values: 4-64

Quantization and QLoRA: memory efficient, but slower than QLoRA
    Quantization = compress numbers--Model stored as compressed (small)
    example: float32 → 32-bit (high precision)
            int8    → 8-bit (compressed)    
    int8 → float32 (dequantization): GPUs compute better in float, math needs precision
    Fly dequantization: use compressed weights → convert only when computing: On-the-fly dequantization = decompress weights only when you need them during computation

## Frameworks

Popular libraries and tools for fine-tuning LLMs:

- **HuggingFace Transformers**: The main library for loading pretrained models and fine-tuning. Easy-to-use API with support for most popular models.
- **PEFT (Parameter-Efficient Fine-Tuning)**: Implements LoRA, QLoRA, and other parameter-efficient methods. Works seamlessly with HuggingFace.
- **PyTorch**: Low-level deep learning framework. Used under the hood by transformers and PEFT. For advanced users.
- **Ollama**: Lightweight framework to run and fine-tune models locally.
- **LLaMA-Factory**: Specialized tool for fine-tuning LLaMA models with support for LoRA and other methods.

**Common workflow:**
1. Load pretrained model with HuggingFace Transformers
2. Set up LoRA with PEFT library
3. Train on your data using PyTorch
4. Save and test the fine-tuned model

