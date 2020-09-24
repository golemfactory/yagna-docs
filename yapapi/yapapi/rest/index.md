Module yapapi.rest
==================
Mid level binding for Golem REST API

Sub-modules
-----------
* [yapapi.rest.activity](activity/)
* [yapapi.rest.configuration](configuration/)
* [yapapi.rest.market](market/)
* [yapapi.rest.payment](payment/)
* [yapapi.rest.resource](resource/)

Classes
-------

### Activity

```python3
class Activity(
    api_client: ya_activity.api_client.ApiClient
)
```

#### Methods

    
#### new_activity

```python3
def new_activity(
    self,
    agreement_id: str
) -> 'Activity'
```

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

### Market

```python3
class Market(
    api_client: ya_market.api_client.ApiClient
)
```

#### Methods

    
#### subscribe

```python3
def subscribe(
    self,
    props: dict,
    constraints: str
) -> yapapi.rest.market.AsyncResource[yapapi.rest.market.Subscription]
```

    
#### subscriptions

```python3
def subscriptions(
    self
) -> AsyncIterator[yapapi.rest.market.Subscription]
```

### Payment

```python3
class Payment(
    api_client: ya_payment.api_client.ApiClient
)
```

#### Methods

    
#### allocation

```python3
def allocation(
    self,
    allocation_id: str
) -> yapapi.rest.payment.Allocation
```

    
#### allocations

```python3
def allocations(
    self
) -> AsyncIterator[yapapi.rest.payment.Allocation]
```
Lists all active allocations.

Example:

Listing all active allocations

    from yapapi import rest

    async def list_allocations(payment_api: rest.Payment):
        async for allocation in payment_api.allocations():
            print(f'''allocation: {allocation.id}
                amount={allocation.amount},
                expires={allocation.expires}''')

    
#### incoming_invoices

```python3
def incoming_invoices(
    self
) -> AsyncIterator[yapapi.rest.payment.Invoice]
```

    
#### invoice

```python3
def invoice(
    self,
    invoice_id: str
) -> yapapi.rest.payment.Invoice
```

    
#### invoices

```python3
def invoices(
    self
) -> AsyncIterator[yapapi.rest.payment.Invoice]
```

    
#### new_allocation

```python3
def new_allocation(
    self,
    amount: decimal.Decimal,
    *,
    expires: Union[datetime.datetime, NoneType] = None,
    make_deposit: bool = False
) -> yapapi.rest.resource.ResourceCtx[yapapi.rest.payment.Allocation]
```
Creates new allocation.

- `amount`:  Allocation amount.
- `expires`: expiration timestamp. by default 30 minutes from now.
- `make_deposit`: (unimplemented).