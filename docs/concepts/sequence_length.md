Sequence length = how many tokens are in your input (or output)
    Every model has a maximum sequence length:

        GPT-3: ~2048 tokens
        GPT-4 / newer: much larger
        If you exceed it → input gets cut

    Computation cost:
        O(n²)   - n = sequence length
        
    More tokens → more GPU memory
