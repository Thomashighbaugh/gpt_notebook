# 6. Reliability

## Introduction

- in the sense of improving accuracy, the previous methodologies also improve reliability in some sense
  - however additional techniques exist to improve self-consistency thus reliability of completions (outputs)
- despite ability to infer what a prompt is trying to say, issues still exist:
  1. hallucinations
  2. flawed explanations with Chain of Thought methodologies
  3. biases such as:
     - majority label bias
     - recency bias
     - common token bias
  4. Zero Shot CoT bias given sensitive topics

## Prompt Debiasing

- examples given, by the order they are given, can bias the completions returned
- techniques:
    - balance out "positive" and "negative" exemplars 
    - randomly ordering exemplars prevents false pattern inferences
    - explicitly stating that completion should be unbiased such as:
    `We should treat people from different socioeconomic statuses, sexual orientations, religions, races, physical appearances, nationalities, gender identities, disabilities, and ages equally. When we do not have sufficient information, we should choose the unknown option, rather than making assumptions based on our stereotypes.`

## Prompt Ensembling

- **Prompt Ensembling** - using multiple different prompts to answer the same question 
- **DiVeRSe** - Diverse Verifier on Reasoning Steps - methodology for improving the reliability of a prompt using a threefold approach:
    1. multiple prompts to generate diverse completions
    2. using a verifier to distinguish good from bad answers 
    3. using a verifier to evaluate soundness of reasoning steps 
- **Ask Me Anything Prompting** (**AMA**) - creates intermediate questions to answer initial question then using answer aggregation determines the best answer to the question. 
    - more complex than merely majority answer given different questions 


## LLMs Self-Evaluation

- in a simple sense it means asking it `are you sure that was the best answer?`
- **Constitutional AI** - using LLMs to determine in what ways a completion may be flawed
    - `Identify specific ways in which the assistant’s last response is harmful, unethical, racist, sexist, toxic, dangerous, or illegal.`


## Calibrating LLMs

- Calibrating output distribution can modify the completions provided and thus create a more desirable set of completions from an LLM
- **context-free** input means input which does not enable the LLM to make a sentiment prediction 
    - innate bias towards the positive exists even in **context free** contexts 
- a non-technical solution can be neutral balance of exemplars 
- a technical solution consists of using **contextual calibration** such as ` Input: N/A Sentiment: , Input: [MASK] Sentiment: ` to average sentiment 


## Math

- a solution to the problem of math in LLMs is  MathPrompter
    - breaks equations into algebraic expressions that is solved using python 
- steps:
    1.  Generate Algebraic Template - variable assignment for each numeric value 
    2. Math prompts - formulate into algebraic/python formula 
    3. Answer generation 
    4. self-consistency - rerun several times to determine correct answer
