There are three components of the current pipeline, that aims to answer 3 questions:
1. How do we predict a player's future score?
2. How do we select the next GW first 11?
3. How do we evaluate a GW's performance?
## Question 1: How do we predict a player's future score?
The aim is to given the first 5 gameweeks, can we predict which players will be the top scoring players by the end of the season? Simplest method is by calculating the R-Value between each statistic from FPL API and the Total Points in 23/24 season. 

Based on the previous season, there seems to be a high correlation between ICT Index and the Total Points at the end of the season (0.71). This means that we can rely on the ICT Index to quickly identify the most likely top performing players for the entire season, while making incremental changes subsequently.

Based on this statistic, we can also rank the players and identify the lowest performing player, to be transferred out if necessary.

**Assumptions**: Although the total points include the first 5 gameweeks that have already passed, there has only been a small percentage of games played (5/38), we assumed that the total points in the first 5 gameweeks are inconsequential when compared to the total points.
### Gameweek 6: Wildcard madness
![[Pasted image 20241001150451.png]]
*Players after Gameweek 5, ranked according to ICT index score. Players in Red are transferred out of the team via Wildcard for GW6*

There were two reasons for activating the Wildcard relatively early in GW6: 
1. Prices are fluctuating wildly in the early part of the season. Taking advantage of this could potentially allow us to increase our squad budget for the rest of the season.
2. Start of the season template have many unexpectedly underperforming players. Would be more efficient to get rid of them at once, rather than slowly transferring them out one by one each gameweek.
#### Transfers Out
By and large, the players removed are based on their ICT index. Obvious players that fit these criteria are **Ben Johnson** and **Ibrahim Sangare**, both of which are at the bottom of the ranking. **Muniz** and **Alexander Isak** are removed as the two worst performing Forwards.

