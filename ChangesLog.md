 [<img _ngcontent-c2="" src="https://avatars1.githubusercontent.com/u/28770833?s=88&v=4" style="background-color: transparent;">](https://ps3838api.github.io)

 
 #  **API Changelog**

## August 28th, 2018 - Lines API

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


## August 28th, 2018 - Bets API 

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

##### 7# <span>FEATURE</span>  - New operation to get Betting Status- `/v1/bets/teaser`




