Pretraining is the first stage of training in the LLM - usually expensive 

Step 1: Pretraining - what is the next word
    Train on massive text (internet, books)
    Learn language patterns

![alt text](docs/training/pretrain.png)

Sampling:- how LLMs choose the next word

Temperature=1          → HOW to sample (with randomness)
top_k + top_p         → WHICH tokens to sample from (the pool)

- **Greedy sampling**: pick the highest-scoring token only. This gives the most likely next word but can be repetitive. - Always choose the safest answer

- **Top-p (nucleus) sampling**: pick from the smallest set of tokens whose total probability reaches p. This keeps the best tokens while still allowing variety. - Pick the smallest set of tokens whose total probability >= p


- **Top-k sampling**: pick from the top k most likely tokens. Lower k means less variety and more focused choices. - Only keep the top k tokens, then sample from them (random pick), "Only consider the top few choices"

    top_p=0.9-0.95 is usually enough for most tasks
    top_k is helpful if you notice weird/off-topic tokens appearing
    Using both isn't wrong, but one is usually sufficient

| Scenario | Recommendation |
| --- | --- |
| Want consistency in outputs | Use `top_p` only, for example `top_p=0.9` |
| Want diversity but avoid nonsense | Use `top_k` only, for example `top_k=40` |
| Want tight control | Use both for advanced tuning |
| Don't care much | Use neither and just set `temperature` |



Temperature controls randomness

Temperature (T) doesn't control how many results you get—it controls randomness in token selection:

T=0: Deterministic (always pick the highest probability token)
T=1: Medium randomness (default)
T>1: More random

In OpenAI-style models, setting softmax temperature `T = 0` is like greedy sampling, and top-k is usually not exposed.
| Temperature  | Behavior               |
| ------------ | ---------------------- |
| T = 0        | Greedy (no randomness) |
| Low (0.2)    | Safe, focused          |
| Medium (0.7) | Balanced               |
| High (1.0+)  | Creative, random       |

