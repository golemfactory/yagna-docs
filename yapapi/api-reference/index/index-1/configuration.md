# yapapi.rest.configuration

## Variables

```text
DEFAULT_API_URL
```

## Functions

#### env\_or\_fail

```text
def env_or_fail(
    key: str,
    description: str
) -> str
```

## Classes

### Configuration

```text
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

```text
activity_url
```

```text
app_key
```

```text
market_url
```

```text
payment_url
```

#### Methods

#### activity

```text
def activity(
    self
) -> ya_activity.api_client.ApiClient
```

#### market

```text
def market(
    self
) -> ya_market.api_client.ApiClient
```

#### payment

```text
def payment(
    self
) -> ya_payment.api_client.ApiClient
```

### MissingConfiguration

```text
class MissingConfiguration(
    key: str,
    description: str
)
```

Common base class for all non-exit exceptions.

#### Ancestors \(in MRO\)

* builtins.Exception
* builtins.BaseException

#### Class variables

```text
args
```

#### Methods

#### with\_traceback

```text
def with_traceback(
    ...
)
```

Exception.with_traceback\(tb\) -- set self.\_traceback_ to tb and return self.

