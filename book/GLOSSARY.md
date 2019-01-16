## token
This generally takes the shape of a very long string of what seems to be random characters. The token is what represents your identity within Nexus. Depending on the Nexus environment or the realm, a token might be valid only for a certain period of time. More generally, a token is a way to enforce security and provides a login system. A token is private and should not be shared.

## payload
A payload is a general term to define a message. It can be a message that is sent or a message that is received. In the later case, we will generally talk about *response payload*. Most of the time, a payload comes as JSON structure and is then translated into a Python dictionary, a Javascript object (depending on the language of choice).

## revision
A revision is a version number, incremented every-time a entity is updated.
