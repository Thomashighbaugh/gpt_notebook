# V. Advanced Applications

## 1. Introduction

- this section covers more advanced utilizations of LLMs
  - such as:
    - searching the internet
    - using external information sources
    - etc

## 2. LLMs Using Tools

- **MRKL Systems** - Modular Reasoning, Knowledge and Language (pronounced miracle); neuro-symbolic architecture that combine LLMs (neural computation) and external tools like calculators (symbolic calculation) to solve complex problems
  - composed of:
    - a set of modules such as:
      - calculator
      - weather API
      - database
    - router - decides how to "route" incoming natural language queries to modules
  - example being an LLM that can use a calculator application
    - LLM is the router
    - calculator is the module
    - query has numbers and operation extracted by LLM and sent to calculator application
  - additional examples:
    - current stock price
    - weather in location determination
    - more complex tasks depending on several sources of information

### External Resources

[Example Playground](https://dust.tt/w/ddebdfcdde/a/98bdd65cb7)

## 3. LLMs that Reason and Act

- **ReAct** - (reason, act) paradigm for enabling language models to solve complex tasks using natural language reasoning.
  - designed for tasks in which LLM is allowed to perform certain actions
  - like in a **MRKL** system when LLM is to interact with external APIs to retrieve information and answer the question based on retrieved information
    - like MRKL systems with the added ability to reason about the actions they can perform
- **HotPotQA** - question answering dataset that requires complex reasoning
  - **ReAct**
    - first reason about question
    - performing an action based on reasoning to send a query to Google
    - receives an observation
    - continues thought, action, observation loop until it reaches a conclusion
- this comes from a paper by Google about the process

## 4. Code as Reasoning

- **Program-Aided Language Models** - example of **MRKL** system; given a question, produces code that provides solution
  - differs from **CoT** in that intermediate reasoning is in code not natural language fp
