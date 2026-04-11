# Interacting with LLMs

How we communicate with AI models - the complete journey from human language to model output.

## The Interaction Pipeline

```
Human Language → Format with Roles → Tokenizer → LLM Processing → Generate Tokens → End Token
```

## Step-by-step breakdown

**1. Human Language**
- You write your question or instruction in natural language
- Example: "Summarize this article for me"

**2. Format with Roles (Chat Template)**
- Structure the message with roles (system, user, assistant)
- Often stored in JSONL format for fine-tuning or API calls
- Example format:
  ```
  {
    "messages": [
      {"role": "system", "content": "You are a helpful assistant"},
      {"role": "user", "content": "Summarize this article for me"}
    ]
  }
  ```
- This helps the model understand context and who is speaking

**3. Tokenizer**
- Converts text into tokens (numbers the model understands)
- Each word or subword becomes a number
- The model works with these numbers, not raw text

**4. LLM Processing**
- The model reads all the tokens
- Uses attention mechanisms to understand relationships
- Generates probabilities for the next token

**5. Token Generation**
- Model predicts the most likely next token (using sampling like greedy, top-p, or top-k)
- Keeps generating one token at a time
- Each new token is added to the context

**6. End Token**
- Model generates a special "end of sequence" token
- Signals that the response is complete
- Example: `|end_of_text|` or `<|endoftext|>`

**7. Convert Back to Human Language**
- Tokens are decoded back into readable text
- The final response is returned to you

## Real Example

User input: "What is 2+2?"

→ Formatted: `{"role": "user", "content": "What is 2+2?"}`

→ Tokenized: `[1234, 5678, 910, 1112]` (simplified)

→ LLM generates: token for "The", then "answer", then "is", then "4", then end token

→ Result: "The answer is 4"
