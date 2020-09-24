Module yapapi.rest.configuration
================================

Variables
---------

```python3
DEFAULT_API_URL
```

Functions
---------

    
#### env_or_fail

```python3
def env_or_fail(
    key: str,
    description: str
) -> str
```

Classes
-------

### Configuration

```python3
class Configuration(
    app_key=None,
    *,
    url: Union[str, NoneType] = None,
    market_url: Union[str, NoneType] = None,
    payment_url: Union[str, NoneType] = None,
    activity_url: Union[str, NoneType] = None
)
```

#### Instance variables

```python3
activity_url
```

```python3
app_key
```

```python3
market_url
```

```python3
payment_url
```

#### Methods

    
#### activity

```python3
def activity(
    self
) -> ya_activity.api_client.ApiClient
```

    
#### market

```python3
def market(
    self
) -> ya_market.api_client.ApiClient
```

    
#### payment

```python3
def payment(
    self
) -> ya_payment.api_client.ApiClient
```

### MissingConfiguration

```python3
class MissingConfiguration(
    key: str,
    description: str
)
```

Common base class for all non-exit exceptions.

#### Ancestors (in MRO)

* builtins.Exception
* builtins.BaseException

#### Class variables

```python3
args
```

#### Methods

    
#### with_traceback

```python3
def with_traceback(
    ...
)
```
Exception.with_traceback(tb) --
set self.__traceback__ to tb and return self.