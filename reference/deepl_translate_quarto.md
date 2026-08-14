# Translate a Quarto book chapter

This assumes the book is set up à la
[babelquarto](https://github.com/ropensci-review-tools/babelquarto).

## Usage

``` r
deepl_translate_quarto(
  book_path,
  chapter,
  force = FALSE,
  render = TRUE,
  yaml_fields = c("title", "description"),
  glossary_name = NULL,
  source_lang = NULL,
  target_lang = NULL,
  formality = c("default", "more", "less", "prefer_more", "prefer_less")
)
```

## Arguments

- book_path:

  Path to book source

- chapter:

  Chapter name

- force:

  Whether to overwrite the chapter in the target language.

- render:

  Whether to run `babelquarto::render_bool()` after translation.

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
temp_dir <- withr::local_tempdir()
babelquarto::quarto_multilingual_book(
  parent_dir = temp_dir,
  book_dir = "blop",
  main_language = "en",
  further_languages = "es"
)
book_path <- file.path(temp_dir, "blop")
deepl_translate_quarto(
  book_path = book_path,
  chapter = "intro.qmd",
  force = TRUE, # the existing chapter is a placeholder
  render = TRUE,
  source_lang = "EN",
  target_lang = "ES",
  formality = "less"
)
# have a look at the translation
readLines(file.path(book_path, "intro.es.qmd"))
# servr::httw(file.path(book_path, "_book"))
} # }
```
