---
description: >-
  This document explains the intricate pricing mechanism for the pawnshop
  system, detailing how item prices dynamically change based on market activity.
---

# Pricing System

## Price Components

* <mark style="background-color:yellow;">**Base Price**</mark><mark style="background-color:yellow;">:</mark> The initial, predefined price for an item
* <mark style="background-color:blue;">**Current Price**</mark>: A dynamic value that fluctuates based on market interactions
* <mark style="background-color:green;">**Price Range**</mark>: Always between 50% and 200% of the base price

## **Configuration Parameters**

{% code title="" overflow="wrap" fullWidth="false" %}
```lua
Config.PriceFluctuation = {
    baseFactor = 0.01,              -- Base price change rate (1%)
    noActivityDivisor = 1000,       -- Minimal change during market inactivity
    salesRatioThresholdHigh = 1.5,  -- Price drops when sales significantly exceed purchases
    salesRatioThresholdLow = 0.66,  -- Price rises when purchases significantly exceed sales
    singleActivityMultiplier = 0.5  -- Smaller changes with one-sided market activity
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

<table data-full-width="false"><thead><tr><th>No Activity Scenario</th><th>High Sales Scenario</th><th>High Purchase Scenario</th></tr></thead><tbody><tr><td><p><mark style="background-color:blue;">Base Price: $500</mark></p><ul><li>Market Activity: No sales or purchases</li><li>Price Change: Minimal (almost no change)</li><li>New Price: $500 (±0.1%)</li></ul></td><td><p><mark style="background-color:blue;">Base Price: $500</mark></p><ul><li>Sales: 10 rings</li><li>Purchases: 5 rings</li><li>Price Change: Slight Decrease</li><li>New Price: $495-$498</li></ul></td><td><p><mark style="background-color:blue;">Base Price: $500</mark></p><ul><li>Sales: 5 rings</li><li>Purchases: 10 rings</li><li>Price Change: Slight Increase</li><li>New Price: $502-$505</li></ul></td></tr></tbody></table>

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

<table data-full-width="false"><thead><tr><th>Balanced Market</th><th>Market Oversupply</th><th>Market Scarcity</th></tr></thead><tbody><tr><td><p>Base Price: $1000</p><ul><li>Sales: 8 phones</li><li>Purchases: 8 phones</li><li>Price Change: No significant change</li><li>New Price: $1000</li></ul></td><td><p>Base Price: $1000</p><ul><li>Sales: 15 phones</li><li>Purchases: 5 phones</li><li>Price Change: Decrease</li><li>New Price: $980-$990</li></ul></td><td><p>Base Price: $1000</p><ul><li>Sales: 5 phones</li><li>Purchases: 15 phones</li><li>Price Change: Increase</li><li>New Price: $1010-$1020</li></ul></td></tr></tbody></table>

## Price Calculation Breakdown

### Price Influence Factors

1. <mark style="background-color:purple;">**Sales-to-Purchase Ratio**</mark>
   * Ratio > 1.5: Price Decreases
   * Ratio < 0.66: Price Increases
   * Ratio ≈ 1: Price Remains Stable
2. <mark style="background-color:blue;">**Fluctuation Factors**</mark>
   * `baseFactor (0.01)`: Controls price change sensitivity
   * `noActivityDivisor (1000)`: Prevents price changes during low activity
   * `singleActivityMultiplier (0.5)`: Reduces price impact of one-sided market

### Price Limits

* **Minimum Price**: 50% of Base Price
  * Diamond Ring: Minimum $250
  * Phone: Minimum $500
* **Maximum Price**: 200% of Base Price
  * Diamond Ring: Maximum $1000
  * Phone: Maximum $2000

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

* Lower `baseFactor` for more stable prices
* Adjust `salesRatioThresholdHigh/Low` to control price sensitivity
* Use `singleActivityMultiplier` to prevent extreme price shifts

{% hint style="warning" %}
**Note**: This pricing system provides a dynamic, responsive economic experience that encourages player interaction and strategic market participation.
{% endhint %}
