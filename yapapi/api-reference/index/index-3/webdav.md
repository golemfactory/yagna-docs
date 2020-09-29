# yapapi.storage.webdav

## Classes

### DavResource

```text
class DavResource(
    /,
    *args,
    **kwargs
)
```

DavResource\(path, length, collection, last\_modified\)

#### Ancestors \(in MRO\)

* builtins.tuple

#### Class variables

```text
collection
```

```text
last_modified
```

```text
length
```

```text
path
```

#### Methods

#### count

```text
def count(
    self,
    value,
    /
)
```

Return number of occurrences of value.

#### index

```text
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

```text
class DavStorageProvider(
    client: aiohttp.client.ClientSession,
    base_url: str,
    auth: Union[aiohttp.helpers.BasicAuth, NoneType] = None
)
```

DavStorageProvider\(client: aiohttp.client.ClientSession, base\_url: str, auth: Union\[aiohttp.helpers.BasicAuth, NoneType\] = None\)

#### Ancestors \(in MRO\)

* yapapi.storage.StorageProvider
* yapapi.storage.InputStorageProvider
* yapapi.storage.OutputStorageProvider
* abc.ABC

#### Class variables

```text
auth
```

#### Static methods

#### for\_directory

```text
def for_directory(
    client: aiohttp.client.ClientSession,
    base_url: str,
    directory_name: str,
    auth: Union[aiohttp.helpers.BasicAuth, NoneType] = None,
    **kwargs
) -> 'DavStorageProvider'
```

#### Methods

#### new\_destination

```text
def new_destination(
    self,
    destination_file: Union[os.PathLike, NoneType] = None
) -> yapapi.storage.Destination
```

Creates slot for receiving file.

## Parameters

destination\_file: Optional hint where received data should be placed.

#### prop\_find

```text
def prop_find(
    self
)
```

#### upload\_bytes

```text
def upload_bytes(
    self,
    data: bytes
) -> yapapi.storage.Source
```

#### upload\_file

```text
def upload_file(
    self,
    path: os.PathLike
) -> yapapi.storage.Source
```

#### upload\_stream

```text
def upload_stream(
    self,
    length: int,
    stream: AsyncIterator[bytes]
) -> yapapi.storage.Source
```

