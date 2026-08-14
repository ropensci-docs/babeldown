# Translate a Hugo post

This translates the Markdown content including the "alt", "caption",
"title" fields of shortcodes.

If it translates the title, it will update the slug.

This assumes the Hugo website uses

- YAML metadata at the top of posts;

- leaf bundles (each post in a folder, `leaf-bundle/index.md`);

- multilingualism so that a post in say Spanish lives in
  `leaf-bundle/index.es.md`.

## Usage

``` r
deepl_translate_hugo(
  post_path = NULL,
  force = FALSE,
  yaml_fields = c("title", "description"),
  glossary_name = NULL,
  source_lang = NULL,
  target_lang = NULL,
  formality = c("default", "more", "less", "prefer_more", "prefer_less")
)
```

## Arguments

- post_path:

  Path to post. If RStudio IDE is installed, it will default to the
  currently open document. If you use Quarto or R Markdown for Hugo,
  translate the source file (qmd or Rmd) and then render it to Markdown.

- force:

  Whether to overwrite the post in the target language.

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
dir <- withr::local_tempdir()
blogdown::new_site(dir = dir)
deepl_translate_hugo(
  file.path(dir, "content", "post", "2016-12-30-hello-markdown", "index.md"),
  source_lang = "en",
  target_lang = "fr",
  formality = "less"
)
readLines(file.path(dir, "content", "post", "2016-12-30-hello-markdown", "index.fr.md"))
} # }
```
