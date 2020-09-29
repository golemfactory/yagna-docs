# yapapi.storage

Storage models.

## Sub-modules

* [yapapi.storage.gftp](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/storage/gftp/README.md)
* [yapapi.storage.webdav](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/storage/webdav/README.md)

## Variables

```text
AsyncReader
```

## Classes

### ComposedStorageProvider

```text
class ComposedStorageProvider(
    input_storage: yapapi.storage.InputStorageProvider,
    output_storage: yapapi.storage.OutputStorageProvider
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* yapapi.storage.StorageProvider
* yapapi.storage.InputStorageProvider
* yapapi.storage.OutputStorageProvider
* abc.ABC

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

### Content

```text
class Content(
    /,
    *args,
    **kwargs
)
```

Content\(length, stream\)

#### Ancestors \(in MRO\)

* builtins.tuple

#### Class variables

```text
length
```

```text
stream
```

#### Static methods

#### from\_reader

```text
def from_reader(
    length: int,
    s: Union[asyncio.streams.StreamReader, aiohttp.streams.StreamReader]
)
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

### Destination

```text
class Destination(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* abc.ABC

#### Descendants

* yapapi.storage.gftp.GftpDestination
* yapapi.storage.webdav.\_DavDestination

#### Instance variables

```text
upload_url
```

#### Methods

#### download\_file

```text
def download_file(
    self,
    destination_file: os.PathLike
)
```

#### download\_stream

```text
def download_stream(
    self
) -> yapapi.storage.Content
```

### InputStorageProvider

```text
class InputStorageProvider(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* abc.ABC

#### Descendants

* yapapi.storage.StorageProvider

#### Methods

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

### OutputStorageProvider

```text
class OutputStorageProvider(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* abc.ABC

#### Descendants

* yapapi.storage.StorageProvider

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

### Source

```text
class Source(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* abc.ABC

#### Descendants

* yapapi.storage.gftp.GftpSource
* yapapi.storage.webdav.\_DavSource

#### Instance variables

```text
download_url
```

#### Methods

#### content\_length

```text
def content_length(
    self
) -> int
```

### StorageProvider

```text
class StorageProvider(
    /,
    *args,
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using inheritance.

#### Ancestors \(in MRO\)

* yapapi.storage.InputStorageProvider
* yapapi.storage.OutputStorageProvider
* abc.ABC

#### Descendants

* yapapi.storage.ComposedStorageProvider
* yapapi.storage.gftp.GftpProvider
* yapapi.storage.webdav.DavStorageProvider

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

