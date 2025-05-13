# 🧠 Notes – Week 1 (LLM Foundations)

## 📘 What I Learned

- LLMs are probabilistic next-token predictors trained on massive corpora.
- Transformers use self-attention to handle sequences in parallel.
- Tokens are not words — a single word can be multiple tokens.

## 🧠 Key Takeaways

- Prompt engineering significantly impacts LLM behavior.
- Understanding temperature, max tokens, and top_p is crucial for output control.
- Clear and role-based prompts improve response quality.

## ❓ Open Questions

- How does the LLM manage context overflow?
- What's the tradeoff between few-shot prompting and fine-tuning?
- How much does token count impact cost and performance?

## 💡 Personal Reflections

- Writing prompts helped solidify my mental model of how the LLM thinks.
- Loved the visual explanation of transformers by Jay Alammar.
- Still need to experiment more with OpenAI parameters like frequency_penalty.


--RAG : RAG simply consists of augmenting LLMs with a knowledge base and requiring the model to use it in its answer rather than relying on what it may or may not have memorized in its model weights, which is also known as the parametric memory (because it is stored in the model parameters).

RAG helps with reducing hellucinations by limiting the LLM to answer based on the existing chosen data.

--Another way to increase LLM performance is through effective prompting some well known prompting techniques are : 

a.Chain-of-Thought” prompting involves asking the model to think through a problem step by step before coming up with a final answer. The key idea is that the LLMs need this step-by-step additional information to figure things out, as they cannot just think and plan what to say, Asking it to go through the step will allow the model to see what steps it must take before generating the real answer, thus simulating some sort of brainstorming (or planning) before acting

b.“Few-Shot Prompting” is when we show the model examples of the answers we want for a given question (similar to those we expect to ask the model). It’s like showing the model a pattern of how we want it to respond

c.“Self-Consistency” involves asking the same question to multiple versions of the model and then choosing the answer that comes up most often.

In short, good prompting is about guiding the model with clear instructions, breaking down tasks into simpler ones, and using specific methods to improve performance
**
Tokenization is the initial phase of interacting with LLMs. It involves breaking the input text into smaller pieces known as tokens. Tokens can range from single characters to entire words, and the size of these tokens can greatly influence the model’s performance. Some models adopt subword tokenization, breaking words into smaller segments that retain meaningful linguistic elements**

--Embeddings are a way to translate tokens, which are words or pieces of words (or rather their numerical IDs), into numbers that the computer can manipulate. They play a key role in helping the model understand the relationships among words making up a statement. This is made possible by the attention mechanism, as we see later in the discussion about attention.

--An embedding gives each token a unique numerical ID (a vector in a multi-dimensional space) that captures its meaning. While the absolute positions of those vectors themselves don’t have specific meanings, the spatial distance among the vectors reflects, in certain ways, the relationships among the vectors. For example, words like “happy” and “joyful”, while different, are relatively close embeddings in the embedding space.

--Initially, every token is assigned a random vector as its embedding. As the model is trained—meaning as it reads and learns from a large volume of text—it adjusts these numbers. The goal is to tweak them such that tokens with similar meanings end up with similar sets of numbers. This adjustment is done automatically by the model as it learns from different contexts in which the tokens appear.

simple explaination via chat gpt :

magine Every Word Starts as a Random Dot on a Map

At the very beginning of training, the model doesn’t know what “cat”, “dog”, or “banana” means.
So it just gives each word a random set of numbers — like placing dots randomly on a map.

“cat” → somewhere in the top-left
“banana” → bottom-right
“friend” → middle of the map

Right now, these positions don’t mean anything.

⸻

🏋️ But Then the Model Starts Reading Sentences…

“The cat sat on the mat.”
“A dog barked at the cat.”
“She ate a banana.”
“My best friend helped me.”

As it sees words used in context, it starts learning:
	•	“Hey, ‘cat’ and ‘dog’ often show up in similar types of sentences.”
	•	“Hmm, ‘banana’ shows up near words like ‘eat’, ‘fruit’, and ‘apple’.”
	•	“‘Friend’ is often used with people, emotions, help.”

