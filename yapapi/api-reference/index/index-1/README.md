# yapapi.rest

Mid level binding for Golem REST API

## Sub-modules

* [yapapi.rest.activity](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/rest/activity/README.md)
* [yapapi.rest.configuration](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/rest/configuration/README.md)
* [yapapi.rest.market](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/rest/market/README.md)
* [yapapi.rest.payment](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/rest/payment/README.md)
* [yapapi.rest.resource](https://github.com/golemfactory/yagna-docs/tree/5ed43c18691a669dfa6246537fb75ebe08b87564/yapapi/yapapi/rest/resource/README.md)

## Classes

### Activity

```text
class Activity(
    api_client: ya_activity.api_client.ApiClient
)
```

#### Methods

#### new\_activity

```text
def new_activity(
    self,
    agreement_id: str
) -> 'Activity'
```

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

### Market

```text
class Market(
    api_client: ya_market.api_client.ApiClient
)
```

#### Methods

#### subscribe

```text
def subscribe(
    self,
    props: dict,
    constraints: str
) -> yapapi.rest.market.AsyncResource[yapapi.rest.market.Subscription]
```

#### subscriptions

```text
def subscriptions(
    self
) -> AsyncIterator[yapapi.rest.market.Subscription]
```

### Payment

```text
class Payment(
    api_client: ya_payment.api_client.ApiClient
)
```

#### Methods

#### allocation

```text
def allocation(
    self,
    allocation_id: str
) -> yapapi.rest.payment.Allocation
```

#### allocations

```text
def allocations(
    self
) -> AsyncIterator[yapapi.rest.payment.Allocation]
```

Lists all active allocations.

Example:

Listing all active allocations

```text
from yapapi import rest

async def list_allocations(payment_api: rest.Payment):
    async for allocation in payment_api.allocations():
        print(f'''allocation: {allocation.id}
            amount={allocation.amount},
            expires={allocation.expires}''')
```

#### incoming\_invoices

```text
def incoming_invoices(
    self
) -> AsyncIterator[yapapi.rest.payment.Invoice]
```

#### invoice

```text
def invoice(
    self,
    invoice_id: str
) -> yapapi.rest.payment.Invoice
```

#### invoices

```text
def invoices(
    self
) -> AsyncIterator[yapapi.rest.payment.Invoice]
```

#### new\_allocation

```text
def new_allocation(
    self,
    amount: decimal.Decimal,
    *,
    expires: Union[datetime.datetime, NoneType] = None,
    make_deposit: bool = False
) -> yapapi.rest.resource.ResourceCtx[yapapi.rest.payment.Allocation]
```

Creates new allocation.

* `amount`:  Allocation amount.
* `expires`: expiration timestamp. by default 30 minutes from now.
* `make_deposit`: \(unimplemented\).

