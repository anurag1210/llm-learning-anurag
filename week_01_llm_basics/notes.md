--RAG : RAG simply consists of augmenting LLMs with a knowledge base and requiring the model to use it in its answer rather than relying on what it may or may not have memorized in its model weights, which is also known as the parametric memory (because it is stored in the model parameters).

RAG helps with reducing hellucinations by limiting the LLM to answer based on the existing chosen data.

--Another way to increase LLM performance is through effective prompting some well known prompting techniques are : 

a.Chain-of-Thought” prompting involves asking the model to think through a problem step by step before coming up with a final answer. The key idea is that the LLMs need this step-by-step additional information to figure things out, as they cannot just think and plan what to say, Asking it to go through the step will allow the model to see what steps it must take before generating the real answer, thus simulating some sort of brainstorming (or planning) before acting

b.“Few-Shot Prompting” is when we show the model examples of the answers we want for a given question (similar to those we expect to ask the model). It’s like showing the model a pattern of how we want it to respond

c.“Self-Consistency” involves asking the same question to multiple versions of the model and then choosing the answer that comes up most often.

In short, good prompting is about guiding the model with clear instructions, breaking down tasks into simpler ones, and using specific methods to improve performance


