[<img _ngcontent-c2="" src="https://avatars1.githubusercontent.com/u/28770833?s=88&v=4" style="background-color: transparent;">](https://ps3838api.github.io)



# Fair Use Policy
This API is protected by copyright laws and is provided only to our players, partners and affiliates.

The use of this resource is subject to our "Fair Use Policy" which is set out below.

Use of the API constitutes your agreement to this policy. You understand and agree that at our sole discretion, and without prior notice, we may block access to our site if we believe that your use of our site has violated or is inconsistent with this Fair Use Policy.

We may at any time, and at our sole discretion, modify this Fair Use Policy, with or without prior notice. Any such modification will be effective immediately upon public posting. Your continued use of our APIs and this site following such modification constitutes your acceptance of the modified terms in this Fair Use Policy.

## Fair usage

The API is provided to players to facilitate wagering and may not be used for data gathering, scrapping or any other purpose. The API usage must be proportionate to wagering activities as determined on a case by case basis by PS3838.

Unless explicitly agreed in writing by PS3838, the commercial usage of the API will lead to the permanent suspension of your access.

You will not attempt or encourage others to:

- To interfere with, disrupt, or disable any API features;
- Use the API for commercial purposes without a written agreement with PS3838;
- Sell, rent, lease, sublicense, redistribute, or syndicate the API to any third party without prior written approval from PS3838.

### Rules 

1\. Delta and snapshot calls are supported in `/fixtures`, `/fixtures/special` , `/odds` and `/odds/special`  endpoints.  Delta calls return changes since the provided  `since` value. For delta calls `since` parameter must not be set to 0 or 1, it must be always set with the `last` property value of the previous call response. Snapshot calls return the current state,  `since` parameter must not be provided for snapshot calls.

2\. Always first issue a snapshot call and continue with the delta calls. This would result in a faster response time and a smaller response payload. As a result, the client will   get the odds/fixtures updates faster.

3\. Client must not call `/odds` or `/fixture` endpoint for each sport league or fixture in the loop.  If the client is interested in certain leagues only,  `leagueIds` parameter must be set with all the league identifiers. 
 Same for the `eventIds` parameter, the client should use it only if interested in specific events in which case all event identifiers must be provided in the same call.

4\. The following limitations must be observed for `/sports` call:
    <ul><li> Requests made for the `/sports`  must be restricted to once every 60 minute. List of sports does not change often. The count of active events is obsolete functionality, that will eventually be decommissioned.</li></ul>

5\. The following limitations must be observed per sport:
    <ul><li> Snapshot call to `/fixtures` and `/odds` endpoints must be restricted to once every 60 seconds, regardless of the `leagueIds`, `eventIds` or `islive` parameters.</li>
    <li> Delta calls to  `/fixtures` and `/odds` endpoints must be restricted to once every 5 seconds, regardless of the `leagueIds`, `eventIds` or `islive` parameters.</li>
    <li> Calls to `/leagues` must be restricted to once every 60 minutes.</li></ul>

6\. Client must not call `/line` endpoint in the loop. The purpose of this endpoint is to check the price prior to the bet placing.

### The following limitations must be observed per sport:

- Requests made for the /fixtures and /odds operation without the since parameter must be restricted to once every 60 seconds;
- Requests made for the /fixtures and /odds operation with the since parameter must be restricted to once every 5 seconds.

#### Recommended calling rate
<table>
  <tr>
    <th>API</th>
    <th>Recommended API Version</th>
    <th>Recommended Interval</th>
  </tr>
  <tr>
    <td>/sports</td>
    <td>/v3</td>
    <td>Every 60s</td>
  </tr>
  <tr>
    <td>/leagues</td>
    <td>/v3</td>
    <td>Every 60s</td>
  </tr>
  <tr>
    <td>/fixtures</td>
    <td>/v3</td>
    <td><p>Every 5s per sport with since parameter</p><p>Every 60s per sport without since parameter</p></td>
  </tr>
  <tr>
    <td>/fixtures/settled</td>
    <td>/v3</td>
    <td><p>Every 5s per sport with since parameter</p><p>Every 60s per sport without since parameter</p></td>
  </tr>
  <tr>
    <td>/fixtures/special</td>
    <td>/v2</td>
    <td><p>Every 5s per sport with since parameter</p><p>Every 60s per sport without since parameter</p></td>
  </tr>
  <tr>
    <td>/fixtures/special/settled</td>
    <td>/v3</td>
    <td><p>Every 5s per sport with since parameter</p><p>Every 60s per sport without since parameter</p></td>
  </tr>
  <tr>
    <td>/odds</td>
    <td>/v3</td>
    <td><p>Every 5s per sport with since parameter</p><p>Every 60s per sport without since parameter</p></td>
  </tr>
  <tr>
    <td>/odds/parlay</td>
    <td>/v3</td>
    <td><p>Every 5s per sport with since parameter</p><p>Every 60s per sport without since parameter</p></td>
  </tr>
  <tr>
    <td>/odds/special</td>
    <td>/v2</td>
    <td><p>Every 5s per sport with since parameter</p><p>Every 60s per sport without since parameter</p></td>
  </tr>
  <tr>
    <td>/odds/teaser</td>
    <td>/v1</td>
    <td>Every 5s per teaser Id</td>
  </tr>
  <tr>
    <td>/inrunning</td>
    <td>/v2</td>
    <td>Every 2s</td>
  </tr>
  <tr>
    <td>/teaser/groups</td>
    <td>/v1</td>
    <td>Every 60s</td>
  </tr>
  <tr>
    <td>/bets (Get Bet)</td>
    <td>/v3</td>
    <td>Every 2s</td>
  </tr>
  <tr>
    <td>/betting-status</td>
    <td>/v1</td>
    <td>Every 1s</td>
  </tr>
  <tr>
    <td>/cancellationreasons</td>
    <td>/v1</td>
    <td>Every 10min</td>
  </tr>
  <tr>
    <td>/currencies</td>
    <td>/v2</td>
    <td>Every 10min</td>
  </tr>
  <tr>
    <td>/line</td>
    <td>/v2</td>
    <td>On demand</td>
  </tr>
  <tr>
    <td>/line/parlay</td>
    <td>/v2</td>
    <td>On demand</td>
  </tr>
  <tr>
    <td>/line/teaser</td>
    <td>/v1</td>
    <td>On demand</td>
  </tr>
  <tr>
    <td>/line/special</td>
    <td>/v2</td>
    <td>On demand</td>
  </tr>
  <tr>
    <td>/translations</td>
    <td>/v3</td>
    <td>On demand</td>
  </tr>
  <tr>
    <td>/client/balance</td>
    <td>/v1</td>
    <td>On demand</td>
  </tr>
</table>


# Disclaimer
PS3838 is not liable for use of the API for any purpose, the API is provided on an “as is” and “as available” basis, without warranties of any kind, either express or implied, including, without limitation, implied warranties of merchantability, fitness for a particular purpose or non-infringement.
