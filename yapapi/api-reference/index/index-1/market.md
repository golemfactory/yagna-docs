# yapapi.rest.market

## Classes

### Agreement

```text
class Agreement(
    api: ya_market.api.requestor_api.RequestorApi,
    subscription: 'Subscription',
    agreement_id: str
)
```

#### Instance variables

```text
id
```

#### Methods

#### confirm

```text
def confirm(
    self
) -> bool
```

#### details

```text
def details(
    self
) -> yapapi.rest.market.AgreementDetails
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

### OfferProposal

```text
class OfferProposal(
    subscription: 'Subscription',
    proposal: ya_market.models.proposal_event.ProposalEvent
)
```

#### Instance variables

```text
id
```

```text
is_draft
```

```text
issuer
```

```text
props
```

#### Methods

#### agreement

```text
def agreement(
    self,
    timeout=datetime.timedelta(seconds=3600)
) -> yapapi.rest.market.Agreement
```

#### reject

```text
def reject(
    self,
    reason: Union[str, NoneType] = None
)
```

#### respond

```text
def respond(
    self,
    props: dict,
    constraints: str
) -> str
```

### Subscription

```text
class Subscription(
    api: ya_market.api.requestor_api.RequestorApi,
    subscription_id: str,
    _details: Union[ya_market.models.demand.Demand, NoneType] = None
)
```

#### Instance variables

```text
details
```

```text
id
```

#### Methods

#### close

```text
def close(
    self
)
```

#### delete

```text
def delete(
    self
)
```

#### events

```text
def events(
    self
) -> AsyncIterator[yapapi.rest.market.OfferProposal]
```

