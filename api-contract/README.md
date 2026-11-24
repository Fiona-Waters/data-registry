# Data Registry API reference

[`data-registry-api.yaml`](data-registry-api.yaml) is the OpenAPI 3.1 contract, with
`info.version` set to `0.9.0`. The API is introduced in RHOAI 3.6; the contract
version and the RHOAI release version serve different purposes.

The contract includes Iceberg REST Catalog-shaped operations and RHOAI extensions
marked `x-rhoai-extension: true`; this does not imply full Iceberg REST
compatibility. OpenAPI-generated clients may help with experimentation, but are
not supported product SDKs.

[`data-registry-api.html`](data-registry-api.html) is the generated reference. GitHub
shows its source; download both the HTML and
[`data-registry-api.yaml`](data-registry-api.yaml) into the same directory, then
open the HTML in a browser. The page's specification download link requires the
adjacent YAML file. Use Node.js 24.4.1 and npm 10 or later to regenerate and
validate it with the pinned Redocly CLI:

```bash
npm ci
npm run api:lint
npm run api:docs
```

Run these commands from the repository root. CI checks that the committed HTML
matches the YAML source.
