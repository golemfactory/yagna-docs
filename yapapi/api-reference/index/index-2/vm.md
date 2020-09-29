# yapapi.runner.vm

## Functions

### repo

```text
def repo(
    *,
    image_hash: str,
    min_mem_gib: float = 0.5,
    min_storage_gib: float = 2.0
) -> yapapi.runner.Package
```

Builds reference to application package.

* _image\_hash_: finds package by its contents hash.
* _min\_mem\_gib_: minimal memory required to execute application code.
* _min\_storage\_gib_ minimal disk storage to execute tasks.

