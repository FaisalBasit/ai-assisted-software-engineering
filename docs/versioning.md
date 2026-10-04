# Standard Versioning and Change Policy

## Version format

Use Semantic Versioning for published standard releases:

- **MAJOR** — incompatible normative changes or substantial restructuring
- **MINOR** — new compatible requirements, guidance, templates or capabilities
- **PATCH** — corrections, clarifications and non-normative fixes

## Draft status

While the methodology is being actively developed, pre-release versions may use:

`0.x`

A `0.x` release is not a claim of maturity or formal standardization.

## Normative changes

A change that alters a MUST/MUST NOT requirement requires:

- rationale
- affected sections/templates
- migration guidance
- security impact review
- updated examples/evidence
- changelog entry

## External references

Record the relevant version of external standards when a requirement depends on it.

Do not silently upgrade a release baseline from a stable version to a draft.

## Deprecation

Deprecated guidance should state:

- what is deprecated
- why
- replacement
- effective version
- removal target where known

## Release checklist

Before publishing a standard release:

- validate internal links
- validate required templates
- run repository CI
- review security-sensitive changes
- update CHANGELOG
- review external references
- verify no accidental secrets or private material
- tag the release from reviewed source
