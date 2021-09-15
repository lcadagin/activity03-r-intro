Activity 3
================
Luke B. Cadagin

Today you will be creating and manipulating vectors, lists, and data
frames to uncover a top secret message.

As you work through this document with your Team members, remember to:

-   Ask questions
-   Google is your friend! If an error is confusing, copy it into Google
    and see what other people are saying. If you don’t know how to do
    something, search for it.
-   Just because there is no error message doesn’t mean everything went
    smoothly. Use the console to check each step and make sure you have
    accomplished what you wanted to accomplish.

Do not edit this first R code chunk. This will allow you to knit your
document and view errors within the knitted report.

### Setup

Each of the following R chunks will cause an error and/or do the desired
task incorrectly. Find the mistake, and correct it to complete the
intended action.

Create three vectors that contain: 1) the lower case letters, 2) the
lower case letters, and 3) some punctuation marks.

``` r
lower_case <- c("a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z")

upper_case <- c("A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z")

punctuation <- c(".", ",", "!", "?", "'", "\"", "(", ")", " ", "-", ";", ":")
```

Comment on what you noticed about the errors and how you used this
information to correct the issues.

**Response**: I saw red squiggley where there was an error ni the code.
When I hovered my cursor over this, an error message appeared that
helped me diagnose the problem.

Make one long vector containing all the symbols.

``` r
my_symbols <- c(lower_case, upper_case, punctuation)
```

Comment on what you noticed about the errors and how you used this
information to correct the issues.

**Response**: The error told me that the arguments for cbind() did not
take multiple vectors, theis indicated that the wrong function was being
used.

Turn the `my_symbols` vector into a data frame, with the variable name
“Symbol”.

``` r
my_symbols <- data.frame(my_symbols)
names(my_symbols) = "Symbol"
```

Comment on what you noticed about the errors and how you used this
information to correct the issues.

**Response**: The error stated that the dataframe() function could not
be found, which suggested it was typed incorrectly. The error stated
that the Symbol variable was not found, this suggested that Symbol
needed quotes.

Find the total number of symbols we have in our data frame.

``` r
len <- lengths(my_symbols)
len
```

    ## Symbol 
    ##     64

Comment on what you noticed about the errors and how you used this
information to correct the issues.

**Response**:

The number of symbols came out to 1, this was incorrect as we needed 64.
The function was lengths() no length() 5. Create a new variable in your
dataframe that assigns a number to each symbol.

``` r
my_symbols$Num <- 1:len
my_symbols
```

    ##    Symbol Num
    ## 1       a   1
    ## 2       b   2
    ## 3       c   3
    ## 4       d   4
    ## 5       e   5
    ## 6       f   6
    ## 7       g   7
    ## 8       h   8
    ## 9       i   9
    ## 10      j  10
    ## 11      k  11
    ## 12      l  12
    ## 13      m  13
    ## 14      n  14
    ## 15      o  15
    ## 16      p  16
    ## 17      q  17
    ## 18      r  18
    ## 19      s  19
    ## 20      t  20
    ## 21      u  21
    ## 22      v  22
    ## 23      w  23
    ## 24      x  24
    ## 25      y  25
    ## 26      z  26
    ## 27      A  27
    ## 28      B  28
    ## 29      C  29
    ## 30      D  30
    ## 31      E  31
    ## 32      F  32
    ## 33      G  33
    ## 34      H  34
    ## 35      I  35
    ## 36      J  36
    ## 37      K  37
    ## 38      L  38
    ## 39      M  39
    ## 40      N  40
    ## 41      O  41
    ## 42      P  42
    ## 43      Q  43
    ## 44      R  44
    ## 45      S  45
    ## 46      T  46
    ## 47      U  47
    ## 48      V  48
    ## 49      W  49
    ## 50      X  50
    ## 51      Y  51
    ## 52      Z  52
    ## 53      .  53
    ## 54      ,  54
    ## 55      !  55
    ## 56      ?  56
    ## 57      '  57
    ## 58      "  58
    ## 59      (  59
    ## 60      )  60
    ## 61         61
    ## 62      -  62
    ## 63      ;  63
    ## 64      :  64

Comment on what you noticed about the errors and how you used this
information to correct the issues.

**Response**: I initially got rid of the % sign, but then I figured out
that the $ needed to be used to create a Num column for each row.

![](README-img/noun_pause.png) **Planned Pause Point**: If things made
sense, feel free to continue on while you wait. Otherwise, contact your
instructor to have them verify your work.

### Decoding the secret message.

This chunk will load up the encoded secret message data and assign it as
a vector. There are no errors here.

