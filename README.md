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
