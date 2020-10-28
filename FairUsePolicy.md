[<img _ngcontent-c2="" src="https://avatars1.githubusercontent.com/u/28770833?s=88&v=4" style="background-color: transparent;">](https://ps3838api.github.io)



# Fair Use
This API is protected by copyright laws and is provided free of charge to our players, partners and affiliates only.

The use of this free resource is subject to our "Fair Use Policy" which is set out below.

When you utilize the API, you are agreeing to this policy. Any breaches of this policy, whether intentional or not, may result in a temporary or permanent suspension of your access without notice at our sole discretion.

# Fair usage

The API is provided to players to facilitate wagering and may not be used for data gathering, scrapping or any other purpose. The API usage must be proportionate to wagering activities as determined on a case by case basis by PS3838.

Unless explicitly agreed in writing by PS3838, the commercial usage of the API will lead to the permanent suspension of your access.

You will not attempt or encourage others to:

- To interfere with, disrupt, or disable any API features;
- Use the API for commercial purposes without a written agreement with PS3838;
Sell, rent, lease, sublicense, redistribute, or syndicate the API to any third party without prior written approval from PS3838.

### The following limitations must be observed per sport:

- Requests made for the /fixtures and /odds operation without the since parameter must be restricted to once every 60 seconds;
- Requests made for the /fixtures and /odds operation with the since parameter must be restricted to once every 5 seconds.

#### Recommended calling rate
API | Recommended API Version | Recommended Interval
------------ | ------------- | -------------
/sports | /v3 | Every 60s
/leagues | /v3 | Every 60s
/fixtures | /v3 | <ul><li>Every 5s per sport with since parameter</li><li>Every 60s per sport without since parameter</li></ul>
/fixtures/special | /v2 | <ul><li>Every 5s per sport with since parameter</li><li>Every 60s per sport without since parameter</li></ul>
/fixtures/settled | /v3 | <ul><li>Every 5s per sport with since parameter</li><li>Every 60s per sport without since parameter</li></ul>
/fixtures/special/settled | /v3 | <ul><li>Every 5s per sport with since parameter</li><li>Every 60s per sport without since parameter</li></ul>
/odds |	/v3 |	<ul><li>Every 5s per sport with since parameter</li><li>Every 60s per sport without since parameter</li></ul>
/odds/parlay | /v3 | <ul><li>Every 5s per sport with since parameter</li><li>Every 60s per sport without since parameter</li></ul>
/odds/teaser | /v1 | Every 5s per teaser Id
/odds/special | /v2 | <ul><li>Every 5s per sport with since parameter</li><li>Every 60s per sport without since parameter</li></ul>
/inrunning | /v2 | Every 2s
/teaser/groups | /v1 | Every 60s
/bets (Get Bet) | /v3 | Every 2s
/betting-status | /v1 | Every 1s
/cancellationreasons | /v1 | Every 10min
/currencies | /v2 | Every 10min
/line	| /v2 |	On demand
/line/parlay | /v2 | On demand
/line/teaser | /v1 | On demand
/line/special | /v2 | On demand
/translations | /v3 | Every 5min
/client/balance | /v1 | On demand

### Best practice

Please use a delta /fixtures and /odds calls (with the since parameter) calls instead of a snapshot /fixtures and /odds calls (without since parameter).

# Disclaimer
PS3838 is not liable for use of the API for any purpose, the API is provided on an “as is” and “as available” basis, without warranties of any kind, either express or implied, including, without limitation, implied warranties of merchantability, fitness for a particular purpose or non-infringement.
