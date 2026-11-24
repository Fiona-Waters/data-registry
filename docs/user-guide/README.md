# Data Registry API user guide

This guide is for a user of Red Hat OpenShift AI (RHOAI) who wants to call the Data Registry API directly. It assumes that you have a RHOAI/OpenShift token that the cluster accepts. Your access to a project and its registry operations is controlled by the permissions granted in that RHOAI environment.

The guide focuses on API consumers. For registering and browsing assets in the dashboard, see the [Data Registry dashboard documentation](https://github.com/opendatahub-io/odh-dashboard/tree/main/packages/data-registry/docs). For a hands-on example, see the [Data Registry customer walkthrough](https://github.com/red-hat-data-services/red-hat-ai-examples/tree/main/examples/data-registry).

For operation details and schemas, use the [OpenAPI contract](../../api-contract/data-registry-api.yaml) or the [generated API reference HTML](../../api-contract/data-registry-api.html). GitHub shows the HTML source; download both files into the same directory and open the HTML in a browser to view the rendered reference and use its specification link.

## Topics

- [Getting started](getting-started.md)
- [Authentication](authentication.md)
- [Authorization](authorization.md)
- [Auditing and logging](auditing-and-logging.md)

The exact API URL, available operations, and access configuration can depend on the RHOAI release and cluster setup. The pages below identify details that still need release-verified guidance.
