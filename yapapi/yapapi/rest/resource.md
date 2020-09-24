Module yapapi.rest.resource
===========================

Classes
-------

### ResourceCtx

```python3
class ResourceCtx(
    /,
    *args,
    **kwargs
)
```

An abstract base class for asynchronous context managers.

#### Ancestors (in MRO)

* contextlib.AbstractAsyncContextManager
* abc.ABC
* typing.Generic

#### Descendants

* yapapi.rest.payment._AllocationTask

#### Methods

    
#### detach

```python3
def detach(
    self
) -> ~_T
```