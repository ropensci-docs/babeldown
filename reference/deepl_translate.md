# Translate a Markdown file

Translate a Markdown file

## Usage

``` r
deepl_translate(
  path,
  out_path,
  yaml_fields = c("title", "description"),
  glossary_name = NULL,
  source_lang = NULL,
  target_lang = NULL,
  formality = c("default", "more", "less", "prefer_more", "prefer_less")
)
```

## Arguments

- path:

  Path to the Markdown file to be translated (character).

- out_path:

  Path where the new translated file should be saved (character).

- yaml_fields:

  Vector of character names of YAML fields to translate.

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

None

## Examples

``` r
if (FALSE) { # \dontrun{
english_lines <- c(
  "## A cool section", "",
  "This is the first paragraph. `system.file()` is cool, right?", "",
  "Another paragraph. I really enjoy developing R packages.", "",
  "Do you enjoy debugging?"
)
file <- withr::local_tempfile()
brio::write_lines(english_lines, file)
out_path <- withr::local_tempfile()
babeldown::deepl_translate(
  path = file,
  out_path = out_path,
  source_lang = "EN",
  target_lang = "ES",
  formality = "less"
)
readLines(out_path)
} # }
```
