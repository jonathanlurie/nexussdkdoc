# Introduction
The Python SDK for BlueBrain Nexus can be used to interact easily with your Nexus environment, from a Python script, an advanced software or a simple Jupiter Notebook.

# Installation
Todo

# Import and configuration
To import the Nexus SDK into your Python project, just write the following:
```python
import nexussdk as nexus
```

To identify who is making the calls to Nexus and to what kind of rights you are granted, the SDK needs a token and the URL to a specific Nexus environment.

```python
token = open('token.txt', 'r').read().strip()
nexus.config.set_token(token)
nexus.config.set_environment('https://bbp-nexus.epfl.ch/staging/v1')
```

> For convenience, it is usually better to store your token in separate text file. If your project is hosted with a *git* solution, thinks about adding your token file to *.gitignore*.  
As shown in the code, we `strip()` the string from this file to make sure the token we send does not start or end with a *space character* or a *new line character*.

This configuration will be used under the hood to perform every single request on Nexus.

# SDK paradygm and returned values
The Python SDK functionalities strictly follows the scope of Nexus' REST API, thus it does not hold state (except the *config*) and can be considered as *functional* rather than *object oriented*.  

The functions of the SDK packages will return the REST API payload as a Python Dictionary. A payload can contain a lot of data and be quite cumbersome to read by a human being. To facilitate that, the SDK provides a *pretty print* function:

```python
import nexussdk as nexus
...
my_payload = nexus.some_package.some_function(...)

# pretty print:
nexus.tools.pretty_print(my_payload)
```

Note that only the `fetch()` functions return the whole set of information of the requested entity (an organisation, a project, a file, a resource). Other functions, such as `create()`, `list()`, etc. return only partial data, usually Nexus metadata.

# Revision system
Every *organization*, *project* and *resource* has a revision identified by the `_rev` field in there response payload. At first, when they are created, the revision is `1`, then each time they are modified, the revision number is incremented and the previous versions are preserved in Nexus to make sure no information is lost.

When fetching or updating an *organization*, *project* or *resource*, you will be asked to provide a revision number (sometime optional, as the SDK kind of figures that out). This ensure that you are modifying the last version available and are fully aware of that.  

If you are trying to modify another version that the last, you will get an error like `409 Client Error: Conflict for url`.
