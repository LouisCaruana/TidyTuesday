Dog Breeds
================

``` r
breed_traits <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2022/2022-02-01/breed_traits.csv')
```

    ## Rows: 195 Columns: 17
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (3): Breed, Coat Type, Coat Length
    ## dbl (14): Affectionate With Family, Good With Young Children, Good With Othe...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
trait_description <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2022/2022-02-01/trait_description.csv')
```

    ## Rows: 16 Columns: 4
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Trait, Trait_1, Trait_5, Description
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
breed_rank_all <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2022/2022-02-01/breed_rank.csv')
```

    ## Rows: 195 Columns: 11
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (3): Breed, links, Image
    ## dbl (8): 2013 Rank, 2014 Rank, 2015 Rank, 2016 Rank, 2017 Rank, 2018 Rank, 2...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
breed_traits %>%
  mutate(number = row_number()) %>%
  select(-'Breed') -> TraitsTidy

breed_rank_all %>%
  mutate(number = row_number()) %>%
  select('Breed', 'number')-> RankTidy 

DogDataTidy <- RankTidy %>% full_join(TraitsTidy)
```

    ## Joining with `by = join_by(number)`

``` r
DogDataTidy %>% filter(Breed %in% c('Retrievers (Labrador)',
                      'Pointers (German Shorthaired)', 
                      'Australian Shepherds',
                      'Great Danes',
                      'Doberman Pinschers',
                      'Border Collies',
                      'Vizslas',
                      'Rhodesian Ridgebacks',
                      'Irish Wolfhounds',
                      'Greater Swiss Mountain Dogs',
                      'Retrievers (Flat-Coated)',
                      'Pointers',
                      'Greyhounds')) %>%
  select(-'number', -'Coat Type', -'Coat Length' ) -> DogDataTidy
DogDataTidy
```

    ## # A tibble: 13 × 15
    ##    Breed    Affectionate With Fa…¹ Good With Young Chil…² `Good With Other Dogs`
    ##    <chr>                     <dbl>                  <dbl>                  <dbl>
    ##  1 Retriev…                      5                      5                      5
    ##  2 Pointer…                      5                      5                      4
    ##  3 Austral…                      3                      5                      3
    ##  4 Great D…                      5                      3                      3
    ##  5 Doberma…                      5                      5                      3
    ##  6 Border …                      5                      3                      3
    ##  7 Vizslas                       5                      5                      4
    ##  8 Rhodesi…                      5                      5                      3
    ##  9 Irish W…                      5                      3                      4
    ## 10 Greater…                      5                      5                      3
    ## 11 Retriev…                      5                      5                      5
    ## 12 Pointers                      5                      3                      5
    ## 13 Greyhou…                      4                      3                      4
    ## # ℹ abbreviated names: ¹​`Affectionate With Family`, ²​`Good With Young Children`
    ## # ℹ 11 more variables: `Shedding Level` <dbl>, `Coat Grooming Frequency` <dbl>,
    ## #   `Drooling Level` <dbl>, `Openness To Strangers` <dbl>,
    ## #   `Playfulness Level` <dbl>, `Watchdog/Protective Nature` <dbl>,
    ## #   `Adaptability Level` <dbl>, `Trainability Level` <dbl>,
    ## #   `Energy Level` <dbl>, `Barking Level` <dbl>,
    ## #   `Mental Stimulation Needs` <dbl>
