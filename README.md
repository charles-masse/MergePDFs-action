# Combine PDFs

GitHub Action to combine PDFs in a specific folder

## Usage

Create a file called main.yml in .github/workflows/main.yml in your repository and copy the code below

Just change "path" with the path of the folder where the pdfs are, and change filename to the name of the output pdf you want

```yml
on: [push]

jobs:
  build:
    name: CombinePDFS
    runs-on: ubuntu-latest
    env:
      path: resources
      filename: example
    steps:
      - uses: actions/checkout@v7
      - uses: charles-masse/MergePDFs-action@1.15
        with:
          path: ${{env.path}}
          filename: ${{env.filename}}
      - name: Upload combined pdf
        uses: actions/upload-artifact@v7
        with:
          name: ${{env.filename}}
          path: ${{env.path}}/${{env.filename}}.pdf

```
