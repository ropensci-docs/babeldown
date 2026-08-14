# Translate Markdown string from clipboard

Read the string from the clipboard using the clipr package. Guesses the
source language using the cld3 package.

## Usage

``` r
deepl_translate_clipboard(
  target_lang,
  source_lang = NULL,
  glossary_name = NULL,
  formality = c("default", "more", "less", "prefer_more", "prefer_less")
)
```

## Arguments

- target_lang:

  Name or code of source language. See [DeepL
  docs](https://www.deepl.com/docs-api/general/get-languages/).

- source_lang:

  Name or code of source language. Guessed using cld3 if not provided.
  See [DeepL
  docs](https://www.deepl.com/docs-api/general/get-languages/).

- glossary_name:

  Name of the glossary to be used, if any (character).

- formality:

  Formality level to use (character), one of

  - "default" (default)

  - "less" – for a more informal language

  - "prefer_more" – for a more formal language if available, otherwise
    fallback to default formality

  - "prefer_less" – for a more informal language if available, otherwise
    fallback to default formality

## Value

Translated Markdown string, also put on the clipboard.

## Details

To make this function less chatty, set the `babeldown.quiet` option to
`TRUE`.

## Examples

``` r
if (FALSE) { # \dontrun{
clipr::write_clip("Je suis en vacances, en fait.")
deepl_translate_clipboard(target_lang = "EN-US")

clipr::write_clip("Je suis en vacances.")
deepl_translate_clipboard(target_lang = "EN-US")
} # }
```
