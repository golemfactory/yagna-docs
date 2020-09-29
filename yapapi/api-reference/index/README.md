# yapapi

Golem Python API.

## Sub-modules

* [yapapi.props](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/props/README.md)
* [yapapi.rest](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/rest/README.md)
* [yapapi.runner](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/runner/README.md)
* [yapapi.storage](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/storage/README.md)

## Functions

### enable\_default\_logger

```text
def enable_default_logger(
    format_: str = '[%(asctime)s %(levelname)s %(name)s] %(message)s',
    level: int = 20
)
```

Enable the default logger that logs to stderr.

### get\_version

```text
def get_version(

) -> str
```

