---
description: >-
  This document explains the intricate pricing mechanism for the pawnshop
  system, detailing how item prices dynamically change based on market activity.
---

# Pricing System

## Price Components

* <mark style="background-color:yellow;">**Base Price**</mark><mark style="background-color:yellow;">:</mark> The initial, predefined price for an item
* <mark style="background-color:blue;">**Current Price**</mark>: A dynamic value that fluctuates based on market interactions
* <mark style="background-color:green;">**Price Range**</mark>: Always between 20% and 400% of the base price

## **Configuration Parameters**

{% code title="" overflow="wrap" fullWidth="false" %}
```lua
Config.PriceFluctuation = {
    baseFactor = 0.05,              -- Base price change rate (5%)
    noActivityDivisor = 200,         -- Minimal change during market inactivity
    salesRatioThresholdHigh = 1.2,  -- Price drops when sales significantly exceed purchases
    salesRatioThresholdLow = 0.8,   -- Price rises when purchases significantly exceed sales
    singleActivityMultiplier = 0.6, -- Smaller changes with one-sided market activity
    minMultiplier = 0.2,            -- Minimum price as % of base price (20%)
    maxMultiplier = 4.0             -- Maximum price as % of base price (400%)
}
```
{% endcode %}

***

## Pricing Example:

### <mark style="background-color:yellow;">Example 1:</mark> Diamond Ring

```lua
Config.ProductLists = {
    ["jewelry"] = {
        [1] = {
            productName = "diamond_ring",
            productLabel = "Diamond Ring", 
            productPrice = "500",      -- Base Price
            moneyType = "money"        -- Currency Type
        }
    }
}
```

#### Price Scenarios

<table data-full-width="false"><thead><tr><th>No Activity Scenario</th><th>High Sales Scenario</th><th>High Purchase Scenario</th></tr></thead><tbody><tr><td><p><mark style="background-color:blue;">Base Price: $500</mark></p><ul><li>Market Activity: No sales or purchases</li><li>Price Change: Gradual increase</li><li>New Price: $500.38 (0.075% increase)</li></ul></td><td><p><mark style="background-color:blue;">Base Price: $500</mark></p><ul><li>Sales: 10 rings</li><li>Purchases: 5 rings</li><li>Sales Ratio: 2.0 (> 1.2 threshold)</li><li>Price Change: Decrease (0.6%)</li><li>New Price: $497.00</li></ul></td><td><p><mark style="background-color:blue;">Base Price: $500</mark></p><ul><li>Sales: 5 rings</li><li>Purchases: 10 rings</li><li>Sales Ratio: 0.5 (< 0.8 threshold)</li><li>Price Change: Increase (0.75%)</li><li>New Price: $503.75</li></ul></td></tr></tbody></table>

### <mark style="background-color:yellow;">Example 2</mark>: Phone

```lua
Config.ProductLists = {
    ["electronics"] = {
        [1] = {
            productName = "phone",
            productLabel = "Smartphone", 
            productPrice = "1000",     -- Base Price
            moneyType = "money"        -- Currency Type
        }
    }
}
```

#### Price Scenarios

<table data-full-width="false"><thead><tr><th>Balanced Market</th><th>Market Oversupply</th><th>Market Scarcity</th></tr></thead><tbody><tr><td><p>Base Price: $1000</p><ul><li>Sales: 8 phones</li><li>Purchases: 8 phones</li><li>Sales Ratio: 1.0 (between 0.8-1.2)</li><li>Price Change: No significant change</li><li>New Price: $1000</li></ul></td><td><p>Base Price: $1000</p><ul><li>Sales: 15 phones</li><li>Purchases: 5 phones</li><li>Sales Ratio: 3.0 (> 1.2 threshold)</li><li>Price Change: Decrease (0.6%)</li><li>New Price: $994.00</li></ul></td><td><p>Base Price: $1000</p><ul><li>Sales: 5 phones</li><li>Purchases: 15 phones</li><li>Sales Ratio: 0.33 (< 0.8 threshold)</li><li>Price Change: Increase (0.75%)</li><li>New Price: $1007.50</li></ul></td></tr></tbody></table>

## Price Calculation Breakdown

### Price Influence Factors

1. <mark style="background-color:purple;">**Sales-to-Purchase Ratio**</mark>
   * Ratio > 1.2: Price Decreases
   * Ratio < 0.8: Price Increases
   * Ratio between 0.8-1.2: Price Remains Stable
2. <mark style="background-color:blue;">**Fluctuation Factors**</mark>
   * `baseFactor (0.05)`: Controls price change sensitivity (5% base rate)
   * `noActivityDivisor (200)`: Minimal price increase during market inactivity
   * `singleActivityMultiplier (0.6)`: Reduces price impact of one-sided market

### Price Limits

* **Minimum Price**: 20% of Base Price
  * Diamond Ring: Minimum $100
  * Phone: Minimum $200
* **Maximum Price**: 400% of Base Price
  * Diamond Ring: Maximum $2000
  * Phone: Maximum $4000

## Strategic Considerations

### For Players

* Monitor item prices before selling/buying
* Diversify selling to prevent market oversaturation
* Take advantage of price fluctuations

### For Server Administrators

* Adjust `Config.PriceFluctuation` parameters to fine-tune economic dynamics
* Experiment with different `baseFactor` and threshold values
* Balance between realistic pricing and engaging gameplay

### Advanced Tips

* Lower `baseFactor` (e.g., 0.01) for more stable prices
* Increase `baseFactor` (e.g., 0.05-0.1) for more dynamic, noticeable price changes
* Adjust `salesRatioThresholdHigh/Low` to control price sensitivity (tighter thresholds = more responsive)
* Use `singleActivityMultiplier` to prevent extreme price shifts
* Adjust `minMultiplier` and `maxMultiplier` to set price boundaries (current: 20%-400%)

{% hint style="warning" %}
**Note**: This pricing system provides a dynamic, responsive economic experience that encourages player interaction and strategic market participation.
{% endhint %}
