# RHOAI Data Registry

This repository contains documentation for the RHOAI Data Registry API. It is intended for RHOAI users and applications that need to register, discover, or manage data asset metadata through the API.

The repository contains the OpenAPI contract and a customer-facing user guide.

## Start here

- [Data Registry API user guide](docs/user-guide/README.md) — getting started, authentication, authorization, and auditing and logging.
- [OpenAPI contract](api-contract/data-registry-api.yaml) and [rendered API reference](api-contract/data-registry-api.html).
- [Documentation index](docs/README.md) — the documentation map and related resources.

## Current implementation

The current API implementation is part of the [Open Data Hub Feast repository](https://github.com/opendatahub-io/feast/tree/master/sdk/python/feast/api/data_catalog). This describes where the implementation lives today; the Data Registry API and its customer documentation are intended to have an identity independent of any particular implementation.

## Related customer documentation

- [Data Registry dashboard documentation](https://github.com/opendatahub-io/odh-dashboard/tree/main/packages/data-registry/docs) covers the dashboard experience. This repository focuses on programmatic API use.
- [Data Registry walkthrough in red-hat-ai-examples](https://github.com/red-hat-data-services/red-hat-ai-examples/pull/122) is the longer step-by-step customer example. This guide will provide a concise API-oriented starting point and link to the walkthrough for a fuller exercise.

## Documentation status

The OpenAPI specification is published in [api-contract/](api-contract/README.md). User-guide pages that still need release-specific or operational details are marked as placeholders rather than making assumptions about a deployment. Later stages may add supporting architecture documentation, with the API contract and consumer guidance remaining the primary focus.
