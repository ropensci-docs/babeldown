# Translate a VTT subtitles file

**\[experimental\]**

## Usage

``` r
deepl_translate_vtt(
  path,
  out_path,
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
vtt <- system.file("pecan.vtt", package = "babeldown")
temp_dir <- withr::local_tempdir()
deepl_translate_vtt(
  vtt,
  out_path = file.path(temp_dir, "pecan.es.vtt"),
  source_lang = "EN",
  target_lang = "ES",
  formality = "less"
)
head(readLines(file.path(temp_dir, "pecan.es.vtt")))
} # }
```
