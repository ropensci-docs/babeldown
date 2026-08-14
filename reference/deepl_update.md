# Update a translation of a file in a Git repo

Re-use existing translation where possible (at the node level:
paragraph, heading, item of list at the first level, etc.)
`deepl_update()` is based on the commit history in a single branch,
`deepl_branch_update()` is based on the commit history in a branch
against another (in a GitHub PR for instance), and requires a
configuration file (see "Configuration" section).

## Usage

``` r
deepl_update(
  path,
  out_path,
  yaml_fields = c("title", "description"),
  glossary_name = NULL,
  source_lang = NULL,
  target_lang = NULL,
  formality = c("default", "more", "less", "prefer_more", "prefer_less"),
  max_commits = 100L
)

deepl_branch_update(repo = ".", max_commits = 100)
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

- max_commits:

  Maximal number of commits to go back to to find when the target and
  source files were updated. You might need to increase it if your
  project is very active.

- repo:

  path to the Git repository.

## Value

None

## Limitations of `deepl_update()`

`deepl_update()` looks for the latest commit that updated the source
file, and for the latest commit that updated the target file. If the
target file was updated later than the source file, or at the same time,
nothing happens: you might need to fix up the Git history with rebase
for instance. Also note that if there were some commits irrelevant to
the translation but containing edits to the source file, like typo
fixes, too much of the target file will be translated automatically
again.

## Configuration for `deepl_branch_update()`

`deepl_branch_update()` is more automatic but needs configuration. In a
branch, for any edits made to any Rmd/qmd/md file, it will update the
translations of the Rmd/qmd/md file with the same name and a language
code. For instance if a branch had commits updating `pkg_building.Rmd`,
`deepl_branch_update()` will update `pkg_building.es.Rmd`. Do not run it
if your PR updated both `pkg_building.Rmd` and `pkg_building.es.Rmd`.
Make sure to read the section about Markdown formatting.

The configuration needed must live under `_deepl.yml` at the root of the
Git repo. It must contains those fields:

- "preferences" that for any source-target pair, indicates the
  preference for the `formality`, `glossary` and `yaml_fields` arguments
  of
  [`deepl_translate()`](https://docs.ropensci.org/babeldown/reference/deepl_translate.md).

- "excludes" that indicates which files to exclude from the automatic
  detection (all Rmd/qmd/md files are otherwise considered). It is used
  as `glob` arguments in calls to
  [`fs::dir_ls()`](https://fs.r-lib.org/reference/dir_ls.html).

- "languages" that for any language code used in file names, indicates
  what DeepL API code to use when it is a source or target language.

Example (`_deepl.yml`):

    preferences:
      - source: en
        target: es-419
        formality: less
        glossary: "glosario"
        yaml_fields: ["title"]
      - source: en
        target: pt-br
        formality: less
        yaml_fields: ["title", "description"]
      - source: pt
        target: en-us
        formality: prefer_less
        yaml_fields: ["title", "description"]
      - source: es
        target: en-us
        formality: prefer_less
        yaml_fields: ["title", "description"]

    excludes: ["*.md"]

    languages:
      - extension: es
        target: es-419
        source: es
      - extension: ''
        target: en-us
        source: en
      - extension: pt
        target: pt-br
        source: pt