Transfers that happened/did not happen for the following players are based on separate discretionary reasons:
- **Joachim Andersen** (STAY): Just transferred to a new team and have not played for the first two games (GW 2,3) after joining Fulham. Should give benefit of doubt and judge after GW 8, where he would have had 5 games.
- **Dean Henderson** (STAY): Solid goalkeeper in a mid-table team. Can farm saves when facing tough opponents, not too far off amongst Goalkeepers in terms of ICT index either
- **Nick Pope** (STAY): Solid goalkeeper in a team that has been rather leaky. Can farm saves when facing tough opponents, ranking 3rd amongst Goalkeepers in ICT index seems good too.
- **Amadou Onana** (STAY): Midfielder was brought in after GW 3 to replace John McGinn. Was previously a DM at Everton but looks like he was going to be the next Douglas Luiz with his 2 goals in 3 gameweeks.
- **Nathan Collins** & **Trent** (STAY): Stay as their ICT Index rankings are within single digits for the defender position
- **Anthony Gordon** (OUT): Transfer since Newcastle seem to be overperforming despite their high points, as detailed in the [Match Report](https://www.bbc.com/sport/football/live/c1wnj90nq21t). With Isak injured, Gordon will be lacking a key finisher for goals as well.
#### Transfers in
![[Pasted image 20241001154414.png]]
*Players in blue are brought in to replace those in red*

By looking at the ICT Index rank type, we can find that each removed player was transferred for someone with a higher ICT Index. Not all of the top performers in ICT Index could be considered for each players, due to price constraints

| In              | Rank | Out       | Rank |
| --------------- | ---- | --------- | ---- |
| Ben Johnson     | 91   | Wout Faes | 14   |
| Ibrahim Sangare | 125  | Luis Diaz | 3    |
| Muniz           | 15   | Raul      | 11   |
| Isak            | 14   | Jackson   | 2    |
| Anthony Gordon  | 21   | Tavernier | 7    |
## Q2: How do we select next GW first 11?
After selecting 15 players, we need to select 11 players for the first team. For the past few gameweeks, they have been selected based on gut feel. For example, Fulham players in GW6 were dropped because Nottingham Forest had been playing decently so far. (E.g.: not losing any of their first 5 matches, always scoring a goal, and even beating Liverpool). **Pope** has been benched because of facing Man City, while **Wout Faes** is benched since he is facing Arsenal
## Q3: How do we evaluate a GW's performance?
We can evaluate a GW's performance by measuring the opportunity cost in terms of points. The opportunity cost can be manifested whenever there are decisions to be made, such as transfers, first 11, captaincy etc.
### Transfers
Realize that by selecting Transfers purely on ICT index, this can be formalized as a variant of a Knapsack Problem: How can we select n players to maximize ICT index score, while maintaining the Budget, and maintaining a valid squad (2 GK, 5 DEF, 5 MID, 3 FWD). 

While I do not have an explicit formula for the above problem, I iteratively arrived at the answer by choosing the following

Without Transfers vs With Transfers, based purely on ICT Index vs With Transfers, based on ICT Index + discretionary choice in transferring:

| Player (w/o Trf) | Points  | Player (w/ Trf, ICT only) | Points   | Player (w/ Trf, ICT & Choice) | Points |
| ---------------- | ------- | ------------------------- | -------- | ----------------------------- | ------ |
| Henderson        | 1       | ***Flekken***             | ***2***  | Henderson                     | 1      |
| Trent            | 1       | ***Sugawara***            | ***0***  | Trent                         | 1      |
| Porro            | 5       | Porro                     | 5        | Porro                         | 5      |
| Collins          | 1       | Collins                   | 1        | Collins                       | 1      |
| ***Sangare***    | ***0*** | Luis Diaz                 | 2        | Luis Diaz                     | 2      |
| Mbeumo           | 9       | ***Maddison***            | ***3***  | Mbeumo                        | 9      |
| ***Gordon***     | 9       | Tavernier                 | 4        | Tavernier                     | 4      |
| Palmer           | 25      | ***Saka***                | ***3***  | Palmer                        | 25     |
| Onana            | 2       | ***McNeil***              | ***15*** | Onana                         | 2      |
| ***Isak***       | 0       | Jackson                   | 5        | Jackson                       | 5      |
| Haaland          | 2       | Haaland                   | 2        | Haaland                       | 2      |
| Nick Pope        | 3       | ***Sanchez***             | ***2***  | Nick Pope                     | 3      |
| Andersen         | 8       | ***Romero***              | ***6***  | Andersen                      | 8      |
| ***Muniz***      | 1       | **Welbeck**               | **2**    | Raul                          | 9      |
| ***Johnson***    | 0       | **Mitchell**              | **1**    | Faes                          | 0      |
| **Total Points** | **67**  | **Total Points**          | **53**   | **Total Points**              | **77** |
| **Total ICT Index**  | **418.9**   | **Total ICT Index**           | **604.6**    | **Total ICT Index**               | **517.9**  |
### Team Selection
Based on ICT Index vs Gut Feel:

| Player (ICT)     | Point   | Player (Gut Feel)    | Point   |
| ---------------- | ------- | -------------------- | ------- |
| ***Nick Pope***  | ***3*** | ***Dean Henderson*** | ***1*** |
| Trent            | 1       | Trent                | 1       |
| Porro            | 5       | Porro                | 5       |
| Collins          | 1       | Collins              | 1       |
| Luis Diaz        | 2       | Luis Diaz            | 2       |
| Mbeumo           | 9       | Mbeumo               | 9       |
| Tavernier        | 4       | Tavernier            | 4       |
| Palmer           | 25      | Palmer               | 25      |
| ***Raul***       | ***9*** | ***Onana***          | ***2*** |
| Jackson          | 5       | Jackson              | 5       |
| Haaland          | 2       | Haaland              | 2       |
| **Total Points** | **67**  | **Total Points**     | **58**  |
## Conclusion

Wildcarded the team to transfer for 5 new players in GW6. While the evidence for the link between ICT index score and Total points were weak when selecting the transfers, there would have been a significant points increase had the team been selected based on the ICT Index.

Perhaps the conclusion that we can draw is that ICT Index can be a good predictor of points, but we can't over optimize for it either. Will need some common sense to come into play too.

More time will be needed to see if the above hypothetical teams would perform better, due to the presence of outliers like Cole Palmer this week.

## Future work
- Can we find statistics that are more relevant for different positions?
- Can we improve the prediction of the scores using sequential ML models? (e.g. LSTM)
- Can I utilise other tech, such as SQL to make sense of the database more efficiently?
- Can we improve the selection of the first 11 using variants of Knapsack Problem?
	- Possible work has been done by others via link & link