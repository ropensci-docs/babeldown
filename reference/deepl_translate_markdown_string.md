# Translate Markdown string

Translate Markdown string

## Usage

``` r
deepl_translate_markdown_string(
  markdown_string,
  glossary_name = NULL,
  source_lang,
  target_lang,
  formality = c("default", "more", "less", "prefer_more", "prefer_less")
)
```

## Arguments

- markdown_string:

  Markdown string to translate

- glossary_name:

  Name of the glossary to be used, if any (character).

- source_lang:

  Name or code of source language. See [DeepL
  docs](https://www.deepl.com/docs-api/general/get-languages/).

- target_lang:

  Name or code of source language. See [DeepL
  docs](https://www.deepl.com/docs-api/general/get-languages/).

- formality:

  Formality level to use (character), one of

  - "default" (default)

  - "less" – for a more informal language

  - "prefer_more" – for a more formal language if available, otherwise
    fallback to default formality

  - "prefer_less" – for a more informal language if available, otherwise
    fallback to default formality

## Value

Translated Markdown string

## Examples

``` r
if (FALSE) { # \dontrun{
deepl_translate_markdown_string(
  "[So _incredibly_ **wonderful**](https://ropensci.org)!",
  source_lang = "EN",
  target_lang = "FR",
  formality = "less"
)
} # }
```
