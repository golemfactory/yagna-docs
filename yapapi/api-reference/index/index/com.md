# yapapi.props.com

## Variables

```text
DEFINED_USAGES
```

```text
LINEAR_COEFFS
```

```text
PRICE_MODEL
```

```text
SCHEME
```

## Classes

### BillingScheme

```text
class BillingScheme(
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
PAYU
```

```text
name
```

```text
value
```

### Com

```text
class Com(
    scheme: yapapi.props.com.BillingScheme,
    price_model: yapapi.props.com.PriceModel
)
```

Com\(scheme: yapapi.props.com.BillingScheme, price\_model: yapapi.props.com.PriceModel\)

#### Ancestors \(in MRO\)

* yapapi.props.base.Model
* abc.ABC

#### Descendants

* yapapi.props.com.ComLinear

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

### ComLinear

```text
class ComLinear(
    scheme: yapapi.props.com.BillingScheme,
    price_model: yapapi.props.com.PriceModel,
    fixed_price: float,
    price_for: Dict[yapapi.props.com.Counter, float]
)
```

ComLinear\(scheme: yapapi.props.com.BillingScheme, price\_model: yapapi.props.com.PriceModel, fixed\_price: float, price\_for: Dict\[yapapi.props.com.Counter, float\]\)

#### Ancestors \(in MRO\)

* yapapi.props.com.Com
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

### Counter

```text
class Counter(
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
CPU
```

```text
MAXMEM
```

```text
STORAGE
```

```text
TIME
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

### PriceModel

```text
class PriceModel(
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
LINEAR
```

```text
name
```

```text
value
```

