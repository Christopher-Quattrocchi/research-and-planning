# research-and-planning

3/11: Python on freeCodeCamp all day.
3/12: Continue in tutorial hell for python
3/13: Should reach the end of tutorials today, after that I can work on the assignments on freeCodeCamp to get my cert and learn how to actually apply stuff.
3/14: Was optimistic. Finishing the last tutorial now, can begin the actual projects soon. Friday and the weekend will likely be devoted to that

3/18: freeCodeCamp python cert earned, beginning to learn about crypto bots. 

Bought two crypto bot courses on udemy. Starting with the shorter program. The point is to have the bot live on the cloud, and access a decentralized crypto exchange. The bot will message your phone with updates. Hopefully I learn a lot from these courses, the idea will be to go along with the coding and then heavily modify it so that it's mine.

Researching kraken, dydx, and CEX exchanges. Probably will choose between CEX and dydx.

dydx not available in US, but I can access it with a VPN

Research VPN

Bought Mullvad VPN, even though I may choose to use CEX instead.

Research CEX API. Can generally do what I'm looking to do for free.

Watching videos from the udemy course, specifically trading strategies. 
Vocab to remember: Statistical arbitrage, cointegration, spread, z-score, hedge ratio, half-life, position sizing. (pip value, forex) zero-crossings. Kelly Criterion

The python library I'll probably be using is statsmodels. 

cointegration: 

statistical arbitrage: cares about price diff convergence and divergence behaviour between two assets

spread: formula is series1 - (half life x series2) A spread's z-score is useful to tell us how much the spread is deviating from its mean, and how many times the standard dev of the spread can fit into that. Identifies larger movements than avg in the spread, in either direction.

half-life: how long for spread to revert back. Bot should look for low half-life (so long as it is positive!) under 24ish?

Kelly Criterion: "position sizing matters". "Fractional Kelly Criterion as an alternative". Use machine learning to decide how much to apply (advanced). Determines what percent of your capital to allocate to a given trade. Using Kelly Criterion you can guarantee a sustainable profit with a 4-5 percent edge. Granted you can't always guarantee that, but sometimes you can. If you have a 51-49 percent edge, you allocate 2 percent of your capital. If you have a 55-45 edge, you allocate 10. success chance-failure chance

Position sizing/risk management/more kelly criterion: Probably shouldn't use leverage as a beginner. Leverage is good for hedging. If you have 100, lose ten, have 90. You can't just gain 10 percent to get back to 100. Lose ten, but must gain more. Shifts odds against you. Enemy is trading cost/leverage. Should look into which markets have the best costs. The exchange is effectively a casino. Need a 54 percent win chance to overcome the fees and make a profit. Guy is claiming statistical arbitrage allows you to be the casino but I have no idea what he's on about.

-------------------------

3/19: Today will be largely dedicated to starting my initial build, and listening/reading explanations of how the various parts of the bot work. Not sure how many days this part will take. I don't want to just do a code-along obviously, so it should be heavily modified.

Looks like some of this is outdated, as the goerli test net is going down soon. I'll probably have to interface with something else, which is fine. Also, I will probably connect this bot to CEX, as opposed to dydx. 

Trying to figure out the testnet stuff. Using goerlifaucet for the time being. They've added security measures, now you need a small amount of real money in the main net before they will allow you to use the test net. Buying a little monero on kraken and sending it to metamask (I think) so that goerli will send me fake ethereum.

Successfully added ethereum to my metamask wallet, and was able to connect to goerli and get 0.2 fake ETH

Problems with goerli test net. The fake ethereum was sent, but does not appear to be registering in my testnet wallet. 

Switching to ethereum sepolia, a more supported test net. Was able to get it to send fake ethereum, and it actually registered.

Connected metamask with dydx. Decided to go with that after all, as the process is unfamiliar and I'd like to see it done first. I do plan to switch to CEX, I think that would be a good challenge. Used dev tools to go into local storage and find a bunch of keys and other values that will be necessary later. Specifically the STARK_KEY_PAIRS and API_KEY_PAIRS

Learning to connect python to dydx

Version changes making this difficult. As far as I can tell I'm following the doc but the v4_client_py module for dydx isn't being recognized. 

Decided to stick with v3 for now. Will change over to v4 as part of an updated build.

Beginning to write code for the bot and learning about what parameters are necessary

Able to connect wallet to dydx exchange api with python. Next, I have to be able to place an order and get data.

What data I need for now: historical price data, 1hr time can be debated. is the opinion of the trader I'm following. Number of candles must be edited
For orders: position_id, market, side, order_type, post_only, size, price, limit_fee, expiration_epoch_seconds, time_in_force. Once confident, look at limit

Able to get market data and make orders

Setting up VS Code environment for project
There are 78 packages to install. Trying to get them to work and make sure things are compatible. 
Everything installed, all errors resolved. 

Beginning build of alpha/mvp version
Things that will matter: Constants. Amount, Mode, Trigger. Get prices, manage open trades, clear all trades, open trades (effectively CRUD)

---------------------------------------------

