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
                      'Bernese Mountain Dogs',
                      'Spaniels (Cocker)',
                      'Border Collies',
                      'Vizslas',
                      'Collies',
                      'Newfoundlands',
                      'Rhodesian Ridgebacks',
                      'Spaniels (English Cocker)',
                      'Pointers (German Wirehaired)',
                      'Old English Sheepdogs',
                      'Irish Wolfhounds',
                      'Setters (Irish)',
                      'Greater Swiss Mountain Dogs',
                      'Retrievers (Flat-Coated)',
                      'Setters (Gordon)',
                      'Pointers',
                      'Afghan Hounds',
                      'Black and Tan Coonhounds',
                      'Greyhounds',
                      'Redbone Coonhounds',
                      'Entlebucher Mountain Dogs',
                      'Scottish Deerhounds')) -> DogDataTidy
DogDataTidy
```

    ## # A tibble: 27 × 18
    ##    Breed                    number Affectionate With Fa…¹ Good With Young Chil…²
    ##    <chr>                     <int>                  <dbl>                  <dbl>
    ##  1 Retrievers (Labrador)         1                      5                      5
    ##  2 Pointers (German Shorth…      9                      5                      5
    ##  3 Australian Shepherds         12                      3                      5
    ##  4 Great Danes                  15                      5                      3
    ##  5 Doberman Pinschers           18                      5                      5
    ##  6 Bernese Mountain Dogs        22                      5                      5
    ##  7 Spaniels (Cocker)            30                      4                      5
    ##  8 Border Collies               32                      5                      3
    ##  9 Vizslas                      35                      5                      5
    ## 10 Collies                      40                      4                      5
    ## # ℹ 17 more rows
    ## # ℹ abbreviated names: ¹​`Affectionate With Family`, ²​`Good With Young Children`
    ## # ℹ 14 more variables: `Good With Other Dogs` <dbl>, `Shedding Level` <dbl>,
    ## #   `Coat Grooming Frequency` <dbl>, `Drooling Level` <dbl>, `Coat Type` <chr>,
    ## #   `Coat Length` <chr>, `Openness To Strangers` <dbl>,
    ## #   `Playfulness Level` <dbl>, `Watchdog/Protective Nature` <dbl>,
    ## #   `Adaptability Level` <dbl>, `Trainability Level` <dbl>, …
