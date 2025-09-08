[<img _ngcontent-c2="" src="https://avatars1.githubusercontent.com/u/28770833?s=88&v=4" style="background-color: transparent;">](https://ps3838api.github.io)


# FAQ
### How to find associated events?

One can use `parentId` from the  [Get Fixtures](https://ps3838api.github.io/docs/?api=lines#operation/Fixtures_V3_Get) to group associated events to the "parent" event. 

A few facts that can help:

 - We have different events for pregame and live, that can be distinguished  by `liveStatus`.
 - In some cases, we may have more than one live event for the same actual event, but we would never offer the same market on both events at the same time. 
 - Parent events are those that don't have `parentId`
 - Parent events are always pre-game ( `liveStatus`=0 or `liveStatus`=2), except in some cases for MLB league and ESports, where live events  ( `liveStatus`=1)  may be missing the  `parentid`
   
 
 Example:

 ``` json
 {
    "sportId": 29,
    "last": 148671597,
    "league": [
        {
            "id": 2331,
            "name": "Norway - 1st Division",
            "events": [
                {
                    "id": 837721686,
                    "starts": "2018-04-10T17:00:00Z",
                    "home": "Viking Fk",
                    "away": "Mjondalen",
                    "rotNum": "6751",
                    "liveStatus": 1,
                    "status": "O",
                    "parlayRestriction": 2,
                    "parentId": 834342247,
                    "altTeaser": false
                },
                {
                    "id": 834342247,
                    "starts": "2018-04-10T17:00:00Z",
                    "home": "Viking Fk",
                    "away": "Mjondalen",
                    "rotNum": "6751",
                    "liveStatus": 2,
                    "status": "I",
                    "parlayRestriction": 2,
                    "altTeaser": false
                }
            ]
        },
        {
            "id": 6816,
            "name": "Norway - 1st Division Corners",
            "events": [
                {
                    "id": 837721684,
                    "starts": "2018-04-10T17:00:00Z",
                    "home": "Viking Fk (Corners)",
                    "away": "Mjondalen (Corners)",
                    "rotNum": "6751",
                    "liveStatus": 1,
                    "status": "O",
                    "parlayRestriction": 1,
                    "parentId": 834342247,
                    "altTeaser": false
                },
                {
                    "id": 837721615,
                    "starts": "2018-04-10T17:00:00Z",
                    "home": "Viking Fk (Corners)",
                    "away": "Mjondalen (Corners)",
                    "rotNum": "6751",
                    "liveStatus": 2,
                    "status": "I",
                    "parlayRestriction": 1,
                    "parentId": 834342247,
                    "altTeaser": false
                }
            ]
        }
    ]
} 
```

There is a pre-game parent event id 834342247, that has associated live event id 837721686, but also 2 corner events in different league - one live event (837721684), while the other one for pre-game (837721615)

Introduction of `parented` eliminates a need for rotation numbers. 
Please note that in the next version of `/fixtures`, the `rotNum` property will be decommissioned.


### When is the market open for betting? 

A market ( `moneyline` , `spreads`, `totals`,  `teamtotal` ) in a period is open for betting if in [Get Odds](https://ps3838api.github.io/docs/?api=lines#tag/Odds) response all these is true:
1. Period `status` = 1
2. Market exists 
3. Period has `cutoff` is in the future.


Example: When the `moneyline` market is not offered, the whole object will be missing. It's the same for other market types.
```json
                 {
                            "lineId": 527557614,
                            "number": 1,
                            "cutoff": "2018-06-30T21:00:00Z",
                            "maxSpread": 250,
                            "maxTotal": 250,
                            "status": 1,
                            "spreads": [
                                {
                                    "hdp": -0.25,
                                    "home": 140,
                                    "away": -172
                                }
                            ],
                            "totals": [
                                {
                                    "points": 0.75,
                                    "over": -128,
                                    "under": 107
                                }
                            ]
                        }

```
 


Please note that for live events, odds change quite frequently as well as the period `status`. 
Due to these frequent changes, it’s possible that you will be getting status `NOT_EXISTS` in the [Get Line](https://ps3838api.github.io/docs/?api=lines#operation/Line_Straight_V1_Get) response more often than for the pre-game events.



### How to place a bet on live events?

Bets placed on events with live delay are treated differently than other bets. They get  `betId`  assigned only once they are `ACCEPTED`.


The only way to find out the  `status`  of such a bet is by querying  `Get Bets`  by `uniqueRequestIds`:

`/v1/bets?uniqueRequestIds=86a90ab9-fca1-4703-a11c-ce329a85584e`

As long as the bet is in `PENDING_ACCEPTANCE`, the response would be:

```json
{
    "straightBets": [
        {
            "uniqueRequestId": "86a90ab9-fca1-4703-a11c-ce329a85584e",
            "betStatus": "PENDING_ACCEPTANCE"
        }
    ]
}

```


NOTE: Status can change from `PENDING_ACCEPTANCE` to `NOT_ACCEPTED` or `ACCEPTED`


If the bet was `NOT_ACCEPTED`, the response would be:

```json

{
    "straightBets": [
        {
            "uniqueRequestId": "86a90ab9-fca1-4703-a11c-ce329a85584e",
            "betStatus": "NOT_ACCEPTED"
        }
    ]
}


```

If the bet was `ACCEPTED`, the response includes the full bet details:

```json

{
    "straightBets": [
        {
            "betId": 800110193,
            "uniqueRequestId": "86a90ab9-fca1-4703-a11c-ce329a85584e",
            "wagerNumber": 1,
            "placedAt": "2017-12-20T21:57:22Z",
            "betStatus": "ACCEPTED",
            "betType": "MONEYLINE",
            "win": 2519.25,
            "risk": 11991.63,
            "oddsFormat": "AMERICAN",
            "updateSequence": 175277412,
            "sportId": 29,
            "leagueId": 5595,
            "eventId": 799939900,
            "price": -476,
            "teamName": "Universitario",
            "team1": "Universitario",
            "team2": "Club Petrolero",
            "periodNumber": 0,
            "isLive": "TRUE"
        }
    ]
}
 
```

We apply live delay of around 6 seconds, so the first call to  `Get Bets V2`  should be 6 seconds after placing a bet. 

30 minutes after placing a bet, we will stop returning a response for provided uniqueRequestId. This is due to cache cleanup to maintain optimal performance.

Please also note that the `RUNNING` bet list does not return any live delay bets that are `PENDING_ACCEPTANCE` or `NOT_ACCEPTED`.


### How often can I refresh your odds?

Please check our fair use policy

### Do you cache responses? For how long?
All feed command requests that have the same parameters (e.g. same client ID/API key/sport ID) are cached for one minute.

`Get Odds`  and  `Get Fixtures`  snapshot calls are cached for 60 seconds.  
`Get Odds`  and  `Get Fixtures`  delta calls are not cached.


### How can I return only those sports and leagues which have data?

`Get Sports`  and  `Get Leagues`  operations have the  `hasOfferings`  property that indicates availability of the markets.

### How do you calculate maximum bet amounts for currencies other than USD?

We follow oanda.com, and update our exchange rates every 24 hours. Please note that for non-USD currencies, we round them to the largest integer less-than or equal-to the specified decimal number resulting from currency conversion. For example, a maximum bet amount of £345.23 would be rounded down to £345.

### What time zone is used for the API?

All times are GMT.

### How can I know if an event is deleted or settled?

Please use  `Get Settled Fixtures`  to find out if the event's period was settled or if the event was deleted.

 
 
 ### What TLS (Transport Layer Security) versions are supported?
 
 To be compliant with the security requirements API supports only TLS 1.2 (preferably ) and TLS 1.1.
 
 

### How to get odds changes?

1) Call the snapshot /odds (without the since parameter) - this would return cached odds snapshot
2) Call the delta /odds (with the `since` parameter,  from the snapshot response) - to get all the changes since the snapshot.

Delta response has only changed periods, with all the markets that are currently offered. For example, if we offer period 0 and period 1 odds on an event and there was a change in one of the markets in period 1, the delta call will have only period 1 with all the markets that we currently offer, not just the changed markets, and the period 0 will not be in the delta response.

Example:

1) Snapshot call returns period `number`=1 and period `number`=0 , and both of them have `moneyline` and `spreads` odds.
2) Subsequent, Delta call returns just period 1 with the  `moneyline` and `totals`
    
 => This means that the period `number`=0 did not have any changes, and on the the period `number`=1 , the `spreads` is not offered anymore while the `totals` are offered now and the `moneyline` may have new prices

 
###  How to calculate max risk from the max volume limits in `/odds`?

`/odds` operation returns max volume limits.

To calculate the max risk from the max volume , for a price in decimal odds format, you can use this formula:

If  price  > 2  then:  
```
maxRisk = maxVolume  
```
, otherwise when price  < 2: 
```
 maxRisk = maxVolume/(price - 1)

```



##### Example:

When `/odds` return this moneyline offering
```json 
{
                            "lineId": 242220498,
                            "number": 1,
                            "cutoff": "2019-08-30T21:00:00Z",
                            "maxMoneyline": 250,
                            "status": 1,
                            "moneyline": {
                                "home": 1.819,
                                "away": 2.03
                            }
                        }

```
Max volume is 250.
Home team max risk is 305. 
Away team max risk is 250.
