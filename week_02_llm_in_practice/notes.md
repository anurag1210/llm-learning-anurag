RAG: Retrieval-augumented generation (RAG) is a technique for enhancing the capabilities of language models by adding data from external sources.This information is combined with the contect already included in the model's prompt, allowing the model to offer more accurate and relevant responses.

Reinforcement Learning from Human Feedback (RLHF): The RLHF approach trains models incrementally to align with human feedback across multiple iterations. This approach can be more effective than SFT as it facilitates continuous improvement based on human input. Similar methodologies include Direct Preference Optimization (DPO) and Reinforcement Learning from AI Feedback (RLAIF).

Instruction Fine-tuning trains a model to follow human instructions, not just generate text, it transform a generic language model into a helpful assistant that understands tasks and acts accordingly.



---

## 🧠 What is the Perplexity Evaluation Metric?

Perplexity is a metric used to evaluate how well a language model predicts the next word in a sequence.

### 🔍 Intuition:
- If the model is **confident and correct**, it has **low perplexity**.
- If the model is **surprised or often wrong**, it has **high perplexity**.

### 📏 Formula (simplified):
```text
perplexity = exp(- (1/N) * sum(log(P(true_token))))
```
This calculates the average log-likelihood of the true tokens, then converts it into an easier-to-understand scale.

### 🧪 Example:
- If the model thinks "mat" has a 90% chance and the real word is "mat" → Low perplexity (good!)
- If the model thinks "mat" is 10% and it's the actual word → High perplexity (bad!)

### ✅ Rule of Thumb:
| Model Type       | Perplexity |
|------------------|------------|
| Small models     | < 100      |
| GPT-2            | ~20–30     |
| GPT-3 / LLaMA    | < 10       |

### 🎯 Use Cases:
- Used during model training to measure progress
- Lower perplexity generally means better fluency and understanding
- Not always a good standalone metric for tasks like summarization or chat

### ✅ TL;DR:
Perplexity tells you how “surprised” the model is when it sees the correct next word.  
**Lower = better.**

---

