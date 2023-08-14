# III. Intermediate

## 1. Chain of Thought Prompting

![Chain of Thought Prompting vs. Standard](https://learnprompting.org/assets/images/chain_of_thought_example-37c925a2720c9c4bb4c823d237bc72c8.png)

- This prompting method is obtained by first feeding the model a few examples (few shot prompting) with the reasoning pattern explained in them.

- **CoT** has shown itself effective in improving results on tasks like arithmetic, commonsense and symbolic reasoning.
  - requires a model have ~100B parameters to get the reasoning right
    - **CoT** improvements are proportional to model size

## 2. Zero Shot Chain of Thought

- Chain of thought without the few shot part
  - achieved by chaining phrases to the end of the prompt
  - `Let's think step by step`
  - improves the same tasks as **CoT**
  - adding the same phrase to content generation can improve the output's length and breadth.

## 3. Self-Consistency

- **Self Consistency** - asking the model the same question multiple times and taking the majority result as the final answer.
  - most powerful when used in conjunction with **CoT**
  - improves the same tasks as **CoT**

## 4. Generated Knowledge

- **Generated Knowledge** - ask the LLM to generate potentially useful information about a subject before generating a final response.
  - This helps gather information on the prompt as well as generates context for the prompt.
  - Methods to approach this with:
    1. Single Prompt Approach - use a single prompt to generate knowledge and the main prompt in a single prompt
       - `Generate 4 facts about the Kermode bear, then use these facts to write a short blog post using the information:`
    2. Dual Prompt Approach - separate the prompt into 2 parts.
    - more effective when using the generated knowledge as part of the final prompt in generating longer content
  - approach comes from need to answer difficult questions more accurately
    - Like **CoT** this forces the LLM to reason out its response step by step
    3. **Knowledge Integration** - Question the user seeks answer is chained together with knowledge generated about the subject
    4. **Recitation Augmented Language Models** - use of multiple Q&A exemplars

## 5. Least to Most Prompting

- **Least to Most Prompting** - breaks problems into sub-problems, each sub-problem building upon the prior. Problems and solutions are separated and done in sequential order. Ultimately, the key is to chain prompts together and get the model to first produce output illuminating the problems and in the second output solve said problems, giving it self-generated context to solve part 2 from part 1.

- **EXAMPLE** Letter Concatenation - sometimes it can be done in a single prompt

```
Q: think, machine
A: The last letter of "think" is "k". The last letter of "machine" is "e". Concatenating "k" and "e" gives "ke". So "think, machine" output "ke".

Q: think, machine, learning
A: "think, machine" outputs "ke". The last letter of "learning" is "g". Concatenating "ke" and "g" gives "keg". So "think, machine, learning" is "keg".

Q: transformer, language
A: The last letter of "transformer" is "r". The last letter of "language" is "e". Concatenating "r" and "e" gives "re". So "transformer, language" is "re".

Q: transformer, language, vision
A: "transformer, language" outputs "re". The last letter of "vision" is "n". Concatenating "re" and "n" gives "ren". So "transformer, language, vision" is "ren".

Q: foo,bar,baz,blip,learn,prompting,world,shaking,event,dancefloor,prisma,giraffe
A:
```

- Advantages of Least to Most Prompting
  1. Improve accuracy over **CoT**
  2. increased generalization on problems harder than those in the prompt
  3. improved performance in compositional generalization (SCAN benchmark)

## 6. What's In a Prompt

- "Ground Truth Matters Little" - when providing few shot style examples, the actual answers (or gold) are not important. Adding random labels barely hurts performance.
- "Labelspace Matters"
  - **labelspace** - all possible labels for a given task
  - providing random labels from the labelspace gives the LLM a better understanding than terms outside of the labelspace
- "Format Matters" - formatting instructs the LLM how best to answer
  - of course, it is concerned with composition and abstracts most of the units of the problem presented effectively as in mathematics or music which both can be used as symbolic languages, as can the linguistics style languages which use human generated sounds to create abstract labels for concepts shared in common between speakers (to varying degrees)
