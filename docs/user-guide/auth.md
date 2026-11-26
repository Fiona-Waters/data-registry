# Authentication and authorization

The Data Registry uses an OpenShift token to identify the caller and Kubernetes
RBAC to authorize operations. **The OpenShift project in the API path is the
access boundary.** For `/v1/team-a/namespaces/training-data`, `team-a` is the
project checked by RBAC; `training-data` is a collection within that project.
A role bound in `team-a` covers its registry collections and assets, but does
not grant access in another project. There are no separate per-collection or
per-asset registry grants.

## Authenticate a direct API request

Sign in to the cluster hosting the registry, then check your identity and get
its token:

```shell
oc config current-context
oc whoami
oc whoami -t
```

Send that token to the protected Data Registry endpoint supplied for your RHOAI
environment. Replace the placeholders in this example:

```shell
curl -i -H 'Authorization: Bearer <token>' \
  'https://<data-registry-host>/v1/<project>/namespaces'
```

For project-prefixed routes, the backend proxy validates the token through
Kubernetes TokenReview, then uses SubjectAccessReview to check the requested
action on `registries.dataregistry.opendatahub.io` in the URL's project.
`registries` is an RBAC policy target, not a Kubernetes object to list. A valid
token alone does not grant project access. Treat the token printed by
`oc whoami -t` as a secret; do not put it in source code, shared notebooks,
logs, or commits.

The [Dashboard guide](https://github.com/opendatahub-io/odh-dashboard/tree/main/packages/data-registry/docs)
covers browser use. The Dashboard and its BFF handle the authenticated request
without asking users to paste a token into the UI.

## Grant access in a project

An OpenShift project administrator, or someone delegated permission to bind the
chosen role, can share access. RHOAI administrator status alone does not grant
permission to manage RoleBindings in the project. The operator-provided
registry roles must already be installed.

| Access needed                                                | Role to bind in the project  |
| ------------------------------------------------------------ | ---------------------------- |
| Read registry metadata and other permitted project resources | `view`                       |
| Manage registry metadata and other project resources         | `admin`                      |
| Read registry metadata only                                  | `feast-data-registry-viewer` |
| Manage registry metadata only                                | `feast-data-registry-admin`  |

Choose **one** role for the recipient. For example, to grant registry-only read
access to `alice` in `team-a`, run as a project administrator:

```shell
PROJECT=team-a
RECIPIENT=alice
BINDING=data-registry-viewer-alice
oc adm policy add-role-to-user feast-data-registry-viewer "$RECIPIENT" \
  -n "$PROJECT" --rolebinding-name="$BINDING"
```

For another access level, change the role and use a new binding name. For a
group, use `oc adm policy add-role-to-group` instead. A RoleBinding to a
ClusterRole grants access only in the binding's project. These grants are
additive: a registry-only binding cannot remove broader access already granted
by another project role.

Registry-only access permits direct API use, but the Dashboard project selector
may also require a project-discovery grant. Connection discovery is a separate
decision: granting `list secrets` can expose **all Secret contents** in the
project. Follow the [sharing walkthrough](https://github.com/red-hat-data-services/red-hat-ai-examples/blob/main/examples/data-registry/04-share-registry-access/README.md)
for those cases, group bindings, and a complete exercise. Registry metadata
access does not itself grant access to Data Connections or underlying storage.

## Verify and revoke

Have the recipient sign in with their own `oc` session and verify the project,
effective rules, and a real registry read or write as appropriate:

```shell
oc whoami
oc get projects
oc auth can-i --list -n team-a
```

Some `oc` versions cannot reliably check virtual registry resources with
`oc auth can-i`; an actual API request is the final check. Missing or invalid
tokens usually return `401`;
insufficient permission in the URL's project returns `403`.

To revoke the example grant, the grantor can delete only the RoleBinding they
created: `oc delete rolebinding data-registry-viewer-alice -n team-a`. Check the
recipient's access again after the change propagates; another binding may
still grant access.
