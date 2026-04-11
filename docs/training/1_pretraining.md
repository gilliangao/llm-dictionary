Pretraining is the first stage of training in the LLM - usually expensive 

Step 1: Pretraining - what is the next word
    Train on massive text (internet, books)
    Learn language patterns

![alt text](docs/training/pretrain.png)

Sampling:- how LLMs choose the next word

- **Greedy sampling**: pick the highest-scoring token only. This gives the most likely next word but can be repetitive. - Always choose the safest answer
- **Top-p (nucleus) sampling**: pick from the smallest set of tokens whose total probability reaches p. This keeps the best tokens while still allowing variety. - Only keep the top k tokens, then sample from them (random pick), “Only consider the top few choices”
- **Top-k sampling**: pick from the top k most likely tokens. Lower k means less variety and more focused choices.- Pick the smallest set of tokens whose total probability ≥ p

Temperature controls randomness
In OpenAI-style models, setting softmax temperature `T = 0` is like greedy sampling, and top-k is usually not exposed.
| Temperature  | Behavior               |
| ------------ | ---------------------- |
| T = 0        | Greedy (no randomness) |
| Low (0.2)    | Safe, focused          |
| Medium (0.7) | Balanced               |
| High (1.0+)  | Creative, random       |


