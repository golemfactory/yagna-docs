# yapapi.props.inf

Infrastructural Properties

## Variables

```text
INF_CORES
```

```text
INF_MEM
```

```text
INF_STORAGE
```

```text
InfVmKeys
```

```text
TRANSFER_CAPS
```

## Classes

### ExeUnitRequest

```text
class ExeUnitRequest(
    package_url: str
)
```

ExeUnitRequest\(package\_url: str\)

#### Ancestors \(in MRO\)

* yapapi.props.base.Model
* abc.ABC

#### Descendants

* yapapi.props.inf.VmRequest

#### Static methods

#### from\_props

```text
def from_props(
    props: Dict[str, str]
) -> ~ME
```

#### keys

```text
def keys(

)
```

### InfBase

```text
class InfBase(
    mem: float,
    runtime: yapapi.props.inf.RuntimeType,
    storage: Union[float, NoneType] = None,
    transfers: Union[List[str], NoneType] = None
)
```

InfBase\(mem: float, runtime: yapapi.props.inf.RuntimeType, storage: Union\[float, NoneType\] = None, transfers: Union\[List\[str\], NoneType\] = None\)

#### Ancestors \(in MRO\)

* yapapi.props.base.Model
* abc.ABC

#### Descendants

* yapapi.props.inf.InfVm

#### Class variables

```text
storage
```

```text
transfers
```

#### Static methods

#### from\_props

```text
def from_props(
    props: Dict[str, str]
) -> ~ME
```

#### keys

```text
def keys(

)
```

### InfVm

```text
class InfVm(
    mem: float,
    runtime: yapapi.props.inf.RuntimeType,
    storage: Union[float, NoneType] = None,
    transfers: Union[List[str], NoneType] = None,
    cores: int = 1
)
```

InfVm\(mem: float, runtime: yapapi.props.inf.RuntimeType, storage: Union\[float, NoneType\] = None, transfers: Union\[List\[str\], NoneType\] = None, cores: int = 1\)

#### Ancestors \(in MRO\)

* yapapi.props.inf.InfBase
* yapapi.props.base.Model
* abc.ABC

#### Class variables

```text
cores
```

```text
runtime
```

```text
storage
```

```text
transfers
```

#### Static methods

#### from\_props

```text
def from_props(
    props: Dict[str, str]
) -> ~ME
```

#### keys

```text
def keys(

)
```

### RuntimeType

```text
class RuntimeType(

)
```

An enumeration.

#### Ancestors \(in MRO\)

* enum.Enum

#### Class variables

```text
EMSCRIPTEN
```

```text
UNKNOWN
```

```text
VM
```

```text
WASMTIME
```

```text
name
```

```text
value
```

### VmPackageFormat

```text
class VmPackageFormat(
    /,
    *args,
    **kwargs
)
```

An enumeration.

#### Ancestors \(in MRO\)

* enum.Enum

#### Class variables

```text
GVMKIT_SQUASH
```

```text
UNKNOWN
```

```text
name
```

```text
value
```

### VmRequest

```text
class VmRequest(
    package_url: str,
    package_format: yapapi.props.inf.VmPackageFormat
)
```

VmRequest\(package\_url: str, package\_format: yapapi.props.inf.VmPackageFormat\)

#### Ancestors \(in MRO\)

* yapapi.props.inf.ExeUnitRequest
* yapapi.props.base.Model
* abc.ABC

#### Static methods

#### from\_props

```text
def from_props(
    props: Dict[str, str]
) -> ~ME
```

#### keys

```text
def keys(

)
```

### WasmInterface

```text
class WasmInterface(

)
```

An enumeration.

#### Ancestors \(in MRO\)

* enum.Enum

#### Class variables

```text
WASI_0
```

```text
WASI_0preview1
```

```text
name
```

```text
value
```

