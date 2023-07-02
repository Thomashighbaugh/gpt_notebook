# Working Prompts

<!-- toc -->

# Introduction

Prompts as blockquotes that I have used, will use or otherwise found helpful to aggregate in this central location for my later consumption or reference. As these may not always be my exact working model, there may be lapses in quality that I will eventually iron out but for now remain hidden among these so make sure to read the prompt before using!

## <a name='Placeholders'></a>Placeholders

Most prompts will contain one or more placeholders that must be replaced in order to have the LLM craft a meaningful response. These placeholders are withing square brackets and capitalized for ease of recognition thus look like the following: `[PROMPT]`

More complex prompts also provide examples that fill in the placeholder with relevant but arbitrary input to give the prompter a sense of what these placeholders are asking for specifically.

<hr/>

## <a name='PromptTemplates'></a>Prompt Templates

The below templates are the same code snippets I have used for each prompt in the markdown files this notebook is written as. Locally, I have these saved as custom snippets in my text editors to ease the writing of these prompts in a consistent way with developer experience and error reduction in mind.

**Note:** while this notebook is derived from Markdown, these snippets are in HTML. This is because Markdown does not include a shorthand for the `<details>` element and Markdown rendering engines will pass inline HTML to the generated HTML pages without modification or error.

```html
<!-- Basic Prompt -->
<details>
  <summary>Prompt Name</summary>
  <blockquote>Prompt Itself</blockquote>
</details>

<!-- Prompt with Example Usage Provided -->
<details>
  <summary>[Prompt Name]</summary>
  <blockquote>[Prompt Itself]</blockquote>
  <hr />
  <b>Example</b>
  <blockquote>[Example of Prompt In Action]</blockquote>
</details>

<!-- Prompt With Important Considerations Provided as Warnings -->
<details>
  <summary>PromptName</summary>
  <blockquote>Prompt Itself</blockquote>
  <hr />
  <p><b>Warning:</b> Whatever the warning is about</p>
</details>
```
