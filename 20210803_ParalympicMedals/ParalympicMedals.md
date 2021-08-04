ParalympicMedals
================

``` r
athletes <- readr::read_csv('https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2021/2021-08-03/athletes.csv')
```

    ## 
    ## -- Column specification --------------------------------------------------------
    ## cols(
    ##   gender = col_character(),
    ##   event = col_character(),
    ##   medal = col_character(),
    ##   athlete = col_character(),
    ##   abb = col_character(),
    ##   country = col_character(),
    ##   grp_id = col_double(),
    ##   type = col_character(),
    ##   year = col_double(),
    ##   guide = col_logical()
    ## )

    ## Warning: 53 parsing failures.
    ##  row   col           expected       actual                                                                                                     file
    ## 7548 guide 1/0/T/F/TRUE/FALSE AVERY Jerome 'https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2021/2021-08-03/athletes.csv'
    ## 7549 guide 1/0/T/F/TRUE/FALSE SILVA Celio  'https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2021/2021-08-03/athletes.csv'
    ## 7550 guide 1/0/T/F/TRUE/FALSE TJIVIJU Even 'https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2021/2021-08-03/athletes.csv'
    ## 7595 guide 1/0/T/F/TRUE/FALSE TJIVIJU Even 'https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2021/2021-08-03/athletes.csv'
    ## 7596 guide 1/0/T/F/TRUE/FALSE SILVA Jonas  'https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2021/2021-08-03/athletes.csv'
    ## .... ..... .................. ............ ........................................................................................................
    ## See problems(...) for more details.

``` r
athletes
```

    ## # A tibble: 19,547 x 10
    ##    gender event          medal  athlete   abb   country grp_id type   year guide
    ##    <chr>  <chr>          <chr>  <chr>     <chr> <chr>    <dbl> <chr> <dbl> <lgl>
    ##  1 Men    Double FITA R~ Gold   LARSEN F~ DEN   <NA>        NA Arch~  1980 NA   
    ##  2 Men    Double FITA R~ Silver BRENNE M~ FRG   <NA>        NA Arch~  1980 NA   
    ##  3 Men    Double FITA R~ Bronze SATO Mas~ JPN   <NA>        NA Arch~  1980 NA   
    ##  4 Men    Double FITA R~ Gold   GEISS H.  FRG   <NA>        NA Arch~  1980 NA   
    ##  5 Men    Double FITA R~ Silver GRUN Guy  BEL   <NA>        NA Arch~  1980 NA   
    ##  6 Men    Double FITA R~ Bronze BUCHANAN~ GBR   <NA>        NA Arch~  1980 NA   
    ##  7 Men    Double FITA R~ Gold   PARKER T. CAN   <NA>        NA Arch~  1980 NA   
    ##  8 Men    Double FITA R~ Silver STEBEKK ~ NOR   <NA>        NA Arch~  1980 NA   
    ##  9 Men    Double FITA R~ Bronze LAFONT G. FRA   <NA>        NA Arch~  1980 NA   
    ## 10 Men    Double FITA R~ Gold   CHAVEZ A~ MEX   <NA>        NA Arch~  1980 NA   
    ## # ... with 19,537 more rows
