# hugolify-theme-persons

## Install

Edit `config/_default/module.yaml` to install the `hugolify-theme-persons` module:

### V2

```yml
imports:
  - path: github.com/hugolify/hugolify-theme-persons/v2
  - path: github.com/hugolify/hugolify-theme/v2
```

### V1

```yml
imports:
  - path: github.com/hugolify/hugolify-theme-persons
  - path: github.com/hugolify/hugolify-theme
```

## vCard

Each person page publishes a vCard (`.vcf`) next to it, e.g. `/team/jane-doe/contact-info.vcf`.
It is built from `title`, `firstname`, `lastname`, `persons_statutes` and `contact` (`phone`, `fax`, `email`).

The download link is added to the contact list of the person page by
`persons/contact/vcard.html`, the hook `commons/contact/contacts.html` looks for.
Nothing to wire.

To place it somewhere else, render it from the resource:

```go-html-template
{{ with partial "persons/vcard.html" . }}
  {{ partial "commons/contact/vcard.html" . }}
{{ end }}
```

`commons/contact/vcard.html` renders the `contact.vcard` label and the Lucide
`contact-round` icon; the resource itself gives `.RelPermalink` and `.MediaType`
if you would rather write your own markup.

Options, in `config/_default/params.yaml`:

```yml
persons:
  vcard:
    enable: true
    organization: '' # ORG field, defaults to the site title
```

## Documentation

https://www.hugolify.io/docs/

## Licensing

Hugolify is free for personal or commercial projects (MIT license)
