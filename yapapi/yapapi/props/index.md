Module yapapi.props
===================

Sub-modules
-----------
* [yapapi.props.base](base/)
* [yapapi.props.builder](builder/)
* [yapapi.props.com](com/)
* [yapapi.props.inf](inf/)

Variables
---------

```python3
ActivityKeys
```

```python3
IdentificationKeys
```

Classes
-------

### Activity

```python3
class Activity(
    cost_cap: Union[decimal.Decimal, NoneType] = None,
    cost_warning: Union[decimal.Decimal, NoneType] = None,
    timeout_secs: Union[float, NoneType] = None,
    expiration: Union[datetime.datetime, NoneType] = None
)
```

Activity-related Properties

#### Ancestors (in MRO)

* yapapi.props.base.Model
* abc.ABC

#### Class variables

```python3
cost_cap
```

```python3
cost_warning
```

```python3
expiration
```

```python3
timeout_secs
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

### Identification

```python3
class Identification(
    name: Union[str, NoneType] = None,
    subnet_tag: Union[str, NoneType] = None
)
```

Identification(name: Union[str, NoneType] = None, subnet_tag: Union[str, NoneType] = None)

#### Ancestors (in MRO)

* yapapi.props.base.Model
* abc.ABC

#### Class variables

```python3
name
```

```python3
subnet_tag
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