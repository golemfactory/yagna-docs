Module yapapi
=============
Golem Python API.

Sub-modules
-----------
* [yapapi.props](props/)
* [yapapi.rest](rest/)
* [yapapi.runner](runner/)
* [yapapi.storage](storage/)

Functions
---------

    
#### enable_default_logger

```python3
def enable_default_logger(
    format_: str = '[%(asctime)s %(levelname)s %(name)s] %(message)s',
    level: int = 20
)
```
Enable the default logger that logs to stderr.

    
#### get_version

```python3
def get_version(
    
) -> str
```