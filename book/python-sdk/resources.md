# Resources
Resources are how Nexus stores JSON structured data within a [project](./projects.md). A resource can be large or small, stores *strings*, *number*, *booleans*, *array* and *composite objects*. In addition, just like every other entity in Nexus, some metadata will be added.  
Just like *organizations* and *projects*, a resource will have metadata regarding its creator, date of creation, a *deprecated* flag, etc. In addition, a resource can be *tagged* and fetched based on a specific tag.

> Note: If you want to store *files* rather than than objects, look into the [file section](./files.md).

## Create a resource

```python
# Your data to put on Nexus
data = {
    "firstname": "Johnny",
    "lastname": "Bravo"
}

payload = nexus.resources.create('my_org', 'my_project', data)

# Pretty print
nexus.tools.pretty_print(payload)
```
In Nexus, everything is identify by a `@id` key. Here, the resource is created and the `@id` is automatically given by Nexus. In some cases, you want to provide the *id* yourself, especially if you already have an indexing system of your own and all your data rely on these ids. Then, just add the id:

```python
# Your data to put on Nexus
data = {
    "firstname": "Johnny",
    "lastname": "Bravo"
}

payload = nexus.resources.create('my_org', 'my_project', data, id="the-fancy-id-i-absolutely-need")

# Pretty print
nexus.tools.pretty_print(payload)
```


## List a resource

## Fetch a resource

## Update a resource

## Deprecate a resource
