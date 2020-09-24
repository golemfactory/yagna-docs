Module yapapi.storage.webdav
============================

Classes
-------

### DavResource

```python3
class DavResource(
    /,
    *args,
    **kwargs
)
```

DavResource(path, length, collection, last_modified)

#### Ancestors (in MRO)

* builtins.tuple

#### Class variables

```python3
collection
```

```python3
last_modified
```

```python3
length
```

```python3
path
```

#### Methods

    
#### count

```python3
def count(
    self,
    value,
    /
)
```
Return number of occurrences of value.

    
#### index

```python3
def index(
    self,
    value,
    start=0,
    stop=9223372036854775807,
    /
)
```
Return first index of value.

Raises ValueError if the value is not present.

### DavStorageProvider

```python3
class DavStorageProvider(
    client: aiohttp.client.ClientSession,
    base_url: str,
    auth: Union[aiohttp.helpers.BasicAuth, NoneType] = None
)
```

DavStorageProvider(client: aiohttp.client.ClientSession, base_url: str, auth: Union[aiohttp.helpers.BasicAuth, NoneType] = None)

#### Ancestors (in MRO)

* yapapi.storage.StorageProvider
* yapapi.storage.InputStorageProvider
* yapapi.storage.OutputStorageProvider
* abc.ABC

#### Class variables

```python3
auth
```

#### Static methods

    
#### for_directory

```python3
def for_directory(
    client: aiohttp.client.ClientSession,
    base_url: str,
    directory_name: str,
    auth: Union[aiohttp.helpers.BasicAuth, NoneType] = None,
    **kwargs
) -> 'DavStorageProvider'
```

#### Methods

    
#### new_destination

```python3
def new_destination(
    self,
    destination_file: Union[os.PathLike, NoneType] = None
) -> yapapi.storage.Destination
```
Creates slot for receiving file.

Parameters
----------
destination_file:
    Optional hint where received data should be placed.

    
#### prop_find

```python3
def prop_find(
    self
)
```

    
#### upload_bytes

```python3
def upload_bytes(
    self,
    data: bytes
) -> yapapi.storage.Source
```

    
#### upload_file

```python3
def upload_file(
    self,
    path: os.PathLike
) -> yapapi.storage.Source
```

    
#### upload_stream

```python3
def upload_stream(
    self,
    length: int,
    stream: AsyncIterator[bytes]
) -> yapapi.storage.Source
```