# README: Fixing CodeQL Workflow Errors

This document outlines the errors encountered while setting up CodeQL analysis for Python and the steps taken to resolve them.

---

## Errors and Fixes

### 1. **Error:**
```text
CodeQL did not detect any code written in languages supported by this CodeQL distribution.
```
**Cause:**
- The `.ipynb` (Jupyter Notebook) file was not recognized as Python source code by CodeQL.

**Solution:**
- Convert the `.ipynb` file to a `.py` file using the following command:
  ```bash
  pip install jupyter
  jupyter nbconvert --to script Survival_Prediction.ipynb
  ```
- This ensures CodeQL can analyze the Python source code.

---

### 2. **Error:**
```text
Unexpected input(s) 'paths', valid inputs are ['tools', 'languages', 'build-mode', 'token', 'registries', 'matrix', 'config-file', 'db-location', 'config', 'queries', 'packs', 'external-repository-token', 'setup-python-dependencies', 'source-root', 'ram', 'threads', 'debug', 'debug-artifact-name', 'debug-database-name', 'trap-caching', 'dependency-caching'].
```
**Cause:**
- The `paths` input is not valid in CodeQL workflows.

**Solution:**
- Remove the `paths` key from the workflow YAML file.
- Replace it with `source-root` to define the root directory for source code.

Updated snippet:
```yaml
- name: Initialize CodeQL
  uses: github/codeql-action/init@v3
  with:
    languages: python
    source-root: .
```

---

### 3. **Error:**
```text
Exit code was 32 and last log line was: CodeQL did not detect any code written in languages supported by this CodeQL distribution.
```
**Cause:**
- CodeQL could not find any supported source files in the repository.

**Solution:**
- Ensure that Python source files (`.py`) exist in the repository’s root or within the directory specified by `source-root`.
- Convert Jupyter Notebook files (`.ipynb`) to Python scripts as mentioned in Error 1.

---

## Updated Workflow File
Here is the corrected `.github/workflows/codeql.yml` file:

```yaml
name: "CodeQL Analysis"

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  analyze:
    name: Analyze (Python)
    runs-on: ubuntu-latest
    permissions:
      security-events: write
    strategy:
      fail-fast: false
      matrix:
        language: [ "python" ]
    steps:
    - name: Checkout repository
      uses: actions/checkout@v4

    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.x'

    - name: Convert .ipynb to .py (if necessary)
      run: |
        pip install jupyter
        jupyter nbconvert --to script Survival_Prediction.ipynb || echo "No conversion needed"

    - name: Initialize CodeQL
      uses: github/codeql-action/init@v3
      with:
        languages: ${{ matrix.language }}
        source-root: .

    - name: Perform CodeQL Analysis
      uses: github/codeql-action/analyze@v3
      with:
        category: "/language:${{ matrix.language }}"
```

---

## Notes
- Always ensure your Python source files are properly placed in the repository.
- Regularly validate the workflow file against [CodeQL documentation](https://docs.github.com/en/code-security/code-scanning/using-codeql/codeql-workflow-syntax).
- Use `jupyter nbconvert` to handle `.ipynb` files when working with CodeQL.

