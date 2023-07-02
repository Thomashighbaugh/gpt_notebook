# Basic Applications

[Source](https://learnprompting.org/ar/docs/category/-basic-applications)

## 01. Introduction

- section intends to survey the range of potential for prompt engineers
- either chatGPT or GPT-3 can be used to replicate the examples provided

## 02. Structuring Data

- You can feed the chat bot data in a paragraph and ask it to produce a table for you with the data structured
- `Generate a table containing this information:`
  - furthermore you can also ask that the table be in Markdown format for ease of copy and paste

## 03. Writing an Email

- can be used to write emails for you

  - Be them simple messages or complex ones.
    - Simple: `Write an email to my boss saying that I will be out of office today since I am sick.`
    - Complex: `Write a humorous yet professional email to my boss saying that I will be out of office today since I am sick. Be concise and funny. Include a funny reason:`
    - Emphasizing the seriousness: `Write a **serious**, professional email to my boss saying that I will be out of office today since I am sick. Be concise:`

- Can be used to summarize the data contained in an email as well, saving time

  - `generate a summary of this and a list of action items`
  - This can then be fed into the AI as part of a prompt for it to write a response.

- Can be used to write the dreaded cold email

  - This could be a simple message pitching a product to a founder
  - Or it could include unstructured data

- One of the great uses and helpful elements of LLMs is that they can cut through information clutter quickly.
  - and parse unstructured data quickly

[Additional Material](https://zapier.com/blog/use-openai-gpt-3-to-write-emails/)

## 04. Blogs

- Significant reductions of writing time for blog posts

  - process should be iterative which looks like the following:
    1. write prompt
    2. see what model outputs
    3. taking pieces out of the output to put in a blog post
    4. repeat until complete
  - Good to start with having it provide an outline
    - if the outline was too long, saying this to the AI and asking for a shorter one is a good next step
      - with GPT-3, the outline will need to precede the new prompt of course

- Other Tools for Writing Blog Posts

  - [Jasper.ai](https://jasper.ai)
  - [Copy.ai](https://copy.ai)

- Big takeaway is that while time saving, its not fully its not fully automated to use AI to write blog posts.

## 05. Study Buddy

- Feeding a passage to the LLM and asking what a specific term there within means can render helpful results
- They can generate practice problems for upcoming tests
  - Can give your notes as context in this process
- **ADDITIONAL IDEAS** - LLMs are excellent at providing the user with topic overviews and lesson plans specific to their requests that may be outside the scope of available tutorials or courses.

## 06. Coding Assistance

- **Code Generation** - can write simple sections of code relatively easily.
- **Code Reformatting** - after prompt include three hashmarks (or other symbol) to delineate the boundaries of what it should read as code
  - `Please add line comments to this Python code and reformat it for legibility:`
- **Debugging** - can determine syntax and logic errors in code fed to it.
  - `Please debug this Python code:`
- **Code Optimization** - Optimization of existing code without breaking the logic
  - `Act like a very senior python developer. Please optimize this script:  `
- **Translating Between Languages** - very useful means of converting from one to another, like an older language to a more modern one.
- **Can Handle Multiple Files** - just include the filenames with the pasted codeusing a structure like this:
  - `BEGIN FILE 1: ./foo/bar.py`
- **Simulating a Database Serer** - can simulate server environments without needing to experiment on production databases
- **Simulating a Web Server** - for getting responses to HTTP headers for instance
- **Simulating a Command Line** - for when a VM is just too much hardware overhead
  - `Act as Debian Linux command shell. Please respond to my commands as the terminal would, with as little explanation as possible.`

[ChatGPT as a Virtual Machine](https://www.engraved.blog/building-a-virtual-machine-inside/)

## 07. Finding Emojis

- LLMs can help find the perfect emoji for a situation

  - include the post/tweet you need emojis for and
    - `What are some good emojis to add to this tweet?`
    - or by sentence
    - or even `What are some good emojis to add to this part of a tweet?`

- Always prefer your own judgment when choosing emojis, ChatGPT and its ilk can only assist you in making the choice, not automate away all your work (for now...)

- This task may be better with ChatGPT as it justifies its responses whereas GPT-3 will not and just outputs a list of emojis.

## 08. Contracts

- LLMs can simplify the process of reading and understanding contracts (and legalese in general)
- finding dangerous legal language
  - `What part of this agreement contains dangerous language?`
- While it can write various legal documents, the less common they are the more caution should be exercised
- Use of LLMs here as everywhere is in an _assistive capacity_

## 09. Different Writing Styles

- You can prompt the LLM to use different tones and author writing voices to change the output dramatically.
  - this includes your own style, which you would include with the prompt of course (few shot prompting)

## 10. Summarizing Text

- can help in digestion of previously written material
  - famous works do not require inclusion (like Romeo and Juliet)
- can summarize or create an outline of text
  - 2,500 words max, longer texts need to be broken into text
  - can also provide outlines

## 11. Zapier for Emails

- Zapier allows using GPT-3
  - which really expands the potential of its automation
  - IFTTT offers in house AI so the utility of this in particular to me is low as I am used to IFTTT, otherwise I would probably wire n8n for this sort of thing.
- take away here is that the LLM can interpret and act on emails easily
  - BUT THERE ARE PRIVACY CONCERNS WITH SUCH
