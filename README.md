# 👉Pointing.so
On-chain SDK for managing gamfield points for your applications powered by NEAR Protocol


## Use Cases
* Use to convert community airdrops for token generation events
* Query points for weeks for community based payouts for existing tokens
* Use to gamify and create system to track and retaining on chain users


## Front End Repo

While most of these rewarding of points will be facilitate via SDK inside your app using your account based “API” key. It will 

Create Point System
* Manage Point Systems
* Add A Badge
* Add Action

View Action
* See everyone rewarded by action (need indexer for this)
* Reward list of users via csv or textbox this action

View Badge
* Possibly to reduce expiry or remove from everyone
* Reward list of users via csv or textbox this badge

Payouts
* Easy pay batches via tieslot and then mark a certain number of points for each user claimed

View User
* Admin review or revoke badges and deduct point with reason

View Leaderboard
* Query by badges, query by action, queries by dates, query by most to least


## SDK

PointSystems consist of actions and badges that serves as base points and boosters. Point systems can have an owner, transfer ownership and add admins to allow for other servers or wallets to handle point logic and distribution like meta transactions relayers or intent based systems.

Points can have delegated admin for a set of badges and actions

All awards emit events for debugging and logging.

Badges have
* Name 
* Description
* Icon
* Optional: Expiry: unix timestamp // usually calculated from fix set amount of time from when awarded
* Boosters Type & Amount: A fix number of points or a multiplier to the action 
* Cardinality: 1: default 1, denotes the number of the same badge 1 user can have
* Max Supply: unlimited aka cardinality x total users: or limited in terms of rewarding. Returns error message

Actions
* Name
* Description
* Idcon
* Cardinality
* Number of Points

User
* Badges
* Actions
* Total Points
    * Total point count is incremented not calculated when querying user
* Claimed Points
    * Points deducted from user account after payments 
* Associated Wallets

Admin Can
* Simply Readjust total points w/ justification memo
* Take away badges or action for users along with associated points w/ justification memo

Payout
* Currency
* Chain // default NEAR
* User
* Amount of POints Claimed


### Contract
* Create PointSystem(Point System)
* Create Badge(Badge)
* Create Action(Action)
* GiveBadge(account, PointSystemID)
* GiveAction(account, PointSYstemID)
* AddPoints(account, PointSystemID)
* RemovePoint(account, PointSystemID)
* RemoveAction(account)
* RemoveBadge(account)
* AddAdmin(account, PointSystemID)
* RemoveAdmin(account, PointsystemID)
* GetPoints(account): float
* Payout(Payout) // logs payout and deduct potinf rom user


## FAQ
How are points different from tokens?
* Points are not tradeable as an asset and they may be rewarded, unless underlying accounts are traited
* Points are simply on chain ledgers that are updated, often with more centralization. Points can also live off chain.
What is on chain
* The calculation of points is on chain on NEAR
What if I want a different chain?
* This can be logged and mapped with user accounts, really just log this in payout
* Payouts will log which chain
