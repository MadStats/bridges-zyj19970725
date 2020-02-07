STAT 479 HW1
================

## General Idea

Generally speaking, bridges’ condition should become worse as time in
usage increases. To verify this, I use the 2018 bridges data and select
the structure number, place code, year built, deck condition,
superstructure condition, substructure condition, location, county code.
Also, I create a new column called Duration to store the time in usage.

Then I plot three boxplots to check the relationship between the deck,
superstructure, substructure condition and time in usage.

According to the three plots, all three kinds of bridge conditions
become worse as time in usage increases.

## Read in and manipulate the data

``` r
# read in and manipulate the 2018 bridges data
bridge_cleaned=read.csv('2018HwyBridgesDelimitedAllStates.txt') %>% 
  select(STRUCTURE_NUMBER_008,PLACE_CODE_004,YEAR_BUILT_027,DECK_COND_058,SUPERSTRUCTURE_COND_059,SUBSTRUCTURE_COND_060,LOCATION_009, COUNTY_CODE_003) %>% 
  mutate(Duration = 2018 - YEAR_BUILT_027) %>% 
  filter(Duration < 200)
```

    ## Warning in scan(file = file, what = what, sep = sep, quote = quote, dec = dec, :
    ## EOF within quoted string

## Box Plots

``` r
ggplot(data = bridge_cleaned, aes(x = DECK_COND_058, y = Duration)) +
  geom_boxplot()+
  xlab('deck condition') +
  ylab('time in usage') +
  ggtitle('Time in usage v.s. deck condition')
```

![](HW1_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

``` r
ggplot(data = bridge_cleaned, aes(x = SUPERSTRUCTURE_COND_059, y = Duration)) +
  geom_boxplot()+
  xlab('superstructure condition') +
  ylab('time in usage') +
  ggtitle('Time in usage v.s. superstructure condition')
```

![](HW1_files/figure-gfm/unnamed-chunk-1-2.png)<!-- -->

``` r
ggplot(data = bridge_cleaned, aes(x = DECK_COND_058, y = Duration)) +
  geom_boxplot()+
  xlab('substructure condition') +
  ylab('time in usage') +
  ggtitle('Time in usage v.s. substructure condition')
```

![](HW1_files/figure-gfm/unnamed-chunk-1-3.png)<!-- -->
