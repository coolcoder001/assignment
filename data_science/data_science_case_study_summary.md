# Verve Group Data Science Case Study

## Problem 1: Estimating the Expected Win Rate

### Assumptions and Steps to Calculate Expected Win Rate

**Assumptions**:

1. **Independence of Auctions**: Each auction is assumed to be independent of the others. This means the outcome of one auction does not affect the outcome of another.
2. **Constant Bid Environment**: The number of competitors and their bidding strategies remain constant over the period the data was collected. Thus, the win rates calculated are reflective of a stable competitive environment.
3. **Complete Data**: The data provided is assumed to be complete and accurate. This means there are no missing records or errors in the win/loss counts and the number of events at each bid price.
4. **Homogeneity of Bids**: All bids at the same price are considered homogeneous, meaning the win rate for a bid price of $0.2, for example, is the same regardless of the time or specific auction context.
5. **First-Price Auction**: Since it's specified that this is a first-price auction, the win is solely determined by the highest bid without considering other auction types or variations.

### Steps to Calculate the Expected Win Rate

**1. Grouping the Data by Bid Price**:
- The data is grouped by the bid_price to aggregate the results of all auctions that had the same bid price.

**2. Calculating Total Events**:
- For each bid_price, the total number of events (auctions) is calculated by summing the events column for both win (win=1) and loss (win=0) outcomes.

**3. Calculating Win Events**:
- For each bid_price, the number of winning events is calculated by summing the events column where win=1.

**4. Calculating Win Rate**:
- The win rate for each bid price is computed by dividing the number of winning events by the total number of events for that bid price.

### Formula:

$$ \text{Win Rate} = \frac{\text{Win Events}}{\text{Total Events}} $$

### Detailed Explanation:

Refer to the notebook's Win rate calculation section for a step-by-step breakdown and code implementation.

By following these steps and assumptions, we can accurately estimate the expected win rate for each bid price in the auction dataset.

## Problem 2: Maximizing Net Revenue

To maximize net revenue, we calculated the net revenue for each bid price using the formula:

$$ \text{Net Revenue} = (\text{Advertiser Payment} - \text{Bid Price}) \times \text{Expected Win Rate} \times \text{Total Events} $$

**Assumptions**:

- **Advertiser Payment**: We assume the advertiser is willing to pay a fixed amount of $0.50 per win. This is a given constant in the problem.
- **First-Price Auction**: The cost to Verve for winning an auction is equal to their bid price, as it is a first-price auction.
- **Independence of Events**: Each auction is considered an independent event, meaning the results of one auction do not influence another.
- **Homogeneity of Bids and Competitors**: The win rates calculated from historical data are assumed to be applicable to future auctions under similar conditions.
- **No Additional Costs**: The calculation assumes there are no additional costs associated with bidding or winning other than the bid price itself.

Assuming the advertiser payment is $0.50, the net revenue calculations are summarized below:

| Bid Price | Total Events | Win Events | Win Rate | Net Revenue  |
|-----------|--------------|------------|----------|--------------|
| 0.01      | 100000       | 0          | 0.0%     | -$0.00       |
| 0.10      | 10000        | 3000       | 30.0%    | $1200.00     |
| 0.20      | 10000000     | 2000000    | 20.0%    | $600000.00   |
| 0.40      | 1000000      | 300000     | 30.0%    | $90000.00    |
| 0.50      | 100000       | 20000      | 20.0%    | $0.00        |
| 0.75      | 10000        | 3000       | 30.0%    | -$750.00     |
| 1.00      | 1000         | 600        | 60.0%    | -$300.00     |
| 2.00      | 100          | 70         | 70.0%    | -$105.00     |
| 5.00      | 10           | 8          | 80.0%    | -$360.00     |
| 9.00      | 1            | 1          | 100.0%   | -$8.50       |

The optimal bid price to maximize net revenue is **$0.2**, which results in the highest net revenue of **$600,000**.

## Conclusion

By bidding $0.2, we can achieve the highest net revenue given the provided data and the assumption that the advertiser pays $0.50 per win. This strategy balances the cost of the bid and the likelihood of winning the auction to maximize profit.
