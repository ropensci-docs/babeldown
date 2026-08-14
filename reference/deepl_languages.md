# Languages supported by DeepL API

Languages supported by DeepL API

## Usage

``` r
deepl_languages(type = c("target", "source"))
```

## Arguments

- type:

  Either "target" or "source"

## Value

A data.frame of languages (language code as "language", name as "name",
whether formality is supported as "supports_formality").

## Examples

``` r
if (FALSE) { # \dontrun{
deepl_languages(type = "source")
deepl_languages(type = "target")
} # }
```
