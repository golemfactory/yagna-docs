# Writing your own provider's market strategy

## LeastExpensiveLinearPayuMS

Let's look at LeastExpensiveLinearPayuMS code.

```python
class LeastExpensiveLinearPayuMS(MarketStrategy, object):
    """A strategy that scores offers according to cost for given computation time."""

    def __init__(self, expected_time_secs: int = 60):
        self._expected_time_secs = expected_time_secs

    async def decorate_demand(self, demand: DemandBuilder) -> None:
        """Ensure that the offer uses `PriceModel.LINEAR` price model."""
        demand.ensure(f"({com.PRICE_MODEL}={com.PriceModel.LINEAR.value})")

    async def score_offer(self, offer: rest.market.OfferProposal) -> float:
        """Score `offer` according to cost for expected computation time."""

        linear: com.ComLinear = com.ComLinear.from_properties(offer.props)

        if linear.scheme != com.BillingScheme.PAYU:
            return SCORE_REJECTED

        known_time_prices = {com.Counter.TIME, com.Counter.CPU}

        for counter in linear.price_for.keys():
            if counter not in known_time_prices:
                return SCORE_REJECTED

        if linear.fixed_price < 0:
            return SCORE_REJECTED
        expected_price = linear.fixed_price

        for resource in known_time_prices:
            if linear.price_for[resource] < 0:
                return SCORE_REJECTED
            expected_price += linear.price_for[resource] * self._expected_time_secs

        # The higher the expected price value, the lower the score.
        # The score is always lower than SCORE_TRUSTED and is always higher than 0.
        score = SCORE_TRUSTED * 1.0 / (expected_price + 1.01)

        return score
```

 `fixed_price` \(cena za start\) + price for second CPU \* oczekiwany czas obliczeń + cena za sekundy TIME \* oczekiwany czas obliczeń

fixed\_price \(cena za start\) + price for second CPU  _oczekiwany czas obliczeń + cena za sekundy TIME_  oczekiwany czas obliczeń + random\(20\)

if \(offer.props\(\)\["golem.node.id.name"\] == "manchester.3"\) { return SCORE\_REJECTED; }



```python
def sample_cheap_offer(offer_list):
    # in each query calculate the mean of score of given offer list 
    _mean   = getMeanOfScore(offer_list)
    # get random sample from given list
    _sample = randomChoice(offer_list)

    # check if score of sample is greater or equal to the average
    if(_sample.score => _mean) {
        # if it is return the sample
        return _sample;
    }
    # if not call the same operation recursively, until it matches to a score lte _mean condition  
    sample_cheap_offer(offer_list)
```

