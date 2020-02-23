How are the best guards in the NBA scoring in todays NBA?

I pulled data from basketball references with the ballR package. I used
data from 2019 and filtered the data to get the top 20 scoring guards in
the NBA.

``` r
sznstats_df <- NBAPerGameStatistics(season = 2019)

# Here I filtered the per game statistics to only point guards and shooting guards then I grabbed the top 20 players in regards to points per game.

sznstats_df%>%
 filter(pos %in% c("SG", "PG")) %>%
 top_n(n = 20, pts) %>% 
distinct() -> top20guards_df
```

``` r
# I created a plot that displays the top 20 scoring guards by how they score they points
ggplot(data = top20guards_df, aes(x = pts, y = player, colour = x3pa, size = fta))+
  geom_point() +
  ggtitle("Top 20 Scoring Guards", subtitle = " Points Per Game Compared by 3 Point Attempts and Freethrow Attempts")
```

![](assignment2_files/figure-gfm/plot-1.png)<!-- -->

``` r
# This graph shows the top 20 scorers in the NBA and how they score. The size and color of the dots are represented by the average free throw attempts and three point attempts the player is taking per game. James Harden, who was the leading scorer of the NBA last season, was on the extreme side of the spectrum in the way he scored as he averaged over 10 free throws and 10 three point attempts per game. This is what lead to his historic scoring run as no one has ever averaged the attempts he has in both categories and that makes him one of the greatest scores of all time. On a more non historic scale, you can see all of the top scores in the nba are at least in the 7 three point attempt per game range and are taking at least 5 free throws a game. This would show if you want to have a top score on your team in the NBA you need to have him attempting at least 7 three pointers a game so a coach should be running offence to maximize that.
```
