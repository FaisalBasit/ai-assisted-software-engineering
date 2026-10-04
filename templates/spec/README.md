# Project Specification Template

Create a `your-project-spec/` directory in each consuming project.

Recommended structure:

```
your-project-spec/
├── product-spec.md
├── user-journeys/
│   ├── <feature>-journey.md
│   └── ...
├── workflows/
│   ├── <workflow>.md
│   └── ...
├── api/
│   ├── <endpoint>.md
│   └── ...
├── routes.md
├── data-model.md
├── authorization.md
├── security.md
├── observability.md
└── acceptance-criteria/
    ├── <feature>.md
    └── ...
```

Every major feature gets a user journey. Every stateful workflow gets explicit transitions and invariants. Every external behavior gets acceptance criteria.
