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
 
 
 
 
 

##### 0# <span>FEATURE</span>  - New version for getting inrunning - `/v2/inrunning`
  
##### 0# <span>FEATURE</span>  - New operation `/v1/periods` to get all periods for a given sport
  
##### 0# <span>FEATURE</span>  - New operation `/v1/teaser/groups` to get all teaser groups
  
##### 0# <span>FEATURE</span>  - New operation `/v1/cancellationreasons` to get all the cancellation reasons

  

## August 14th, 2018 - Bets API 

##### 1# <span>FEATURE</span>  - Bet object added to the `v2/bets/parlay` , `v1/bets/teaser`  and `v2/bets/special`  response.  
