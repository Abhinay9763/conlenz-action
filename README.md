# Conlenz Audit Scan

A GitHub Action to deep-scan your repository for sensitive data, secrets, and low-quality images.

## Usage

Create a `.github/workflows/security-scan.yml` file in your repository:

```yaml
name: Conlenz Scan
on:
  push:
    branches: [main]

jobs:
  scan:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
        
      - name: Run Conlenz
        uses: Abhinay9763/conlenz-action@main
        with:
          mode: deep
        env:
          RESEND_KEY: ${{ secrets.RESEND_KEY }}
          RESEND_MAIL: ${{ secrets.RESEND_MAIL }}
          REPORT_RECIPIENT: ${{ secrets.REPORT_RECIPIENT }}
```

## Inputs

- `mode`: The scan mode (`quick` or `deep`). Default is `deep`.
- `path`: The path to scan. Default is `.`.
