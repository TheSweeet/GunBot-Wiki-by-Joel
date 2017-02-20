             

The GUNBOT Users manual and license agreements
----------------------------------------------

> *Requirements:*

---------------

 - Both Windows and *nix are supported (probably OSX too but I don't have a box to try it). However, this is a NET and node.js program so run it on Win. If you really can't avoid to run it on nix, please PM me and I will guide you trough the installation process.
 - Software: if you are on Win just download and unzip the copy of your GUNBOT and start GUNBOT.exe. On *nix, you want to navigate to the GUNBOT folder and do npm install. It will install node.js and all dependencies (included poloniex wrapper)
 - Hardware: not at all a CPU consumer, it takes 20k of ram for each currency pair you trade

----------

Start GUNBOT.exe (or node gunbot if you are on *nix)
![enter image description here](https://ibin.co/35Kibir1XaWJ.png)


----------


Insert your poloniex API key and API secret and press continue. The GUNBOT will ask permission to poloniex and will return a success message if API keys are correct and if your GUNBOT license is valid. If anything goes wrong (i.e. you typed wrong credentials) it will give you an error message. Note: the GUNBOT license is unique and personal for each user. You can't login to another user's GUNBOT using your API keys. If you need more than 1 license, PM me for details.

 -  Once your login is successful, the GUNBOT configurator appears on your screen:
 ![enter image description here](https://ibin.co/35Kn6qTZkQNq.png)


----------

> Let's dig in those values but, if you leave default values as they are, you will start to make a profit (just change the currency pair to the currency you want to trade and start GUNBOT). 

 - **Currency pair:** trading other pairs than BTC/Altcoins is boring to me
   as there is not enough volatility on poloniex for my trading style,
   in the future (if users demand) I might add other poloniex markets.
   So, just type the poloniex symbol of the altcoin you want to trade
   against BTC. The format is 3 to 5 letters by poloniex market symbols
   (i.e. ETH for Ethereum, ETC for Etherum classic, XMR for Monero and
   so on).
 - **Margin to sell:** margin to sell when altcoin increases its value of x
   %. For example 2%. This value is a "minimum" value. It means you will
   probably get a higher profit, based on the instant your order is
   placed and other factors coming from the trading style you choose.
   GUNBOT will never sell at less than what you put in here tho (unless
   you set a STOP LIMIT loss. We will talk about STOP LIMITS later).
 - **Margin to buy:** margin to buy when altcoin decreases its value of x %.
   For example 2%. The price calculation is based on some indicators
   (you can read more here). What is important is that this value is
   continuously calculated based on the market trends. We will talk
   about indicators later, anyway: doesn't matter the market trends, you
   will always buy low and sell high.
 - **Security margin:** sell all your altcoin balance if its value decreases
   x % after you bought it. This is similar to a STOP LIMIT loss: do not
   put this value too close to the daily variation of the coin or you
   will lose money for no reasons unless you know what you are doing. We
   will talk about STOP LIMIT later.
 - **Max latest prices:** limit of latest prices to analyze when deciding if
   the price is growing or falling. For example: analyze latest 100
   prices will analyze latest 100 variations in price BTC/altcoin.
 - **Time delay price:** time, in seconds, to verify margin price again if it
   is frozen. Do not put this below 20 seconds or your IP will get
   banned from poloniex. Do not put this above 2 minutes or you will
   lose the right time to place an order. The default is 40.
 - **Minimum volume:** minimum 24h volume to determine if it is a good
   currency to trade: no volume == no volatility. Better to focus on
   more traded currencies to have more chances. This is only used in
   daily recommendations. If you know what you are doing, you can ignore
   this.
 - **Minimum variation:** Again this is only used in daily recommendations
   and it depends on your trading style indeed. I put default to 5% as
   the most of my trades occur between 2% up to 4% of profit per trade.
   You can change this to your own trading style. Beware: THIS IS NOT
   THE MINIMUM PROFIT TO BUY/SELL.
 - **EMA1 period:** this is the core indicator of GUNBOT algorithm (together
   with EMA2). Be careful to set these 2 parameters because will change
   the way you trade: time is in hours, the interval between EMA1 and
   EMA 2 should be doubled. If you set EMA1 to 2 hours, you should set
   EMA2 to 4 hours and so on. The shortest time you analyze, the more
   reactive is the price calculation: if you want calm and quiet trading
   with only a few trades per day, set EMA1 to 6 hours and EMA2 to 12
   hours; If you want more trades per day, set EMA1 to 2 or 4 hours and
   EMA2 to 4 or 8 hours. Do your own tests and set it when you think it
   satisfies your trading style.
 - **EMA2 period:** this is the core indicator of GUNBOT algorithm (together
   with EMA1). Be careful to set these 2 parameters because will change
   the way you trade: time is in hours, the interval between EMA1 and
   EMA 2 should be doubled. If you set EMA1 to 2 hours, you should set
   EMA2 to 4 hours and so on. The shortest time you analyze, the more
   reactive is the price calculation: if you want calm and quiet trading
   with only a few trades per day, set EMA1 to 6 hours and EMA2 to 12
   hours; If you want more trades per day, set EMA1 to 2 or 4 hours and
   EMA2 to 4 or 8 hours. Do your own tests and set it when you think it
   satisfies your trading style.
 - **Candlesticks period:** Self-explanatory. Allowed values are 5,15,30,60
   etc. I do not suggest you set it anything different from 15 minutes
   as trading with EMA above or below 15 minutes candlesticks is useless
   for this algorithm. If you really know what you are doing, change
   this to your desired values.
 - **Trading style:** We have to understand this carefully. I'm mostly
   aggressive: more trades per day (per hours, minutes if possible) with
   a smaller profit per trade. Sometimes I trade with Moderate style:
   fewer trades per day (some per hour, no trades in minutes). With the
   default value of 1% of minimum buy/sell, you can expect 1.50% up to
   2.50% profit per trade with Aggressive style and up to 4.50% per trade with Moderate style. Please do your own considerations, related
   to the altcoin you are trading and your own trading style.
 - **Start GUNBOT:** just do it! Cheesy. Once you push the button a new
   window will open with the real GUNBOT brain ready to run. I suggest
   you to not close the configurator window (just minimize it) because
   if you want to start a new pair to trade, you will have to type your
   API keys again.
![enter image description here](https://ibin.co/35KoIDUclwCN.png)
This is your GUNBOT brain at work. On top-left there are 3 buttons. Hover your mouse over them to see tips: start GUNBOT, stop GUNBOT and cleanup console logs. Push the first one (with the GUNBOT target icon) and it begins...
![enter image description here](https://ibin.co/35KqyJh1Z6Br.png)
It gives you some information at the start: date/time logs of starting point, your BTC balance, some information about currency pair you selected and the trading style. Check all information log: if anything is wrong, push the stop button, close the trading console and use the configurator again.
          If you let it run it starts its calculations: EMA1 and EMA2 values following the time in hours you set in the configurator, recommended currencies to trade today (with currency pair, last 24 volume, and variation); it will show up only currencies matching values you typed in the configurator (Minimum volume and Minimum variation), all other currencies are discarded. Once in 24 hours, the GUNBOT will update the list again. Then it starts its job with the pair to trade (picture below):
![enter image description here](https://ibin.co/35KrjSg7CgcZ.png)
