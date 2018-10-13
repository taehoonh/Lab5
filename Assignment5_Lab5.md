Assignment Five for Lab5
================
Taehoon Ha
10/12/2018

-   [Question 1.](#question-1.)
-   [Question 2.](#question-2.)

### Question 1.

Modify your function from the Problem 2 (Lab5 Activity). The function should simulate N rounds of the game (instead of just one) and return the proportion of times you win the bet. Run the function with *N* = 1, 000 and *N* = 10, 000.

``` r
gambling <- function(N){
    vec <- c()
    for (i in 1:N) {
        bet <- replicate(4, sample(1:6, 1, replace = T))
        result <- sum(bet == 4) >= 1
        vec[i] <- ifelse(result, 1, 0)
    }
    return(sum(vec) / N)
}

gambling(N = 1000)
```

    ## [1] 0.516

``` r
gambling(N = 10000)
```

    ## [1] 0.5175

### Question 2.

Write a function that will find the smallest element of a given vector (built-in **`min()`** is not allowed). Your function should return the smallest element and index of the smallest element.

Ex. vector is (1, 4, 2, 0, 5), then the smallest element - 0 and index is 4.

``` r
find.min <- function(vec) {
    min.element <- vec[1]
    for (i in (seq_along(vec[-1]) + 1)) {
        if(vec[i] < min.element)
            min.element <- vec[i]
    }
    min.element
}

vec <- c(1, 4, 2, 0, 5)
find.min(vec)
```

    ## [1] 0