``` r
# Read in full csv file
top_secret <- readr::read_csv("data/secret_code.csv", col_names = FALSE)
```

    ## 
    ## ── Column specification ────────────────────────────────────────────────────────
    ## cols(
    ##   X1 = col_double()
    ## )

``` r
# Pick off only the column X1
top_secret <- top_secret$X1
```

By altering this top secret set of numbers, you will be able to create a
message. Write your own code to complete the steps below.

1.  Add 14 to every number.
2.  Multiply every number by 18, then subtract 257.
3.  Exponentiate every number. (That is, do e ^ \[each number\]. You may
    need to Google how to this!)
4.  Square every number.

``` r
#Step 1
top_secret <- top_secret + 14

#Step 2
top_secret <- (top_secret * 18) -257

#Step 3
top_secret <- exp(top_secret)

#Step 4
top_secret <- top_secret ^ 2

top_secret
```

    ##    [1]   43.0   12.0   67.0   33.0   15.0   13.0   22.0   77.0   53.0   34.0
    ##   [11]   83.0   56.0   44.0   29.0   44.0   35.0   39.0   97.0   39.0  101.0
    ##   [21]   61.0   55.0   55.0   62.0   64.0   77.0  115.0   69.0   59.0   74.0
    ##   [31]  123.0   68.0   75.0   73.0   74.0  133.0   89.0  112.0 3799.0   81.0
    ##   [41] 3803.0   88.0  167.0  137.0 3811.0  108.0  175.0  457.0  123.0  101.0
    ##   [51]  463.0  129.0 3827.0  637.0  191.0 1633.0  178.0 3837.0  119.0 3841.0
    ##   [61]  266.0  205.0 1647.0 1649.0  274.0  157.0 3855.0  332.0  139.0  309.0
    ##   [71]  167.0 3865.0  930.0  773.0 3871.0  161.0  218.0  157.0  354.0  169.0
    ##   [81]  187.0 3885.0  230.0  249.0  531.0 3893.0  223.0  257.0  502.0  324.0
    ##   [91]  218.0  508.0  267.0  213.0  386.0  208.0 3915.0  205.0  199.0  369.0
    ##  [101]  227.0 3925.0  207.0  217.0  534.0  437.0  575.0  577.0 3939.0  221.0
    ##  [111] 3943.0  420.0  251.0  253.0  246.0  376.0  259.0 3957.0  239.0  436.0
    ##  [121]  258.0 3965.0  607.0  473.0  475.0  448.0 3975.0  617.0  322.0  285.0
    ##  [131] 3983.0  280.0  347.0  284.0 3991.0 1793.0  338.0  301.0 3999.0  641.0
    ##  [141]  283.0  453.0  311.0 4009.0 1019.0 1813.0 4015.0  360.0  523.0  469.0
    ##  [151]  327.0 4025.0 1827.0  372.0  335.0  636.0  339.0 4037.0  319.0  644.0
    ##  [161]  347.0 4045.0  687.0  353.0  814.0  357.0  530.0 1857.0  363.0  365.0
    ##  [171]  538.0 4188.0  971.0  373.0  351.0  676.0 4198.0  581.0  502.0  376.0
    ##  [181] 4083.0  368.0  591.0  993.0  731.0 4093.0  375.0  572.0  394.0 4101.0
    ##  [191] 1903.0  448.0  411.0  469.0  714.0 4113.0  475.0  412.0  423.0  401.0
    ##  [201] 4123.0  629.0  442.0 4129.0  446.0  853.0  610.0 4137.0 1643.0  781.0
    ##  [211] 4143.0  428.0  451.0  509.0  626.0  481.0 4155.0  517.0  634.0 4161.0
    ##  [221]  443.0 4165.0  495.0  449.0  646.0  501.0 4175.0  465.0  459.0  604.0
    ##  [231]  606.0  489.0  482.0 4189.0 2586.0  536.0  499.0 4197.0 1378.0  561.0
    ##  [241]  843.0  493.0  567.0  744.0  634.0  517.0  855.0 3412.0 4219.0  564.0
    ##  [251]  583.0   49.0   64.0 3721.0  225.0  196.0 3721.0    9.0  324.0    1.0
    ##  [261]    9.0  121.0 2916.0 3721.0 1521.0  225.0 1521.0   81.0  196.0 3249.0
    ##  [271] 3721.0    1.0 3721.0  169.0    1.0    9.0   64.0   81.0  196.0   25.0
    ##  [281] 3721.0   49.0  441.0  196.0 3721.0 2116.0   81.0  169.0   25.0 3721.0
    ##  [291] 2116.0   81.0  169.0   25.0 3721.0 3721.0 1156.0  441.0  324.0  324.0
    ##  [301]   81.0    9.0    1.0  196.0   25.0 3721.0  729.0  196.0  196.0   81.0
    ##  [311]   25.0 3721.0  324.0   81.0  256.0  256.0   25.0   16.0 3721.0 1521.0
    ##  [321]   64.0   25.0 3721.0    9.0   25.0   81.0  144.0   81.0  196.0   49.0
    ##  [331] 3721.0  225.0   36.0   36.0 3721.0    1.0 3721.0    9.0   64.0  441.0
    ##  [341]  324.0    9.0   64.0 3721.0    1.0  196.0   16.0 3721.0  121.0   81.0
    ##  [351]  144.0  144.0   25.0   16.0 3721.0   25.0  484.0   25.0  324.0  625.0
    ##  [361]  225.0  196.0   25.0 3721.0   81.0  196.0  361.0   81.0   16.0   25.0
    ##  [371] 3721.0 2601.0  225.0  441.0 3721.0 1521.0  441.0  324.0  196.0 3721.0
    ##  [381]  225.0  196.0 3721.0 1521.0   64.0   25.0 3721.0 1521.0   25.0  144.0
    ##  [391]  144.0  625.0 3721.0    1.0  196.0   16.0 3721.0   25.0  484.0   25.0
    ##  [401]  324.0  625.0 3721.0  225.0 1521.0   64.0   25.0  324.0 3721.0  361.0
    ##  [411] 1521.0  225.0  324.0  625.0 3721.0   81.0  361.0 3721.0 1521.0   25.0
    ##  [421]  144.0  144.0   81.0  196.0 3249.0 3721.0  625.0  225.0  441.0 3721.0
    ##  [431]  361.0  225.0  169.0   25.0    4.0  225.0   16.0  625.0 3721.0   16.0
    ##  [441]   81.0   25.0   16.0 3721.0 2025.0   81.0  361.0 1521.0   25.0  324.0
    ##  [451] 3721.0  121.0   81.0  144.0  144.0   25.0   16.0 3721.0   64.0   25.0
    ##  [461]  324.0 3721.0    4.0    1.0    4.0   25.0   61.0   57.0    3.0    1.0
    ##  [471]   21.0   19.0    5.0   61.0   19.0    8.0    5.0   61.0    3.0   15.0
    ##  [481]   21.0   12.0    4.0   14.0   57.0   39.0   61.0    1.0    6.0    6.0
    ##  [491]   15.0   18.0    4.0   61.0   39.0   15.0   61.0    6.0    5.0    5.0
    ##  [501]    4.0   61.0    9.0   39.0   61.0   27.0   14.0    4.0   61.0   23.0
    ##  [511]    5.0   57.0   18.0    5.0   61.0   19.0    5.0   14.0    4.0  109.0
    ##  [521]  114.0  107.0  161.0  116.0  105.0  115.0   16.0   12.0    5.0   61.0
    ##  [531]   39.0   15.0   61.0   39.0    8.0    5.0   61.0   13.0   15.0   15.0
    ##  [541]   14.0   61.0   45.0    5.0   16.0   39.0    5.0   13.0    2.0    5.0
    ##  [551]   18.0   61.0   13.0   25.0   61.0    3.0   15.0   21.0   19.0    9.0
    ##  [561]   14.0   61.0   39.0   18.0    9.0    5.0    4.0   61.0   18.0    5.0
    ##  [571]    5.0    6.0    5.0   18.0   61.0    6.0   15.0   18.0   61.0   39.0
    ##  [581]    8.0    5.0   61.0   22.0    5.0   18.0   25.0   61.0    6.0    9.0
    ##  [591]   18.0   19.0   39.0   61.0   39.0    9.0   13.0    5.0   61.0   40.0
    ##  [601]   15.0   23.0   61.0    8.0    5.0   57.0   19.0   61.0    4.0   15.0
    ##  [611]    9.0   14.0    7.0   61.0    8.0   15.0   18.0   19.0    5.0   63.0
    ##  [621]   61.0    9.0   39.0   57.0   19.0   61.0   36.0   21.0   14.0    5.0
    ##  [631]   61.0   46.0    9.0   13.0    5.0   61.0   46.0    9.0   13.0    5.0
    ##  [641]   61.0   61.0   35.0   39.0   57.0   19.0   61.0   19.0    9.0   12.0
    ##  [651]   12.0   25.0   54.0   61.0   14.0   15.0   56.0   61.0   49.0    8.0
    ##  [661]    5.0   14.0   61.0    1.0   61.0   18.0   15.0    3.0   11.0    5.0
    ##  [671]   39.0   61.0   19.0    8.0    9.0   16.0   61.0    5.0   24.0   16.0
    ##  [681]   12.0   15.0    4.0    5.0   19.0   61.0   27.0   14.0    4.0   61.0
    ##  [691]    5.0   22.0    5.0   18.0   25.0    2.0   15.0    4.0   25.0   61.0
    ##  [701]   19.0   39.0    9.0   12.0   12.0   61.0   23.0    1.0   14.0   39.0
    ##  [711]   19.0   61.0   39.0   15.0   61.0    6.0   12.0   25.0   61.0   45.0
    ##  [721]   15.0   13.0    5.0   61.0   19.0    1.0   25.0   61.0    1.0   61.0
    ##  [731]   13.0    1.0   14.0   61.0    1.0    9.0   14.0   57.0   39.0   61.0
    ##  [741]    8.0    1.0   16.0   16.0   25.0   61.0   47.0   14.0   12.0    5.0
    ##  [751]   19.0   19.0   61.0    0.5   30.5    6.5    0.5    7.0   30.5   19.5
    ##  [761]    9.0   10.5    6.0   12.5   30.5    2.0    4.5    2.5    9.5   30.5
    ##  [771]   20.5    4.0   27.0   30.5   11.5    4.0   12.5   28.0   30.5   23.0
    ##  [781]    4.5    6.5    2.5   30.5   23.0    4.5    6.5    2.5   30.5   30.5
    ##  [791]   14.0    0.5    1.0   12.5   30.5    6.5    0.5    5.5    2.5   30.5
    ##  [801]    0.5   30.5    9.5    8.0    2.5    2.5    1.5    4.0   27.0   30.5
    ##  [811]    9.5   19.5    0.5    9.0   30.5   11.5    0.5    9.0    9.5   30.5
    ##  [821]    3.0    6.0   12.5   30.5   20.0    2.5    4.5    3.5    4.0    1.0
    ##  [831]    7.5    9.0    9.5   30.5    5.0   10.5    9.5   19.5   30.5    9.5
    ##  [841]    4.0    4.5    7.0    2.5   30.5    4.5   19.5   30.5    7.5    7.0
    ##  [851]   30.5   14.0   10.5   19.5   30.5    4.5    3.0   30.5    0.5   30.5
    ##  [861]    7.0    4.5    3.5    4.0   19.5   30.5    3.0    0.5    6.0    6.0
    ##  [871]    9.5   30.5    0.5    7.0    2.0   30.5    0.5   30.5    1.0    7.5
    ##  [881]    6.5    1.0   30.5    3.0    0.5    6.0    6.0    9.5   30.5   24.5
    ##  [891]    4.5    6.0    6.0   30.5    0.5    7.0   12.5    1.0    7.5    2.0
    ##  [901]   12.5   30.5    9.5    2.5    2.5   30.5   19.5    4.0    2.5   30.5
    ##  [911]    2.0    0.5   11.5    7.0   30.5   23.0    4.5    6.5    2.5   30.5
    ##  [921]   23.0    4.5    6.5    2.5   30.5   30.5   17.5    9.5   30.5    4.5
    ##  [931]   19.5   30.5    9.5    4.5    6.0    6.0   12.5   27.0   30.5    7.0
    ##  [941]    7.5   28.0   30.5   24.5    4.0    2.5    7.0   30.5    0.5   30.5
    ##  [951]    9.0    7.5    1.5    5.5    2.5   19.5   30.5    1.0    6.0    7.5
    ##  [961]   11.5    9.5   30.5   10.5    8.0   30.5   13.5    7.0    2.0   30.5
    ##  [971]    2.5   11.0    2.5    9.0   12.5    1.0    7.5    2.0   12.5   30.5
    ##  [981]    9.5   19.5    4.5    6.0    6.0   30.5   11.5    0.5    7.0   19.5
    ##  [991]    9.5   30.5   19.5    7.5   30.5    3.0    6.0   12.5   30.5   22.5
    ## [1001]    7.5    6.5    2.5   30.5    9.5    0.5   12.5   30.5    6.5    0.5
    ## [1011]    7.0   30.5    0.5    4.5    7.0   28.5   19.5   30.5    4.0    0.5
    ## [1021]    8.0    8.0   12.5   27.0   30.5   19.5    9.0   10.5    6.0   12.5
    ## [1031]   30.5   23.5    7.0   19.5    4.5    6.0   30.5    0.5   30.5    6.5
    ## [1041]    0.5    7.0   30.5   19.5    9.0   10.5    6.0   12.5   30.5    2.0
    ## [1051]    4.5    2.5    9.5   30.5   20.5    4.0   27.0   30.5   11.5    4.0
    ## [1061]   12.5   28.0   30.5   20.5    4.0   27.0   30.5   11.5    4.0   12.5
    ## [1071]   28.0   30.5   22.5    4.5    3.5    7.0   30.5    7.5   28.5   30.5
    ## [1081]   19.5    4.0    2.5   30.5   23.0    4.5    6.5    2.5    9.5   30.5
    ## [1091]   23.0    4.5    6.5    2.5   30.5   23.0    4.5    6.5    2.5   30.5
    ## [1101]   30.5   22.5    4.5    3.5    7.0   30.5    7.5   28.5   30.5   19.5
    ## [1111]    4.0    2.5   30.5   19.5    4.5    6.5    2.5    9.5   30.5    6.5
    ## [1121]    2.5    9.5    9.5   30.5   11.5    4.5   19.5    4.0   30.5   12.5
    ## [1131]    7.5   10.5    9.0   30.5    6.5    4.5    7.0    2.0   30.5   17.0
    ## [1141]   10.5    9.0    9.0   12.5   30.5    1.0    2.5    3.0    7.5    9.0
    ## [1151]    2.5   30.5    4.5   19.5   28.5    9.5   30.5   19.5    7.5    7.5
    ## [1161]   30.5    6.0    0.5   19.5    2.5   30.5   19.0    2.5   19.5   28.5
    ## [1171]    9.5   30.5    3.0    0.5    6.0    6.0   30.5    4.5    7.0   30.5
    ## [1181]    6.0    7.5   11.0    2.5   27.0   30.5    3.5    2.5   19.5   30.5
    ## [1191]    6.5    0.5    9.0    9.0    4.5    2.5    2.0   27.0   30.5    4.0
    ## [1201]    0.5   11.0    2.5   30.5    0.5   30.5    1.0    0.5    1.0   12.5
    ## [1211]   30.5   24.5    2.5   28.5    6.0    6.0   30.5    1.5    0.5    6.0
    ## [1221]    6.0   30.5    4.0    4.5    6.5   30.5   20.0    0.5   19.5    2.5
    ## [1231]   27.0   30.5    4.5    3.0   30.5    4.5   19.5   28.5    9.5   30.5
    ## [1241]    0.5   30.5    1.0    7.5   12.5   30.5   23.0    4.5    6.5    2.5
    ## [1251]   30.5   23.0    4.5    6.5    2.5

