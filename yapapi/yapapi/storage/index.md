Module yapapi.storage
=====================
Storage models.

Sub-modules
-----------
* [yapapi.storage.gftp](gftp/)
* [yapapi.storage.webdav](webdav/)

Variables
---------

```python3
AsyncReader
```

Classes
-------

### ComposedStorageProvider

```python3
class ComposedStorageProvider(
    input_storage: yapapi.storage.InputStorageProvider,
    output_storage: yapapi.storage.OutputStorageProvider
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* yapapi.storage.StorageProvider
* yapapi.storage.InputStorageProvider
* yapapi.storage.OutputStorageProvider
* abc.ABC

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

### Content

```python3
class Content(
    /,
    *args,
    **kwargs
)
```

Content(length, stream)

#### Ancestors (in MRO)

* builtins.tuple

#### Class variables

```python3
length
```

```python3
stream
```

#### Static methods

    
#### from_reader

```python3
def from_reader(
    length: int,
    s: Union[asyncio.streams.StreamReader, aiohttp.streams.StreamReader]
)
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

### Destination

```python3
class Destination(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.storage.gftp.GftpDestination
* yapapi.storage.webdav._DavDestination

#### Instance variables

```python3
upload_url
```

#### Methods

    
#### download_file

```python3
def download_file(
    self,
    destination_file: os.PathLike
)
```

    
#### download_stream

```python3
def download_stream(
    self
) -> yapapi.storage.Content
```

### InputStorageProvider

```python3
class InputStorageProvider(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.storage.StorageProvider

#### Methods

    
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

### OutputStorageProvider

```python3
class OutputStorageProvider(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.storage.StorageProvider

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

### Source

```python3
class Source(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.storage.gftp.GftpSource
* yapapi.storage.webdav._DavSource

#### Instance variables

```python3
download_url
```

#### Methods

    
#### content_length

```python3
def content_length(
    self
) -> int
```

### StorageProvider

```python3
class StorageProvider(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* yapapi.storage.InputStorageProvider
* yapapi.storage.OutputStorageProvider
* abc.ABC

#### Descendants

* yapapi.storage.ComposedStorageProvider
* yapapi.storage.gftp.GftpProvider
* yapapi.storage.webdav.DavStorageProvider

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