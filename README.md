
<!-- README.md is generated from README.Rmd. Please edit that file -->

# pcg2

There are several R packages that implement the preconditioned conjugate
gradients (pcg) method, but none of them allow for the passage of a
function handle in place of the matrix vector products A\*x. This
functionality is available in Matlab via the
[`pcg`](https://www.mathworks.com/help/matlab/ref/pcg.html) function and
in Python via the
[`scipy.sparse.linalg.cg`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.sparse.linalg.cg.html)
and
[`scipy.sparse.linalg.LinearOperator`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.sparse.linalg.LinearOperator.html)
functions. This package is a simple implementation of the pcg method
allowing the user to pass a function handle in place of the matrix
vector product A\*x.

Other pcg packages in R:

  - [pcg](https://cran.r-project.org/package=pcg)
  - [Rlinsolve](https://cran.r-project.org/package=Rlinsolve)
  - [cPCG](https://cran.r-project.org/package=cPCG)

## Installation

The **pcg2** package is currently only available from Github.

``` r
devtools::install_github("natbprice/pcg2")
```

## Example

``` r
A <- matrix(c(4, 1, 1, 3), nrow = 2)
b <- c(1, 2)
x0 <- c(2, 1)

Ax <- function(x) {
  A %*% x
}

M <- matrix(c(4, 0, 0, 3), nrow = nrow(A))

pcg(Ax, b, M, x0)
#> $x
#>            [,1]
#> [1,] 0.09090909
#> [2,] 0.63636364
#> 
#> $resid
#> [1] 2.220446e-16
#> 
#> $iter
#> [1] 3
```