**HQ UPDATE:** Headquarters has informed you that at this stage of
decoding, there should be 496 numbers in the secret message that are
below 17.

5.  Turn your vector of numbers into a matrix with 5 columns.
6.  Separately from your top secret numbers, create a vector of all the
    even numbers between 1 and 502. Name it “`evens`”. That is, `evens`
    should be an R object that contain the values 2, 4, 6, 8, …, 502.
7.  Subtract the “evens” vector from the first column of your secret
    message matrix.
8.  Subtract 100 from all numbers 18-24th rows of the 3rd column.
9.  Multiply all numbers in the 4th and 5th column by 2.
10. Turn your matrix back into a vector.

``` r
#Step 5
```

**HQ UPDATE:** Headquarters has informed you that at this stage of
decoding, all numbers in indices 500 and beyond are below 100.

11. Take the square root of all numbers in indices 38 to 465.
12. Round all numbers to the nearest whole number.
13. Replace all instances of the number 39 with 20.

**HQ UPDATE:** Headquarters has informed you that your final message
should have 421 even numbers.

![](README-img/noun_pause.png) **Planned Pause Point**: If things made
sense, feel free to continue on while you wait. Otherwise, contact your
instructor to have them verify your work.

## The secret message!

Use your final vector of numbers as indices for `my_symbols` to discover
the final message, by running the following code:

``` r
stringr::str_c(my_symbols$Symbol[top_secret], collapse = "")
```

    ## [1] NA

Google the first line of this message, if you do not recognize it, to
see what it is.

**delete this line and comment on what on the activity as a whole**

Comment on what you noticed about the activity as a whole.

**Response**:

Push your updated report to your `<username>` branch - you are done with
this `.Rmd` file and can go back to the README directions while you wait
for you Team Members.

## Attribution

This activity is based on a lab from [Dr. Kelly
Bodwin](https://www.kelly-bodwin.com/)’s Stat 331 course
