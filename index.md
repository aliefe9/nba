Evaluating NBA Lottery Picks Using Career Performance

**Group Members:**  
Ali Efe Isik, Djordje Lazarevic  
   
**Colab Worksheet**

**Introduction**  
&emsp;&emsp;&emsp;&emsp;This project looks into the career success of NBA players who were selected in the first 10 places in the NBA draft. We used a dataset from kaggle that contains detailed statistics from multiple NBA seasons, and our research question is: “How successful have first 10 draft picks been, and which teams made the most draft mistakes?”  
&emsp;&emsp;&emsp;&emsp;We evaluated player performance using the Performance Index Rating(PIR), a generally used efficiency metric in the basketball world outside the NBA, that incorporates all positive statistical contributions and subtracts negative contributions. As it summarizes on-court impact in a single number, it is a good comparison number between players. We learned about PIR from Euroleague which adapted this statistic that was found by the Spanish ACB league in early 1990s [(Player Index Rating)](https://en.wikipedia.org/wiki/Performance_index_rating).  
&emsp;The goal of the analysis is to compare PIR between players and identify which players underperformed or outperformed in their careers and answer following questions: 

* How successful have the top 10 lottery pick players been compared with each other?  
* Which NBA team has drafted the most underperforming players?   
* Which NBA team has drafted the least underperforming players?  
* Does playing time correlate with player performance? 

&emsp;Our approach involved data cleaning, calculating PIR from box-score data, aggregating statistics to the player level, and using k-means clustering and visualizations to categorize players into performance tiers  
&emsp;We encountered a few data issues. First, the dataset contained multiple rows per player (e.g., multiple seasons and non-NBA leagues), so we had to filter and aggregate to obtain one career summary per player. Second, the dataset included statistics from leagues outside the NBA, so we restricted our analysis to NBA data only to keep the context consistent.  

**Methods and Results**  
&emsp;The dataset was imported from Kaggle and contains NBA data since 1999, including biographical information, draft position, and box-score statistics such as points, rebounds, assists, steals, blocks, field-goal attempts, free-throw attempts, and turnovers. We filtered the data to include only players drafted between picks 1–10, and we removed players born before 1965\. Since our dataset begins with the 1999 season, those older players would be far beyond their prime, making it misleading to compare their late-career performance to players drafted during the dataset’s time window. We computed PIR using the standard formula:

PIR \= (points+rebounds+assists+steals+blocks)−\[(FGA−FGM)+(FTA−FTM)+turnovers\].

&emsp;For each top 10 pick, we constructed a career level summary containing player name, average PIR, team drafted the player, minutes per game (MPG). Using these variables, we created visualizations to examine the relationship between playing and PIR to separate players into performance clusters. To define the performance clusters, we applied k-means clustering on average PIR and MPG and labeled the three clusters using colors:

Yellow: Low Performers  
Blue: Medium Performers  
Pink: High Performers

**Visualization 1**

<iframe
  src="player_performance_kmeans.html"
  width="130%"
  height="600"
  style="border:none;"
>
  <p>Your browser does not support iframes.</p>
</iframe>

&emsp;From this visualization, we can see a clear positive association between average minutes per game and average PIR for top-10 picks. Players who appear in the high-PIR region of the plot also tend to play more minutes, while most low-PIR players cluster at lower minute totals. The presence of a substantial pink cluster indicates that a meaningful subset of top-10 picks significantly outperformed the rest and can reasonably be viewed as “hits” or star-level outcomes, which connects back to our question about how often teams succeed with early lottery selections. At the same time, there is noticeable spread in the plot: not every high-minute player has an elite PIR, and some efficient players have moderate minutes, showing that performance and playing time are related but not perfectly aligned

**Visualization 2**

<iframe
  src="underperforming_lottery_picks.html"
  width="130%"
  height="600"
  style="border:none;"
>
  <p>Your browser does not support iframes.</p>
</iframe>

&emsp;In the second visualization, we summarize how many low-performing top-10 picks (yellow-cluster players) each team drafted over the period covered by our dataset. Each bar represents a team, and its height is the count of players from the low-PIR cluster. This view answers our question about which franchises have struggled the most with top-10 selections: the Sacramento Kings stand out with 8 underperforming picks, compared to an average of about 2.93 per team. Other teams cluster closer to the average, and some franchises have very few or no low-PIR top-10 picks, suggesting a stronger track record with their high draft choices

**Conclusion**   
&emsp;This analysis shows that the career performance of top-10 draft picks varies widely, even among players selected at the very top of the draft. Using PIR as our main performance metric and clustering players into low, medium, and high performers, we found that a meaningful subset of top-10 picks land in the high-PIR (pink) cluster and can reasonably be viewed as successful “hits,” while a substantial number fall into the low-PIR (yellow) cluster and underperform relative to expectations for such a high selection. In other words, being drafted in the top 10 does not guarantee a star-level career; outcomes range from clear busts to franchise-level players.  
&emsp;Our results also highlight clear differences across franchises. When we count yellow-cluster players by drafting team, the Sacramento Kings stand out with 8 underperforming top-10 picks, well above the sample average of about 2.93 per team. Other teams are much closer to the average, and a few franchises have drafted very few (or no) low-PIR top-10 players over the period we studied, suggesting a stronger track record with their high picks. Taken together, these patterns answer our second and third questions: some organizations have consistently struggled with early lottery selections, while others have managed to avoid large numbers of busts.  
&emsp;Finally, the minutes–PIR visualization indicates a clear positive correlation between playing time and efficiency: players with higher PIR generally appear among those with higher average minutes per game, whereas low-PIR players are more common at lower minute totals. However, this relationship should be interpreted as an association rather than a one-way causal effect. It is likely that better performance leads to more minutes (coaches reward effective players) and that more minutes give players more opportunities to accumulate positive statistics, so both processes can operate at the same time. Overall, our findings suggest that draft position, organizational decision-making, and opportunity (playing time) all interact to shape how successful a top-10 pick’s career becomes, and that even at the top of the draft there is significant uncertainty in long-term outcomes

**References**  
Pérez-Toledano, MÁ, et al. “Players’ Selection for Basketball Teams, through Performance Index Rating.” *PLOS ONE*  
Mikołajec, Krzysztof, et al. “Game Indicators Determining Sports Performance in the NBA.” *Journal of Human Kinetics*  
*Wikipedia Contributors. “Performance Index Rating.” Wikipedia, Wikimedia Foundation, 19 Sept. 2025\.*

[kaggle.com](http://kaggle.com) was used for the dataset


