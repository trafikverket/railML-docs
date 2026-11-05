# railML Documentation Hub

## Overview

This repository is the entry point for the railML documentation site.  
It contains general information about the railML standard and the Antora playbook that assembles the site from this repository and all implementation-specific repositories (e.g. `railML-implementation-ertms-interlocking`).

Antora is a static documentation site generator that processes AsciiDoc sources and builds a modular site.  
See [Antora Docs](https://docs.antora.org/antora/latest/) for details.

## Information Classification

All content in this repository is classified as “1 – Non-sensitive” according to the Swedish Transport Administration’s (Trafikverket’s) information classification model. This means that the material does not contain confidential, personal, security-related, or otherwise protected information, and its distribution poses no risk to operational, legal, or security interests. The repository may therefore be published, used, and shared publicly without restrictions.

## Repository Structure

````
railML-docs/
├── antora-playbook.yml     # Defines site content & UI bundle
├── antora.yml              # Component metadata (ROOT)
├── modules/ROOT/pages/     # General documentation pages
├── modules/ROOT/nav.adoc   # Navigation for general info
├── ui-bundle-trv-latest.zip # UI theme bundle
└── package.json            # Node dependencies for Antora
````

## Updating an Antora Site

1. See the Workflow section in the railML-implementation-ertms-interlocking.
2. Build the site by running `npx antora --clean .\antora-playbook.yml` in the root of this repository.
3. The site is built under the `build` directory in the repo root.
4. Publish the generated site to your documentation host.

## Add a new Antora Site/Implementation Specification

1. Create a new repo.
2. Add Antora assets, static files and navigation file.
3. Add CSV file compatible with the railml-antora-doc-generator.
4. Add JSON config compatible with the railml-antora-doc-generator.
5. Create the antora.yml file in the new repo.

### Add New Implementation Docs

To include additional railML implementations, add a new `source` entry in `antora-playbook.yml`:

```yaml
content:
  sources:
    - url: ./
    - url: ../railML-implementation-ertms-interlocking/
      start_path: GeneratedDocs
```

## Developer Setup
VS Code was used for the original development but is not a requirement.
- Install the [AsciiDoc plugin](https://marketplace.visualstudio.com/items?itemName=asciidoctor.asciidoctor-vscode) in VS Code if you want to see how the page will render.
-	Install Node.js using the guide in the [ALM-Wiki](http://tfs.trafikverket.local:8080/tfs/trv/Wiki/_wiki/wikis/Wiki.wiki/4184/Node.js-och-npm).

## UI Bundle
The UI bundle is a simplified application of the [Antora Default UI Bundle](https://gitlab.com/antora/antora-ui-default).
The relevant files have been downloaded, placed in this repo, and have been modified to suit our needs. 

### References
- [Node.js LTS and npm](https://nodejs.org/en/download/)
- [Antora CLI and site-generator](https://docs.antora.org/antora/latest/install-and-run-quickstart/)

### Install and Build the Site
```bash
npm install
npx antora --clean .\antora-playbook.yml
```

## Search Support (Lunr)

This documentation site uses the **Lunr** search engine, which runs in the browser and does not require a backend server. Antora generates the search index at build time via the `@antora/lunr-extension`.

## Useful Links

* [Antora Navigation Guide](https://docs.antora.org/antora/latest/navigation/single-list/)
* [AsciiDoc Language Reference](https://docs.asciidoctor.org/asciidoc/latest/)


