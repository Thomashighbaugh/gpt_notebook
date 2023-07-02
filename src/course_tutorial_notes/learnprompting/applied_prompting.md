# IV. Applied Prompting

<!-- vim-markdown-toc GFM -->

- [1. Introduction](#1-introduction)
- [2. Multiple Choice Questions](#2-multiple-choice-questions)
- [3. Solve Discussion Questions](#3-solve-discussion-questions)
- [4. Build ChatGPT from GPT-3](#4-build-chatgpt-from-gpt-3)
- [5. Chatbot + Knowledge Base](#5-chatbot--knowledge-base)
  - [How Chatbot Could Work with GPT-3](#how-chatbot-could-work-with-gpt-3)
  - [Disambiguating Questions with GPT-3](#disambiguating-questions-with-gpt-3)
  - [Problems With Generating Answers With GPT-3](#problems-with-generating-answers-with-gpt-3)
  - [Take Away](#take-away)

<!-- vim-markdown-toc -->

## 1. Introduction

These are end-to-end community walk-throughs where the LLM is utilized in solving some issue or being deployed in some specific way.

Thus, the notes will be more sparse even than the prior notes, which hardly rank among my most voluminous but serve the intended purposes in making the topics easily recalled all at once.

## 2. Multiple Choice Questions

- Solving LSAT questions (I got a 98th percentile score on the 2014 LSAT just saying. No I am not a lawyer, long story where I was struck suddenly by morality...)
- Model getting correct solution depended on providing the term "Let's explain step by step"
  - this increases the verbosity of the model
- When a formula (Bayes) is required to solve the problem, then including `the formula for bayes is` yields the correct answer.
  - remember the chatbot is mathematically challenged, representing a mean average of a population barely literate

## 3. Solve Discussion Questions

- Here the model is being asked to compose 100-700 word responses to questions of the manner common in undergraduate courses.
  - here, including the phrase `Respond to the following:` is inconsistent in output generated
    - instead use something like the following: `Write a highly detailed essay with introduction, body, and conclusion paragraphs responding to the following:`
  - some questions would need to be fleshed out into literate phrases in order to generate an accurate response from the LLM
    - turning `"The Civil War a conflict over expansion? Agree our Disagree and why?"` into `"Explain the causes of the Civil War and whether expansion played a role in the conflict. Include evidence to support your argument."`
      - this can also be prompted to obtain, asking the model `Could you write a better prompt that is more optimal for [LLM] and would produce better results`
  - Iteration of the prompts, **expanding step by step** yields better results than cold prompting
    - you then feed each piece into the prompt, using phrases like `here is what I have so far`

## 4. Build ChatGPT from GPT-3

- ChatGPT is a fine-tuned GPT-3 instance offering a user friendly interface
  - the biggest determinant of the effectiveness of ChatGPT or GPT-3 is good prompting
  - **few-shot** or **in-context learning\*** - providing examples in the prompt
    - the more information incorporated in the prompt the more expansion the model goes through to respond
      - there is a limit to this nonetheless
        - about 3k words
    - using a pre-defined prompt can make the chatbot do things like "therapy" where it asks about a person's day
    - mimic a personality it is provided context for
- example in codeblocks below is in Python (author's choice not mine, common in AI despite being awfully ugly)

```python
chatbot_prompt = """
    As an advanced chatbot, your primary goal is to assist users to the best of your ability. This may involve answering questions, providing helpful information, or completing tasks based on user input. In order to effectively assist users, it is important to be detailed and thorough in your responses. Use examples and evidence to support your points and justify your recommendations or solutions.

    <conversation history> # using python this can be replaced

    User: <user input> # this too
    Chatbot:"""
```

- This will be looped and the variables values thus kept track of

```python
import openai

openai.api_key = "YOUR API KEY HERE"
model_engine = "text-davinci-003"
chatbot_prompt = """
As an advanced chatbot, your primary goal is to assist users to the best of your ability. This may involve answering questions, providing helpful information, or completing tasks based on user input. In order to effectively assist users, it is important to be detailed and thorough in your responses. Use examples and evidence to support your points and justify your recommendations or solutions.
<conversation_history>
User: <user input>
Chatbot:"""


def get_response(conversation_history, user_input):
    prompt = chatbot_prompt.replace(
        "<conversation_history>", conversation_history).replace("<user input>", user_input)

    # Get the response from GPT-3
    response = openai.Completion.create(
        engine=model_engine, prompt=prompt, max_tokens=2048, n=1, stop=None, temperature=0.5)

    # Extract the response from the response object
    response_text = response["choices"][0]["text"]

    chatbot_response = response_text.strip()

    return chatbot_response


def main():
    conversation_history = ""

    while True:
        user_input = input("> ")
        if user_input == "exit":
            break
        chatbot_response = get_response(conversation_history, user_input)
        print(f"Chatbot: {chatbot_response}")
        conversation_history += f"User: {user_input}\nChatbot: {chatbot_response}\n"

main()

```

- and then that tutorial abruptly ends but the takeaways
  - the functionality of the chatbot itself is based on a prompt
  - despite being ugly and painful to implement on NixOS, Python makes interacting in a specific way with GPT-3 easy
  - loop functionality is where the memory is "stored" and it is then all fed to the chatbot, hence the limits of the memory usually

## 5. Chatbot + Knowledge Base

- Despite downfalls, like bias and hallucinations, have a lot of potential in chat bots
- **Intent-based Chatbots** - designed to respond to specific user intents
  - made up of set of sample questions and response, user questions are matched to samples in the parameters
  - drawbacks:
    - large number of sample questions required
    - even similar questions will require different sample questions (intents)
- GPT-3 can utilize a broader set of intents from which to derive the sample responses from user input
  - can leverage knowledge base documents
- **Knowledge Base** - (KB) is information stored as structured and unstructured data, ready to be used for analysis or inference
  - may be composed as a series of documents explaining how to use your products
- Using a **Knowledge Base**, each intent is sourced from your documents instead of a sample question and answer
  - therefore one intent would exist for multiple queries, instead of vice-versa
  - reduces the number of intents that need to be stored and managed considerably
  - biggest hindering factor is the size of text that can be fed to GPT-3 at a time (4k tokens)

### How Chatbot Could Work with GPT-3

- Two Step Process

1.  select appropriate intent for a user question
    - solved by semantic search
      - pre-trained models from the `sentence-transformers` library to assign a score to each document based on user input
        - highest scored document is then fed into GPT-3 for the next step
2.  then leverage GPT-3 for an appropriate answer

    - requiring of course a good prompt
    - once the right document is acquired by the above step, we feed it to GPT-3 for the answer
    - **Prompt Characteristics**

      - **Role Prompting** - heuristic technique that assigns a specific role to AI
        - `As an advanced chatbot named Skippy, your primary goal is to assist users to the best of your ability.`
      - Relevant KB Information - document assigned by prior step

        - > START CONTEXT
          > Login to VideoGram from Website
          >
          > 1. Open your web browser and go to the VideoGram website.
          > 2. Click on the “Login” button located in the top right corner of the page.
          > 3. On the login page, enter your VideoGram username and password.
          > 4. Once you have entered your credentials, click on the “Login” button.
          > 5. You should now be logged in to your VideoGram account.

               > Login to VideoGram from Mobile App
               > 1. Open the VideoGram app on your mobile device.
               > 2. On the main page, tap the “Login” button located in the bottom right corner.
               > 3. On the login page, enter your VideoGram username and password.
               > 4. Once you have entered your credentials, tap the “Login” button.
               > 5. You should now be logged in to your VideoGram account.
               > END CONTEXT

      - Last Messages Between the User and the Chatbot
        - > SKIPPY: Hello, I’m Skippy! How can I help you?
          > USER: I can’t find the login button.
          > SKIPPY:
      - User Question
      - Temperature of `0.7`

### Disambiguating Questions with GPT-3

- with more vague user input like `can't login!`
- prompt:
  > As an advanced chatbot named Skippy, your primary goal is to assist users to the best of your ability.> START CONTEXT
  > Login to VideoGram from Website
  >
  > 1. Open your web browser and go to the VideoGram website.
  > 2. Click on the “Login” button located in the top right corner of the page.
  > 3. On the login page, enter your VideoGram username and password.
  > 4. Once you have entered your credentials, click on the “Login” button.
  > 5. You should now be logged in to your VideoGram account.
  >    Login to VideoGram from Mobile App
  > 6. Open the VideoGram app on your mobile device.
  > 7. On the main page, tap the “Login” button located in the bottom right corner.
  > 8. On the login page, enter your VideoGram username and password.
  > 9. Once you have entered your credentials, tap the “Login” button.
  > 10. You should now be logged in to your VideoGram account.
  >     END CONTEXT
  >     SKIPPY: Hello, I’m Skippy! How can I help you?
  >     USER: Can’t login
  >     SKIPPY:
- GPT-3 will then answer with a question to better understand the user's question such as
  > I’m sorry to hear that. Can you tell me if you are trying to login via the VideoGram website or mobile app?
- **TAKE AWAY** - given the right contextual information, GPT-3 can manage disambiguation

### Problems With Generating Answers With GPT-3

- can generate false information if outside of context
  - won't often happen if the answer is in context
- user input often being short and ambiguous cannot always be effectively queried for in step 1

### Take Away

- can be useful in generating chat bots
- is limited by model hallucinating information not provided in the context