Building app. What it has to do: Connect to DYDX, place market order, abort all open orders, construct market prices, store cointegrated pairs (I don't remember what this means!), and while true: manage existing trades, and open positions

Blew everything up with compatibility issues

Fixing things slowly

----------------------------------------------

3/21

Still fixing incompatibilities

Total defeat. Giving up, rewriting the whole thing in v4. The list of dependencies is absolutely endless, nothing is compatible. I can't find help, chatgpt doesn't work, etc. 

Environment finally working after endless registry editing and other nonsense. I have a better idea how to set up and manage environments now. There are problems when I run main.py and try to connect to dydx to close orders. The console gives me wrong info about how much money I have, and doesn't seem to successfully close the open orders. Still, progress.

--------------------------------------------------

3/25
Had to upgrade dydx-v3-python to work with sepolia network. Surprisingly, this didn't break dependencies. Bot can now successfully close open orders

BUGFIX: Typo prevented bot from constructing market prices. Resolved

Tried for a while to calculate cointegration and save cointegrated pairs. Was using a newer, apparently better method to calculate cointegration, but I couldn't get it to work with the API somehow. The old version is fine, and should do what it needs to. I don't understand why the newer version doesn't work and would like to.

Bot saves cointegrated pairs to a csv file

Working on bot agent. The bot agent will open and check trades

Bot Agent more or less built, not yet tested

---------------------------------------------------------
3/26

Building trading behavior

Endless code along sections

Nearly done finishing main bot behaviors - placing orders, closing orders, analyzing the market, connecting wallet to api, etc. Most of the coding done. Next sections are about incorporating telegram so that the bot can warn you if it screws up, and hosting it on the cloud. At that point I have the fully functional bot. I've learned some, but once I have the bot I'll dig into it and have chatgpt/somebody break down exactly what's going on, maybe make a chart of it. Then I can begin planning the switch from metamask to rabby, and from dydx3 to dydx4 (or CEX). After that, I can examine the trading behavior in greater depth and see if I can optimize it further. 

----------------------------------------------------------
3/27

Finishing main bot behaviors, only thing left is setting up telegram and hosting it on the cloud

Nevermind, more coding

Most functions done but having trouble getting certain sections of code to trigger when they should

------------------------------------------------------------
3/28

Trading bot works! Placing and making trades on the exchange. Must be run through the command line. This is great, but I don't think it's actually supposed to work yet?

Trial run in progress

Next will be enabling it to give error messages. 

Note: people on the statistical arbitrage discord are saying that it can be very hard to make a profit like this because of gas fees. This is something I will have to address with my bot, either by finding some formula to tell me the max acceptable gas fee while making a profit, or by diversifying the trading strategies that the bot can use (or both)

Learning how to deploy the bot to the cloud

Bot can message telegram on my phone

Bot has error messages for all relevant errors

Advantage of the cloud is I can control when it runs more easily

Using EC2. Creating security group.

Bot running on the cloud, and is correctly updating my phone via telegram. Going to leave this running for the foreseeable future. I need to learn about how gas prices affect this, and how the bot works in a more detailed and thorough way. Some of the crypto-heads in the trading discord think that there are easier strategies than statistical arbitrage, so I will try to learn more and incorporate that. Rabby seems to be a straight upgrade to metamask, so I need to think about switching that. An issue is that I have an insane amount of dependencies, and they're all pretty old. I'd like to make an updated version as I already had to change stuff to get this one to even run. There must be a way to update it without breaking everything. I need to create a UI for this eventually - an option to run on the cloud is nice and convenient, but I want to be able to alter parameters and behavior without editing the code or using the command line.

Need to incorporate a cron file for full automation

Need to connect this to a database instead of using a json file

---------------------------------
3/29 

after doing some more research and chatting with crypto heads, ive come to the conclusion that statistical arbitrage, as a primary strategy for a crypto bot, has a lot of problems and may not be viable. the bot is doing okay on the test net, but fees kill it. Apparently the way to make money is to have positions on multiple platforms and wait for a discrepancy in the price of a coin. the coin should be chosen carefully, it sbouldnt be a huge coin less prone to volatility, but it shouldnt be a coin that has a realistiv chance of cratering? something like that. Anyway, i have research to do before I fully understand what this strategy eould look like step by step, and i think this will be mucj more complicated behavior to create. but i have to figure this out for the bot to actually be useful.

------------------------------------
4/1
Was pretty sick this weekend/this morning, starting a bit late. The stat arb trading tactic works well, has been running with no errors since friday. So I built a trading bot with the simplest trading behavior (stat arb), but this is also the least useful trading behavior. For most people currently, these bots are almost guaranteed losers over the long term. I will be transitioning this bot from stat arb (trying to take advantage of price variations/predict reversion to the mean) to an arb bot (holds positions on the same coins on different exchanges, and takes advantages of price discrepancies. This behavior is more complex, but with some know-how on the side of the guy running the bot, will likely be profitable. Long term, the best kind of bot to build would be a so called "front runner" bot, that looks for huge trades on DeFi networks, and then very quickly makes a trade to take advantage of the price change the large trade will cause. These bots will make the most money, but are by far the most complex and difficult to make work well. The code will need to be written in a fast language, and it will need to be written efficiently, and it will need to be hosted on a very fast service (default aws probably not good enough, have to shell out for speed). But if a front runner bot is optimized to the point where it is faster than most, it can make a lot of money. This will be a good long term challenge. First step is adding arbitrage to stat arb as a tactic that the bot can use.

I am sort of at a crossroads. THe bot is running, has no UI, if I'm going to make it an arbitrage bot it needs a UI as the user will have to enter information frequently enough that updating to code to change behavior is suboptimal








