# Create or update glossary

Create or update glossary

## Usage

``` r
deepl_upsert_glossary(filename, glossary_name = NULL, source_lang, target_lang)
```

## Arguments

- filename:

  Name of the glossary file. See [DeepL docs on supported
  formats](https://www.deepl.com/en/docs-api/glossaries/formats/).
  babeldown is stricter: the columns need to be named like `source_lang`
  and `target_lang`.

- glossary_name:

  Name for the glossary. Defaults to the filename without extension.

- source_lang:

  Name or code of source language. See [DeepL
  docs](https://www.deepl.com/docs-api/general/get-languages/).

- target_lang:

  Name or code of source language. See [DeepL
  docs](https://www.deepl.com/docs-api/general/get-languages/).

## Value

glossary ID

## Examples

``` r
if (FALSE) { # \dontrun{
deepl_upsert_glossary(
  system.file("example-es-en.csv", package = "babeldown"),
  glossary_name = "rstats-glosario",
  target_lang = "Spanish",
  source_lang = "English"
)
} # }
```
