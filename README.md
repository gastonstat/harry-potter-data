<!-- README.md is generated from README.Rmd. Please edit that file -->

# 1) About

This repository contains various data files that can be used to perform
a text analysis of [Harry
Potter](https://en.wikipedia.org/wiki/Harry_Potter) books, written by
Joanne Kathleen Rowling:

1.  Harry Potter and the Philosopher’s Stone

2.  Harry Potter and the Chamber of Secrets

3.  Harry Potter and the Prisoner of Azkaban

4.  Harry Potter and the Goblet of Fire

5.  Harry Potter and the Order of the Phoenix

6.  Harry Potter and the Half-Blood Prince

7.  Harry Potter and the Deathly Hallows

To perform the text analysis, we recommend using *tidyverse* tools (see
packages below) and getting inspiration from the book [Text Mining with
R: A Tidy Approach](https://www.tidytextmining.com/index.html) (by Silge
& Robinson):

``` r
library(tidyverse)
library(tidytext)
```

------------------------------------------------------------------------

# 2) Content

The content of this repo is divided in **three directories**, each one
containing different types of files.

-   [csv-data-file/](csv-data-file) contains the text of all Harry
    Potter books in a single CSV file.

-   [rda-data-files/](rda-data-files) contains the seven Harry Potter
    books stored in R-Data (binary) files—one file per book.

-   [sentiment-lexicons/](sentiment-lexicons) contains a handful of
    sentiment lexicons, also stored in R-Data (binary) files—one file
    per lexicon.

------------------------------------------------------------------------

## 2.1) Harry Potter CSV file

The data of all the books is available in `csv` format—in a single file:
`harry_potter_books.csv`.

Assuming that this file is in your working directory, you can import
it—via tidyverse’s `readr()`—as follows:

``` r
# requires package tidyverse
hp_books = read_csv("harry_potter_books.csv", col_types = "ccc")
```

This data set is fairly simple—in terms of its structure—although the
text content is far from being tidy. The dataset has 95085 rows and 3
columns:

1.  `text`: text content

2.  `book`: title of associated book

3.  `chapter`: associated chapter number

------------------------------------------------------------------------

## 2.2) Harry Potter R-Data Files

The data of each book is also available in its own R-Data `rda` file
(see [rda-data-files/](rda-data-files)):

-   `"philosophers_stone.rda"`
-   `"chamber_of_secrets.rda"`
-   `"prisoner_of_azkaban.rda"`
-   `"goblet_of_fire.rda"`
-   `"order_of_the_phoenix.rda"`
-   `"half_blood_prince.rda"`
-   `"deathly_hallows.rda"`

These files come from the R package `"harrypotter"` by Bradley Boehmke

<https://github.com/bradleyboehmke/harrypotter>

To import these files use the `load()` function. For example, consider
the first book “Harry Potter and the Philosopher’s Stone”; here’s how to
`load()` it in R:

``` r
# assuming that the rda file is in your working directory
load("philosophers_stone.rda")
```

Assuming that `"philosophers_stone.rda"` has been loaded, the text of
this book is available in the homonym character vector
`philosophers_stone`

``` r
# text is in a character vector
# (with as many elements as chapters in the book)
length(philosophers_stone)
#> [1] 17
```

The number of elements in `philosophers_stone` corresponds to the number
of chapters in this book: 17 chapters.

You may want to use these files to perform bigram analysis (or other
type of n-gram analysis).

------------------------------------------------------------------------

## 2.3) Sentiment Lexicons

In addition to the Harry Potter text, you can also find data for a
handful of sentiment lexicons from the R package `"textdata"` (by
Hvitfeldt and Silge):

-   `"bing"`: Bing Liu’s General purpose English sentiment lexicon that
    categorizes words in a binary fashion, either positive or negative

-   `"afinn"`: AFINN is a lexicon of English words rated for valence
    with an integer between minus five (negative) and plus five
    (positive). The words have been manually labeled by Finn Årup
    Nielsen in 2009-2011.

-   `"nrc"`: General purpose English sentiment/emotion lexicon. This
    lexicon labels words with six possible sentiments or emotions:
    “negative”, “positive”, “anger”, “anticipation”, “disgust”, “fear”,
    “joy”, “sadness”, “surprise”, or “trust”. The annotations were
    manually done through Amazon’s Mechanical Turk.

-   `"loughran"`: English sentiment lexicon created for use with
    financial documents. This lexicon labels words with six possible
    sentiments important in financial contexts: “negative”, “positive”,
    “litigious”, “uncertainty”, “constraining”, or “superfluous”.

These lexicons come in `rda` data files (see
[sentiment-lexicons/](sentiment-lexicons)):

-   `bing.rda`
-   `afinn.rda`
-   `bing.rda`
-   `loughran.rda`

To import them in R, use the `load()` function. For example, here’s how
to import the Bing lexicon:

``` r
# assuming that the rda files are in your working directory
load("bing.rda")
```

Assuming that you’ve loaded the file `"bing.rda"`, the associated
lexicon is available in the homonym tibble `bing`

``` r
bing
#> # A tibble: 6,786 × 2
#>    word        sentiment
#>    <chr>       <chr>    
#>  1 2-faces     negative 
#>  2 abnormal    negative 
#>  3 abolish     negative 
#>  4 abominable  negative 
#>  5 abominably  negative 
#>  6 abominate   negative 
#>  7 abomination negative 
#>  8 abort       negative 
#>  9 aborted     negative 
#> 10 aborts      negative 
#> # ℹ 6,776 more rows
```
