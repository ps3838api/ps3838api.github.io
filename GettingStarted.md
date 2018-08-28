<img _ngcontent-c2="" src="https://avatars1.githubusercontent.com/u/28770833?s=88&v=4" style="background-color: transparent;"> 

# Getting Started
## Step 1 – Sign Up

To get started you would need to create an account.

Please note that in order to access PS3838 API the account must be funded.

### Step 2 - Get a List of Offered Sports and Leagues

You would need to get the list of sports from Get Sports operation. If you are interested in particular leagues you can get all sport leagues by calling Get Leagues operation. **[Lines API](https://ps3838api.github.io/docs?api=lines)**


### Step 3 - Place Bet

To place a bet, please check sections How to place a straight bet? And How to place a parlay bet?

### Step 4 - Get Bets

To check the status of the placed bet you need to call Get Bets operation. The recommended way is to use bet id.

For bets on live events that are in PENDING_ACCEPTANCE state, you can call Get Bets every 5 sec to get the new status of the bet, to see if it’s accepted or rejected.

# How to Place a Straight Bet?

### Step 1 – Call Get Fixtures operation **[Lines API](https://ps3838api.github.io/docs?api=lines)**


This will return the list of events that are currently offered. To get updates use delta requests (with since parameter).

### Step 2 – Call Get Odds operation **[Lines API](https://ps3838api.github.io/docs?api=lines)**


This will return the list of odds that are currently offered. To get updates use delta requests (with since parameter).

### Step 3 - Get Line (optional)  **[Lines API](https://ps3838api.github.io/docs?api=lines)**


Call Get Line operation if you need exact stake limits or if you are interested only in a specific line. Please note that the limits in the Get Feed response are just general limits. Limits in the Get Line response are the exact limits.

### Step 4 - Place Bet **[Bets API](https://ps3838api.github.io/docs?api=bets)**


To place a bet you need to call Place Bet operation.

The table shows how to do mapping of Get Odds operation response to Place Bet and Get Line request.

Parameter	Get Odds response parameter
sportId	sportId
leagueId	League Type -> id
eventId	Event Type -> id
periodNumber	Period Type -> number
team	
Depends on selected odds from:

· Spread Type
· Moneyline Type
· Team Total Points

check the value in the corresponding Get Leagues Response -> League Type -> homeTeamType and set the appropriate value.
Example 1: 

Given:
    homeTeamType="Team1"
When:
    Selected odds is Spread Type -> away
Then:
    team=Team2

Example 2:
When:
    Selected odds is Moneyline Type -> draw
Then:
    team=Draw

Example 3: 

Given:
    homeTeamType="Team2"
When:
    Selected odds is Team Total Points Type -> away
Then:
    team=Team1
handicap	Spread Type -> hdp
Total Points Type -> points
Team Total Points Type -> Total Points Type -> points
lineId	Period Type -> lineId
altLineId	Spread Type ->altLineId
Total Points Type -> altLineId
If you call Get Line operation, use the lineId (altLineId) from the response.

A period in an event is open for betting if:

Get Fixtures Response -> Event Type -> status has a value I or O
Event period has odds in Get Odds Response
Get Odds Response -> Period Type -> cutoff is in the future.
Please note that for live events, odds change quite frequently as well as the event status, from O/I to H and vice versa. Due to these frequent changes, it’s possible that you will be getting status NOT_EXISTS in the Get Line response more often than for the dead ball events.

# How to Place a Parlay Bet?

### Step 1 – Call Get Fixtures operation. **[Lines API](https://ps3838api.github.io/docs?api=lines)**

This will return the list of events that are currently offered. To get updates use delta requests (with since parameter)

### Step 2 – Call Get Odds operation. **[Lines API](https://ps3838api.github.io/docs?api=lines)**

This will return the list of odds that are currently offered. To get updates use delta requests (with since parameter)

### Step 3 – Call Get Parlay Lines operation. **[Lines API](https://ps3838api.github.io/docs?api=lines)**

For each event and bet type you want to bet on, construct a Leg object for Get Parlay Lines call and submit your request using

#### POST /line/parlay **[Lines API](https://ps3838api.github.io/docs?api=lines)**

If response contains Invalid Legs – remove them and resubmit the request.

If response have status = ‘VALID’ – place parlay bet request can be created.

### Step 4 – Call Place Parlay Bet. **[Bets API](https://ps3838api.github.io/docs?api=bets)**


Construct a list of legs using lineId values from Get Parlay Lines response and specify roundRobbinOptions out of those retuned in Get Parlay Lines response.