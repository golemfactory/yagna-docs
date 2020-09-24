Module yapapi.props.base
========================

Variables
---------

```python3
Props
```

Functions
---------

    
#### as_list

```python3
def as_list(
    data: Union[str, List[str]]
) -> List[str]
```

Classes
-------

### Model

```python3
class Model(
    **kwargs
)
```

Helper class that provides a standard way to create an ABC using
inheritance.

#### Ancestors (in MRO)

* abc.ABC

#### Descendants

* yapapi.props.Identification
* yapapi.props.Activity
* yapapi.props.com.Com
* yapapi.props.inf.InfBase
* yapapi.props.inf.ExeUnitRequest

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