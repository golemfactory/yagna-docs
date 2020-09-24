Module yapapi.storage.gftp
==========================
Golem File Transfer Storage Provider

Functions
---------

    
#### provider

```python3
def provider(
    
) -> AbstractAsyncContextManager[yapapi.storage.StorageProvider]
```

    
#### service

```python3
def service(
    debug=False
) -> AbstractAsyncContextManager[yapapi.storage.gftp.GftpDriver]
```

Classes
-------

### GftpDriver

```python3
class GftpDriver(
    *args,
    **kwargs
)
```

Golem FTP service API.

    

#### Ancestors (in MRO)

* typing.Protocol
* typing.Generic

#### Methods

    
#### close

```python3
def close(
    self,
    *,
    urls: List[str]
) -> Literal['ok', 'error']
```
Stops exposing GFTP urls created by [publish(files=[..])](#publish).

    
#### publish

```python3
def publish(
    self,
    *,
    files: List[str]
) -> List[yapapi.storage.gftp.PubLink]
```
Exposes local file as GFTP url.

`files`
:   local files to be exposed

    
#### receive

```python3
def receive(
    self,
    *,
    output_file: str
) -> yapapi.storage.gftp.PubLink
```
Creates GFTP url for receiving file.

:  `output_file` -

    
#### shutdown

```python3
def shutdown(
    self
) -> Literal['ok', 'error']
```
Stops GFTP service.

After shutdown all generated urls will be unavailable.

    
#### upload

```python3
def upload(
    self,
    *,
    file: str,
    url: str
)
```

    
#### version

```python3
def version(
    self
) -> str
```
Gets driver version.

### PubLink

```python3
class PubLink(
    /,
    *args,
    **kwargs
)
```

GFTP linking information.

#### Ancestors (in MRO)

* builtins.dict

#### Methods

    
#### clear

```python3
def clear(
    ...
)
```
D.clear() -> None.  Remove all items from D.

    
#### copy

```python3
def copy(
    ...
)
```
D.copy() -> a shallow copy of D

    
#### fromkeys

```python3
def fromkeys(
    iterable,
    value=None,
    /
)
```
Create a new dictionary with keys from iterable and values set to value.

    
#### get

```python3
def get(
    self,
    key,
    default=None,
    /
)
```
Return the value for key if key is in the dictionary, else default.

    
#### items

```python3
def items(
    ...
)
```
D.items() -> a set-like object providing a view on D's items

    
#### keys

```python3
def keys(
    ...
)
```
D.keys() -> a set-like object providing a view on D's keys

    
#### pop

```python3
def pop(
    ...
)
```
D.pop(k[,d]) -> v, remove specified key and return the corresponding value.
If key is not found, d is returned if given, otherwise KeyError is raised

    
#### popitem

```python3
def popitem(
    self,
    /
)
```
Remove and return a (key, value) pair as a 2-tuple.

Pairs are returned in LIFO (last-in, first-out) order.
Raises KeyError if the dict is empty.

    
#### setdefault

```python3
def setdefault(
    self,
    key,
    default=None,
    /
)
```
Insert key with a value of default if key is not in the dictionary.

Return the value for key if key is in the dictionary, else default.

    
#### update

```python3
def update(
    ...
)
```
D.update([E, ]**F) -> None.  Update D from dict/iterable E and F.
If E is present and has a .keys() method, then does:  for k in E: D[k] = E[k]
If E is present and lacks a .keys() method, then does:  for k, v in E: D[k] = v
In either case, this is followed by: for k in F:  D[k] = F[k]

    
#### values

```python3
def values(
    ...
)
```
D.values() -> an object providing a view on D's values