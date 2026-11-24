# Authentication

Data Registry API requests use a RHOAI/OpenShift bearer token. Send the token in the HTTP `Authorization` header:

```http
Authorization: Bearer <your-token>
```

Use a token issued for your authenticated RHOAI/OpenShift identity and accepted by the cluster hosting the API. Authentication identifies the caller; it does not by itself grant access to a project or an operation. See [authorization](authorization.md) for the access-control guide.

The supported way to obtain or refresh a token, its lifetime, and safe handling guidance must be verified against the target RHOAI release before this page is expanded with commands. Do not put a live token in source code, notebooks shared with others, or committed files.