So it starts adjusting the dots (vectors). It nudges them closer or further apart.

⸻

🎯 The Goal:

Move similar words closer together on this “meaning map,”
and push unrelated ones further apart.

	•	“cat” and “dog” slowly move closer
	•	“banana” moves toward “fruit”
	•	“friend” moves toward “kindness”, “help”, etc.
	•	“cat” and “banana” move apart

⸻

🔁 All of this happens automatically.
	•	It’s not hand-coded.
	•	The model updates the embeddings through backpropagation during training.
	•	After millions of sentences, these embedding vectors become incredibly rich representations of meaning.



# 📓 Anurag's LLM Q&A Notebook

This notebook contains answers to key foundational LLM concepts we've explored so far.

---

## 🧠 What is an RNN in simple terms?

RNN (Recurrent Neural Network) is like reading a sentence word-by-word, remembering past words to understand the next one. It's sequential, meaning it learns one step at a time and passes a memory forward. But it struggles with long sequences and forgets old information easily.

---

## 🧠 What is the vanishing gradient problem?

It’s like playing Chinese whispers: when you try to pass learning signals backward through many steps, they shrink too much, and the early steps learn nothing. That’s why RNNs struggle to remember things far back in time.

---

## 🧠 Did Transformers replace RNNs?

Yes. Transformers process all words at once using self-attention and solve vanishing gradients, memory, and scalability problems. They're now the standard in NLP and LLMs.

---

## 🧠 What is the Transformer architecture in simple terms?

Transformers look at the entire sentence all at once using self-attention. For each word, they ask, “which other words should I pay attention to?” This lets them understand context and relationships without forgetting.

---

## ⚠️ Limitations of Transformers

- Fixed context size (limited memory per input)
- Expensive to train and run (quadratic scaling)
- No true long-term memory
- Prone to hallucination
- Hard to explain how they work internally

---

## 🧠 What are Embeddings in LLMs?

Embeddings are like “meaning maps” for words. Each word is turned into a vector. Similar meanings = vectors that are close. Used in search, RAG, semantic similarity, and more.

---

## 🧠 How are embeddings trained?

Initially, each token gets a random vector. As the model reads more text, it nudges those vectors based on how words are used in context. Over time, similar words move closer together on the “meaning map.”

---

## 🧠 What is context size in LLMs?

Context size = how many tokens the model can see at once. It’s like the model’s short-term memory. GPT-3.5 has 4k tokens, GPT-4 Turbo has 128k, Claude has 200k. Once you go over, the model forgets earlier tokens.

---

## 🧠 Why are embeddings so powerful compared to rule-based systems?

The advantage of using embeddings is that they enable the models to capture the nuances of human language, such as:
- Multiple meanings of the same word
- Word meaning depending on context
- Flow and coherence of a sentence

This was not possible in older rule-based systems, which relied on manually defined grammar and word lists. It is practically impossible to heuristically capture all the subtle ways meaning is formed in real human communication. Embeddings let the model learn those patterns from data — automatically and deeply.

---

## 🧠 How does the model know whether to bring word embeddings closer or push them apart?

The model doesn't "know" in a human sense. It just learns by adjusting itself based on mistakes. Here's how:

When it predicts the wrong word (e.g., "hat" instead of "mat"), it calculates a "loss" — a score showing how wrong it was. Then it uses backpropagation to figure out which parts of the network (including the embeddings) contributed to that mistake.

- If "hat" caused the wrong output, its embedding is pushed away from the context.
- If "mat" would have reduced the loss, its embedding is pulled closer to the context.

This happens automatically using gradients — small mathematical nudges that tell the model how to reduce future errors. Over time, words that appear in similar contexts are moved closer together, even though the model never understands their meaning — it just learns from the structure of language through feedback.

---


# 📓 Anurag's LLM Q&A Notebook

This notebook contains answers to key foundational LLM concepts we've explored so far.
...

---

