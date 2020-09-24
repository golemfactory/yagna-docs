Module yapapi.props.com
=======================

Variables
---------

```python3
DEFINED_USAGES
```

```python3
LINEAR_COEFFS
```

```python3
PRICE_MODEL
```

```python3
SCHEME
```

Classes
-------

### BillingScheme

```python3
class BillingScheme(
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
PAYU
```

```python3
name
```

```python3
value
```

### Com

```python3
class Com(
    scheme: yapapi.props.com.BillingScheme,
    price_model: yapapi.props.com.PriceModel
)
```

Com(scheme: yapapi.props.com.BillingScheme, price_model: yapapi.props.com.PriceModel)

#### Ancestors (in MRO)

* yapapi.props.base.Model
* abc.ABC

#### Descendants

* yapapi.props.com.ComLinear

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

### ComLinear

```python3
class ComLinear(
    scheme: yapapi.props.com.BillingScheme,
    price_model: yapapi.props.com.PriceModel,
    fixed_price: float,
    price_for: Dict[yapapi.props.com.Counter, float]
)
```

ComLinear(scheme: yapapi.props.com.BillingScheme, price_model: yapapi.props.com.PriceModel, fixed_price: float, price_for: Dict[yapapi.props.com.Counter, float])

#### Ancestors (in MRO)

* yapapi.props.com.Com
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

### Counter

```python3
class Counter(
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
CPU
```

```python3
MAXMEM
```

```python3
STORAGE
```

```python3
TIME
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

### PriceModel

```python3
class PriceModel(
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
LINEAR
```

```python3
name
```

```python3
value
```