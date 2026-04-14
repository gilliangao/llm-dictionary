Perplexity = how “confused” the model is when predicting text
    Low perplexity → model is confident
    High perplexity → model is uncertain

Equation
    Perplexity = exp(-1/N * sum(log P(word_i)))

In normal words
    It measures how surprised the model is by the correct next word
    Lower perplexity = better predictions
    Higher perplexity = more guessing

Perplexity ≈ 1.1

    almost no confusion

Perplexity ≈ 5

    model is confused between 5 options
