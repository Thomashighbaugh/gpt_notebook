# Working Prompts

<!-- toc -->

# Introduction

Prompts, contained within blockquotes, that I have used, will use or otherwise found helpful or interesting to aggregate in this central location for my later consumption and/or reference. As these may not always be my exact working model, there may be lapses in quality and style that I will eventually iron out and try to keep to a minimum but I am a human thus am prone to error.

## Use of HTML Tags Ahead

If you are viewing these notes in their raw Markdown file form, you might notice they are mostly HTML. This is to take advantage of the wonderful `<details>` tag enabling the rendered notes to be more neatly compacted together and the prompts themselves only exposed when the user is so inclined. It keeps the page from being too busy to locate needed information easily in my opinion and there are not any awards for Markdown Puritanism, which will be rendered into HTML by mdbook anyway. While Markdown covers most basic formatting needs, HTML provides more flexibility and control over the presentation of the content. In these notes, I strike the balance that works best for me.

## Placeholders

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
