Module yapapi.rest.market
=========================

Classes
-------

### Agreement

```python3
class Agreement(
    api: ya_market.api.requestor_api.RequestorApi,
    subscription: 'Subscription',
    agreement_id: str
)
```

#### Instance variables

```python3
id
```

#### Methods

    
#### confirm

```python3
def confirm(
    self
) -> bool
```

    
#### details

```python3
def details(
    self
) -> yapapi.rest.market.AgreementDetails
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

### OfferProposal

```python3
class OfferProposal(
    subscription: 'Subscription',
    proposal: ya_market.models.proposal_event.ProposalEvent
)
```

#### Instance variables

```python3
id
```

```python3
is_draft
```

```python3
issuer
```

```python3
props
```

#### Methods

    
#### agreement

```python3
def agreement(
    self,
    timeout=datetime.timedelta(seconds=3600)
) -> yapapi.rest.market.Agreement
```

    
#### reject

```python3
def reject(
    self,
    reason: Union[str, NoneType] = None
)
```

    
#### respond

```python3
def respond(
    self,
    props: dict,
    constraints: str
) -> str
```

### Subscription

```python3
class Subscription(
    api: ya_market.api.requestor_api.RequestorApi,
    subscription_id: str,
    _details: Union[ya_market.models.demand.Demand, NoneType] = None
)
```

#### Instance variables

```python3
details
```

```python3
id
```

#### Methods

    
#### close

```python3
def close(
    self
)
```

    
#### delete

```python3
def delete(
    self
)
```

    
#### events

```python3
def events(
    self
) -> AsyncIterator[yapapi.rest.market.OfferProposal]
```