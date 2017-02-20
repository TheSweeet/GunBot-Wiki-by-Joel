             

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

 The price updates every x second you set in the configurator (Time delay price). Don't set it too long or you will miss trades. Don't set it <20 seconds or your IP will get banned from poloniex. With the price calculations it starts to set price to buy: in this example you see the last price < price to buy so....it places a buy order (picture below):

![enter image description here](https://ibin.co/35Kt4VmJbAci.png)

 The poloniex callback to your GUNBOT occurs and it notifies you a trade: order number, date/time, amount, rate, total, trade id, type. If you log in at poloniex, you can see that trade on your order book. By now, the GUNBOT gives out another important information: the price target to sell. This is a very important step: if we will need to make a manual trade, we will know what to do. We will talk about manual trades later.
 
![enter image description here](https://ibin.co/35KukATTwev2.png)

Target to sell information on price updater. In the picture above you can see the last price is > price target to sell so.....it sells! Profit 1.24%!!!

![enter image description here](https://ibin.co/35KvOkx5Egds.png)

> Note about fees: at poloniex, you will never know what fee you are paying before the trade. It depends on your tier status and if you are a maker or not. The most users are paying 0.15%-0.25% (depends if you are a maker on that trade). The GUNBOT assumes you are always a maker and it calculates the profit with the maximum fees: 0.25%. That's the reason why he sold at 1.24% of profit even if you set 1% of profit in the configurator.
          This is it! The GUNBOT does it over and over, repeatedly 24/7, even when you sleep! In one of the next posts on this thread, we will talk about possible ways to help the GUNBOT in case it needs your help because the market conditions are apocalyptic Wink 
          

The picture below shows the profit/loss calculation at poloniex website for the currency pair and the trades that occurred with GUNBOT while I was writing this tutorial Tongue
------------------------------------------------------------------------
*You can do it with any currency pair you want, 24/7...with your own GUNBOT!!!*

![enter image description here](https://ibin.co/34tK8VYfMhcB.png)

**If you are not able to duplicate this with your own GUNBOT, means your computer is broken so, I will refund what you paid to buy the GUNBOT to help you to buy a new computer Tongue.**

------------------------------------------------------------------------

             The GUNBOT Terms of Service
---------------------------
 - **Terms**
By purchasing the GUNBOT, you are agreeing to be bound by these Terms and Conditions of Use, all applicable laws, and regulations, and agree that you are responsible for compliance with any applicable local laws. If you do not agree with any of these terms, you are prohibited from purchasing, using or accessing a GUNBOT. The materials contained in the GUNBOT software are protected by applicable copyright.
 - **Use License**
Permission is granted to temporarily download one copy of the software for each purchased license of GUNBOT for personal, non-commercial transitory use only. This is the grant of a license, not a transfer of title, and under this license, you may not:
 - modify or copy the GUNBOT;
 - use the GUNBOT for any commercial purpose,
   or for any public display (commercial or non-commercial); 
 - attempt to decompile or reverse engineer any software contained in the GUNBOT
   package; 
 - remove any copyright or other proprietary notations from the
 - transfer the GUNBOT to another person without permission from
   the original coder (hereby defined as guntharLab or Gunthar).

This license shall automatically terminate if you violate any of these restrictions and may be terminated by guntharLab or Gunthar at any time. Upon terminating your use of the GUNBOT or upon the termination of this license, you must destroy any downloaded software in your possession whether in electronic or printed format.
3. **Disclaimer**
The GUNBOT software packages are provided “as is”. The original coder makes no warranties, expressed or implied, and hereby disclaims and negates all other warranties, including without limitation, implied warranties or conditions of merchantability, fitness for a particular purpose, or non-infringement of intellectual property or other violation of rights or lost of money related to cryptocurrencies trading on Poloniex. Further, the original coder does not warrant or make any representations concerning the accuracy, likely results, or reliability of the use of the GUNBOT, included lost of money related to cryptocurrencies trading on Poloniex due to the different settings and configurations of the GUNBOT the end-user is allowed to change. However, there is an implicit "Money back guarantee": accordance with the Consumer Code , the customer has a period of 14 days of receipt of the GUNBOT to return it to Gunthar or guntharLab against the refund. This law is applicable and subject to conditions for all products shipped to the customer or downloaded from a server by Gunthar or guntharLab. Right to refund with the contractual conditions stipulated and the maximum time allowed for implementation of the entire process: maximum 14 days to the inquiry, from the date of receipt of the GUNBOT, ordered and maximum 30 days to return the GUNBOT within our walls. By our walls we define the official communication of the end-user of compliance to art.2 Use of license of this Terms of Service, comma 5: "Upon terminating your use of the GUNBOT or upon the termination of this license, you must destroy any downloaded software in your possession whether in electronic or printed format."

Any claim made after the period of 14 days will not be accepted. 

***3a. Conditions for the Money Back Guarantee***

   Due to the different configurations of the GUNBOT you may apply that
   could lead to trading at loss, there are some criteria for the Money
   Back Guarantee: 
   

 - You shall not use a Security Margin too close to the altcoin daily variation (see Common errors to avoid using the GUNBOT)
 - You shall not use a Margin to buy or Margin to sell higher than the daily variation of the coin's pair you want to trade (see Common errors to avoid using the GUNBOT)
 - You shall not stop the GUNBOT to run while there is a buy order placed at Poloniex order book with your API keys, unless you manually place a sell order with same amount of the buy order and rate => last buy rate + 0.25% as market fee (see Common errors to avoid using the GUNBOT)
 - You shall not trade a coin with a continuous downtrend during the past 48 hours (see Common errors to avoid using the GUNBOT)
 - You shall not trade a coin that has increased or decreased its market rate over 50% of its latest month average rate (see Common errors to avoid using the GUNBOT)
 - You shall not put manual orders with the same API keys your GUNBOT is operating unless it has been provably set because of a manual market adjustment of a GUNBOT automatic order, due to an increased/decreased market conditions over 20% of its latest 24 hours average rate (see Common errors to avoid using the GUNBOT)
 - You shall not allow other users/bots to login with the same API keys the GUNBOT is operating with
 - You shall previously communicate your intentions to purchase an extendable 15 days license as a commitment to adhere to the Consumer Code's Money Back Guarantee
 - You shall provide, upon request, any reasonable proof of trading at loss using the GUNBOT and the default values described in The GUNBOT User's Manual and coder's recommendations, included screenshots, archived pages and bot/system logs.
 - Any infringement to these Terms of Service and to the Conditions listed in this section 3a, will invalidate the Money Back Guarantee and a final GUNBOT license would been issued at your account and all your funds held in escrow released
 - You and the escrow service you provided, confirm this agreement by purchasing the GUNBOT license and by proceeding with the 15 days Money Back Guarantee license and holding funds in escrow
 - If, for any reason, you or your escrow service are unable to provide the above-mentioned proofs of good use of the GUNBOT configurations, the Money Back Guarantee would be invalidated and a final GUNBOT license would been issued at your account and all your funds held in escrow released
 - If you or your escrow service, fail to release the funds upon termination of a 15 days license or upon an infringement of these Terms of Service, you and your escrow service would be implied in an open scam accusation and if the overdue balance persists, to a Court of Law.
 
 4. **Limitations**
In no event shall Gunthar or its suppliers be liable for any damages (including, without limitation, damages for loss of data or profit, or due to business interruption,) arising out of the use or inability to use the packages of the GUNBOT, even if Gunthar or guntharLab or a Gunthar or guntharLab authorized representative has been notified orally or in writing of the possibility of such damage. Because some jurisdictions do not allow limitations on implied warranties, or limitations of liability for consequential or incidental damages, these limitations may not apply to you.
5. **Revisions and Errata**
The materials appearing on the GUNBOT's packages and software could include technical, typographical, or photographic errors. Gunthar or guntharLab do not warrant that any of the materials on its software are accurate, complete, or current. Gunthar or guntharLab may make changes to the materials contained on its software at any time without notice. Gunthar or guntharLab do not, however, make any commitment to update the materials.
6. **Links**
Gunthar has not reviewed all of the sites linked to its software and is not responsible for the contents of any such linked site like Poloniex. The inclusion of any link does not imply endorsement by Gunthar or guntharLab of the site. Use of any such linked website is at the user’s own risk. Poloniex is trademarks of Poloniex, Inc. Gunthar or guntharLab and the GUNBOT are not affiliated with or sponsored by Poloniex.
7. **Site Terms of Use Modifications**
Gunthar or guntharLab may revise these terms of use for its software at any time without notice. By using this software you are agreeing to be bound by the then-current version of these Terms and Conditions of Use.
8. **Governing Law**
Any claim relating to Gunthar or guntharLab shall be governed by the laws of the Republic of Italy without regard to its conflict of law provisions.

**PRIVACY POLICY**

Your privacy is very important to us. Accordingly, we have developed this Policy in order for you to understand how we collect, use, communicate and disclose and make use of personal information. The following outlines our privacy policy.
Before or at the time of collecting personal information, we will identify the purposes for which information is being collected.
We will collect and use of personal information solely with the objective of fulfilling those purposes specified by us and for other compatible purposes, unless we obtain the consent of the individual concerned or as required by law.
We will only retain personal information as long as necessary for the fulfillment of those purposes.
We will collect personal information by lawful and fair means and, where appropriate, with the knowledge or consent of the individual concerned.
Personal data should be relevant to the purposes for which it is to be used, and, to the extent necessary for those purposes, should be accurate, complete, and up-to-date.
We will protect personal information by reasonable security safeguards against loss or theft, as well as unauthorized access, disclosure, copying, use or modification.
We will make readily available to customers information about our policies and practices relating to the management of personal information.
We are committed to conducting our business in accordance with these principles in order to ensure that the confidentiality of personal information is protected and maintained.

Common errors to avoid using the GUNBOT
---------------------------------------

> There are some technical errors you must avoid to not loose money. They are related to the use of GUNBOT. The GUNBOT gives you the freedom to change options but you must know what you are doing:

 - We already said it: **dont trade an unreliable coin or a coin that is surging/dying**. As a start, select one or two of the most traded coins (ETH, ETC, XMR) and start to make a profit with them. You have time to expand your market and to invest more BTC later, when you learned what you are doing.
 - **Dont set a Margin to buy or Margin to sell too low or too high:** if you set Margin to buy or Margin to sell too low or too high, you will trade at loss because the fees or because the next price variation will eat your balance or you will have to wait 2 years before to see a trade (if ever).
 - **Do not set a security margin too close to the coin daily variation,** it will eat your money: I understand you probably are not happy to lose more than 10% of what you invested but, if the coin you want to trade got a 24 hour variation of 11%, it will sell all your coins at price to sell < price you bought, causing you a loss. Personally, i set stop limit to 60% because I watch the markets and if anything goes wrong I trade manually. Start with 60% of security margin you too, as I'm sure you will stay 24/7 with your eyes on your screen watching your GUNBOT at beginning  Grin: when you are confident enough and made some profit, you can start to play with security margin if you want. AGAIN: if you go to sleep with your security margin to 10%, it may happen overnight that you sell at loss.
 - **Do not set Max latest prices too low: 100 price variations are good.** You have to give your GUNBOT enough data to analyze to decide if we are bullish/bearish or static. The algo GUNBOT uses is a mix of trend and EMA for some decisions it makes to pre-sell or pre-buy: if you put this value too low it will confuse GUNBOT and you will probably loose some trades.
 - About EMA1, EMA2 and candlesticks: **this strategy has its standard which is 15 minutes of candlesticks period.** Playing with EMA over a period below or above 15 minutes candlesticks makes no sense. Try it yourself on poloniex: set EMA1 to 20 and EMA2 to 10 (BEWARE ON POLONIEX NOT ON GUNBOT!!!!) and then set candlesticks at 15 minutes. Look at EMA1 and EMA2 changing as you change candlesticks. Please on GUNBOT use candlesticks of 15 minutes and play with EMA1 and EMA2: if you rush to profit set them to 2-4 hours. If you are more relaxed put them to 4-8 hours. If you are my grandpa, set them to 6-12 hours and go to sleep: you will make profit anyway .
 - **NEVER EVER STOP YOUR GUNBOT WITHOUT A GOOD AND CONTROLLED REASON:** ok sorry, caps intended. The most common error I have seen with people using bots is to stop them just because they can. This is not the case of GUNBOT. There are 2 cases only you are allowed to put your hands on your running GUNBOT, and both are controlled (it means you know what you are doing).
1st case: it happens sometimes that a buy order is not completely fulfilled. The GUNBOT will wait. Soon as the partial order can fulfill, Poloniex will do it. Sometimes tho, the price changes with a partial order on the book. You have 2 possibilities: wait...and wait....and wait....or cancel your partial order on POLONIEX and let GUNBOT go ahead with the partial amount of coin. In this case, DO NOT TOUCH your GUNBOT and cancel the partial buy order on POLO. The GUNBOT will follow your order and will continue with its job. This is not a GUNBOT limit nor a Poloniex limit: this is just related to the coin availability at a certain price and a defined time (your order). I won't allow partial orders to be fulfilled with a different price like other bots do: it is too high risk to loose money. Just cancel your buy order if you see it stuck for hours on partial fulfillment. Maybe in a future release I will implement a saving order book locally but in my opinion, it is useless to persist with a trade at the risk of losing other 10 possible trades.
The second case you are allowed to put your hands on your running GUNBOT is part of the "dumps" and "dumbs" section so, we will talk about it later.

How to choose a coin to trade with GUNBOT
---------------------------------------
 ***Ok, there are some general rules:***
 

 - Depending on your trading style: high volume coins give you more
   frequent trades. You can trade low volume coins if you are a
   speculator of satoshis trades (for example STELLAR or QORA or
   DIGIBYTE) 
 - Do not trade with GUNBOT on surging coins or just premined coins: for example ZEC or dormant coins that just awakened to the moon: trade them manually
 - DO not trade with GUNBOT on falling coins: by falling coins, i didn't mean "dumps". Read news, ask on the forum: if a coin is about to die or have been dropping their price for DAYS, trade them manually, on an exchange that allows you to short.
 
***Theoretically, the best coin to trade appears like this:***
            
![enter image description here](https://ibin.co/34vf3CsOxLU4.png)

***Do not start to trade on coins like this:***
-----------------------------------------------

 
![enter image description here](https://ibin.co/34vgOZKlehcq.png)

***Nor like this:***
--------------------

 ![enter image description here](https://ibin.co/34vio7aMQfAb.png)

> What about if you started to trade on a coin like this? I will teach
> you how to not panic and how to eventually correct it manually,
> helping the poor GUNBOT to come out the shit you put it in .
> 

            A final note of this chapter about time to trade: like in forex and stocks, 
            there is more volume (and more trades opportunities) during EU time,
            because EU is in the middle of EAST and WEST (USA and Asia)
            so their office time takes a little part from both WEST nights and EAST mornings.
            Expect less volume (and so fewer trades) while Americans sleep and while Asians sleep.
  
 How To Profit
---------------------------------------
 ***So: buy low and sell high. Right! But...how to? How to know when it is low enough to buy? And how to know when it is high enough to sell?***
 

Let's start from beginning: cryptocurrencies trading is not like FOREX or Stocks trading. You simply CANT loose 10 to 15 years of your life studying indicators and meaningless drawings on a graphic. By then...your favorite crypto coin would be dead...

          But...if indicators and shits like that are meaningless...
          why Poloniex (and other exchanges) bothered so much to provide us
          with nice candlesticks graphic and a bunch of indicators?
          Ok here is the answer: because they let you know when it is low enough to buy or high enough to sell.
          You think I'm crazy uh...ok let's see: the following graphic shows a random period
          of a random cryptocurrency trading against BTC. 
          Besides candlesticks, i enabled 2 lines of 2 different colors: EMA1 and EMA2

![enter image description here](https://ibin.co/34vAbqfvuV3G.png)

EMA1 and EMA2 are kinda of a weighted average of price and quantity. Literally, it is Exponential Moving Average. The number 1 and the number 2 on the side of EMA, indicate 2 different periods of calculations. Usually, EMA1 is calculated on longer periods and EMA2 on shorter periods. It indicates the average moving (up or down) of the latest prices calculated in the defined time. I suggest you set EMA1 to 2 hours and EMA2 to 4 hours if you want recurring trades in one hour or higher (4 to 8 hours or 6 to 12 hours) if you are fine with fewer trades per hour/day. 
              Next: when to buy? When to sell? Ok, this is the answer: there is a space between EMA1 and EMA2 (sometimes there is not and they run like they were equals). Every price below the bottom of EMA1 and EMA2 is a time to buy. Every price above the top of EMA1 and EMA2 is a time to sell. So: let's use some new colors now: yellow to buy and azure to sell. The graphic above would become like this:

![enter image description here](https://ibin.co/34vJBrt4vQBH.png)


             When you see the yellow it is time you buy.
             When it is azure it is time to sell. You can try it with manual trades!
             There is a gray area between the EMA1 and EMA2: it is a pre-buy area and a pre-sell area.
             If the trend is going down, get ready to buy, if the trend is going up get ready to sell.
             HOLD YOURSELF to buy or sell in the gray area! 
             You will know if the trend is really going up or down AFTER.
             So again: buy in yellow area and sell in azure. 
             Try it! This is what GUNBOT does: repeatedly, 24/7, even when you sleep. Think about it...

Are there any apocalyptic cases that this will not work? Yes: we will talk about it later, in the topic about the "dumps" and "dumbs".

 How Not To Panic During A Dump
---------------------------------------
 ***Ok, this is probably the most waited topic of this thread so I'm going to be straight: when a dump starts there is nothing you can do. It will continue until the last penny has been sold. I will give you 2 weapons to fight the dumpers: a psychological one and a technical one.***
 

 - Understand that trading is possible only because the price goes down and then it goes up. If it goes only up or only down, you can't trade. None would. So, take the bears as a part of the scenario. Accept it. Like it. As the price goes down, you know it will go up again, over and over. Oh wait....your GUNBOT bought when the price was up? Ok then, here to you the solution:
 - The Bollinger Band: Poloniex was smart enough, they gave us another indicator to trade with crypto. What is the Bollinger Band exactly? It is an indicator of the volatility of the coin, related to the quantity of trades volume in a given instant. Open your Poloniex graphic and enable Bollinger lines, you will see something like this:
 
 ![enter image description here](https://ibin.co/34wIWzp8WcXX.png)
 
 The larger the Bollinger Band is the more volatility on the market. As the Bollinger Band tights, there is less volatility. Said that, how to use the Bollinger Band? Well: it is a technical support to your weak morale because of a dump. Look the next picture:
 
![enter image description here](https://ibin.co/34wLAuWNCdE8.png)


 ![enter image description here](https://ibin.co/34wN3MsLwIXH.png)

> After any azure arrow, there is a bearish trend. The right moment for
> a change of the trend is when the candlesticks exit and THEN enter
> back inside the band. Sometimes they get very close to the band and
> the trend changes without crossing borders. Use the Bollinger Band to
> be aware of what is going on: it is a dump, yes, but you know exactly
> when it will stop and you know exactly when the bear will turn into a
> bull. Stay calm...take a deep breath....and don't stop the GUNBOT 

 So, do you like it? Did you ever see this? If yes: did you ever use the Bollinger Band as a tool to be aware you are not losing
 all your money and you don't have to stop your bot but it is just the
 wonderful world of trading going on? Well, now you know it...if you
 need more help on this, just shoot me a PM and please again...don't
 stop your GUNBOT, let it do its job for you...I didn't code emotions
 in it...
             



  
  





