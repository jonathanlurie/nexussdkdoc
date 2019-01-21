# Projects
A project always belongs to an [organization](./organization.md). It can contain [resources](./resources.md) and [files](./files.md). In addition, *projects* provides isolation from resource of other projects (unless a resolver is set up).


## Create a project
A project can only be created within a specific organization. We will see later ([permissions](./permissions.md) and [acls](./acls.md)) that all the *resources* and *files* within a project are granted with the same access rights.

```python
payload = nexus.projects.create("my_org", "my_project")

# pretty print
nexus.tools.pretty_print(payload)
```
In this example, `"my_org"` is the name of the organization that will host the project. The organization must exist. The second argument: `"my_project"` is the name you want to give to your project.

In addition, the `.create()` function can take an optional argument:
- **config** *dict*: Can include data such as `name`, `base` or `apiMappings` see the [API doc](https://bluebrain.github.io/nexus/docs/api/admin/admin-projects-api.html#create-a-project) for more info


## List projects
Generally, you will want to list the project of a certain *organization*, but you can also list all the projects available within the entire environment.  

List projects within an organization:
```python
# For an organization name "my_org"...
payload = nexus.project.list("my_org")

# pretty print
nexus.tools.pretty_print(payload)
```

List projects within the entire environment:
```python
payload = nexus.project.list()

# pretty print
nexus.tools.pretty_print(payload)
```

In addition, you can specify some optional arguments:
- **org_label** *string*: Get only the list of project for this given organization
- **pagination_from** *int*: Index of the list to start from (default: *0*)
- **pagination_size** *int*: Size of the list (default: *20*)
- **deprecated** *boolean*: Lists only the deprecated if *True*, lists only the non-deprecated if *False*, lists everything if not provided or *None* (default: *None*)
- **full_text_search_query** *string*: List only the orgs that match this query (default: *None*)

The returned value is a *dictionary* containing the list of projects.  
**Note** that each project entry contains partial informations about each project. To the whole set of data for a given project, use the [`.fetch()`](./organizations.md#fetch-a-project) function.


# Fetch a project
Fetching a project means getting all the data and metadata related to this particular project. Though, it does **not** fetch the resources bound to this project (to fetch resource, go to the [resource section](./resource.md)).

Since a project belongs to an organization, the `.fetch()` function requires this information:
```python
payload = nexus.projects.fetch("my_org", "my_project")

# pretty print
nexus.tools.pretty_print(payload)
```
Additionally, you can use:
- **rev** *int*: The specific revision of the wanted project. If not provided, will get the last
