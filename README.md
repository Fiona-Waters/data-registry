# RHOAI Data Registry

This repository contains documentation for the RHOAI Data Registry API. It is intended for RHOAI users and applications that need to register, discover, or manage data asset metadata through the API.

The repository contains the OpenAPI contract and a customer-facing user guide.

## Start here

- [Data Registry API user guide](docs/user-guide/README.md) — getting started, authentication, authorization, and auditing and logging.
- [OpenAPI contract](api-contract/data-registry-api.yaml) and [generated API reference HTML](api-contract/data-registry-api.html). GitHub shows the HTML source; download the file and open it in a browser to view the rendered reference.
- [Documentation index](docs/README.md) — the documentation map and related resources.

## Current implementation

The current API implementation is part of the [Open Data Hub Feast repository](https://github.com/opendatahub-io/feast/tree/master/sdk/python/feast/api/data_catalog). This describes where the implementation lives today; the Data Registry API and its customer documentation are intended to have an identity independent of any particular implementation.

## Related customer documentation

- [Data Registry dashboard documentation](https://github.com/opendatahub-io/odh-dashboard/tree/main/packages/data-registry/docs) covers the dashboard experience. This repository focuses on programmatic API use.
- [Data Registry walkthrough preview in red-hat-ai-examples](https://github.com/briangallagher/red-hat-ai-examples/blob/codex/data-registry-rhoai-3.6/examples/data-registry/README.md) is the longer step-by-step example. It is still under review and is not yet published on the upstream default branch.

## Documentation status

The OpenAPI specification is published in [api-contract/](api-contract/README.md). User-guide pages that still need release-specific or operational details are marked as placeholders rather than making assumptions about a deployment. Later stages may add supporting architecture documentation, with the API contract and consumer guidance remaining the primary focus.
