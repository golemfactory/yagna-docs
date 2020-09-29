# yapapi.storage.gftp

Golem File Transfer Storage Provider

## Functions

#### provider

```text
def provider(

) -> AbstractAsyncContextManager[yapapi.storage.StorageProvider]
```

#### service

```text
def service(
    debug=False
) -> AbstractAsyncContextManager[yapapi.storage.gftp.GftpDriver]
```

## Classes

### GftpDriver

```text
class GftpDriver(
    *args,
    **kwargs
)
```

Golem FTP service API.

#### Ancestors \(in MRO\)

* typing.Protocol
* typing.Generic

#### Methods

#### close

```text
def close(
    self,
    *,
    urls: List[str]
) -> Literal['ok', 'error']
```

Stops exposing GFTP urls created by [publish\(files=\[..\]\)](gftp.md#publish).

#### publish

```text
def publish(
    self,
    *,
    files: List[str]
) -> List[yapapi.storage.gftp.PubLink]
```

Exposes local file as GFTP url.

`files` : local files to be exposed

#### receive

```text
def receive(
    self,
    *,
    output_file: str
) -> yapapi.storage.gftp.PubLink
```

Creates GFTP url for receiving file.

: `output_file` -

#### shutdown

```text
def shutdown(
    self
) -> Literal['ok', 'error']
```

Stops GFTP service.

After shutdown all generated urls will be unavailable.

#### upload

```text
def upload(
    self,
    *,
    file: str,
    url: str
)
```

#### version

```text
def version(
    self
) -> str
```

Gets driver version.

### PubLink

```text
class PubLink(
    /,
    *args,
    **kwargs
)
```

GFTP linking information.

#### Ancestors \(in MRO\)

* builtins.dict

#### Methods

#### clear

```text
def clear(
    ...
)
```

D.clear\(\) -&gt; None. Remove all items from D.

#### copy

```text
def copy(
    ...
)
```

D.copy\(\) -&gt; a shallow copy of D

#### fromkeys

```text
def fromkeys(
    iterable,
    value=None,
    /
)
```

Create a new dictionary with keys from iterable and values set to value.

#### get

```text
def get(
    self,
    key,
    default=None,
    /
)
```

Return the value for key if key is in the dictionary, else default.

#### items

```text
def items(
    ...
)
```

D.items\(\) -&gt; a set-like object providing a view on D's items

#### keys

```text
def keys(
    ...
)
```

D.keys\(\) -&gt; a set-like object providing a view on D's keys

#### pop

```text
def pop(
    ...
)
```

D.pop\(k\[,d\]\) -&gt; v, remove specified key and return the corresponding value. If key is not found, d is returned if given, otherwise KeyError is raised

#### popitem

```text
def popitem(
    self,
    /
)
```

Remove and return a \(key, value\) pair as a 2-tuple.

Pairs are returned in LIFO \(last-in, first-out\) order. Raises KeyError if the dict is empty.

#### setdefault

```text
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

```text
def update(
    ...
)
```

D.update\(\[E, \]\*\*F\) -&gt; None. Update D from dict/iterable E and F. If E is present and has a .keys\(\) method, then does: for k in E: D\[k\] = E\[k\] If E is present and lacks a .keys\(\) method, then does: for k, v in E: D\[k\] = v In either case, this is followed by: for k in F: D\[k\] = F\[k\]

#### values

```text
def values(
    ...
)
```

D.values\(\) -&gt; an object providing a view on D's values

