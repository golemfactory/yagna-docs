Module yapapi.props.inf
=======================
Infrastructural Properties

Variables
---------

```python3
INF_CORES
```

```python3
INF_MEM
```

```python3
INF_STORAGE
```

```python3
InfVmKeys
```

```python3
TRANSFER_CAPS
```

Classes
-------

### ExeUnitRequest

```python3
class ExeUnitRequest(
    package_url: str
)
```

ExeUnitRequest(package_url: str)

#### Ancestors (in MRO)

* yapapi.props.base.Model
* abc.ABC

#### Descendants

* yapapi.props.inf.VmRequest

#### Static methods

    
#### from_props

```python3
def from_props(
    props: Dict[str, str]
) -> ~ME
```

    
#### keys

```python3
def keys(
    
)
```

### InfBase

```python3
class InfBase(
    mem: float,
    runtime: yapapi.props.inf.RuntimeType,
    storage: Union[float, NoneType] = None,
    transfers: Union[List[str], NoneType] = None
)
```

InfBase(mem: float, runtime: yapapi.props.inf.RuntimeType, storage: Union[float, NoneType] = None, transfers: Union[List[str], NoneType] = None)

#### Ancestors (in MRO)

* yapapi.props.base.Model
* abc.ABC

#### Descendants

* yapapi.props.inf.InfVm

#### Class variables

```python3
storage
```

```python3
transfers
```

#### Static methods

    
#### from_props

```python3
def from_props(
    props: Dict[str, str]
) -> ~ME
```

    
#### keys

```python3
def keys(
    
)
```

### InfVm

```python3
class InfVm(
    mem: float,
    runtime: yapapi.props.inf.RuntimeType,
    storage: Union[float, NoneType] = None,
    transfers: Union[List[str], NoneType] = None,
    cores: int = 1
)
```

InfVm(mem: float, runtime: yapapi.props.inf.RuntimeType, storage: Union[float, NoneType] = None, transfers: Union[List[str], NoneType] = None, cores: int = 1)

#### Ancestors (in MRO)

* yapapi.props.inf.InfBase
* yapapi.props.base.Model
* abc.ABC

#### Class variables

```python3
cores
```

```python3
runtime
```

```python3
storage
```

```python3
transfers
```

#### Static methods

    
#### from_props

```python3
def from_props(
    props: Dict[str, str]
) -> ~ME
```

    
#### keys

```python3
def keys(
    
)
```

### RuntimeType

```python3
class RuntimeType(
    
)
```

An enumeration.

#### Ancestors (in MRO)

* enum.Enum

#### Class variables

```python3
EMSCRIPTEN
```

```python3
UNKNOWN
```

```python3
VM
```

```python3
WASMTIME
```

```python3
name
```

```python3
value
```

### VmPackageFormat

```python3
class VmPackageFormat(
    /,
    *args,
    **kwargs
)
```

An enumeration.

#### Ancestors (in MRO)

* enum.Enum

#### Class variables

```python3
GVMKIT_SQUASH
```

```python3
UNKNOWN
```

```python3
name
```

```python3
value
```

### VmRequest

```python3
class VmRequest(
    package_url: str,
    package_format: yapapi.props.inf.VmPackageFormat
)
```

VmRequest(package_url: str, package_format: yapapi.props.inf.VmPackageFormat)

#### Ancestors (in MRO)

* yapapi.props.inf.ExeUnitRequest
* yapapi.props.base.Model
* abc.ABC

#### Static methods

    
#### from_props

```python3
def from_props(
    props: Dict[str, str]
) -> ~ME
```

    
#### keys

```python3
def keys(
    
)
```

### WasmInterface

```python3
class WasmInterface(
    
)
```

An enumeration.

#### Ancestors (in MRO)

* enum.Enum

#### Class variables

```python3
WASI_0
```

```python3
WASI_0preview1
```

```python3
name
```

```python3
value
```