## 🧠 Is ChatGPT learning when I give it a sentence like "The cat sat on the..."?

No — ChatGPT is **not learning from your input**. The model was already trained before you used it.

Here's how it works:

- During **training**, the model learned language patterns by reading billions of sentences. It adjusted weights and embeddings based on how well it predicted the next word at each step.
- During **inference** (when you use ChatGPT), it's just **applying what it learned** to predict the next token.

So when you type "The cat sat on the", it's not learning — it's simply guessing the next most likely word based on patterns it saw during training.

✅ In summary: ChatGPT is not training on your input. It uses what it learned to generate predictions — no weights are changed, and no new learning is happening during inference.

---

CLM is more “natural” because it generates text one word at a time, just like humans do.
MLM (like BERT) learns from artificially masked sentences, which is less realistic.

Let’s bring it to life:

⸻

🗣️ Imagine You’re Speaking:

“I went to the __ yesterday to buy some groceries.”

You think of a word to fill the blank:

“store”

You didn’t see [MASK] — you just remembered your sentence from left to right, sequentially.

That’s what CLM does.

⸻

🤖 Compare How GPT (CLM) Handles It:

Why would [MASK] even be there during training? Aren’t we training on real sentences?”

✅ Yes — BERT is trained on real sentences…

But the [MASK] token is intentionally added during training as part of a training trick called Masked Language Modeling (MLM).

Let’s break it down:

⸻

🧪 How BERT Training Works:

Let’s say the original sentence is:

"The cat sat on the mat"

BERT doesn’t just train on this raw sentence.

Instead, it creates a self-supervised task by modifying the sentence:

👉 It randomly replaces some words with [MASK]:

"The cat [MASK] on the mat"

And now the training task is:

“Hey model, try to guess what the [MASK] word is.”

📌 This is done intentionally to:
	•	Simulate a “fill-in-the-blank” task
	•	Teach the model to understand meaning from context on both sides


  But You’re Right to Wonder:

“But real-world sentences don’t have [MASK], right?”

Exactly!

⚠️ This is the drawback of BERT:
	•	During training, it sees [MASK] tokens.
	•	During inference (real-world use), there are no [MASK] tokens.

This is called a pretrain–fine-tune mismatch.

That’s one reason why GPT (which never uses [MASK]) is better for generating natural language — because it’s trained the same way it’s used.

BERT (MLM)
GPT (CLM)
Adds [MASK] to real sentences
Uses real sentences as-is
Trains on “fill in the blank” tasks
Trains to predict next word
Good for understanding/context tasks
Good for generation and conversation
Real sentences are altered during training
Real sentences stay untouched


The [MASK] token in BERT is artificially added during training to create a learning problem.
It helps BERT learn to understand context — but makes it less natural at generating text compared to GPT.


# 📓 Anurag's LLM Q&A Notebook

This notebook contains answers to key foundational LLM concepts we've explored so far.
...

---

## 🧠 What is LLaVA and how does it work (diagram explanation)?

LLaVA (Large Language and Vision Assistant) is a multimodal model that combines vision and language understanding. Here's a breakdown of how it works:

### 🖼️ Input: An image is given to the model

### 🔍 Step 1: CLIP Visual Encoder
CLIP acts like the model's eyes. It "looks" at the image and turns it into a vector of features — a numerical summary of what's in the image (like shape, texture, color, etc.).

### 🔁 Step 2: Linear Projection Layer (W)
This is a translator. It takes the visual features and reshapes them to match the **word embedding space** of the language model. That way, the language model can treat the visual info like it's part of a sentence.

### 🧠 Step 3: Vicuna Language Model
Now that the image has been turned into "word-like" tokens, Vicuna (a ChatGPT-style LLM) can read and reason over them — just like it would with regular text.

### 🗣️ Step 4: Output
The model generates text based on the image. Example:  
> "A cat is sitting on a wooden table."

### ✅ Summary:
LLaVA = CLIP (for vision) + Vicuna (for language), connected via a simple linear projection. Once image features are embedded like words, the language model takes over and does the rest.

---







