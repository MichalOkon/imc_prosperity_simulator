# IMC Prosperity game simulator

This tool provides a way to simulate rounds of the IMC prosperity trading game using custom traders. You can find the official page of the competition at https://prosperity.imc.com/dashboard.

### Usage
To run the simulation, use the following command in the console:


```
python runner.py <name_of_the_trader> <csv_filename_with_round_data> <csv_filename_with_trades_data>
```
Make sure to replace <name_of_the_trader> with the name of your custom trader and <csv_filename_with_round_data> and <csv_filename_with_trades_data> with the respective filenames.

For instance, to run the simulation with a sample trader, you can use the following command:
```
python runner.py sample_trader round_data/prices_round_4_day_1.csv round_data/trades_round_4_day_1_nn.csv
```
### Trades
When a trader places an order to buy or sell a specific quantity of a product, the order is filled according to the most favorable prices available. This means that if a trader wants to buy 3 pearls at a price of 10002, and there are two sell orders available with equal quantities of 2, one priced at 10001 and the other at 10002, then the order priced at 10001 will be filled completely, while only 1 unit of the order priced at 10002 will be filled.

As players do not have access to information about how other bots fill their orders, this feature is currently unavailable.

It is also important to note that the position limits are not imposed, as is the case in the official game, which means that the orders are not cancelled if the postion limit of a specific product is exceeded.
### Profit
The profit and loss for a product is determined by the following formula:

profit(product) = (money spent/received from trading the product) + (mid_price(product) * position(product))
