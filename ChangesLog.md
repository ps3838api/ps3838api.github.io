 [<img _ngcontent-c2="" src="https://avatars1.githubusercontent.com/u/28770833?s=88&v=4" style="background-color: transparent;">](https://ps3838api.github.io)

 
 #  **API Changelog**

## August 2025 – Lines API

##### 1. <span>DEPRECATION</span> – Deprecate several properties in the `v1/periods` endpoint. Properties being removed:
  + spreadDescription
  + moneylineDescription
  + totalDescription
  + team1TotalDescription
  + team2TotalDescription
  + spreadShortDescription
  + moneylineShortDescription
  + totalShortDescription
  + team1TotalShortDescription
  + team2TotalShortDescription


## July 2025 – Lines API

##### 1. <span>FEATURE</span> – New version for getting odds – `v4/odds` to add support for Buy/Sell markets for Team Totals.
##### 2. <span>FEATURE</span> – New version for getting parlay odds – `v4/odds/parlay` to add support for Buy/Sell markets for Team Totals.
<br/>
## September 12, 2022 - Lines API

#### 1. IMPROVEMENT - Tennis events trading.

Currently, all Tennis markets are offered with the `Regular`  `resultingUnit`,  except for the Set Handicaps markets which have `Sets` `resultingUnit`. The Set Handicaps markets events have the resulting unit and the handicap points in the team names and are offered as Moneylines. 
Future tennis events will start using proper `resultingUnit`  and the Sets Handicaps markets will have handicap points removed from the team names and offered as spread markets.

## February 19, 2019 - Lines API 

##### 1# <span>FEATURE</span>  - New property liveStatus in the `/v2/fixtures/special` response 

Will start offering live betting on specials soon. This property was introduce so that clients can differentiate live from pregame specials. Please note that live delay will be applied to betting on live specials.

## January 11, 2019 - Bets API 

##### 1# <span>FIX</span>  - Added optional handicap parameter for placing straight bet `/v2/bets/place`, This parameter to prevent NOT_EXISTS Error
Note: Input line id and alt line ID must be valid line id.

## January 8, 2019 - Bets API 

##### 1# <span>FEATURE</span>  - New property eventStartTime for straight and special bets in the `/v3/bets` response 
<br/>
## January 8, 2019 - Lines API
##### 1# <span>FEATURE</span>  - FEATURE - Added handicap parameter to `/v2/line/special` 

As contestant's handicap is a mutable property, it may happened that line/special returns status:SUCCESS, but with the different handicap from the one that client had at the moment of calling the line/special. One can specify handicap parameter in the request and if the contestant's handicap changed, it would return status:NOT_EXISTS. This way line/special is more aligned to how /line works.


## October 9, 2018 - Bets API 
##### 1# <span>FEATURE</span>  - Add fillType parameter to `/v2/bets/place`

  + NORMAL(Default) - bet will be placed on specified stake.
  + FILLANDKILL - If the stake is over the max limit, bet will be placed on max limit, otherwise it will be placed on specified stake.
  + FILLMAXLIMIT - bet will be places on max limit, stake amount will be ignored. Please note that maximum limits can change at any moment, which may result in risking more than anticipated. This option is replacement of isMaxStakeBet from v1/bets/place'

## August 28, 2018 - Customer API
##### 1# <span>FEATURE</span>  - New version for getting Translations - `/v3/translations` <br>
<br/>
## August 28, 2018 - Lines API

##### 1# <span>FEATURE</span>  - New version for getting Sports - `v3/sports` to support new properties
  + leagueSpecialsCount
  + eventSpecialsCount
  + eventCount

##### 2# <span>FEATURE</span>  - New version for getting Leagues - `v3/leagues` to support new properties
  + container
  + leagueSpecialsCount
  + eventSpecialsCount
  + eventCount

##### 3# <span>FEATURE</span>  - New version for getting Fixtures  - `/v3/fixtures`
 + New parameter `eventIds` 
 + New properties `parentId`, `resultingUnit` in response
 
##### 4# <span>FEATURE</span>  - New version for getting Special Fixtures - `/v2/fixtures/special`

##### 5# <span>FEATURE</span>  - New version for getting Settled Fixtures - `/v3/fixtures/settled`
 + New property `cancellationReason` in response

##### 6# <span>FEATURE</span>  - New version for getting Settled Special Fixtures - `/v3/fixtures/special/settled`
 + New property `cancellationReason` in response
 
##### 7# <span>FEATURE</span>  - New version for getting Straight Odds  - `/v3/odds`
 + New parameter `eventIds`, `toCurrencyCode`
 + New properties `status` in response
 
##### 8# <span>FEATURE</span>  - New version for getting Parlay Odds  - `/v3/odds/parlay`
 + New parameter `eventIds`
 + New properties `status` in response
 
##### 9# <span>FEATURE</span>  - New operation `/v1/odds/teaser` to get odds for specified teaser
  
##### 10# <span>FEATURE</span>  - New version for getting Special Odds - `/v2/odds/special`

##### 11# <span>FEATURE</span>  - New version for getting Straight Line - `/v2/line`

##### 12# <span>FEATURE</span>  - New version for getting Parlay Line - `/v2/line/parlay`

##### 12# <span>FEATURE</span>  - New version for getting Special Line - `/v2/line/special`

##### 13# <span>FEATURE</span>  - New operation `/v1/line/teaser` to get bet limit and price on success

##### 14# <span>FEATURE</span>  - New version for getting inrunning - `/v2/inrunning`
  
##### 15# <span>FEATURE</span>  - New operation `/v1/periods` to get all periods for a given sport
  
##### 16# <span>FEATURE</span>  - New operation `/v1/teaser/groups` to get all teaser groups
  
##### 17# <span>FEATURE</span>  - New operation `/v1/cancellationreasons` to get all the cancellation reasons
<br/>
## August 28, 2018 - Bets API 

##### 1# <span>FEATURE</span>  - New version for placing straight bet - `/v2/bets/place` 
Most important changes:
  + New property `straightBet` object in response 
  
##### 2# <span>FEATURE</span>  - New version for placing parlay bet - `/v2/bets/parlay` 
Most important changes:
  + New property `parlayBet` object in response 
  
##### 3# <span>FEATURE</span>  - New operation to place teaser bet - `/v1/bets/teaser`

##### 4# <span>FEATURE</span>  - New operation to place specials bet - `/v2/bets/special`

##### 5# <span>FEATURE</span>  - New version for getting Bets - `/v3/bets` 
Most important changes: Support paging for getting bets  
  + New parameters `betStatuses`, `sortDir`, `pageSize`, `fromRecord`
  + New properties `moreAvailable`, `pageSize`, `fromRecord`, `toRecord` in response 
    
##### 6# <span>FEATURE</span>  - New version for getting Bets Settled - `/v3/bets/settled` 
Most important changes: Support paging for getting bets  
  + New parameters `specialId`, `uniqueRequestIds`, `sortDir`, `pageSize`, `fromRecord`
  + New properties `moreAvailable`, `pageSize`, `fromRecord`, `toRecord` in response 

##### 7# <span>FEATURE</span>  - New operation to get Betting Status- `/v1/bets/betting-status`




