How are the best guards in the NBA scoring in todays NBA?

I pulled data from basketball references with the ballR package. I used
data from 2019 and filtered the data to get the top 20 scoring guards in
the NBA.

``` r
sznstats_df <- NBAPerGameStatistics(season = 2019)

sznstats_df%>%
 filter(pos %in% c("SG", "PG")) %>%
 top_n(n = 20, pts) %>% 
distinct() -> top20guards_df
```

``` r
ggplot(data = top20guards_df, aes(x = pts, y = player, colour = x3pa, size = fta))+
  geom_point() +
  ggtitle("Top 20 Scoring Guards", subtitle = " Points Per Game Compared by 3 Point Attempts and Freethrow Attempts")
```

![](assignment2_files/figure-markdown_github/unnamed-chunk-1-1.png)

After you have constructed the visualization, write a caption and a
paragraph describing the visualization, and how it answers the question
you posed. Think of the figure, the caption, and the text as material
you might include in a research pape
