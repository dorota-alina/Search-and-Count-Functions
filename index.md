## In a nutshell

`findNeedles` method counts how many `needle` words occur within a `haystack` text with a seach limitation of up tp five words.

## In depth

`findNeedles` API method searches throught a particular text (`haystack`) for a specific word (`needle`). If found, `findNeedles` counts and logs its occurances. <br>
* `haystack` is a file stored locally.
* `needles` are arrays of words.<br>
It first checks whether the size of needles is greater than 5. If it is, it prints an "error" and subsequently exits.

If not, the method uses split function to split the given input argument string using following literals: \"\'\t\n\b\f\r

\" double quotes character
\' single quote character
\t tab space character
\n new line character
\b back space character
\f form feed character
\r carriage return character

It then splits the haystack string over a number of characters (including single and double quotes, tabs, newlines, word boundaries, form feeds and carriage returns) into an array of words called words.

Each "needle" (element of the needles array) is compared to each element of the words array and if a "needle" is encountered as an element of the words array, a "counter" for the respective needle is incremented.

After the search, each needle is displayed along with the number of times it occurred in the haystack.

The function then exits.

You can use the [editor on GitHub](https://github.com/dorota-alina/findNeedles-API-reference/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/dorota-alina/findNeedles-API-reference/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
