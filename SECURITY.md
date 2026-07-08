# Security Policy

## Supported Versions

The current public release line is:

```text
1.0.x
```

## Reporting a Vulnerability

Please report security issues through a private GitHub security advisory if available, or by contacting the maintainer through GitHub.

Do not open a public issue that includes secrets, credentials, private infrastructure details, or exploit instructions.

## Data Handling

Handoff is designed to store repo-local markdown summaries. It should not write secrets or sensitive operational data into handoff files.

If a handoff output includes sensitive data, treat it as a bug and remove the data from the affected repository history before sharing the project.
