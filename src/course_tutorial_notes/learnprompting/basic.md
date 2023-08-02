# Basics

<!-- toc -->

This is the first section of notes from the [Learn Prompting](https://learnprompting.org) tutorials.

## 1. Introduction

- lesson introduces terminology and techniques

### What is AI?

- AI is a field in which people have created "smart" algorithms that "think" like humans.
  - these algorithms can:
    - write essays
    - solve math problems
    - make art
  - recent improvements have meant it could:
    - write sales emails
    - create news articles
    - win art competitions
- AI is currently revolutionizing industries and will see expanded deployment in everyday lives
- This course interacts with AI in English (or other vernacular languages)
  - this interaction directs the AI to accomplish some task

### Why Should I Care?

- AI can be used to automate numerous tasks, saving hours of work _right now_
  - any task that can be described well enough to the AI can be automated

### Dyno Embeds

- this course offers an interactive learning experience using Dyno Embeds placed throughout the lessons
  - these are AI functions embedded into the HTML page the user can interact with
  - requires using API key from OpenAI, which is free for now
    - which is saved in local storage (**entered**)

## 2. Prompting

- **prompting** - directing an AI how to do a task
- prompts can be a simple instruction or question
  - can also be complex chunks of text featuring numerous - examples of prompting
  - summarizing articles
  - math problem solving

### Prompt Engineering

- sometimes with a basic math problems (and other things) AI is wrong
  - for math problems it is getting wrong, one could add
    - `Make sure your answer is exactly correct`
    - Setting temperature to 0 to remove randomness is also necessary for this task.
- this field answers the need to query AI with the optimal prompts to insure its answers yield the best results on a given task

## 3. Giving Instructions

- instructing the chatbot is done using vernacular English and conforms to the same rules and syntax as interacting verbally with others in everyday life. - the difference is the literal nature of the chatbot, while lower than most machines, is much less developed than the average person

## 4. Role Prompting

- _role prompting_ - prompting technique where prompt begins by telling the AI its role
  - like `you are a lawyer` or `you are a doctor`

### Example 1

```
USER: You are a brilliant mathematician who can solve any problem in the world.
Attempt to solve the following problem:

What is 100*100/400*56?

ASSISTANT: The answer is 1400.
```

- Normally the above without role prompting would have been incorrect

### Roles are Context

- by assigning a role, we provide the AI context on the answer we are looking for
  - role prompting is no longer as effective with newer AIs but highlights a useful point about context

### Additional Examples

```
USER: I want you to act as an etymologist. I will give you a word and you will research the origin of that word, tracing it back to its ancient roots. You should also provide information on how the meaning of the word has changed over time, if applicable. My first request is "I want to trace the origins of the word 'pizza'".

USER: I want you to act as an absurdist. The absurdist's sentences are meaningless. The words used by an absurdist are completely ridiculous. The absurdist does not make commonplace sentences in any way. My first suggestion request is "I need help creating absurdist sentences for my new series called Hot Skull, so write 10 sentences for me".
```

## 5. Few Shot Prompting

- _few shot prompting_ - prompt technique where the model is shown a few examples
  - _shots_ in this context means examples
  - an example is showing it several statements classified as positive or negative then showing it an unclassified statement and asking it to classify it.

### More On Structure

- few shot prompting is useful when the output needs to be structured in a specific way that is difficult to describe to the model
  - showing it the correct format leads to the correct output
  - aids the model's consistency as well

### Variants of Shot Prompting

- shot is a synonym of example here (I reiterate)
- variants
  - 0 shot prompting - no examples are shown to the model
    - most basic form of prompting overall
  - 1 shot prompting - a single example is shown to the model
  - few shot prompting - 2+ examples shown

## 6. Combining Techniques

- one means of creating more complex prompts involves combining the techniques, obviously

## 7. Formalizing Prompts

- the field is ever changing
  - so is the terminology
- this lesson seeks to review common terms that one comes across in the wild working with generative AI

### Parts of a Prompt

- a role
- an instruction/task
- a question
- context
- examples/shots

### Standard Prompts

- **standard prompts** consist solely of a question
  - commonly referenced term
- in context learning means learning without parameter updates to the model

## 8. Chatbot Basics

- GPT-3 has no memory, does not remember what you have asked it prior
  - this is not true of ChatGPT
    - it remembers conversation history
      - making it better for things like customer service
- chatbots can answer questions, provide summaries, analysis and write code just like no-memory models
  - thus they are a significant improvement over their predecessors with significant potential
- to best utilize chatbots and their memory, there are methodologies such as style guidance, descriptors and priming

### Modifying Your Prompt

#### Style Guidance

- asking the model to speak in a certain style
- default style is a moderately formal tone
- at the end of the prompt, adding something like `in a series of limericks` will produce a more interesting answer.
- this takes over from `role prompting` and serves to replace it, as clear in the following example:
  `Write in the style and quality of an expert in [field] with 20+ years of experience and multiple Ph.D.'s. Prioritize unorthodox, lesser known advice in your answer. Explain using detailed examples, and minimize tangents and humor.`

#### Descriptors

- adding adjectives that will shift the tone
  - words like "funny" or "curt" will effect the output of the model

### Priming

- use of earlier prompts to modify hwo the chatbot responds - example of priming with a student and teacher conversation with the instruction set - compared to the unprimed model, giving a list of items in a brief format - output was instead a more rich, paragraph ased description

## 9. Pitfalls of LLMs

- this technology is not perfect and has some recognized failings to keep in mind

### Citing Sources

- LLMs do not have internet access thus cannot cite sources accurately
  - this can be fixed with search augmented LLMs

### Bias

- LLMs are biased towards generating stereotypical responses
  - even with safeguards, they can be offensie

### Hallucinations

- when asked a question it does not know, models typically generate falsehoods
  - sometimes they will state they don't know too

### Math

- LLMs are bad at math
  - fixed by tool augmented LLMs

### Prompt Hacking

- it is possible to trick the LLM into generating desirable content
  - will explain how to make various chemical weapons, drugs, weaponry, explosives, etc.
  - found with quick Google search (scary)

## 10. LLM Settings

- output can be affected by _configuration hyperparameters_
  - an example being how random the response is
  - adjustments can produce more diverse, creative and interesting output
  - different from regular hyperparameters like learning rate, number of layers, hidden size, etc

### Temperature

- configuration hyperparameter
  - controls an image's randomness
    - high temperature = more unpredictale
    - low temperature - more common and conservative output

### Top P

- aka nucleus sampling
  - also controls randomness
  - it sets a probability and selects the top tokens to generate output
    - setting corresponds to percentage of words in probability mass it will select from

### Other Hyperparameters

- others exist such as frequency, presence penalties

### How These Affect Output

- both control the degree of randomness and diversity in the generated text
  - more randomness can also increase chance of nonsense and errors
  - low randomness is needed where accuracy is important

## 11. Understanding AI Minds

- Thousands, maybe even millions of AIs exist.

  - some are better than others
  - different AIs produce different responses when asked the same questions
  - course uses either GPT-3 or ChatGPT
    - GPT-3 is more reproducible but more challenging to access
    - ChatGPT is a chatbot that is less reproducible but easier to interact with

  ### How These AIs Work

  - Made up of artifical neurons
    - the structure of these neurons is the **transformer architecture**
    - the network thus produced is a **neural network** as it replicates neural structures
  - These AIs are just math functions.
    - Instead of `f(x)=x2f(x)=x2`, they are more like `f({thousands of variables}) = {thousands of possible outputs}`.
  - they understand sentences by breaking them into words/subwords called tokens (e.g. the AI might read I don't like as "I", "don", "'t" "like").
    - each token is then converted into a list of numbers, so the AI can process it.
  - they predict the next word/token in the sentence based on the previous words/tokens (e.g. the AI might predict apples after I don't like).
    - Each token they write is based on the previous tokens they have seen and written;
      - every time they write a new token, they pause to think about what the next token should be.
  - they look at every token at the same time. They don't read left to right, or right to left like humans do.

- this is a developing field and the nature of the AI used above is deliberately cynical
- Anthropomorphizing the AI is one way of understanding it and better exploring it.
  - none the less, there is reason to pause and remember that words such as neuron, think and brain are metaphors for what is actually occurring
  - the model is not truly thinking it is a mathematical formula running through human data

### Notes on AI Minds

- [Resource for Learning About How AI Mind Functions](https://www.d2l.ai/)

## 12. Starting Your Journey

- this lesson is about how to find and use resources to contiunue educating one's self on this particular topic.
  - thus is a sort of meta-lesson

### Example Workflow

Assumption: You want to generate an {WHATEVER} with ChatGPT

#### **Step 1**: Research

- Google is your friend
- Resources you have found useful
  - examples include: 1. [Awesome ChatGPT Prompts](https://github.com/f/awesome-chatgpt-prompts) 2. [FlowGPT](https://flowgpt.com/) 3. [r/promptdesign](https://www.reddit.com/r/PromptDesign/) 4. [Learn Prompting Discord](https://discord.gg/learn-prompting)

#### **Step 2** : Experiment

- modify and manipulate the prompt in order to achieve the desired output,
- often this stage will require additional research as well

#### **Step 3:** Get Feedback and Iterate

- continue to improve and expand the prompt in time to make for a more perfect prompt or adapted to the context

> **PERSONAL NOTE** Not sure how people would do this otherwise but maybe that's just because I learned to code using this methodology...
