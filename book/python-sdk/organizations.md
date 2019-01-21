# Organizations
An *organization* is used to organize and categorize its sub-resources. An organization can contain [*projects*](./projects.md).  
All the functions related to organization exposed in the SDK are in the `organization` package. You can use this package this way:
```python
import nexussdk as nexus
...
some_payload = nexus.organization.some_function(...)
```

## Create an organization
Creating an organization is usually the starting point of actually using Nexus. Then it will allow you to create projects, resource, etc.
```python
payload = nexus.organization.create("my_lab_org", description="The organization for my lab")

# pretty print
nexus.tools.pretty_print(payload)
```


## Listing organizations
This function lists all the organizations available in the nexus environment you set with `nexus.config.set_environment()`.
```python
payload = nexus.organization.list()

# pretty print
nexus.tools.pretty_print(my_payload)
```

In addition, you can specify some optional arguments:
- **pagination_from** *int*: Index of the list to start from (default: *0*)
- **pagination_size** *int*: Size of the list (default: *20*)
- **deprecated** *boolean*: Lists only the deprecated if *True*, lists only the non-deprecated if *False*, lists everything if not provided or *None* (default: *None*)
- **full_text_search_query** *string*: List only the orgs that match this query (default: *None*)

The response payload returned as a Python dictionary is the list of organizations just like mentioned in the [REST API doc](https://bluebrain.github.io/nexus/docs/api/admin/admin-orgs-api.html#list-organizations).


## Fetch an organization
If you already know the `_label` (aka. name) of an organization and want to get more details about it, you can fetch it. This will provide informations such as the creation date, the description, the user who created it, etc.
```python
payload = nexus.organization.fetch("my_org")

# pretty print
nexus.tools.pretty_print(my_payload)
```

In addition, you can specify some optional arguments:
- **rev** *int*: Get informations about a specific revision of an organization. If not provided or *None*, we get details about the last revision (default: *None*)


## Update an organization
For the moment, it is only possible to update the description of an organization. Like most *update* functions in the SDK, you are asked to provide the full response payload of a *fetch*:

```python
# first we fetch the organization
payload = nexus.organization.list()
nexus.tools.pretty_print(payload)

# then we modify the description field
payload["description"] = "an updated description"

# finally, we update the distant version of the org
other_payload = nexus.organization.update(payload)

# pretty print
nexus.tools.pretty_print(other_payload)
```
**IMPORTANT:** At the moment you modify the first payload, you should not use it for anything else as the *revision number* will not be updated. To get the trully updated version of the organization, **you must fetch it again**.

## Deprecate an organisation
Nexus does not allow deleting, but it allows deprecating. Flagging an organization as *deprecated* prevent any adding of project.

```python
previous_rev = 1
payload = nexus.organization.deprecate("my_org", previous_rev)

# pretty print
nexus.tools.pretty_print(payload)
```
Providing the *previous_rev* is mandatory as it ensures the user is fully aware of what he is deprecating.
