# [Trading View](http://balupton.com/tradingview) Strategies

Naming convention are female names iterating through letters of the english alphabet. Once Z is done, restart at A.

This naming convention was done to promote short unique and memorable names, which are described by their accompanying text. As descriptions masquarding as names, are not memorable, short, unique, nor effective.


## Alice

Preview:

- [Strategy](https://www.tradingview.com/script/io4a1E6r-bal-alice-strategy/)
- [Study](https://www.tradingview.com/script/fI0Pd71c-bal-alice-study/)

Prescription:

- Chart Type: Renko
- Long Enter: After X Rising Blocks
- Long Exit: After X Falling Blocks
- Short Enter: After X Falling Blocks
- Short Exit: After X Rising Blocks

Method:

1. `rising` and `falling` functions
1. `change(time)` so only complete blocks are counted

Pros:

1. allows customisation of streak size
1. easy algorithm
1. adaptable to different change internals
1. backtesting goes back a long way

Problems:

1. Trading View's backtester on renko charts places trades at prices that do not match up with the realtime price
1. Trading View's `rising` and `falling` do not seem to work accurately on renko charts, making this strategy risky in practice


## Bethany

Preview:

- [Strategy](https://www.tradingview.com/script/81bFZHWd-bal-bethany-strategy/)
- [Study](https://www.tradingview.com/script/0ZcQwovr-bal-bethany-study/)

Prescription:

- Chart Type: Candle Stick
- Long Enter: After 2 Rising Renko Blocks
- Long Exit: After 1 Falling Renko Blocks
- Short Enter: After 2 Falling Renko Blocks
- Short Exit: After 1 Rising Renko Blocks

Method:

1. `renko` function
1. use `valuewhen(change(RenkoClose))` several times to get last few block values
1. use manual comparison to figure out current trend

Pros:

1. at 1 minute change interval on chart type, it appears to reproduce similar results to the renko chart
1. more accurate backtesting than Alice

Problems:

1. `renko` function returns a series that has values for every minute, rather than just the changes. This means you cannot combine it with other indicators.
1. ambigious combination of the chart type change interval, and `renko` function resolution
1. backtesting does not go back that far (a few days to a week or so)
1. not easy to customise streak size


## Candice

Preview:

- [Strategy](http://www.tradingview.com/script/EqaAAeCj-bal-candice-strategy/)
- [Study](https://www.tradingview.com/script/bT9L205H-bal-candice-study/)

Prescription:

- Chart Type: Candle Stick
- Long Enter: After X Rising Renko Blocks
- Long Exit: After X Falling Renko Blocks
- Short Enter: After X Falling Renko Blocks
- Short Exit: After X Rising Renko Blocks

Method:

1. `renko` function
1. use a for loop to find renko bar changes, and establish trend direction and streak size

Pros:

1. allows customisation of streak size
1. more accurate backtesting than Alice

Problems:

1. `renko` function returns a series that has values for every minute, rather than just the changes. This means you cannot combine it with other indicators.
1. ambigious combination of the chart type change interval, and `renko` function resolution
1. backtesting does not go back that far (a few days to a week or so)
