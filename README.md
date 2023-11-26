# Eve EA

Developer: Forex Robot Easy Team

Website: [forexroboteasy.com](https://forexroboteasy.com)

This code is a sample implementation of Eve EA, a multi-currency and fully automated trading system for the American trading session. Please note that ForexRobotEasy is not the official developer of this product. We only provide this code as a demonstration of how the product can work.

For detailed reviews and trading results of this product, please visit the [product review page on forexroboteasy.com](https://forexroboteasy.com/forex-robot-review/review-eve-ea-multi-currency-and-fully-automated-trading-system-for-american-trading-session/).

## Features
- Trades multiple currency pairs: EURNZD, AUDNZD, EURAUD, GBPCAD, NZDCAD, EURGBP
- Executes trades during the specified trading session
- Avoids trading during the rollover period
- Sets stop-loss and take-profit levels for each trade

## Usage
1. Define the currency pairs to be traded by modifying the `currencyPairs` array.
2. Set the trading session start and end times by modifying the `sessionStartTime` and `sessionEndTime` variables.
3. Set the rollover period start and end times by modifying the `rolloverStartTime` and `rolloverEndTime` variables.
4. Specify the stop-loss and take-profit levels by modifying the `stopLoss` and `takeProfit` variables.
5. Customize the `OnInit` and `OnDeinit` functions if necessary.
6. Implement the `OrderSend` function to execute buy and sell orders according to your trading strategy.
7. Add any necessary custom functions for managing multiple currency pairs and adjusting trading parameters.

## Example
```mql5
// Define the currency pairs to be traded
string[] currencyPairs = {'EURNZD', 'AUDNZD', 'EURAUD', 'GBPCAD', 'NZDCAD', 'EURGBP'};

// Define the trading session start and end times
datetime sessionStartTime = D'19:00';
datetime sessionEndTime = D'24:00';

// Define the rollover period start and end times
datetime rolloverStartTime = D'00:00';
datetime rolloverEndTime = D'01:00';

// Define the stop-loss and take-profit levels
double stopLoss = 50.0;
double takeProfit = 100.0;

// ...

//+------------------------------------------------------------------+
//| Expert start function                                            |
//+------------------------------------------------------------------+
void OnTick()
{
   // Check if the current time is within the trading session
   if (TimeCurrent() >= sessionStartTime && TimeCurrent() <= sessionEndTime)
   {
      // Check if the current time is not within the rollover period
      if (!(TimeCurrent() >= rolloverStartTime && TimeCurrent() <= rolloverEndTime))
      {
         // Loop through each currency pair
         for (int i = 0; i < ArraySize(currencyPairs); i++)
         {
            // Place a market order to enter the market
            OrderSend(currencyPairs[i], OP_BUY, 0.01, Ask, 0, Bid - stopLoss * Point, Bid + takeProfit * Point, 'Eve EA', 0, 0, Green);
         }
      }
   }
}

// ...
```

Please note that the `OrderSend` function needs to be implemented according to your specific trading strategy.

For more information on the official developer of this product, please visit MQL5.
