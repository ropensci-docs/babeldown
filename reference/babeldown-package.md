# babeldown: Helpers for Automatic Translation of Markdown-based Content

Provide workflows and guidance for automatic translation of
Markdown-based R content using DeepL API.

## API URL

The DeepL API URL depends on your API plan. babeldown uses the DeepL
*free* API URL by default. If you use a Pro plan, set the API URL via

    Sys.setenv("DEEPL_API_URL" = "https://api.deepl.com")

## API key

Set your API key via the environment variable `DEEPL_API_KEY`. You could
store it with the keyring package and retrieve it like so:

    Sys.setenv(DEEPL_API_KEY = keyring::key_get("deepl"))

## See also

Useful links:

- <https://docs.ropensci.org/babeldown>

- <https://github.com/ropensci-review-tools/babeldown>

- Report bugs at
  <https://github.com/ropensci-review-tools/babeldown/issues>

## Author

**Maintainer**: Maëlle Salmon <msmaellesalmon@gmail.com>
([ORCID](https://orcid.org/0000-0002-2815-0399))

Other contributors:

- Xavier Timbeau \[contributor\]

- rOpenSci ([ROR](https://ror.org/019jywm96)) \[funder\]
