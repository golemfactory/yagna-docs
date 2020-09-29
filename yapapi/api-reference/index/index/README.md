# yapapi.props

## Sub-modules

* [yapapi.props.base](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/props/base/README.md)
* [yapapi.props.builder](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/props/builder/README.md)
* [yapapi.props.com](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/props/com/README.md)
* [yapapi.props.inf](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/props/inf/README.md)

## Variables

```text
ActivityKeys
```

```text
IdentificationKeys
```

## Classes

### Activity

```text
class Activity(
    cost_cap: Union[decimal.Decimal, NoneType] = None,
    cost_warning: Union[decimal.Decimal, NoneType] = None,
    timeout_secs: Union[float, NoneType] = None,
    expiration: Union[datetime.datetime, NoneType] = None
)
```

Activity-related Properties

#### Ancestors \(in MRO\)

* yapapi.props.base.Model
* abc.ABC

#### Class variables

```text
cost_cap
```

```text
cost_warning
```

```text
expiration
```

```text
timeout_secs
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

### Identification

```text
class Identification(
    name: Union[str, NoneType] = None,
    subnet_tag: Union[str, NoneType] = None
)
```

Identification\(name: Union\[str, NoneType\] = None, subnet\_tag: Union\[str, NoneType\] = None\)

#### Ancestors \(in MRO\)

* yapapi.props.base.Model
* abc.ABC

#### Class variables

```text
name
```

```text
subnet_tag
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

