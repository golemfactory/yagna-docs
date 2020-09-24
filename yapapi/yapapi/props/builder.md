Module yapapi.props.builder
===========================

Classes
-------

### DemandBuilder

```python3
class DemandBuilder(
    
)
```

#### Instance variables

```python3
cons
```

```python3
props
```

#### Methods

    
#### add

```python3
def add(
    self,
    m: yapapi.props.base.Model
)
```

    
#### ensure

```python3
def ensure(
    self,
    constraint: str
)
```

    
#### subscribe

```python3
def subscribe(
    self,
    market: yapapi.rest.market.Market
) -> yapapi.rest.market.Subscription
```