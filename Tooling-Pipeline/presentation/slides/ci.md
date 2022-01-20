# Continuous Integration


## CircleCI
  * Run Tests
  * Build Artifacts


./.circleci/config.yml
```
version: 2.1

jobs:
  build:
    steps:
      - checkout
      - run: npm ci
      - run: npm run build
      - run: npm run lint
      - run: npm run test:ci
      - run: ./scripts/test-cc-report.sh

...
```


## GitHub Actions
  * Run Tests
  * Build Artifacts


./.github/workflows/[name].yml
```
name: Create Archive

on:
  push:
    tags:
    - "v*.*.*"

jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
      - name: Install Dependencies
        run: npm ci

      - name: Build the CSS files
        run: npm run styles

      - name: Create release artifact
        uses: thedoctor0/zip-release@master
        with:
          type: 'zip'
          filename: 'bit-wptheme.zip'
          path: './theme'

      - name: Create Release
        uses: ncipollo/release-action@v1
        with:
          artifacts: 'bit-wptheme.zip'
          token: ${{ secrets.GH_TOKEN }}
```


## Requirements
Use one of these tools to run tests and build a deployable artifact with each PR.
